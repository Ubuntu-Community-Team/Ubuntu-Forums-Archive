---
title: "dual boot won't boot"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by diracnafobia on 2007-12-25
Hi,

I installed feisty on my compaq presario v2000 as my only operating system. I recently decided I wanted to dual boot with windows xp. I used a gparted live cd to repartition my hard drive. After partitioning, ubuntu booted fine. I then installed windows xp professional on the blank partition of the hard drive. Windows installed fine and now it just boots to windows. The ubuntu partition still exists and still has data on it, but I can't figure out how to boot to ubuntu. Can anybody help me out?

---

### Post by meierfra on 2007-12-25
Click on FixGrub in my signature. If you need  additional help, boot from the Ubuntu LiveCD, open a terminal, (Applications->Accessories->Terminal), type

```
sudo fdisk -l
```
(l is a lower case L) and post the output.

---

### Post by diracnafobia on 2007-12-26
No dice. Same error. Here are the results of my fdisk -l.

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device                              Boot        Start        End        Blocks             Id      System
/dev/hda1                     1              2530      20322193+    7       HPFS/NTFS
/dev/hda2         *          2531        6992      35841015      83     Linux
/dev/hda3                     6993        7296      2441880        5       Extended
/dev/hda5                     6993        7296      2441880        82     Linux swap/ Solaris


I have been doing all this on a gparted live cd. Is that ok?

---

### Post by LaRoza on 2007-12-26
Reinstall grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by diracnafobia on 2007-12-26
This is exactly what I did. Did you not mean for me to click on that link? As far as I can tell this is what the first guy was suggesting. Am I missing something? Do I need to be using the ubuntu live cd and not gparted live, or just the grub prompt that it allows me to access?

---

### Post by LaRoza on 2007-12-26
> **diracnafobia said:**
> This is exactly what I did. Did you not mean for me to click on that link? As far as I can tell this is what the first guy was suggesting. Am I missing something? Do I need to be using the ubuntu live cd and not gparted live, or just the grub prompt that it allows me to access?

You used the Ubuntu Live CD to restore Grub? I think I missed something here....

What have you done so far?

---

### Post by diracnafobia on 2007-12-26
Ok, let me see if I can recap.

I have been able to get to  grub> two ways to do the whole, root () and setup () thing as per the link. One way is that I have a gparted live cd that lets me access a terminal:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

The other is that after I get the error 17 and the boot fails, it gives me the option to go to the grub> prompt. Does that clear it up? I'm in sort of unfamiliar waters.

---

### Post by LaRoza on 2007-12-26
> **diracnafobia said:**
> Ok, let me see if I can recap.

I have been able to get to  grub> two ways to do the whole, root () and setup () thing as per the link. One way is that I have a gparted live cd that lets me access a terminal:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

The other is that after I get the error 17 and the boot fails, it gives me the option to go to the grub> prompt. Does that clear it up? I'm in sort of unfamiliar waters.

Can you use the Ubuntu disk?

If all else fails, you can transfer all your files to the Windows partition and reinstall Ubuntu over the old installation.

---

### Post by diracnafobia on 2007-12-26
OK. I was hoping to not have to reinstall, and I don't have an install disk but i can make one. I will do that and try to reinstall grub.

---

### Post by meierfra on 2007-12-26
I assume that you did

root (hd0,1)
setup (hd0)

at the grub prompt. So you should be able to get to  the grub menu at boot-up (Press "ESC" during the count down).

This should get you into  ubuntu:

 At the grub menu at boot-up, select ubuntu. But do not press "enter". Press "e" instead. At the new screen, press "e" again. Change the line to "root (hd0,1)". Press "enter" and then "b". 

Hopefully  you will boot into ubuntu.

Open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Look for the line

#groot (hd0,0)

Change it do 

#groot (hd0,1)


You also need to add Windows to menu.lst:


Change

hiddenmenu to #hiddenmenu


You might also want to change "timeout 3"   to "timeout 10" to give yourself more time to select windows at the grub menu.

Add this to the end of the file:

title windows xp professional
root (hd0,0)
chainloader +1

Save the file.  In a terminal

```
sudo update-grub
```

Reboot and you should be able to boot into Ubuntu and Windows from the grub menu.

---

### Post by TrapMakeR on 2007-12-26
diracnafobia,

I would suggest you to post your /boot/grub/menu.lst. Or check this:

# Examples

# Directory /boot is a separate filesystem
#title datacore
#root (hd0,5) # /boot filesystem /dev/hda6
#kernel /kernel-2.6.16.27_003 root=/dev/hda5 # kernel on /boot and then / filesystem

# Directory /boot is on / filesystem
#title test
#root (hd0,16)
#kernel /boot/kernel-2.6-02 root=/dev/hda17

# This is for windows as an example
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

---

