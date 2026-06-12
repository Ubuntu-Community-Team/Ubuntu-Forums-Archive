---
title: "error: no such partition. Grub rescue&gt;"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by fede_duarte on 2011-10-21
Hi, here's what happened:
I tried to install ubuntu 11.10 yesterday on my school's netbook so i run ubuntu from a usb and started to install it. While installing i made a mistake selecting the empty partition (i found later that i was doing it right) so i got scared to uninstall windows and, without stopping the installation, i unplugged de usb and rebooted the netbook. Later, when i tried to run the netboook again and i got the message "error: no such partition. grub rescue>"
I tried solutions from other threads but no one solved the problem, thanks.

---

### Post by raja.genupula on 2011-10-21
install the Ubuntu now at what ever the partition you want gonna solve this .

have you tried this

[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting).

---

### Post by oldfred on 2011-10-21
If it is the schools computer you should not be installing in it. But you may be able to use the USB. Grub defaults its install to sda or usually the internal drive you you have to use manual install or Something else to install and be sure to install the grub2 boot loader to sdb or whatever device the external is.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you do not have a Windows repairCD. You can do this to get windows to boot from an Ubuntu liveCD or USB.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by Ifwill013 on 2011-12-15
I have the same problem. In my case
-installed windows first ubuntu second
-for some reason, erased windows partition via ubuntu
-reboot-hid ubuntu partition
-reboot, and the message came up

the stupid reason why i hid ubuntu partition is because i thought it'll make my windows installation cd detectable. Now, not only the cd not detected i also don't have anything to boot from. Well, i still haven't try live usb. I'll try it tomorrow. Anyway, any suggestion on what method should i use to create a bootable usb? I want it so it can boot on any computer. I have a 8gb flashdrive.
Thanks a bunch.

---

### Post by linuxadore on 2011-12-25
@raja.genupula
I've just done Boot Repair with SuperOS 11.04 Live CD.
Tnx a lot...Now, reboot...):P

---

### Post by Andrew_nuts on 2012-01-20
This solution has been solved here on this thread
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Grub can be installed Using Live CD just go through the link and you will find your answers:P

---

### Post by Ddic1 on 2012-08-14
I have the same error, except mine came about when I deleted one of my partitions (I had 3 different OS's, and deleted one that I did not use).  Now it says"error: no such partition. grub rescue>"  Help?

---

### Post by oldfred on 2012-08-14
@Ddic1

This thread is older, much better to start you own thread so we can investigate your issues. Did you try the reinstall of grub posted in the threads above?

Also now may like this.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by lemonoid on 2012-08-27
> **Ddic1 said:**
> I have the same error, except mine came about when I deleted one of my partitions (I had 3 different OS's, and deleted one that I did not use).  Now it says"error: no such partition. grub rescue>"  Help?

I know this was re-directed to a new thread, but I saw this was a week ago he posted this comment, and the EXACT same thing down to the nail just happened to me. I had three OS's, deleted my old OS, and now I'm getting the same screen with no such partition and grub rescue command prompt. My PC will not read a live USB, I have not yet tried the CD. I just wanted to post this to hopefully see if Ddic1 made a new thread and was able to find a solution.

---

