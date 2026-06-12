---
title: "New hardware support is available"
date: 2014-07-13
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-13
I just received notice from Update manager that new hardware support is available (Dell Vostro 3500 running 12.04.3 64-bit).  However, when I attempt update, I get:

The following packages have unmet dependencies:

libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed
                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed
                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed

Is this a known bug?

Thank you 

John

---

### Post by P . P . L . on 2014-07-13
I've got the same update showing this morning [ new hardware support available ] but it dosen't say what it's going to update, I'm running 12.04lts x32.

Will it f.u.b.a.r. anything, I haven't let it update yet.

---

### Post by John Coulthard on 2014-07-16
I just installed it on my backup machine (12.04lts x32). The install completed and called for a restart. Now I get "Input Not Supported" on the display. Repeat reboots are no good. Can't see the machine on the network. Next step will be to install 14.04 from scratch after I have tested it from a live cd. (I may wait a few days for this). Annoying for sure. 

Approach with caution. 

John.

---

### Post by cigtoxdoc on 2014-07-17
I have had this update work on two PCs and fail on two.  The two PCs for which it worked are hp/compaq dx2250m (running 12.04 64-bit) and hp/compaq dx2200m (running 12.04 32-bit).  Update has failed on my Dell Vostro 3500 laptop (12.04 64-bit, CPU is Intel(R) Core(TM) i5 CPU M 520 @ 2.40GHz) and it also failed on a home-built desktop that has a AMD thlon(tm) II X3 450 processor.  That PC is also 12.04 64-bit.

Does anyone know what is going on?

John

---

### Post by koenr on 2014-07-17
Have you thought of problems with closed source graphic drivers?

---

### Post by cigtoxdoc on 2014-07-17
One PC with nVidia driver upgraded correctly.  It is only a single cpu processor.  Problem seems to be 3.8.0-44-generic kernel.

John

---

### Post by John Coulthard on 2014-07-17
My problem seems to be related to the newer OS not recognizing the graphics adapter. My backup machine is a HP Pavilion, dual 4400 with Nvida and 2gig. 14.04 comes up in 640x480 mode. After all updates applied the system restarted with the correct display size then froze. On reboot I get "Input not supported". Backed down to 12.04.4 and got "Input not supported". Fortunately I still had a 12.04.3 install CD (which was my original install on that machine) and it comes up fine. System... details shows "Graphics: Unknown" but it is working ok. Applied all updates ok. I'm pretty well back to normal now and am not interested in exploring this problem any deeper right now. 

Needless to say I have no plans to upgrade from 12.04 or apply any "New hardware support..." until maybe later this winter when I have more time. ("It's summertime and the living is easy...."). 

John.

---

### Post by cigtoxdoc on 2014-07-18
I tried removing the dependencies, but it looks like when I did that, I wiped out programs that did not install; inclduing ones controlling Internet access.  How do I recover?

John

---

### Post by bapoumba on 2014-07-18
Would it be related with this [http://ubuntuforums.org/showthread.php?t=2234478](http://ubuntuforums.org/showthread.php?t=2234478) ?

To recover packages that got removed, the best way is :
1- to ensure your repos are stock ubuntu (main, restricted, universe, multiverse) for security and updates, without third party repos or ppa
2- reinstall ubuntu-desktop if running ubuntu (or the flavor one if running a flavor).

---

### Post by cigtoxdoc on 2014-07-18
Thank you, bapoumba.  Several problems here: 1) when one got rid of the offending packages, network commnications were lost; 2) I was getting both wlc_scan errors and borken pipe errors, and 3) I have lost the nVdia (304) drivers which are much better than the nouveau drivers.  It would appear that the simplest solution is to change the video drivers to nouveau drivers and the hardware upgrade will probably be okay.

John

---

### Post by bapoumba on 2014-07-18
From what I have gathered here and there, best for now is to wait.
Can you give an up-to-date situation and the problems you are running into, with error messages if you have them, thanks.

---

### Post by cigtoxdoc on 2014-07-18
Thank you for your reply.  Both problem PCs have had the hardware upgrade and are back with nVidia video drivers.  Those in charge of Ubuntu should have provided step-by-step instructions for identyfying problem PCs, removing the offending video drivers, converting to the nouveau drivers, running the hardware upgrade, and installing the new nVidia drivers.  For both PCs, removing the offending nVidia drivers also resulted in loss of network communications and failure of the PC to reboot correctly.  I spent about eight (8) hours removing the nVidia drivers, dealing with the "hell" that followed, getting the nouveau drivers installed, doing the hardware update, and reinstalling the nVidia drivers.

John

---

### Post by P . P . L . on 2014-07-19
Hi.

I let it do the update the other day and it did some more updates yesterday as well, I have not had any problems so far.

---

### Post by yura2 on 2014-07-22
**Thanks guys** for letting others know that this **new hardware support** may **mess up** Ubuntu **installation**.

Decided **not to install** new hardware support since I have a lot of work to do and basically **don't have spare working days to play with it**.

I believe this saved me a lot of time - **thanks again**!

**P.S. **It **would be** really **nice if Ubuntu warned** users that it is **not 100% safe**. New users may have been burned by this.

---

### Post by kansasnoob on 2014-07-22
> **yura2 said:**
> **Thanks guys** for letting others know that this **new hardware support** may **mess up** Ubuntu **installation**.

Decided **not to install** new hardware support since I have a lot of work to do and basically **don't have spare working days to play with it**.

I believe this saved me a lot of time - **thanks again**!

**P.S. **It **would be** really **nice if Ubuntu warned** users that it is **not 100% safe**. New users may have been burned by this.

But you also need to be aware of the kernel support schedule:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule)

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Hopefully Canonical will have it sorted out by August 8th.

---

### Post by John Coulthard on 2015-02-27
Seven months later so I thought I would give this another try. (HP Pavilion, dual 4400 with Nvida and 2gig.). Still fails although I get a few more opportunities to carry on. Run in low graphics mode...., Reconfigure graphics, Troubleshoot error, Exit to console login. None of these are any use (Even the "Exit to console login" ends in a hung machine.) except the "Troubleshoot error" does let me see the Xserver Log which ultimately ends in "Failed to load the NVIDIA kernel module.". 

This is a backup machine which I use to mirror my main computer, fairly old now although it has been reliable. I'm not inclined to put a lot of work into it so will probably just reinstall the old system. I won't upgrade my main computer - I like to have the two running identical software.

---

### Post by John Coulthard on 2015-03-04
I re-installed 12.04.3 and am back to normal. I will stay with the configuration I have until 16.04 LTS is released.

---

### Post by kansasnoob on 2015-03-05
> **John Coulthard said:**
> I re-installed 12.04.3 and am back to normal. I will stay with the configuration I have until 16.04 LTS is released.

If you're then running the 3.8 series kernel you'll be running a long time with no security-related kernel updates:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

Did the 12.04.1 images with the 3.2 series kernel not work? It would at least be supported until April 2017. They're archived here:

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

---

