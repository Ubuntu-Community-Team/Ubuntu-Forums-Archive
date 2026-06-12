---
title: "Update R version running on ubuntu"
date: 2024-12-05
forum: Installation &amp; Upgrades
---

### Post by amiraple on 2024-12-05
Hello!

I currently use ubuntu as a linux subsystem on my windows machine. 

I run a conda environment (qiime2) which uses R. Recently, I realized that one of the R packages used by qiime2 was built under a newer version compared to what I currently have:
```
Warning message:package ‘optparse’ was built under R version 4.2.3
R version 4.2.2 (2022-10-31)
```

I updated my R version based on the instructions here [HTML]https://gcore.com/learning/how-to-install-r-on-ubuntu/[/HTML]: 

But when I check the R --version it defaults back to the older version:
```
(qiime2-amplicon-2023.9) angelica@angelica_xps15:~/GQ_fastq/qiime_gq$ R --versionR version 4.2.2 (2022-10-31) -- "Innocent and Trusting"
Copyright (C) 2022 The R Foundation for Statistical Computing
Platform: x86_64-conda-linux-gnu (64-bit)
```

I had installed the new R version outside of the conda environment with no issue: 
```
(base) angelica@angelica_xps15:~/GQ_fastq/qiime_gq$ R --version
R version 4.4.2 (2024-10-31) -- "Pile of Leaves"
Copyright (C) 2024 The R Foundation for Statistical Computing
Platform: x86_64-pc-linux-gnu
```


Any advice on what to do? 

Best,
Angelica

---

