---
title: "Cannot install 14.04 alongside Windows 8.1"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by norgrove on 2014-09-30
There are a number of similar sounding topics but none of them seem to address my problem. I have been using 12.04 for some time but the PC was getting old and slow. So rather than upgrade to 14.04 on that machine I have a new machine. This machine has come with pre-installed Windows 8. I have an ISO image of 14.04 on DVD which I have used without problem to install alongside windows 7 on my Laptop. However, when trying to install on the new desktop the 'installation options' screen tells me that there are no operating systems installed and the option to install alongside is not available. It does run fine as a live boot from the DVD. I downloaded a new copy of the ISO file and made a new DVD but that has made no difference, I also upgraded the Windows from 8 to 8.1, also made no difference. So I seem to be in a dead end unless I let the installation overwrite the windows, which I don't want to do.
Thanks for any help.
Keith

---

### Post by ubfan1 on 2014-09-30
You should read:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
Did you turn off the Windows power option "fast startup", and things like raid? Did you shrink the Windows partition (from within Windows) and chkdsk on the smaller partition?  With free space on the disk, do you still not get the "beside" option?

---

### Post by norgrove on 2014-09-30
Thanks,
I had looked at your first link which just confused me more, the second one looks more useful and I'll go through it in detail in the next couple of days, work permitting.
It does seem to expect me to be able to do things within windows 8 which could be a problem as I have had it only two days. I have not touched any partitions as yet and have no idea how to do that within windows, sounds like a session with the help system. One of the pages I was looking at suggested using GParted and I have tried to make a Cd for that but it fails to boot so far.
Regards
Keith

---

### Post by oldfred on 2014-09-30
Best to use Windows own tools to shrink the Windows partition and immediately reboot. Do no use Windows to add partitions, it cannot create Linux partitions anyway.

You can use gparted for all new partitions and editing Linux partitions. Gparted is also in the Ubuntu live Desktop version. If one of the other flavors like Kubuntu it may not be included but can easily be added.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

ubfan1 links are two of the better ones, a few more if you want in the link in my signature.

---

### Post by cressrt2 on 2014-10-01
I had a similar issue that "oldfred" helped me with. I followed this link, which gives as step by step guide that includes screenshots as well. [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by norgrove on 2014-10-02
I have had a go following those instructions, all seemed to go reasonably well until the last bit about boot repair and fixing the boot loader, this has not worked as yet and I am not getting it to boot into ubuntu.
Had enough for today, will try again later.
Thanks for the help so far.
Keith

---

### Post by oldfred on 2014-10-02
What brand & model computer? Some require work arounds as the vendor has modified UEFI to only boot the Windows entry.

Best to also see details.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If Boot-Repair offers its work around of rename files say no for now. That renames the Windows file and it usually is better to rename others.

---

