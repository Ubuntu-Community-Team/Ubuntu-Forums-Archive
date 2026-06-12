---
title: "Monitor Goes “Out of Range” When Using LiveCD"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by cricnt on 2007-01-11
Monitor Goes “Out of Range” When Using LiveCD

Steps to Reproduce Problem:

1. Insert Ubuntu 6.10 Desktop LiveCD
2. Restart Computer
3. When Ubuntu CD Menu appears, select “Start or install Ubuntu”
4. After splash screen is done loading (just before GNOME would appear), monitor will blank out and display an “Out of Range” message

Attempts to Overcome Problem (all produced same problem):

a. Instead of selecting “Start or install Ubuntu,” use “Start in Safe Mode”.
b. Manually select resolution using F4, then “Start or install Ubuntu”
c. Use F6 to add “break=bottom” to options. 
 NOTES: This gave me access to a prompt from which I looked at xorg.conf. It lists vesa as the 	video card, and correctly indicates that my monitor is an “FP767”. h/vsynv values were not 	listed. I would have liked to have changed vesa to nv, but there did not appear to be any text editor available, i.e. nano.
d. Tried Ubuntu 6.06 Desktop LiveCD
e. Tried Xubuntu 6.10 Desktop LiveCD

Additional Information:

-The CD was checked for correctness.
-Windows 2000/XP, Fedora Core 4/5 have been installed without incident in the past.
-My guess is that the hsync/vsync values are too high

Hardware:
CPU: Athlon XP 2100+
MB: VIA KT4AV
MEM: 2 GB DDR400
HD: Western Digital IDE ATA133 160GB
Graphics: Geforce FX 5200
Monitor: BENQ FP767

Thanks in advance,

-Joshua C.

---

### Post by Paerez on 2007-01-11
One quick thing that probably won't work but is worth trying:
- When you get "out of range" turn the monitor off and on again and press the "Auto" button.

This may work:
Unplug the monitor, boot ubuntu. When your computer stops making noise (i.e. it booted ubuntu all the way) plug the monitor in. Hopefully ubuntu won't try to figure out your monitor and it will assume something generic.

My guess is the h/v sync stuff is messing up. I had a Rosewill monitor that would display the correct image (the desktop) but put "out of range" on the screen, even though it was working! :rolleyes:

---

### Post by wpshooter on 2007-01-11
Josh:

What type of video card is a Geforce FX 5200 ?  Is this a Nvida or ATI.  Nvida I think but all of my video cards are ATI and I had this same problem.  The solutions for ATI cards to to install the fglrx driver from Synaptic and then substitute the fglrx parameter in the proper slot in the xorg.conf file.  However, if this is a Nvida card, my guess is that you just need to install an up-to-date driver from Nvidia.

Good luck.

---

### Post by cricnt on 2007-01-11
> **Paerez said:**
> One quick thing that probably won't work but is worth trying:
- When you get "out of range" turn the monitor off and on again and press the "Auto" button.

This may work:
Unplug the monitor, boot ubuntu. When your computer stops making noise (i.e. it booted ubuntu all the way) plug the monitor in. Hopefully ubuntu won't try to figure out your monitor and it will assume something generic.

My guess is the h/v sync stuff is messing up. I had a Rosewill monitor that would display the correct image (the desktop) but put "out of range" on the screen, even though it was working! :rolleyes:

Thank you for your reply. I tried both and they still produced the "Out of Range" message. If I could edit the xorg.conf file I would manually set the sync values, but there doesn't appear to be any editors. Maybe dpkg-reconfigure xserver-xorg will work...

-Joshua C.

---

### Post by Paerez on 2007-01-11
dpkg-reconfigure xserver-xorg may help, but i doubt it. Usually, you do this:

1) change xorg.conf
2) restart Xorg

but in the live cd, step 2 will reboot you, killing your changes. dpkg-reconfigure will do step 1, but you still have to restart Xorg, resulting in the reboot.

Do you have a VGA on your motherboard you could use temporarily until you install ubuntu, then switch to your geforce?

---

### Post by cricnt on 2007-01-11
> **wpshooter said:**
> Josh:

What type of video card is a Geforce FX 5200 ?  Is this a Nvida or ATI.  Nvida I think but all of my video cards are ATI and I had this same problem.  The solutions for ATI cards to to install the fglrx driver from Synaptic and then substitute the fglrx parameter in the proper slot in the xorg.conf file.  However, if this is a Nvida card, my guess is that you just need to install an up-to-date driver from Nvidia.

Good luck.

Thank you for your reply. Indeed, the graphics card is made by Nvidia. Given that, I am not sure how I would install a new driver given that I can't get the OS to load up correctly (from the LiveCD), and the break point I am using prevents most programs from running since most of the libraries haven't been loaded yet.

-Joshua C.

---

### Post by cricnt on 2007-01-11
> **Paerez said:**
> dpkg-reconfigure xserver-xorg may help, but i doubt it. Usually, you do this:

1) change xorg.conf
2) restart Xorg

but in the live cd, step 2 will reboot you, killing your changes. dpkg-reconfigure will do step 1, but you still have to restart Xorg, resulting in the reboot.

Do you have a VGA on your motherboard you could use temporarily until you install ubuntu, then switch to your geforce?

I do not. I am going to go grab another monitor, and see what happens...

-Joshua C.

---

### Post by cricnt on 2007-01-11
> **cricnt said:**
> I do not. I am going to go grab another monitor, and see what happens...

-Joshua C.

Different monitor, same problem. Sadly the only other monitor I had around, was a BENQ FP557s, which is the FP767's little brother (15" instead of 17").

Regarding dpkg-reconfigure, it is not available. I found that nano is available from root/bin but, since the curses library is not available, it won't run.

-Joshua C.

---

### Post by dbott67 on 2007-01-11
Hi Joshua,

I had the same problem & this is what I did:

1. Boot from the Live CD
2. Once the monitor goes "Out of Range", what a minute or so until the computer would normally get to the login prompt.
3. Press **CTRL-ALT-F1** (or **CTRL-ALT-F2**) to get a terminal window
4. Use **nano** to edit your xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```
Add the appropriate **VertRefresh** value under the "Monitor" section:
```
Section "Monitor"
        Identifier   "DELL 2007FP"
        [COLOR="Red"]VertRefresh  60.0 - 60.0[/COLOR]
        Option      "DPMS"
EndSection
```
5. Save the file
6. Press **CTRL-ALT-F7** to get back to Xwindows (or perhaps **CTRL-ALT-BKSPACE**)

-Dave

PS - This worked for me once, but another time I couldn't seem to have any luck, so I downloaded the "Alternate ISO" & used it to install.

The other thing to try would be to run **sudo dpkg-reconfigure xserver-xorg** after step 3, instead of manually editing the **xorg.conf** file.

---

### Post by cricnt on 2007-01-11
All right finally got everything working. Much thanks to all who replied.

Step-by-Step:

1. Get alternative Ubuntu iso
2. Reboot using said CD
3. Install Ubuntu in text mode
4. After installing and restarting, just before the login screen, the monitor will go "out of range"
5. CTRL-ALT-F1 to get a prompt
6. Login
7. $sudo apt-get install nvidia-glx nvidia-kernel-common
8. $sudo nvidia-xconfig
9. $reboot

-Joshua C.

---

### Post by Paerez on 2007-01-11
genius! didn't think about switching once it was up.

---

### Post by bdcreator on 2007-04-09
I tried to install on Virtual PC 2007. Can see the installation screen. But once click start Ubuntu (even in safe graphics mode) the screen will change to unrecognizable colour seems like distorting    for incorrect resolution. And Virtual PC reports the screen size doesn't fit.

Is it same issue? My hardware set as follows:

Intel E6300 Core2Duo
motherboard DG965SS with onboard GMA X3000
HP pavilion vf51 LCD monitor
microsoft wireless multimedia keyboard 1.1 (can't use the Function key, but I will start use the traditional one to install if necessary)

Many thanks.

By the way, will 6.06 better? Is it more stable? Necessary to upgrade? Or even can wait for version 7?

Savio

---

### Post by ashvini on 2007-05-03
Thanks Joshua. Your solution worked for me.
I was trying to install Xubuntu - Feisty Fawn on a machine with Nvidia FX6600 processor and Viewsonic VA712 monitor. Using live CD would result in monitor displaying Frequency Out of Range message. I was able to complete the install using text mode of alternate CD but on booting the system the same problem appeared. I had to select recovery mode from GRUB menu and then installed the packages mentioned above. After that, the Xfce came up normally.

---

