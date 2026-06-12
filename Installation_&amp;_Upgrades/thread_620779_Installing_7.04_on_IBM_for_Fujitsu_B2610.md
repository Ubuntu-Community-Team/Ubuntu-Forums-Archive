---
title: "Installing 7.04 on IBM for Fujitsu B2610"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by stareye on 2007-11-23
I have a Fujitsu B2610, and its install of WIndows XP got corrupted. As it does not have an optical drive, the only way to install a new OS on it is to take out the HDD and put it into another computer, then install the OS and put it back into the Fujitsu. I have an old IBM A20, and so am installing 7.04 on it. What I need to know is what specifications I need to use while installing it so that it will work on the Fujitsu.
Thanks for all help!

---

### Post by Sef on 2007-11-23
Read this:  [Ubuntu Minimum Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

> Desktop installation

Most people will want to install a desktop system such as Ubuntu or Kubuntu. A desktop system is typically used for personal computing tasks and has a graphical user interface.
Minimum requirements

    *

      300 MHz x86 processor
    *

      64 MB of system memory (RAM)
    *

      At least 2 GB of disk space (for full installation and swap space)
    *

      VGA graphics card capable of 640x480 resolution
    *

      CD-ROM drive

If your system has less than 192 MB of system memory, use the Alternate Installation CD.
Recommended minimum requirements

    *

      500 MHz x86 processor
    *

      192 MB of system memory (RAM)
    *

      8 GB of disk space
    *

      Graphics card capable of 1024x768 resolution
    *

      Sound card
    *

      A network or Internet connection

Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation. 

---

### Post by stareye on 2007-11-23
> **Sef said:**
> Read this:  [Ubuntu Minimum Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
Gee, thanks? I'm not quite sure if you were just trying to be a jerk, or you thought it would be funny to shove simple facts that don't help much in my face. 
Thank you, no, I don't know what minimum requirements mean. No, I wasn't asking for you to detail to me what my computer needs, I know, it's tough for a small brain to comprehend this. Actually, what I was asking was if there was a way to do it without a cd drive. A simple, it really won't work, would've sufficed. 
Thanks again, and I'm glad you took your time to be piss off a forum user in your spare time!

---

### Post by col.panic on 2008-03-08
I did the same thing with my b2610

Essentially Do the install as normal on the IBM then put the hard drive back into the laptop.  Depending on the configuration of the ibm you may need to mess around with the Grub bootloader to point it at the laptop drive once you put it back in the laptop.  The X-server will also probably crash because the b2610 has a different hardware setup than the IBM.  to remedy this run:

```
sudo dpkg-reconfigure xserver-xorg
```

This will run you through a hardware setup.  Everything should work after this.  Also check out xubuntu because the overhead of gnome is a lot on this machine

---

