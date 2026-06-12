---
title: "grub problem - only minimal bash shows after fresh install alongside windows7"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by edison23 on 2014-09-26
[SIZE=3][COLOR=#ff0000]Before you start even reading this, check whether you have correct version of installation file. [/COLOR][COLOR=#ff0000][/COLOR][/SIZE][COLOR=#ff0000](I was trying to install 32bit version on 64bit computer, that was the whole problem. You can find that out by suffix after the file name - "i386" is 32bit, "amd64" is 64bit.)[/COLOR]

Hi, I'm pretty desperate so I'm hoping to get some advice here. I'll try to describe my situation as accurate as I can.

I have laptop Asus N56, windows 7 installed on one partition (ends somewhere no 95th GB on HDD), then around 8 GB partiton I long time ago created for some linux, unused up to today. Then data partition, then at the very end of HDD another free space, around 24 GB, where I wanted to have new Ubuntu 14.04 install.
Now, I've installed Ubuntu on that partition, it asked for a boot reserved partition, so I gave it to it on the end of that small 8 GB free space (made it around 100 MB big). I also put there swap. After install successfuly finished and I restarted, only minimal grub bash greeted me (sth like this: [http://members.iinet.net.au/~herman546/p15/fig2grub.gif](http://members.iinet.net.au/~herman546/p15/fig2grub.gif) ). So I tried installing Ubuntu as I always (on other computers) did before, ie. without the boot reserved partition... obviously didn't work either. So I did a bit of a research, tried Boot Repair program - it told me I have to use 64bit version, but since it's not in repos, I can't cause I dont have a CD with me to burn it on and I dont have a clue how to use it without it (I found only .iso image of it, cca 500 MB, strangely big). So I searched more, tried a lot of stuff until I finally found some reasonable chain of things to do to make this work (at least so I thought). I learned that the boot reserved partition should be within first 100 GB on the HDD, so I deleted all the linux partitions I had, restoring the original state, did a clean install, created somewhere on 96th GB in that 8 GB free space the BootPartition (again cca 100 MB), made root for instalation (also in the 8GB free space) and mounted as /home the 24 GB free space (now formatted as ext4). Same minimal bash greeted me again.
So I tried this [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) (worked without an error) - again, minimal bash after reboot; and then this: [http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293) and here I got stuck on **insmod loopback **- when I do **ls (hd[COLOR=Red]X,Y[/COLOR])/usr/lib/grub/i386-pc** I can see the loopback.mod there, but the insmod always returnes error on this and on **ntfs** too (file not found on both). Not on the other mod files.

I feel the whole thing has something to do with EFI, secure boot (which I found not in BIOS) and such stuff, but I'm pretty clueless here.

So, that's about it, do you have any idea, what should I do? Give up on Ubuntu? Commit suicide?

Thanks in advace.

---

### Post by oldfred on 2014-09-26
Is Windows installed in UEFI boot mode?
Windows only boots from gpt partitioned drives with UEFI and if Ubuntu needed a bios_grub partition you were installing in BIOS boot mode on a gpt partitioned drive.

And only Ubuntu 64 bit is compatible with UEFI. But that is the standard download from the Ubuntu site.

       Also how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it 
[http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

If you have it installed but not working, run the summary report from Boot-Repair and post link.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Before any UEFI reinstalls be sure to fully backup Windows. And do not do any auto installs, just something else or manual install. See link in signature below for more info.

---

### Post by yancek on 2014-09-26
Did you use GPT partitioning when you installed windows 7?  You can check this from the Ubuntu Live CD, open a terminal and run:  sudo fdisk -l(Lower Case Letter L in the command) and it will output a warning message along the lines of fdisk not recognizing GPT and to use GParted.  If you don't see that then you are using standard partitioning.  If you do see it you are using GPT.  I don't use GPT myself but from reading numerous posts here one apparently needs all systems using GPT or all systems using MBR.

You could also try from the Ubuntu downloading and running either the bootinfoscript or boot-repair script and posting the output so more details are available to those familiar with GPT.

---

### Post by edison23 on 2014-09-26
I think I am cardinal idiot... I do have GPT and I do have Windows running on UEFI, yet I somehow managed to have 32bit install file of Ubuntu. I'm now going to try installation with 64bit.

---

### Post by edison23 on 2014-09-26
Ok, **I am a total idiot. **It really was all about having wrong installation file for Ubuntu. So I spent virtually whole day solving a non-existent problem xD Anyway, thank you very much guys, if it wasn't for you, I might have never noticed.
Is there a way to make a official suggestion, that user should be notified in some way that the system is 64bit and installation file is 32bit (and vice versa)? I think it's quite essential, I don't believe I'm the only one being an idiot.
Well, end's good, all's good.

---

