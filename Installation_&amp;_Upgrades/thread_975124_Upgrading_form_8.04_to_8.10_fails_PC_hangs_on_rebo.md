---
title: "Upgrading form 8.04 to 8.10 fails PC hangs on reboot."
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by sukhhari on 2008-11-08
Hi,

After upgrading from 8.04 to 8.10 my laptop unable to reboot, it just hanging, could anybody come-a-cross.

Harish
#-o

---

### Post by cosborn72 on 2008-11-08
Where is it hanging?  After the restart and as it is booting?  Also, what hardware are you running it on?  You should be able to boot in 'verbose mode', which should show you exactly where it is stopping.  You might want to try this.

If you can provide that information, it will be easier to troubleshoot.

---

### Post by sukhhari on 2008-11-08
Thanks Mr.cosborn72

While rebooting / shutdown its hanging, Ubuntustudio Upgraded from 8.04 to 8.10 AMD64bit on Acer 5920 Laptop with 2 GB Memory.

Harish
:)

---

### Post by Mafy on 2008-11-08
Hi!
I have a similar issue. 
I have upgraded from 8.04 to 8.10.
But after the first restart the new Ubuntu failed to load. 
It stops on boot and there is nothing on the screen (no text mode, no mouse or keyboard cursor, no errors/info - just a black screen).
Also I have removed the "quiet" from the appropriate line from /boot/grub/menu.lst but still no output.
How to enable a verbose mode in another way?
I have Win XP installed too that works without any issue.

Dell Inspiron 6400
Proc: Intel Core 2 Duo, AMD64bit, 2GHz
Mem: 1GB dual channel 
Video: ATI Mobility Radeon X1400

Regards,
Mafy

---

### Post by Mafy on 2008-11-09
Anyway this update looks a real disaster.
It was expected to be a simple operation, an update.
But the result was to screw everything.
After I have struggled to install Oracle (a real pain), I have struggled to install a secondary monitor to my laptop (it toked around 2 weeks to find a solution)... now everything is gone.


An important thing that I have noticed during the update (I might be wrong... though):
all the configuration files are simply **REPLACED **and not **UPDATED**.
I tend to believe that is the major issue with the update and the reason that all the existing configurations are lost.
The update should just update the corresponding items in the configuration files and not replace them with new files... the result is that the existing configurations are lost.

---

### Post by avikrc on 2008-11-09
I had this problem when I upgraded to the 8.04. The comp quite simply stalled while booting. I just couldn't get it back up :(. I had to scrub the had drive and reinstall Ubuntu which knocked out all the tinkering I had done. I had that series going since I started using Ubuntu (5.10 version).
I thought it was just my old hardware which caused the failure. But it seems this is a common problem! I am hesitant to upgrade to 8.10 now.

---

### Post by Mafy on 2008-11-10
That's a really great experience...

I have downloaded the Ubuntu 8.10 CD.
The installation failed too, not only the update.
The installation freezes during the installation with the same black screen.

I am pretty suspect regarding the quality/quantity of the tests done over the 8.10 release (if there are any).

Why everything works during the 8.04 installation and during 8.10 both update and installation failed? That's quite a performance...

The scope of a new version is to bring improvements over the previous ones, but not to introduce issues and make it totally useless!!!

---

