---
title: "Extracting ddrescue.tar.gz"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by Royalist on 2012-08-08
I have downloaded ddrescue-1.16.tar.gz and I am trying to extract it from  the 'Downloads directory to /media/Data/Downloads/ddrescue-unzipped.

I have ownership of that folder and full user rights to both locations and I am using either sudo or gksu 

e.g. gksu tar xzvf ddrescue-1.16.tar.gz /ddrescue-unzipped

I am sure that there is nothing wrong with the paths as I have been able to change directory into them both.

This is the latest result:
roy@roy-desktop:~$ cd /media/Data/Downloads
roy@roy-desktop:/media/Data/Downloads$  gksu tar xzvf ddrescue-1.16.tar.gz /ddrescue-unzippedtar: Exiting with  failure status due to previous errors
roy@roy-desktop:/media/Data/Downloads$ sudo tar xzvf ddrescue-1.16.tar.gz  ddrescue-unzipped
tar: ddrescue-unzipped: Not found in archive
tar: Exiting with failure status due to previous errors

Please can anybody help. I have been on this for over four hours. Many thanks :confused:

---

### Post by drmrgd on 2012-08-08
First in the command line, you should be using sudo, and not gksu.

Try running the tar command, but without specifying the output directory.  I think that's what's screwing it up:

```
sudo tar xzvf ddrescue-1.16.tar.gz
```

That should give you a new folder, which will probably be something like 'ddrescue-1.16/', which you can change with a 'mv' command if you like.

---

### Post by steeldriver on 2012-08-08
if you want to extract TO a different directory, the syntax is

```
tar x[v]zf archive.tar.gz **-C** dir
```iirc the syntax you're using (without the -C) just queries the archive for a file called 'ddrescue-unzipped'

---

