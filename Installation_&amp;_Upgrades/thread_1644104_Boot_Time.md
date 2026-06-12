---
title: "Boot Time?"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by gt3pilot on 2010-12-12
I sucessfully made a CF image of the UBUNTU-10.10 -netbook-i386 and put it in a Ampro RB800 SBC. It finds the CF and starts to run UBUNTU but it takes over 30 minutes to get to the login page.
 
800MHz Celeron processor
1GByte of memory
 
Is the prcessor just too slow for all of this? 
 
I also made an image of the CLI UBUNTU - UBUNTU-Mini-Remix-10.10-i386 - it boots to the command line in about 10 seconds if that is of any help.
 
Thank you in advance.
 
Kirk

---

### Post by oldfred on 2010-12-14
Welcome to the forums.

30 minutes seems very long. Does your computer directly boot the cF card or is it plugged into a USB card reader?

Have you check log files. System, administartion, Log File Viewer. Look at dmesg, kern.log and others. Look for very long times between the time stamps, or repeated attempts at loading something and then timing out.

---

### Post by gt3pilot on 2010-12-14
I did not get a chance to look at it last night other than to make sure that it was still up and running and to start a scan of the system to see if it thinks that this hardware is running/stable/etc. It was still cranking away after 10 minutes so I left it to finish up and I will look at it tonight.
 
I get the same boot up time regardless of CF or USB Pendrive - s.l.o.w... I will go see if I can extract off the logs onto a thumb drive and get the someplace where I can look through them, thank you for the suggestion. 
 
These SBCs were realeased with a UBUNTU base with several of their add ons, claimed it to be part of GNU Open Source but I cannot find any of the original distribution files on the net...I say this as I imagine that you are pointing me in the right direction as they have added things that are specific to their board that makes it so slow. As in, it does not recognize the monitor but it displays perfectly, it recognizes the hard drive c0onnected to it, the partition on it but does not know anything about it other than it has a boot sector on it...just various odd things that make me suspect that I am going to need to find the original Ampro distribution disk.
 
Thanks again,
 
Kirk
 
 
SNIPPET ADDED:
 
This version was created starting from the Ubuntu 7.10 Alternative CD distribution. It is based on the Ubuntu Linux 2.6.22 kernel. To this Ampro added:
&#8226; Selected standard Ubuntu desktop packages
&#8226; The Fluxbox (rather than GNOME) graphical application framework
&#8226; Selected packages from UME (Ubuntu Mobile & Embedded)
&#8226; The 2.6.23.9 and 2.6.23.9-rt Linux kernels, downloaded as source from kernel.org and compiled by Ampro
 
Second Snippet
 
It appears that going through all of the hardware tests that it finds each of the respective chipsets and that each function tests normally...so one thing potentially out of the way. I am downloading the 7.1 ver and will build it later and see what happens with it, not crossing my fingers but is is another direction to head. Sure wish I could find the original release of the Ampro SW - I have five of these boards!

---

### Post by gt3pilot on 2010-12-16
I so enjoy talking to myself...!?!  ;-)  At elast it gives me a place to keep my notes when I have time to jot them down!

I downloaded the desktop version of 7.10 and got it onto the CF last night, boot time was under a couple of minutes (still not as good as I want though) and it does not recognize the graphics chipset.  

It sets up a 800x600 graphics driver that works (?), but doesn't recognize the monitor (didn't really expect it to if it didn't recognize the chipset).  I decided for grins not to run it live and see how it handled an install to a HD...started the process and the windows that come up during install over scan the monitor and they cannot be resized to fit.  I hid the task bar at the bottom and moved task bar from the top to the side to increase the vertical space on the monitor - this allowed me to at least see the tops of the radio buttons from the install windows to get things to continue.  Having gotten the install to officially start I went merrily off to bed...this morning I found out that it stalled at 15% on the monitor during the install.

No time to trouble shoot at the time, I guess that is what is in store for this evening.

Carry on...

Kirk

---

### Post by oldfred on 2010-12-16
You realize 7.10 is beyond its life.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Ubuntu 7.10
Gutsy Gibbon
Release date
October 18, 2007
End of life date
April 18th, 2009

---

### Post by gt3pilot on 2010-12-16
> **oldfred said:**
> You realize 7.10 is beyond its life.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Ubuntu 7.10
Gutsy Gibbon
Release date
October 18, 2007
End of life date
April 18th, 2009

Yes, sir, I do - but if it gives me a foundation to start building from - so be it, I will just have more work to do to get things stable.  

I am willing to take advice, if it is given.

Kirk

---

### Post by oldfred on 2010-12-16
Any time you have long boot times you want to check log files for very long times between entries or a repeated entry that then times out. Then those areas are ones for further research of specific issues. Sometimes just removing splash quiet from boot can let you see what is not working.

Since it is an older system it just may need a parameter or two.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

