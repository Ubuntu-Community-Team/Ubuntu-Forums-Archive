---
title: "Tar.gz installations"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by CommuneOfLoon on 2011-07-19
I've tried a number of times to figure out how to install tar.gz files. I keep running into a wall. My most recent attempt is the most promising (for me), but still no dice:

Utilizing tar -xjf, I'm getting:
    bzip2: (stdin) is not a bzip2 file
    tar: Child returned status 2
    tar: Exiting with failure status due to previous errors

Using tar -xfv, I'm getting:
    tar: v: Cannot open: No such file or directory
    tar: Error is not recoverable: exiting now
(using -xfv did however allow me to use the tab-autocomplete, where tabbing after -xjf did nothing)

Tried this with two different tar.gzs I have. Also tried just extracting with GUI Unrar, but using ./configure resulted in:
    bash: ./configure: No such file or directory

Any clue what's  going on here or a way to fix it? 

Thanks.

---

### Post by SeijiSensei on 2011-07-19
.tar.gz files are compressed using gzip.  Use "tar xzvf /path/to/file.tar.gz" to expand them and get a list of the files the archive contains.  The "z" represents gzip compression, and the "v" for verbose operation generates the list of files.

"j" applies to files compressed with bzip2.  They'll usually be called "file.tar.bz2".

---

### Post by aysiu on 2011-07-19
Kind of depends what it is. All we know from .tar.gz is that it's a compressed file. It could be source code. It could be a precompiled binary. It could be something else.

What's the file? What application are you trying to install?

---

### Post by raja.genupula on 2011-07-20
[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

---

### Post by CommuneOfLoon on 2011-07-25
Sorry it's taken me so long to reply.

> **SeijiSensei said:**
> .tar.gz files are compressed using gzip.   Use "tar xzvf /path/to/file.tar.gz" to expand them and get a list of the  files the archive contains.  The "z" represents gzip compression, and  the "v" for verbose operation generates the list of files.

"j" applies to files compressed with bzip2.  They'll usually be called "file.tar.bz2".

Thank you; I didn't realize each of the letters had a specific meaning.

> **aysiu said:**
> Kind of depends what it is. All we know from  .tar.gz is that it's a compressed file. It could be source code. It  could be a precompiled binary. It could be something else.

What's the file? What application are you trying to install?

How would somebody determine this information? I don't have a specific  tar.gz file in mind to install, I'm just trying to figure out how to do  it in the future. The above code readout is from an indie game I have as  a tar.gz.


> **raja.genupula said:**
> [http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

Thanks, useful resource.



As of right now, tar xzvf and tar zxf work to extract the folder, but when I ./configure from inside the folder, I get "no such file or directory". Do I need to specify a file to configure within the folder?

---

### Post by aysiu on 2011-07-25
I guess my point is that there isn't really an established procedure. Most of the time to install an application you'd just go to the Ubuntu Software Center (kind of like the AppStore or Android Market). Sometimes .tar.bz2 or .tar.gz files are source, and sometimes precompiled binaries, or installation scripts.

---

