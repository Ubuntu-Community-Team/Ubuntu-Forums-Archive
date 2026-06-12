---
title: "Can't install 10.4 on a dell m4500 mobile workstation"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by cheshirekow on 2010-07-05
I have a brand new Dell m4500 workstation. Here are some hardware features:

Core i7-820 processor
4 GB RAM
256GB Solid state disk
NVidia quadro FX 1800M graphics card

When I try to run the 10.04 graphic installer (from a CD or from a USB stick built using pendrivelinux) I see all of the text information as it is loading (i.e. all the white text and dots and stuff) but then the screen just goes blank.

When I try to run the 10.04 alternative installer from a CD, I can install successfully, however when I boot into it, I get the same problem as the installer. I see a bunch of text as it's booting up, and then the screen goes blank. I figure this is a graphics driver issue, so I downloaded the NVidia drivers, and then tried to start the computer in "recovery mode" to get to a root shell and install the drivers. But after selecting "recovery mode", I again see a bunch of white text, and then I get a momentary (~0.5sec) view of the recovery menu (i.e. dpkg, root, netroot, xfix) or something like that. Then... surprise... the screen goes blank.

I tried both the 10.04 64bit and the 10.04 32bit versions with the same results. 

After installing 10.04, and after booting up with the blank screen, on a whim I entered my user name and password and happened to hear that familiar login sound... though the screen is still blank. I tried logging into the root shell from the "recovery mode" via memory (pressing down a whole bunch, and then up one), and then I tried to run the NVidia display driver installation by typing the installer name, and then by entering options based on notes I took when I ran the installer from 9.04... however since I can't see the screen there's no way to tell if that worked... and nothing has changed.

I'm currently running 9.04 which is working moderately well, with the exception that the SDCard reader and the network card don't work. I'm using a USB network device for now. I don't know enough about linux to know how to diagnose this problem, but this bug report looks like it might be related: [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/556856](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/556856)

Any help diagnosing the issue will be greatly appreciated.

---

### Post by DJonsson2008 on 2010-07-05
Have you tried booting with a live CD?

---

### Post by DJonsson2008 on 2010-07-05
I read the bug report you listed looks like a deep problem. Maybe try 9.10 on live CD for hopefully better network support, perhaps try Ubuntu Netbook Remix 9.10 10.04 on Live CD as well and see if there is any indication of better communication with your hardware. Just some suggestions.

---

### Post by cheshirekow on 2010-07-05
OK, I got it working... It did involve following the steps in the bug report. This is how I did it (including installing the NVIDIA drivers).

1. I installed 9.04 (Jaunty)
2. I used gparted to resize the Jaunty partition and make room for a 10.04 (lucid) parition
3. I used gparted to make a partition with the freespace
4. I followed the instructions in [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux), Alternate CD, procedure 2. I used 10.04 Amd86 image.
5. When given the option to install the grub boot loader to the MBR I said "no" and installed it instead to the lucid partition
6. I restarted into Jaunty (not Lucid)
7. I edited /boot/grub/menu.lst to add two lines for Lucid and Lucid recovery mode
8. I mounted the Lucid partition into /mnt/lucid
9. I followed the instructions at [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting) to turn off KernelModeSetting (in particular I used the following command: 

```

echo options nouveau modeset=0 > /mnt/lucid/etc/modprobe.d/nouveau-kms.conf

```

10. I downloaded the NVIDIA driver and copied it to /mnt/lucid/root/NVIDIA-Linux-x86_64-256.35.run
11. I rebooted into lucid recovery mode (this time the screen did not turn black)
12. I slected "root" 
13. I ran 

```

./NVIDIA-Linux-x86_64-256.35.run

```

14. I rebooted
```

shutdown -r now

```

And it now works. BTW, Lucid detects my network card just fine. Unfortunately, still not the SD card reader :(. If I reinstall in the future, I will probably modify the steps by using my Jaunty install cd as a live cd, and editing modprobe.d/nuveau-kms.conf from there.

P.S. NVIDIA, please, please, please open source your drivers!

---

### Post by boilerbots on 2010-07-20
I just got one of these laptops and ran into the same problem. I started with the 32 bit 10.04 live image. When it was starting up I hit Esc and on the main menu under the advanced options checked the "nomodeset" and installed.

That seems to work and is way easier!

---

### Post by cheshirekow on 2010-07-20
> **boilerbots said:**
> I just got one of these laptops and ran into the same problem. I started with the 32 bit 10.04 live image. When it was starting up I hit Esc and on the main menu under the advanced options checked the "nomodeset" and installed.

That seems to work and is way easier!

Good idea, though the image may have been updated. My disk had no options under "advanced options". The only option was "go back" (to the main menu).

---

### Post by davidfkane on 2010-07-21
I had the same problem with drivers on my Dell M4500.   I was able to easily solve this by plugging in an older desktop flat-screen monitor into the back of the M4500.  

I was able to see Ubuntu there and install the NVIDIA drivers with ease, by going to *System* > *Administration* > *Hardware Drivers*

Something like this: [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

Then everything worked perfectly after a reboot.

David Kane.

---

### Post by ydant on 2010-08-01
I had the same issue and solved it by using the SVGA plug on the laptop as well. Once the OS + nvidia driver was installed it seemed to be fine.

---

