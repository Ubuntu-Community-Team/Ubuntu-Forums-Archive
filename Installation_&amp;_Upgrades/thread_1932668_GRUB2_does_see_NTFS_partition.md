---
title: "GRUB2 does see NTFS partition"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by skrahimi on 2012-02-27
Hello,
  I just installed Ubuntu 10.10 on the second partition of a hard drive that is about 100G. The first partition is a Windows XP (50G). I allowed Ubuntu to use the free space (the second 50G or so). Installation went smooth. Now, when I rebooted the system, grub2 does not show the NTFS partition. So, I cannot start my Windows system anymore. Doing a fdisk –l, shows the disk is 100G, the Linux partition 50G, the swap area and not the NTFS. The loader knows the partition is there but cannot allow booting from it. Did my MBR get corrupted during the installation of Grub? Any help is appreciated.
  Thanks. :(

---

### Post by raja.genupula on 2012-02-27
hi look at my signature for bootinfoscript and post the output of it . 

Give a try with reinstalling MBR of XP 
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

---

### Post by Miljet on 2012-02-27
If running sudo fdisk -l doesn't show any NTFS partition, I think it is possible that you selected the wrong partition during installation and installed Ubuntu over your Windows partition.

You can install GParted and run it to see what you have. Or post the output from sudo fdisk -l here so someone can look at it for you.

---

### Post by oldfred on 2012-02-28
May be best to run boot info script to see entire configuration.

One way to run it that can do some repairs:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.


The new git version has some fixes that make it better to run now.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

If you need instructions, the standard version has those:


Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by skrahimi on 2012-02-29
Hi,
Thank you very body for your input. After checking the fdisk -l output, I  realized that the cylinders allocated to Ubuntu server started from 1  and they did overlap what I know about my XP installation (which also  started from cylinder 1). As a result (and what Miljit has suspected) my NTFS partition was overwritten. I am going to reinstall the server and claim the entire disk since I did not need the NTFS on this machine anyway.
I marked the thread as SOLVED to close it.
Regards.:p

---

