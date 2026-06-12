---
title: "how to install des-tse des-perf"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by zagagyan on 2012-04-15
Hi all, i am new on ubunto, I dont know hot to install i software that i have downloaded from this URL..

[http://www1.cs.columbia.edu/~nowick/asynctools/des/]("http://www1.cs.columbia.edu/%7Enowick/asynctools/des/")
for downloading, you need to enter any email or name.. just type anything you want..

I have unpacked the tgs file, and dont know the rest..
could anyone help me please??
I have been trying for 2 hours.. need help.
thanks for helping

---

### Post by zagagyan on 2012-04-16
anyone?

---

### Post by rpupa on 2012-04-16
Is it a linux version of software or windows. The software providers must have provided some information about how to install the software , or how to use it .........try searching the website

---

### Post by zagagyan on 2012-04-16
in the readme file, it says that i have copied below..: (and what is PATH variable in your Linux environment??)




INSTALLING The DES Analyzer
-----------------------------------------------------------------------------
There are two methods to install the DES Analyzer.

  Method #1. No PATH Set-up
  
    In this method, the PATH variable in your Linux environment is not 
    updated. To run des-tse or des-perf, you must specify the path to 
    the binaries.

  Method #2. Add des-tse and des-perf to your PATH 

    Once you have unpacked the .tgz package for the DES Analyzer,
    you will have a directory structure with a 'bin' subdirectory
    which contains the des-tse and des-perf executables. Add 'bin' to
    the PATH variable of your Linux environment.

    In particular, if you opened the .tgz file in your directory XXXXX,
    then add XXXXX/bin to PATH:

         => for example (when bash shell is used),

            # export PATH=$PATH:XXXXX/bin

        You should then be able to call des-tse and des-perf from any
        directory.

    *** NOTE: ***

    Alternatively, you may want to move the des-tse and des-perf
    binaries to a different directory, for example, a 'shared' location
    such as "/usr/local/bin". To do so, move des-tse and des-perf to the
    shared location (/usr/local/bin). Then set the PATH environment
    variable appropriately, if it is not already set:

         => for example (when bash shell is used),

            # export PATH=$PATH:/usr/local/bin

---

### Post by zombifier25 on 2012-04-16
If I read correctly you received 2 executable files from the download correct? If so, make a directory in your home folder called bin, then copy those executables to that folder. Don't forget to mark them as executable first:
```
chmod +x /path/to/filename
```
Then run this in your terminal:
```
source .bashrc
```
After that, you will be able to run them directly as programs by entering their name (only your user can run it though). I could go into details about what the commands do, if you are interested.

---

### Post by zagagyan on 2012-04-16
I am in the directory from the terminal, i have guide the terminal to that place where the two files are..
the names of the files are des-tse and des-perf

I am in this directory from the terminal:
rtai@rtai-desktop:~/Dropbox/DES-analyzer-v0_1-linux/bin$ 

can i just type chmod +x des-tse

nothing happens..

---

### Post by zombifier25 on 2012-04-17
You marked them as executable.
Then, get back to your home directory, make a folder named bin and copy the files des-tse and des-perf to that folder.

---

