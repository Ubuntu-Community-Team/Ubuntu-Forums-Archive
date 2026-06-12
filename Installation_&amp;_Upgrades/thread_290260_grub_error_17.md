---
title: "grub error 17??"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by dontknow on 2006-11-01
ok, to begin with i'm a total dweeb when it comes to linux. i'm really lost when it comes to all this so if someone could take me through this in layman's terms that would be super. 

anywho....
my laptop has 2 windows xp pr partition and had one linux partition with ubuntu on it. since i needed more space, i decided to use the linux parition to store windows stuff. I went into disk management and reallocated that partition to windows (while in windows xp). (it said it was logic partition??)

when i tried booting the laptop up today...grub error 17 appears and i'm totally panicking. (I have windows files on the laptop that i need to access.) 

(usually when i turn on the laptop it first has a screen where i scroll down to pick xp to boot .... the first choice (default) was set as ubuntu.)
  
what do i do? help!

---

### Post by confused57 on 2006-11-01
You need to restore the Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by dontknow on 2006-11-01
i was unable to find the .iso file when i extracted the super grub disk file. 

so i'm back to square one.

i got an xp pro recovery disk and got to the point where i typed in fixmbr and it asked if i wanted to go ahead but i chickened out because i was afraid i might never get back all my data files. 

i found my ubuntu install disk and was wondering how i can re-establish mbr file in the linux partition so i can properly expunge ubuntu and re allocate that partition to windows. 

right now i have some windows files in the (previously) linux partition that i have backups of....but the original windows partition has data and files and software that i can not lose. 

if i fixmbr with the xp pro disk will the files in the original windows partition be lost? how do i safeguard against this? 

could someone tell me?

---

### Post by confused57 on 2006-11-01
> **dontknow said:**
> i was unable to find the .iso file when i extracted the super grub disk file. 

so i'm back to square one.

i got an xp pro recovery disk and got to the point where i typed in fixmbr and it asked if i wanted to go ahead but i chickened out because i was afraid i might never get back all my data files. 

i found my ubuntu install disk and was wondering how i can re-establish mbr file in the linux partition so i can properly expunge ubuntu and re allocate that partition to windows. 

right now i have some windows files in the (previously) linux partition that i have backups of....but the original windows partition has data and files and software that i can not lose. 

if i fixmbr with the xp pro disk will the files in the original windows partition be lost? how do i safeguard against this? 

could someone tell me?
When you extract the downloaded SGD zip file, the iso is the only file that is contained in and extracted from the zip.  You'd need to use your cd burning program to burn it to cd "as an image", at a low speed(8x or less)...don't burn as a data or bootable cd.

You "should" be able to reinstall Ubuntu onto the partition(s) it was on and grub would be reinstalled to the mbr allowing you to boot Windows, you'd still need to find a way to restore the Windows mbr before deleting Ubuntu.

You can always recover data by mounting the Windows partition from the desktop live cd and copying files to a flashdrive or external USB:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

You probably wouldn't be able to copy software programs.  Try extracting the SGD iso again to the same folder with the zip file.

You can't restore the Windows mbr with a recovery cd, you have to  use a Windows installation cd or a boot floppy(or SGD) as described in the link I gave in my other reply.

---

### Post by dontknow on 2006-11-01
ok, i've looked on the extracted files from the super grub disk zip file and i see ALOT of little files. I'm still not sure how you get just one .iso file from extracting all this. 

in any case i'm gonna try to reinstall ubuntu in the hopes of restoring things so i can get to windows. 

what are some things i should pay particular attention to if i DON'T want to erase anything on the windows partition? 

how do i partition the hd so it uses what used to be the linux partition (which i switched over to windows more recently....therefore erasing/damaging the mbr)?

---

### Post by dontknow on 2006-11-01
in the extracted files i see boot file, rr_removed file , boot.cat file....there were also some readme documents as well.

---

### Post by dontknow on 2006-11-01
what i want to do is to restore ubuntu,

get access to windows again...back up the data,


then fiddle around with the mbr in windows/expunge ubuntu.

in the process i don't want to lose the files/data in windows partition. 


if i don't know anything about ubuntu and follow along (with prompts on the install...i'm hoping) will it reload on the old partition or should i be worried that the new install will write over windows partition data/files?

i reassigned the old linux partition so windows could access it now.

---

### Post by confused57 on 2006-11-01
> **dontknow said:**
> what i want to do is to restore ubuntu,

get access to windows again...back up the data,


then fiddle around with the mbr in windows/expunge ubuntu.

in the process i don't want to lose the files/data in windows partition. 


if i don't know anything about ubuntu and follow along (with prompts on the install...i'm hoping) will it reload on the old partition or should i be worried that the new install will write over windows partition data/files?

i reassigned the old linux partition so windows could access it now.
You could boot up the desktop live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".
Determine which partition is the one that you previously had Ubuntu installed on...here's an excellent guide to installing Ubuntu using the desktop cd:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
You'd need to select the "manual install" option and make sure you don't select to format any of your other partitions containing Windows OS or files.

I'm no expert and you might want to wait for someone more experienced that might have more specific advice.  The psychocats homepage has some excellent "howto's", planning partitions, mounting partitions, etc,  that you might want to read over that may help you.

---

### Post by dontknow on 2006-11-01
ok, i'll look over that website...thanks input.

---

### Post by dontknow on 2006-11-02
what's the url for downloading ubuntu livecd?

---

### Post by confused57 on 2006-11-02
> **dontknow said:**
> what's the url for downloading ubuntu livecd?
The Desktop cd is the live cd, but here's the download mirrors, just pick the one closest to you(or the fastest):
[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

The above link is just from the "download" section of the Ubuntu main website:
[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by dontknow on 2006-11-04
could someone give me a url with the super grub disk iso? i've been trying fruitlessly to extract sgd and when i do, i don't see the iso file. much thanks.

---

### Post by confused57 on 2006-11-04
> **dontknow said:**
> could someone give me a url with the super grub disk iso? i've been trying fruitlessly to extract sgd and when i do, i don't see the iso file. much thanks.
See the section "Where to get your Super Grub Disk":
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I use WinRar to extract the iso from the downloaded SGD bzip file.
Maybe you could download the free trial version of WinZip or WinRar  to extract the iso file...there's probably some free software for Windows to extract zip files.  SGD is only about a 500 kb download.

If you decide to reinstall Ubuntu, you can always use the gparted live cd(30 mb) to determine your current partition table and to delete or reformat the partition that you want to reinstall on:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

