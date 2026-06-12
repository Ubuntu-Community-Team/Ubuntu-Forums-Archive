---
title: "How to update cmake via putty?"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by pixartist2 on 2011-02-20
I'm trying to compile an application and I'm getting 
"WARNING: This project requires version 2.6 of CMake.  You are running version 2.4.7."

How can I update the cmake version (I'm a total newbie @ linux)

---

### Post by Old_Grey_Wolf on 2011-02-20
If you are using Ubuntu 9.10, 10.04, or 10.10, login to the computer using PuTTY. After logging in enter these commands ```
sudo apt-get update
sudo apt-get install cmake
```You will need to enter your password.

---

### Post by pixartist2 on 2011-02-20
hm this did not really help, it still says 
cmake version 2.4-patch 7
:(
how can I found out what version of ubuntu is running ?

---

### Post by Old_Grey_Wolf on 2011-02-20
While logged into Ubuntu type this command to find the version you have.
```
cat /etc/*release

```

---

### Post by pixartist2 on 2011-02-20
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.3 LTS"

:/

---

### Post by Old_Grey_Wolf on 2011-02-20
You can try to download cmake from [www.cmake.org](www.cmake.org) and install it that way.

---

### Post by pixartist2 on 2011-02-20
> **Old_Gray_Wolf said:**
> You can try to download cmake from [www.cmake.org](www.cmake.org) and install it that way.

well, I tried that, but the cmake command gave me an error, it said that bin/cmake couldn't be found, so I guess I made a mistake.

---

### Post by Old_Grey_Wolf on 2011-02-20
> **pixartist2 said:**
> well, I tried that, but the cmake command gave me an error, it said that bin/cmake couldn't be found, so I guess I made a mistake.

Did you download the .sh or one of the .tar files?

Did the Ubuntu downloader extract the files for you?

If you try the tar.gz file the archive manager should offer to extract it for you.

Edit: and download it from the Binary distributions list.

---

### Post by pixartist2 on 2011-02-20
> **Old_Gray_Wolf said:**
> Did you download the .sh or one of the .tar files?

Did the Ubuntu downloader extract the files for you?

If you try the tar.gz file the archive manager should offer to extract it for you.

Edit: and download it from the Binary distributions list.

where should I install it ?

---

### Post by Old_Grey_Wolf on 2011-02-20
> **pixartist2 said:**
> where should I install it ?

If you download the .tar.gz file, the Archive Manager will install it in the right place for you. 

I don't remember if 8.04 automatically starts the archive manager, its been several years since I've used that version of Ubuntu.

---

### Post by pixartist2 on 2011-02-20
I downloaded the sh this time, what command should I use to install that? last time is used the archive and it did not work

edit: hmm


Using target directory: /home/cmake/cmake-2.8.4-Linux-i386
Extracting, please wait...

tar: Skipping to next header

gzip: stdin: invalid compressed data--format violated
tar: Error exit delayed from previous errors
Problem unpacking the cmake-2.8.4-Linux-i386


what exact command do i need to install from the tar ?

---

### Post by Old_Grey_Wolf on 2011-02-20
If nothing you have tried so far has worked, I would suggest upgrading to Ubuntu 10.04. At least the version of cmake in the 10.04 repositories is a newer version. 8.04 is over 2 1/2 years old, and is only going to be supported with patches for another 2 months.

If you choose to upgrade to 10.04 read my signature.

---

### Post by pixartist2 on 2011-02-20
I don't really know if I can upgrade my OS on a virtual rootserver ;(

---

### Post by Old_Grey_Wolf on 2011-02-20
> **pixartist2 said:**
> I don't really know if I can upgrade my OS on a virtual rootserver ;(

If it is your computer, then you should be able to upgrade.

Edit: I googled "rootserver" which is a term I was not familiar with. Differences in language I guess. So, you are using a hosting service for the VM. Surely they have newer VMs than 8.04.

One last try.

To untar a file from the terminal, cd to the directory where you saved it. It looks like you will need to ```
cd /home/cmake
``` If you downloaded the cmake-2.8.4-Linux-i386.tar.gz file, enter ```
tar -zxvf cmake-2.8.4-Linux-i386.tar.gz
```

If you stay in the /home/cmake directory or wherever you untared the file, then type cmake to see if it gives you the man page of instructions for using the cmake command.

---

