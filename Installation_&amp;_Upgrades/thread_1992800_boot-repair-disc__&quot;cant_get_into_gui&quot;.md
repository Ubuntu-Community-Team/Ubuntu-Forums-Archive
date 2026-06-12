---
title: "boot-repair-disc  &quot;cant get into gui&quot;"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by jd mack on 2012-05-31
Hello, I have recently installed windows xp  alongside my existing Lubuntu 11.10 and as expected can now only boot into windows. Having searched this forum about getting my Lubuntu to dual boot I have found a possible solution with "boot-repair-disc". After starting this program in my computer it goes through a bunch of text and then stop's and does nothing right before the gui is supposed to start. I have tried using the special boot parameters in the help section of the program but "no joy". I have tested the disc I made on another computer and it seems to work fine. The problem computer is and old Dell laptop latitude c600 Pentium3 -751.7mhz, memory 256k and the chip is Intel i440bx and I believe the graphics driver is ATI. Any help on how to get this program to function would be greatly appreciated.  Thanks  John.

---

### Post by oldfred on 2012-05-31
Welcome to the forums.

I think the boot repair is based on Ubuntu so it may not work with only 256MB or may take forever to load.

You should be able to just use terminal to repair grub2's boot loader.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root (or try above, if it does not work try the one below).:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by wilee-nilee on 2012-05-31
Boot a live Ubuntu cd and download the bootscript, extract the download to your desk top, and run the command.

Copy and paste all the text from the generated results.txt to a reply.

When you have all the text pasted highlight all of it and click on the # in the reply panel then submit reply.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

Do this if oldfred's repair does not work.

---

### Post by jd mack on 2012-06-02
Thank you both for your instant reply's. I have tried oldfreds instructions using a "puppy" live cd and was able to install grub to sda5 but after that all commands came back with "command not found". As I am not a "computer guy" and really don't know what I am doing with the terminal commands I will continue to do some more research on my own and if that fails will just re-install lubuntu again. Thank you both for your assistance.  John

---

### Post by wilee-nilee on 2012-06-02
> **jd mack said:**
> Thank you both for your instant reply's. I have tried oldfreds instructions using a "puppy" live cd and was able to install grub to sda5 but after that all commands came back with "command not found". As I am not a "computer guy" and really don't know what I am doing with the terminal commands I will continue to do some more research on my own and if that fails will just re-install lubuntu again. Thank you both for your assistance.  John

Post the bootscript that will help us to debug your set up.

That command that you ran needs to be run from a ubuntu/lubuntu cd/usb flash of a equal to the installs (11.10) release booted to the live desktop.

honestly though with that low a ram even lubuntu will be chunky.

I would run the puppy on it, it will fly.

---

### Post by jd mack on 2012-06-02
wilee-nilee Thanks for the reply, I tried running a live ubuntu cd a while ago and it just stalls, that is why I used the Puppy cd for oldfreds help and is also the reason I can't get you the boot-script. Is there a Ubuntu live cd  version that you think might work with my low ram unit? Lubuntu 11.10 works great on this machine as does Knoppix. I will see what I can do to get a live cd to work.    Thanks again for your help.   John

---

### Post by wilee-nilee on 2012-06-02
> **jd mack said:**
> wilee-nilee Thanks for the reply, I tried running a live ubuntu cd a while ago and it just stalls, that is why I used the Puppy cd for oldfreds help and is also the reason I can't get you the boot-script. Is there a Ubuntu live cd  version that you think might work with my low ram unit? Lubuntu 11.10 works great on this machine as does Knoppix. I will see what I can do to get a live cd to work.    Thanks again for your help.   John

You could try the mini cd for Ubuntu and install a really light desktop like open box maybe, it is a net install.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This is just a install idea.

---

### Post by jd mack on 2012-06-03
wilee-nilee, Thanks for your help, and sticking with me on this issue. Not wanting  to waste anymore of your time I took the easy way out and just re-installed Lububtu and all is fine now.  I do have one more question;  is there any easy way to now backup/copy the MBR and save it to a disc and then re-install it if I need to at a later date?  Thanks again for your help.

---

### Post by oldfred on 2012-06-03
The commands I gave in Post #2 should work from your Lubuntu liveCD to reinstall grub2's boot loader to the MBR.

You can use dd to backup the MBR but dd is very low level and powerful also know as Data Destroyer. Since any typo in using dd causes major corruption, I do not suggest using that method. If you really want it, repost to confirm & I will post it. ( I do not use dd to backup MBR as I can reinstall from liveCD or USB easily).

---

### Post by jd mack on 2012-06-03
Oldfred, Thank you for your help. I have this thread bookmarked and am sure I be referring back to your instructions often. I WILL NOT be using the dd method  as I am just a recent linux junkie and have no confidence in my abilities (particularly at the command line)except for burning iso discs and installing different distro's. Thanks again for your detailed instructions.   John

---

