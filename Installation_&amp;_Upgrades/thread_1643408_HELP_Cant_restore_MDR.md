---
title: "HELP Cant restore MDR"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by tacomanmcjab on 2010-12-11
Hello guys,  

I decided to uninstall ubuntu by booting into windows 7 via grub and deleting the ubuntu partition and extending the windows partiiton to take up its space.

Doing so I did not restore the mdr.  So when I rreboot my computer I am greeted with grub rescue.

I tried booting into a ubuntu live cd and entering

On the terminal: 

sudo apt-get install ms-sys 

then

ms-sys --mbr /dev/hdX 

unfotunatley I am greeted with:  "couldn't find package ms-sys"

What do I do guys D: I am quite lost, and really would like to use my windows.

---

### Post by wilee-nilee on 2010-12-11
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between. Personally it wouldn't hurt to post the script before running the command.

Here is a link for a W7 recovery disc and the instructions to it's use, see also the W7 forums link as well just run the one highlighted command.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by matt_symes on 2010-12-11
Hi

You can use Lilo as well to fix the MBR using the Live CD.

sudo apt-get install lilo[FONT=monospace]

[/FONT]sudo lilo -M /dev/sda mbr

(assuming sda)

As for ms-sys, read this

[https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349](https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349)

Kind regards

---

