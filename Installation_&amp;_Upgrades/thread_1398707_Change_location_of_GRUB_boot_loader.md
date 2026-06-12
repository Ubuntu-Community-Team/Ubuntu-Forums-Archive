---
title: "Change location of GRUB boot loader"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by dtm808 on 2010-02-04
Hello. I am new to ubuntu . i installed it on a external HDD. my primary OS is windows 7 on my 1 internal hard drive. After i installed ubuntu whenever i boot up my computer i have to have my external hdd plugged in and turned on or else i get "cannot find GRUB" then some rescue thing comes up where i can type stuff. i would just like to move the GRUB loader to my primary hard drive or at least recover my windows loader but have ubuntu on it. any help?

---

### Post by Sef on 2010-02-04
With the Live CD go into 'fix broken packages', there is an option to set the grub boot loader there.

---

### Post by stlsaint on 2010-02-04
If im following you correctly you have a laptop with windows installed and ubuntu on an external hdd. In what you are asking than you would just install Grub to the internal hdd but even if you do that you are still required to have that ext hdd plugged in to boot ubuntu. So moving Grub isnt going to change you having to have that hdd plugged in to run ubuntu.
Is this what you were asking about or are you wanting to do a dual boot of windows and ubuntu on the internal drive. 
p.s- To answer your question NO. You cannot have the windows bootloader and use that to boot into ubuntu.

---

### Post by dtm808 on 2010-02-05
Well what i want to do is just move the boot loader to to my internal HDD so i dont have to have my external plugged in everytime i boot i know i wont be able to boot linux without my external but i usually use windows 7 so i just dont want to have to turn on my external and connect it every single time i turn on the computer. thanks

---

### Post by darkod on 2010-02-05
> **dtm808 said:**
> Well what i want to do is just move the boot loader to to my internal HDD so i dont have to have my external plugged in everytime i boot i know i wont be able to boot linux without my external but i usually use windows 7 so i just dont want to have to turn on my external and connect it every single time i turn on the computer. thanks

I think it's the other way around. Grub2 is actually on your int hdd MBR but the grub configuration files are always in the ubuntu root partition. And since that's on your ext hdd, grub2 can't find its config files with the ext hdd disconnected and gives an error.

What you should do:
With the ext hdd connected, boot with ubuntu 9.10 cd, Try Ubuntu option into the live desktop. In terminal execute:
sudo fdisk -l

that will show you your partitions and drives. If you know to "read" the results, just keep reading and execute the commands. If you don't know what is what, post the results of fdisk here and wait for precise commands.

Under ASSUMPTION your int hdd is named /dev/sda, the following commands in terminal will write windows bootloader on it:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings. That will make your win7 boot from your int hdd. If the int hdd is NOT /dev/sda, if it is /dev/sdb for example, change the command accordingly.

Under ASSUMPTION the ubuntu root (linux) partition on your ext hdd is /dev/sdb5 for example, in terminal reinstall grub2 to the MBR of /dev/sdb:
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

That will install grub2 on the MBR of your ext hdd.

So.... If you boot from the int hdd, win7 will boot straight away. No ubuntu.
If you boot from the ext hdd, you get the grub menu where you can select ubuntu or windows.
Is that what you wanted?

---

### Post by presence1960 on 2010-02-05
> **darkod said:**
> I think it's the other way around. Grub2 is actually on your int hdd MBR but the grub configuration files are always in the ubuntu root partition. And since that's on your ext hdd, grub2 can't find its config files with the ext hdd disconnected and gives an error.

What you should do:
With the ext hdd connected, boot with ubuntu 9.10 cd, Try Ubuntu option into the live desktop. In terminal execute:
sudo fdisk -l

that will show you your partitions and drives. If you know to "read" the results, just keep reading and execute the commands. If you don't know what is what, post the results of fdisk here and wait for precise commands.

Under ASSUMPTION your int hdd is named /dev/sda, the following commands in terminal will write windows bootloader on it:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings. That will make your win7 boot from your int hdd. If the int hdd is NOT /dev/sda, if it is /dev/sdb for example, change the command accordingly.

Under ASSUMPTION the ubuntu root (linux) partition on your ext hdd is /dev/sdb5 for example, in terminal reinstall grub2 to the MBR of /dev/sdb:
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

That will install grub2 on the MBR of your ext hdd.

So.... If you boot from the int hdd, win7 will boot straight away. No ubuntu.
If you boot from the ext hdd, you get the grub menu where you can select ubuntu or windows.
Is that what you wanted?

+1 Darko!

Just make sure you change "sdb5" to the actual partition your ubuntu / is on.

---

### Post by plusunim on 2011-01-23
Should this procedure apply where a windows xp is involved?
 
In short I also have a similar problem. my idea was to install ubuntu on an external harddrive so as i can use this ext. hd on another pc, which got its booting sequence corrupted in some way, and maybe have the ability to access the files of a particular logical partition.
 
cheers
plusunim
 
ps: i used the following lines of code in terminal to make the ext.hd bootable (as per idea above)...but ended up with the usage of the ext.hd compulsory - 
 
#mount /dev/sdb1 /mnt
#mount --bind /dev /mnt/dev
#mount --bind /proc /mnt/proc
#chroot /mnt
#apt-get update 
#apt-get upgrade
#grub-install --recheck /dev/sdb
#update-grub2
 
The machine I'm using now is a dell laptop, the machine with the corrupted boot sequence is a pc; both winxp OS

---

### Post by OLar on 2011-03-22
I have a similar problem, but if I understand the posts correctly I want a somewhat different solution.
I have a pc with a built in disk and two exchangeable disks. On the internal disk I have Windows XP, and on one of the others I also have Windows XP, let's call this disk Exch1.
At boot I was asked to choose what to boot, Windows XP or "the other disk". No other disk needed to be installed as long as I didn't try to boot from it.

Occasionally I've been testing Ubuntu, but now I wanted to be more thorough and see if I can leave Windows and go with Ubuntu completely. (I will need Windows for printing, but that's another matter.)

I started out with installing Ubuntu 10.10 on a second exchangeable disk, let's call this Exch2.
It worked just fine. At boot I was asked to choose between Windows XP, "the other disk" or Ubuntu.
When choosing Ubuntu I was asked to choose from a few more alternatives. 
As before I could boot Windows without any other disk installed. And with any of the other two disks installed, I could boot from either of the three. The Ubuntu installation on Exch2 only used half of the disk, so I thought I'd try installing from CD and use the whole disk.
If I remember correctly Ubuntu seemed very keen on installing on my internal disk, but I persuaded it to install on Exch2, which worked fine.

However, Ubuntu has now thoroughly messed up also my boot choices.
The first list of choices I get now are the Ubuntu ones with Windows XP as fifth choice.
Choosing Windows XP I get the old list of choices, i.e. Windows XP, "the other disk" or Ubuntu.
The only one of them that works now is Windows XP.
Choosing "the other disk", which would be Exch1 doesn't work of course as the Ubuntu disk must be installed in the slot where I otherwise would insert Exch1.
Choosing Ubuntu (which is not needed of course) just gives a grub prompt.

What I want is to be able to boot from the internal disk without any other disk being installed, or from either of the two other disks. Return to the way it was when Ubuntu was installed with the Windows install program that is.

Is there a safe and reasonably simple way to do this without reinstalling Windows and Ubuntu?
I'm familiar with the concept of boot loaders, but I have no experience whatsoever of working with them.
I've not found any solution that is obvious to me, and although the posts in this thread seem to be about the same as my problem, it's not obvious to me that solutions here are what I'm looking for. (Or maybe I just need some more explaining :-))

It feels as if Ubuntu has installed some kind of boot loader on the internal disk, bypassing the original one and pointing to one on Exch2, where one of the choices points back to the original one on the internal disk.

---

### Post by oldfred on 2011-03-22
Welcome to the forums.

Yes, unless you specify where to install grub it defaults to the boot drive usually sda. If you install to sdb or sdc, you have to use manual install, specify partitions & then you also get to specify which drive's MBR to install grub to.

First you need to fix grub by installing grub to the MBR of the Ubuntu drive. Then you need to fix the MBR of the internal drive with lilo or the standard windows boot loader. 

All the instructions you need are in the above posts by darko. 

If you need more help or specific instrucitons post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by OLar on 2011-03-26
Thanks oldred, parts of it worked beautifully.
Running lilo restored the original behaviour for the two Windows disks.
And installing grub into sdb seems to have worked fine too. As far as I can interpret the bootinfo script it all looks great.
Now, as far as I can understand, all I need to do to be able to boot from the Ubuntu disk, is to figure out what to change in C:\boot.ini on the internal disk. It now reads
```
d [boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="External disk" /fastdetect 
C:\wubildr.mbr = "Ubuntu"
```Obviously I need to change the last line of this file for it to point to the external disk. Something like
```
D:\wubildr.mbr
```perhaps?

---

### Post by oldfred on 2011-03-26
I am a fan of grub2. Why not boot the Ubuntu drive and use it to boot into windows. If it does not show windows run this:

sudo update-grub

You posted to boot.ini entry for wubi which is a version of Ubuntu that runs from a file inside the Windows NTFS partition.
I have seen some users copy the grub boot sectors to mrb.bin and link to that. But I do not know how and find grub a lot easier to use.

---

### Post by OLar on 2011-03-30
It wasn't quite as easy. I now know I need to do something like create a link containing the first 512 bytes of the MBR. But it was solved in quite a different way. It seems my Ubuntu disk crashed. So I've installed Ubuntu on another disk using the install program for Windows.

---

