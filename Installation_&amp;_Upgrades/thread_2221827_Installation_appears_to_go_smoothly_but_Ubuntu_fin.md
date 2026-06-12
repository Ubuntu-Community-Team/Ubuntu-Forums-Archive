---
title: "Installation appears to go smoothly but Ubuntu finds serious errors when booting."
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by colinglanville on 2014-05-03
By way of background, I am many years away from hands-on technical work and have almost always used a GUI when using either Mac OSX or Windows. My current aim is to see how Ubuntu feels to work with and I wanted to avoid running Ubuntu (or some other flavour of Linux) inside a virtual machine. I came across a description of wubi.exe which seemed to be just what I want.

I downloaded wubi.exe to install Ubuntu on my Windows 7 Home Premium laptop (Intel dual core CPU running at 1.4GHz; 3GB Ram; 67GB free space on the hard drive). Then I started wubi running and provided some simple details of which the installation size is the only one which may be relevant. The popup dialog box said 18GB was needed and I selected 30GB from the choices offered. There was 67GB free so the 30GB seemed safe to me. Wubi then continued. It downloaded Ubuntu 14.04 apparently with no errors. The next step was a reboot to complete the installation. That also went smoothly with no error reports. Towards the end of the installation process all the 64 bit packages were removed - I was not surprised by this because the laptop is not a recent model. 

Finally came the boot into Ubuntu. When given the option, I went with the simplest choice of Ubuntu rather than 'Advanced options with Ubuntu'. Then Ubuntu itself seemed to start but fairly quickly reported serious errors when checking for the disk /. There was no explanation of what that meant, not even some error numbers. I was given simply three options, I for ignore, S to skip mounting and M for manual recovery. First I waited for a bit to see if anything would change, then used the I option but got straight back to the error report screen with the same three options. So all I could do was S to skip mounting.

When all this occurred I wondered if those errors, whatever they were, indicated some issue in the downloads. I uninstalled Ubuntu using the Windows 7 Control Panel and started again. Exactly the same outcome. 

Can someone advise me on possible solutions? 

colinglanville

---

### Post by ubfan1 on 2014-05-04
Pretty sure WUBI doesn't work with 14.04 -- try 12.04 if you really want WUBI.  You might be better off trying the live media in the "try" mode first.  No changes need to be made to the hard disk until you are ready.  On Windows, use unetbootin ro create a live boot media from the downloaded iso.  Then boot the live media (DVD or USB).  A true virtual machine like virtual box would be another way, but performance would be less than a native install.

---

### Post by colinglanville on 2014-05-04
Thanks! I wasn't aware that wubi doesn't work with 14.04. Shall follow your advice.

---

