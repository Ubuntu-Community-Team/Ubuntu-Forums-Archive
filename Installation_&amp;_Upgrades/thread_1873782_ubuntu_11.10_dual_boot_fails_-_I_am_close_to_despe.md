---
title: "ubuntu 11.10 dual boot fails - I am close to despertate"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by unclesam.xu on 2011-11-01
I have been using ubuntu for 4 years , now I am really in trouble and I don't have a clue on how to fix it.

I just assemble a mini-ITX pc. bought a SATA 1TB drive. no CD drive yet ( on back up order). My plan is install Win7 on primary partition 1, install ubuntu 11.10 ( first time install, I used from 7.04 to 10.10 till this installation).

I can only manage fully automatic installation successfully on ubuntu.And after reset, I can boot into ubuntu with no issue. BUT, If I choose advance install which means I partition the disk manually, say- where is "/", where is "/home", how big they are. after installation - restart , It will show "bootmgr is missing" and then stop there. The live USB runs ubuntu with no problem.It shows fully automatic installation will generate a FAT16 partition(every small in size, I forgot how big,and that partition shows the flag of "boot") ahead of ext4 partition and a swap partition.

I can install win 7 without any issue.

But, 

I want dual boot. there are something ubuntu can't do. But most of the things - I like ubuntu way more.

The nightmare of mine is, I can't make dual boot happen.

1) I did fully automatic installation ( choose install with win 7).
2) I did manual installation

the result are : grub 2 menu didn't show, boot into win 7 directly. 

3) I read this article which is a step by step instruction of install win 7 and ubuntu 11.10, put grub 2 to /boot partition, then use easyBCD to control boot process - which is really good idea:

[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/comment-page-4/#comments](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/comment-page-4/#comments)

the result is : after I choose ubuntu from easyBCD, the grub load with only like this:

grub>

I thought it was grub make the problem , then I googled and manaully reinstall grub from live USB ubuntu session. when I run sudo grub update, it only found win 7 as a grub 2 entry , it does even found ubuntu in hard drive. 

Anybody can help me?

I am still using old computer with win xp and ubuntu 10.10 . I rather do it right then say bye bye to ubuntu because I really like it.

PLEASE.

sam

---

### Post by oldfred on 2011-11-01
Post boot script. If system is real new, are you in BIOS or UEFI mode? Boot script does not parse UEFI's efi partition  to see if correct boot files are there.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"

---

