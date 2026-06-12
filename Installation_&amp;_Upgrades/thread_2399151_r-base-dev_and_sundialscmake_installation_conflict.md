---
title: "r-base-dev and sundials/cmake installation conflict - Please Help!!"
date: 2018-08-22
forum: Installation &amp; Upgrades
---

### Post by j.l.os on 2018-08-22
Hi all,

I just upgraded to U18.04, less out of choice, more because my previous OS (16.04) had an identity crisis and the fix suggested was to reinstall Ubuntu.  And perhaps unsurprisingly I'm having some teething issues.

I use the library sundials and and IDE which relies on cmake in numerical models written in C++ so these packages are essential!  But I also study the output of my simulations using R, so also essential!

Unfortunately when I try to install r-base-dev or r-base-core I get a warning regarding unmet dependencies that apparently can only be resolved by removing packages that are essential to my work!

The following is the prompt/output in a linux shell.  Note I use a partitioned Mac so don't be fooled by the username, this is Ubuntu 18.04

```


jack@jack-MacBookPro:~$ sudo aptitude install r-base-dev
The following NEW packages will be installed:
  cdbs{a} dh-translations{a} intltool{a} jq{a} libcurl3{ab} libjq1{a} liblzma-dev{a} libonig4{a} libreadline-dev{a} r-base-core{a} r-base-dev r-cran-boot{ab} r-cran-class{a} 
  r-cran-cluster{a} r-cran-codetools{ab} r-cran-foreign{a} r-cran-kernsmooth{a} r-cran-lattice{a} r-cran-mass{a} r-cran-matrix{a} r-cran-mgcv{a} r-cran-nlme{a} r-cran-nnet{a} 
  r-cran-rpart{a} r-cran-spatial{ab} r-cran-survival{a} r-doc-html{a} r-recommended{a} 
0 packages upgraded, 28 newly installed, 0 to remove and 10 not upgraded.
Need to get 15.9 MB/40.6 MB of archives. After unpacking 64.9 MB will be used.
The following packages have unmet dependencies:
 libcurl3 : Conflicts: libcurl4 but 7.58.0-2ubuntu3.2 is installed
 libcurl4 : Conflicts: libcurl3 but 7.58.0-2ubuntu2 is to be installed
 r-cran-boot : Depends: r-api-3.4 which is a virtual package, provided by:
                        - r-base-core (3.4.4-1ubuntu1), but 3.4.4-1xenial0 is to be installed

 r-cran-spatial : Depends: r-api-3.4 which is a virtual package, provided by:
                           - r-base-core (3.4.4-1ubuntu1), but 3.4.4-1xenial0 is to be installed

 r-cran-codetools : Depends: r-api-3.4 which is a virtual package, provided by:
                             - r-base-core (3.4.4-1ubuntu1), but 3.4.4-1xenial0 is to be installed

The following actions will resolve these dependencies:

     Remove the following packages:                                       
1)     cmake [3.10.2-1ubuntu2 (bionic, now)]                              
2)     libcurl4 [7.58.0-2ubuntu3.2 (bionic-security, bionic-updates, now)]
3)     libsundials-dev [2.7.0+dfsg-2build1 (bionic, now)]                 

     Keep the following packages at their current version:                
4)     r-cran-boot [Not Installed]                                        
5)     r-cran-codetools [Not Installed]                                   
6)     r-cran-spatial [Not Installed]                                     
7)     r-recommended [Not Installed]                                      

     Leave the following dependencies unresolved:                         
8)     r-base-core recommends r-recommended


Accept this solution? [Y/n/q/?] Y


```


Does anyone with a better understanding of the inner workings of the Linux OS than me have any advice as to how to resolve this conflict???


Thankyou!

Jack

---

### Post by steeldriver on 2018-08-22
Did you have a cran / rstudio PPA in your repositories in 16.04? You may need to remove that and re-add the appropriate bionic version(s)

---

### Post by j.l.os on 2018-08-22
Hi @steeldriver.  Thanks for the reply! I had to google PPAs but it seems I do have a cran.rstudio ppa on my machine, and you totally right, it's outdated!

```


jack@jack-MacBookPro:~$ apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 https://cran.rstudio.com/bin/linux/ubuntu xenial/ Packages
     release v=16.04,o=CRAN,a=xenial,n=xenial,l=CRAN,c=
     origin cran.rstudio.com


```

etc...


Other forum posts gave me this:

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:whatever/ppa

```

as a safe method for deleting PPAs, could you just let me know how to replace whatever/ppa in the above?  Presumably I'd be calling rstudio in some way but the list of PPAs at the top doesn't seem to explicitly name them.  Sorry if it's obvious, I'd rather avoid further messing around with software I use everyday!

---

### Post by steeldriver on 2018-08-23
I honestly don't know the right way to proceed here - I'm not sure whether it's r-cran packages or rstudio that's the problem

I'm not sure that a Bionic version of RStudio is available yet

---

