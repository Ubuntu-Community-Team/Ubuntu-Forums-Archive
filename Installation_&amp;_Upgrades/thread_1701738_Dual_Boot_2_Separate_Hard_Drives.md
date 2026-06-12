---
title: "Dual Boot 2 Separate Hard Drives"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by vezinadj on 2011-03-06
Hello,

I am kind of a newbie to all the file systems associated with linux so bear with me please.

Heres the outline:
I have 2 different hard drives in my laptop, a 500gb and a 320gb. I have my 500gb hard drive containing ubuntu 10.10.

My goal is to install a version of windows onto the 320gb hard drive. This is simple, its just when using "gparted" on linux, my 320gb hard drive shows 3 partitions already containing 2 linux file systems. There is the unallocated space (where i plan on installing windows) and dev/sdb5 Linux-Swap at 10.94gb and /dev/sdb2 extended at 10.94gb. 

These also show up on my primary hard drive (500gb). 

Now the issue is, if I take out my 320gb hard drive and just try to boot, I get hung up in the startup with a blinking hyphen like its trying to boot but it remains at the screen. BUT, when I put the 320gb drive in, it works as normal.

This leads me to think that some startup files are contain on the other drive? It must have happened during installation perhaps if that is possible. 

My first thoughts were it possibly is the grub boot loader, but like I said, I do not know much about it. If anyone could help would be great. I want to just reformat the 320gb drive but I dont want to remove any needed startup files for ubuntu. 

Thank you in advance!

---

### Post by drs305 on 2011-03-06
The MBR of your boot drive (320GB) probably points to your Linux files on the 500GB drive. To fix this, boot to the Ubuntu Desktop with both drives attached.

Open a terminal and run the following commands. First, determine the designation of the Ubuntu drive. I'm assuming it's going to be sdb1:
```
sudo fdisk -l
```
Look at the first line for each drive and find the 500GB drive. If it's sdb with filetype "Linux": partitions:
```
sudo grub-install /dev/sdb
```
That should point the Ubuntu drive's MBR to the Ubuntu boot files on the same drive.

Reboot and enter the BIOS setup. Change the first boot drive to the Ubuntu drive (look for the 500GB disk).

Now you should be able to boot without having the 320GB drive connected.

If you have problems, download the Boot Info Script from the following site. Run it and post the contents of RESULTS.txt, which will display the status of your boot files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Hakunka-Matata on 2011-03-06
Use the [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) courtesy of meierfra in my signature.  Download and execute according to the excellent instructions in the Link.  Post the results.

---

### Post by Hakunka-Matata on 2011-03-06
Sorry drs305, I thought he'd gone a long time without one of you guys getting in there to help him.

---

### Post by drs305 on 2011-03-06
> **Hakunka-Matata said:**
> Sorry drs305, I thought he'd gone a long time without one you guys getting in there to help him.

The more the merrier.  Anyone is welcome to help. Thanks.  :-)

---

### Post by vezinadj on 2011-03-06
Thank you very much for the replies everyone, fortunately the grub install command worked like a charm. I pointed it to sda and everything boots up fine with the 320gb drive disconnected. Thank you very much again, this saved a lot of time!

---

