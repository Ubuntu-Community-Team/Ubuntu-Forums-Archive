---
title: "Blank Screen with 7.10 Install"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by rwnz on 2007-10-24
I've been installing 7.10 on my Toshiba laptop but the process stops after some time with just a blank screen and flashing cursor being displayed. It may be a graphic driver issue as I've seen mention on other posts of this causing problems (especially on laptops) and the installation progress window, titled 'Select and Install Software' had been showing references to 'video' immediately prior to the failure so I assume it was selecting and installing a video driver. Is there a way that I can prevent this from happening, such as entering a command at the start by pressing F6?

I've used the 'alternate' versions of Xubuntu (which I'd prefer as this has only 256MB RAM) and Ubuntu and the problem occurs at the same stage for both. I've previously had Ubuntu 7.04 successfully running on this laptop but have since wiped the HD. I did an md5sum on the 'alternate' downloaded file, and I've also run both CD's 'live' on other computers, so I'm happy that the CD's are OK.

---

### Post by Pumalite on 2007-10-24
You cannot boot a Live CD with 256 MB of RAM unless you make a 500 MB /swap partition ahead of time. So, I recommend the Alternate Xubuntu CD. Let's try to sort this out. Graphics?

---

### Post by rwnz on 2007-10-24
According to a brochure that I've just found on line this Toshiba Satellite 1800 has a Trident CyberBlade graphics controller with AGP bus and 8Mb memory.

I am using the Xubuntu Alternate CD.

I haven't tried to run the live CD on this computer - I ran it on another Windows XP computer with plenty of RAM. I made the comment to show what steps I've taken to prove the CD is OK.

---

### Post by Pumalite on 2007-10-24
You are having graphics problems. This should have been resolved by the Alternate CD. All references that I have found say that your graphics have too little memory to run most programs.
All I can tell you is to try a smaller distro like: DSL or Puppy.

---

### Post by rwnz on 2007-10-24
Thanks Pumalite. However I managed to run Ubuntu 7.04 for 6 months or so on this computer so it must be possible unless 7.10 needs more resources. I don't recall anything special that I did for that, though I do remember some mucking around before it would install.

---

### Post by rwnz on 2007-10-24
I've played around further - I did a fresh install, this time of the command line version of Xubuntu from the alternate CD, after which I installed and ran Lynx web browser OK . I then entered the command 'sudo aptitude install xubuntu-desktop' (because I found it on a post somewhere and it looked like it might add the gui). I haven't a clue what 'aptitude' refers to but it ran for about 45 minutes and appears to have installed the gui version. 

Now when I boot I end up with the error message "Failed to start the X server (your graphical interface). It is likely it is not set up correctly." 

The X server output states "/etc/gdm/failsafeXServer: line 47 [: too many arguments
Warning: Could not retrieve EDID because get-edid is not installed" and the o/s reverts to the command line format. 

How do I try installing get-edid? I tried sudo install get-edid but it asked for a destination file operand. The systems tempts me to pursue an answer as I still get a colourful Xubuntiu logo splash when the system shuts down.

---

### Post by simeruk on 2007-10-28
Hi, I had the same problem - before touching screen settings, install "read-edid" package - in my case it helped ! Also before doing any changes to screen settings, make a copy of /etc/X11/xorg.conf

Cheers

Szymon

---

### Post by xneck on 2007-10-30
It seems that this doesn't work.

```

get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 200
        VBE string at 0x11110 "Trident CYBER 8620"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged

```

---

