---
title: "installing without a cdrom or usb option"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by svQuick on 2007-12-13
So here is  the test of logic.  Ia m sure that there is a solution.  I purchased four itronix ix250 laptops and someone failed to mention the lack of a CDROM drive, in fact they are the most proprietary cdrom cases that I have ever seen.  There is no usb bootable option in the bios and they do not see an external cdrom drive as a device in  the bios.  I tried pulling a loaded gutsy disk from one of my other laptops and tried to let the hardware muttle through but xorg issues kill it.  Can I install on a partition and reformat the disk form there?  How can I get this installed?

---

### Post by foolsh on 2007-12-13
is there a network adapter built in?
if so is there a boot from lan option in the bios?
if so boot from lan but you'll have to setup a lan server to do this.
I check around and see if what I can come up with.

---

### Post by svQuick on 2007-12-15
Thats the problem...I have boot options of A: (missing), D: and CDROM (missing) and thats it.  I tried to pull another harddisk out of another laptop loaded with 7.10 but the hardware detection fraks out on x.org.  I have been trying to install an iso to a disk, install it to a usb mounted hd and then pull the ISO disk out and install the the formated disk but I can't seem to get it to work.  


Thanks for your reply.

---

### Post by Pumalite on 2007-12-15
You can do netboot, but for that you need the Internet:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by mpince on 2007-12-15
--

---

### Post by Rhubarb on 2007-12-15
Use a laptop hard disk that already has ubuntu on it, put it into the troublesome notebook.
When you see an xorg error, press Ctrl + Alt + F2
Enter your username and password.
```
sudo dpkg-reconfigure xserver-xorg
```
Answer all the questions that come up on the screen, write the changes to disk.
Then to restart your laptop:
```
sudo shutdown -R now
```
When your laptop boots up, it should all be working now.

I've personally done this successfully with many CD-ROMless laptops and PCs before.
Let us know here if it works / doesn't work for you.

---

### Post by svQuick on 2007-12-24
yep...you the man.  Works great.

---

### Post by rykel on 2008-05-11
Hi,

I am trying to install Ubuntu Hardy. I have the Hardy ISO, internet access on a Windows XP partition, a ready-to-install Linux partition, NO CD-drive and laptop CANNOT boot from USB thumbdrive.

I believe that one way is to configure GRUB to boot the Ubuntu ISO from a separate partition but I do not have the exact details.

Any help? Thanks!!

---

### Post by ugm6hr on 2008-05-11
A few options for you to consider:
1. [http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)
Downside is you have to re-download everything.
2. [http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)
Downside is you need an existing Linux installation (or LiveCD/USB to use).

---

### Post by rykel on 2008-05-11
Hi,

I cannot use Gujin because I deleted enough files from my Linux partition to ensure that I can no longer access a GUI.   : P

As for UNetBootin, I installed it in Windows XP and it insists on installing Ubuntu to C: drive, instead of the Linux partition.

This results in a Ubuntu install that boots up alright BUT the GUI becomes a blue blank screen, which means I cannot do anything useful with it.

Any other help?

I am relatively familiar with the command line, so perhaps I can run UNetBootin and the ISO file from within the Linux commandline? If so, how?

Thanks for your help!!

---

