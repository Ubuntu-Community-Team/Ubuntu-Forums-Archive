---
title: "GRUB Error 17 - Partition Mess"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by fiestaforever on 2012-04-20
Hi, 

somehow I managed to mess things up when installing Xubuntu 11.10 on an old laptop that already has Windows 98 on it (and previously had an old version - 5.10? - of Xubuntu on it as well). 
On boot, I get the infamous "Error 17" after "GRUB loading stage 1.5".
I know that this somehow means that GRUB can't find the root/boot partition, but I don't know how to fix it.

This is how my partitions are set up: 

sda1 Windows FAT32
sda2 Extended Partition 
  sda5 Linux ext4
  sda6 Linux swap
  sda7 Windows Data FAT32
  sda8 Windows Data FAT16

Note that there is no sda3 or sda4. Why, I have no idea. (Maybe those are reserved for primary partitions?) Compared to the previous Xubuntu install, the installer decided to switch the positions of the Linux and Swap partitions. So /dev/sda5 would have to be it.

I found several hints how to fix GRUB, but they seem contraditory to me. 
Most refer to something like this: 
sudo grub
grub>root (hd0,0)
grub>setup (hd0)
grub>quit
I simply don't know how "sda5" translates to "hd0,x", given the extended partition and the strange numbering of partitions sda1-sda8. 

OTOH, I read somewhere that this procedure is for an old version of grub, so it might be wrong in the first place. 

Another thing I'm not sure about is whether maybe what I'm seeing might be remnants of the old GRUB install, not the new one. 

Thanks in advance 
Alex

---

### Post by oldfred on 2012-04-20
Your error message is from grub legacy, and Ubuntu's default has been grub2 since 9.10. You can install grub legacy or may have it if you upgraded from older installs. With grub version 1.99, you do need to use liveCd that is same version as install to repair.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Any of the four primary partitions can be the extended partition holding all of the logicals which always start at sda5. So with sda2 as the extended then you have logicals starting as sda5. You just have not used sda3 or 4 as primaries.

---

### Post by dino99 on 2012-04-20
boot on a livecd and:

sudo grub-install /dev/sda
sudo update-grub

note: actually grub2 (grub-pc) is used and can conflict with the old grub-legacy (grub1) with its menu.list (so needs to remove them first.

but to get something well installed, maybe its better to do a fresh install.

[http://ubuntuforums.org/showthread.php?t=1962097](http://ubuntuforums.org/showthread.php?t=1962097)

---

### Post by darkod on 2012-04-20
> **dino99 said:**
> boot on a livecd and:

sudo grub-install /dev/sda
sudo update-grub



Please make more effort and don't give wrong information.

You can't run grub-install without the --root-directory option from live mode. How will it know where is your root partition???

---

### Post by fiestaforever on 2012-04-20
Thank you for your answers. Do I understand correctly that both of you refer to installation of grub2? 

In the meantime, I read somewhere (in a somewhat confusing article, for me) that grub2 may need more space at the beginning of the disk (directly after the MBR, before the first partition) than legacy DOS/Windows partitioning may have. So I'm a little afraid to overwrite the beginning of the first partition. 

Would it be safer to use grub legacy?

Actually, I already tried the procedure I mentioned above, from the live CD. First, I was told to apt-get install grub, which I did (although I always thought installing programs from a live CD was impossible). Then, I tried "root (hd0,4)" and "setup (hd0)" when I got back: "Checking if "/boot/grub/stage1 exists ... no", "Checking if /grub/stage1 exists ... no", "Error 15: File not found"

---

### Post by darkod on 2012-04-20
The remark about grub2 mainly refers to disks with GPT partition table. You have MSDOS, because extended partitions don't exist in gpt.

So, it's fine. That is the default bootloader of 11.10 and it's best to use it.

The commands like root (), setup (), /boot/grub/stage... are for grub1.
And you don't need to apt-get install grub. That package is grub1 anyway, the package for grub2 is called grub-pc.

If you are sure /dev/sda5 is your linux partition, once you boot into live mode it takes literary only two short commands, like oldfred wrote:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```That should get it going. His second command is little different, with --boot-directory instead of --root-directory but the end result should be the same.

---

### Post by fiestaforever on 2012-04-20
Thanks, I managed to boot now, following the commands from oldfred. 

Unfortunately, now there is no boot menu anymore, and I can't access the existing Windows installation. 

BTW: This whole mess started when Xubuntu's installer failed to recognize the existing Windows installation, and from there I somehow lost my way.

Another problem I have is that display settings only allow 800x600, while the screen is 1024x768. 
This is an old Fujitsu Lifebook S4542 w/ Pentium III/600 and 250 MB RAM. 
Grapics is a Trident (?) card w/ 2.5 MB of RAM, so it should be able to run at 1024x768/24 bit color, if I'm not mistaken. At least it should do 1024x768/16 bit.

---

### Post by Hylas de Niall on 2012-04-20
Try the live CD of this:

[http://sourceforge.net/projects/boot-repair/files/](http://sourceforge.net/projects/boot-repair/files/)

Boot with the live CD, wait for the LXDE desktop to appear, notice the two options in the open app window, click the top (recommended) one and Grub is all better! (I just used it myself!)

HTH

---

### Post by darkod on 2012-04-20
If windows fails to be recognized correctly, it is normal that it doesn't create entry for it. It can't see it, so no entry.

You would have to troubleshoot what happened with windows.

You can run the boot info script from the link in my signature that will show more details.

---

### Post by fiestaforever on 2012-04-20
Hylas de Niall, Darko, 
thanks, but I decided to get rid of grub2 and reverted to grub legacy [as per these instructions]("http://ubuntuforums.org/showthread.php?t=1298932"), and then just edited menu.lst as per [my first encounter with a similar problem six years ago]("http://ubuntuforums.org/showthread.php?t=117149"). 

But I still have lots of problems, and am getting increasingly tired of searching and fiddling. Especially the display issue is driving me nuts. All of this is kind of déjà vu. Every now and then I take a try on Linux, and every time it turns into a frustratingly crappy experience... 
Xubuntu 11.10 is dog-slow on this machine, btw. 5.10 was completely different, but that was years ago. 

:(

---

### Post by darkod on 2012-04-21
If the spec is too weak, maybe Lubuntu will work better. It needs less resources than Xubuntu and Ubuntu as far as I know.

Also, if seeing issues and don't mind using the same version for years, try to stick with LTS releases (long term supported). They have best compatibility.

Not sure how often does Lubuntu and Xubuntu release LTS, Ubuntu currently does it every 2yrs.

---

