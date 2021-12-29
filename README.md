# LiMACC
LiMACC is an framework of calling significant interactions from multiple types of chromosome conformation capture assays, including Capture-C, Capture-HiC and HiChIP experiments.
It's implemented through a R package *limacc*.


## Install from Github 
```
library(devtools)
install_github("wbaopaul/limacc")
```

## Install from source codes

* Download source codes [here](https://www.dropbox.com/s/vwelb99sd5nr3gk/limacc_1.0.tar.gz?dl=0) 
and In R type:
 
```
install.packages('path to limacc_1.0.tar.gz', type = 'source', rep = NULL)
```

## Note
* The latest *limacc* needs R version 3.5.1 or later

## Required Inputs
* *fragment_file* A bed file (or in similar format) indicates the genomic coordinates of either the restriction enzyme fragments for Capture-C, Capture-HiC, or the binned fragments, in 5kb for instance, for HiChIP data.  
  - for Capture-C or Capture-HiC data, an example of *fragment_file (chromosome start end fragment_id)* to indicate the genomic location of the HindIII enzyme fragment :

  ```
  chr1	0	3002504	chr1_1
  chr1	3002504	3005876	chr1_2
  chr1	3005876	3006265	chr1_3
  ......
  ```
  - An example of *fragment_file (chromosome start end fragment_id)* in 5kb resolution for HiChIP is given similarly:

  ```
  chr1	0	5000	1
  chr1	5000	10000	2
  chr1	15000	20000	3
  ......
  ```
  **Note that the fourth column *fragment_id* could be any user specified character**
  
* *contact_file* contact matrix file, a three column file with columns (*bin_i bin_j count*):

  ```
  chr1_10	chr1_11	2
  chr1_10	chr1_15	4
  chr1_15	chr1_20	5
  ......
  ```
  **Note that the first two columns in the *contact_file* should be included in the fourth column of the *fragment_file*.**

* *dtype* data type, 'CHiC', 'CC' or 'HiChIP'
* *peakFile4HiChIP* Bed file of 1D peak as virtual viewpoints for HiChIP, set as NULL when dtype is not 'HiChIP'

## Output
  * A data frame providing the significant interactions
  * The significant interactions were also saved in a file with user specificed file name


## Help in R

```
library(limacc)
help(limacc)

```

## Alternative run through bash command line (for Linux and macOS)

* copy scripts *limacc4command* and *limacc_withArgs.R* in this reporitory to the same directory, for example, current directory, then

  ```
  ./limacc4command -f your_fragment_file -c your_contact_file1,file2 -t CHiC 
  ```
* for more help, see
  ```
  ./limacc4command --help
  ```



## Reference
The detailed information of LiMACC algorithm is described in the following paper:




