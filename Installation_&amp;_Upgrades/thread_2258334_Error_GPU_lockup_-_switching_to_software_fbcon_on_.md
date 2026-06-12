---
title: "Error GPU lockup - switching to software fbcon on install"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by Billy_Martinez on 2014-12-26
Hello I have a very old machine that was built in 2005 that I'm trying to install Lubuntu on. When I start up from my Lubuntu Live DVD I'm able to get to the menu, but once I try to launch the live CD from the menu the Lubuntu installer freezes on the Lubuntu logo. If you let the computer sit for a while the Lubuntu logo eventually goes away and I'm left with a mouse pointer (that I can move) and a blank light blue screen with dots on it. Then if you continue to wait the blue screen eventually goes away and the terminal screen appears with the error message "GPU lockup - switching to software fbcon on install".   I did some research online and I found another forum that said that issues like that are caused by the video card drivers and they recommended that I try modifying the boot file in the Lubutu Live CD menu and setting it to boot in nomodset mode. I did that and it didn't work. The video card that I have is a BFG Tech GeForce 7800GT 256MB video card, model number BFGR78256GTOC. The processor is an amd 64 bit chip clocked at 2.2GHz. I have 3 gigs of ram, the machine is custom built. 

Any help would be appreciated.

---

### Post by MAFoElffen on 2014-12-26
On initial boot... at the fisrst panel where it has an icon on the bottom, hit the escape key and get to the alternate boot menu. At that menu, hit <F6> and select "nomodeset", then try it. Use the instruction from post #3 of my sticky.... link in my sig line.

---

### Post by Billy_Martinez on 2014-12-26
> **MAFoElffen said:**
> On initial boot... at the fisrst panel where it has an icon on the bottom, hit the escape key and get to the alternate boot menu. At that menu, hit <F6> and select "nomodeset", then try it. Use the instruction from post #3 of my sticky.... link in my sig line.


I tried that already, in my first post I stated that.
 > **MAFoElffen said:**
> they recommend that try modifying the boot file in the Lubutu Live CD menu and setting it to boot in nomodset mode. I did that and it didn't work.

---

### Post by Billy_Martinez on 2014-12-27
I have an update, I was curious about whether Fedora would work on the machine so I downloaded a Fedora Live CD. When I ran it on the machine, just like the Lubuntu the live CD it froze right after I exited the Live CD menu. I tried Ubuntu and that also froze right after I exited the menu. I'm starting to wonder if I should just give up because it seems like that video card isn't compatible with any version of linux out there. The machine is currently running Windows 7 fine so it can't be the hardware.

---

### Post by Billy_Martinez on 2014-12-27
Another thing that I noticed is that right after the Live CD menu screen the terminal appears for 3 seconds with a message saying that there is no compatible ACPI.

---

### Post by MAFoElffen on 2014-12-27
> **Billy_Martinez said:**
> I have an update, I was curious about whether Fedora would work on the machine so I downloaded a Fedora Live CD. When I ran it on the machine, just like the Lubuntu the live CD it froze right after I exited the Live CD menu. I tried Ubuntu and that also froze right after I exited the menu. I'm starting to wonder if I should just give up because it seems like that video card isn't compatible with any version of linux out there. The machine is currently running Windows 7 fine so it can't be the hardware.
Differing flavors of the same thing. Even Unix, if you are running X, is using the same.

I'm running nVidia: Geforce GTX 9800 x2 SLI... Other here I have in my test suite, nVidia and Radeon, Some the Intel GPU's. I can tell you that it does work with nVidia the same techniques used for all favors.

At a LiveCD's SELinux menu, for nVidia grahics, you could use either "nomodeset" or "nouveau.modeset=0" at the end of the linux boot line, after the "-" character. Either tell the kernel to disable KMS for nVodoa and allow it to use another driver (usually nouvoeu or vesa), until you can get an nVidia driver installed.

If you were refering that other paid-for OS'es are more user friendly with nVidia... M$ has paid agreements where they can use things with that paid agreement. Since those specific drivers are licensed (non-free)... a freely licensed OS cannot include that type of licensed material without the user doing it themsleves... agreeing to that vendor's licensing terms. It's still free to us either way, but it's a legaleze factor.

I always thought that could be taken care of in scripting, to probe the hardware, prompt the user for their acceptance of a non-free driver... Makes sense to me, but I'm not a lawyer... I suggested that years ago... and that IS now what the additional drivers utility does... but that is part of the full installed, version, and can only be gotten to after the system is installed.

As for the OS you asked about... I have that installed also. I have it installed because of school course-work. It is not as intuative or user friendly. Nor is it as stable. I like Debian branched Linux. I support Ubuntu for a reason. It is easier for users, with the stability people expect and deserve. (I am brutally honest.)

---

### Post by Billy_Martinez on 2014-12-27
> **MAFoElffen said:**
> Differing flavors of the same thing. Even Unix, if you are running X, is using the same.


At a LiveCD's SELinux menu, for nVidia grahics, you could use either "nomodeset" or "nouveau.modeset=0" at the end of the linux boot line, after the "-" character. Either tell the kernel to disable KMS for nVodoa and allow it to use another driver (usually nouvoeu or vesa), until you can get an nVidia driver installed.


I tried putting nouveau.modeset=0 at the end of the linux boot line "--" just like you said and it didn't work. I'm getting a black screen with the mouse pointer on it.

---

### Post by Billy_Martinez on 2014-12-27
I was able to get it to work! I used the nomodeset settings in the option under F6 and I edited the end of the end bootline to nouveau.modeset=0.

Now what's going to happen after the install when I have to restart?  Is the kernal going to go back to the default settings? How do I update the drivers on Linux?

---

### Post by MAFoElffen on 2014-12-27
Yes... After is installs and you restart the system the first time... Put your finger over the left shift key. As it gets past the BIOS messages, start hitting that key intermittantly, until you see the Grub boot menu. As som at it appears, hit a <down arrow key> so it doesn't time out and go away. The arrow back up to the first menu item and press <E> to get into an edit mode. Arrow down to the line that starts with "linux". Go to the end of that line and add the same option. Hit <cntrl><X> to boot. 

After it boots, Go to "System Settings". The last tab is "Additional Drivers". That will seen your card and recommend drivers for your card. Accept and Install those drivers. Then you will be golden. The video driver will be installed and updated with your other system files. 

Like I explained, they are non-free drivers, so it takes extra individual user interaction to accept the licensing to use it, outside of something as a default.

I'll keep an eye to ensure you have no other problems. Once done, please use the thread tools to mark this thread as "Solved."

---

### Post by Billy_Martinez on 2014-12-27
> **MAFoElffen said:**
> Yes... After is installs and you restart the system the first time... Put your finger over the left shift key. As it gets past the BIOS messages, start hitting that key intermittantly, until you see the Grub boot menu. As som at it appears, hit a <down arrow key> so it doesn't time out and go away. The arrow back up to the first menu item and press <E> to get into an edit mode. Arrow down to the line that starts with "linux". Go to the end of that line and add the same option. Hit <cntrl><X> to boot. 

After it boots, Go to "System Settings". The last tab is "Additional Drivers". That will seen your card and recommend drivers for your card. Accept and Install those drivers. Then you will be golden. The video driver will be installed and updated with your other system files. 

Like I explained, they are non-free drivers, so it takes extra individual user interaction to accept the licensing to use it, outside of something as a default.

I'll keep an eye to ensure you have no other problems. Once done, please use the thread tools to mark this thread as "Solved."


Thanks for all of your help I was able to get it working.

---

### Post by andrei-digital on 2015-05-01
I'm facing this issue when trying to install Elementary OS Freya from a usb stick and the fix above doesn't work. I simply can't get in, either i'm stuck at the Elementary logo with a cursor, black screen with a cursor which changes to Gpu lockup message or sometimes both. Any other ideas on getting around this?
ps. my graphics card is a nvidia go 7300

UPDATE: [Billy_Martinez]("http://ubuntuforums.org/member.php?u=1961845") suggestion worked!

---

### Post by vitaly-krugl-web on 2015-05-04
When I first tried to upgrade my 2005/2006 Asus P4C800 Deluxe-based PC from Widows XP to Ubuntu, I was facing the black screen with blinking "cursor" line in top left corner. I eventually went back to Asus's sw update page and found that there were several BIOS updates that were newer than the BIOS on my PC. The latest released BIOS didn't help, but they had a more recent BETA version BIOS, which allowed Ubuntu to boot fully. Hope this helps.

---

### Post by pini.deb on 2015-06-04
For what it worths, I've had far better results with boot parameter **[FONT=courier new]nouveau.noaccel=1[/FONT]** than with [FONT=courier new]nomodeset[/FONT] or [FONT=courier new]nouveau.modeset=0[/FONT]. The latters disable Nouveau and activate VESA with no better resolutions than 1024x768.
My card is a NVidia Quadro FX 350M rev a1 not supported by the last releases of the proprietary driver.

---

### Post by syntaxerror74 on 2015-08-28
nouveau.noaccel=1 ? 

I'd be very careful with this setting...especially if you're running Compiz or so, with that lovely fish tank scene. The fish will only ever swim in slo'mo' if you use this setting. :D

Ah, and thanks people for 'nomodeset'. Had the same issue with a FX6200 card here, which brought up the "GPU lockup" message and ... never even made it to LightDM ... ever.
Instead, it would always show gibberish which most likely was poison for my gfx hardware.
So thanks alot everybody at the nouveau team - you've concocted a piece of junk  that is really not up to the usual Linux quality standard.
And in case you wonder, I have 1280x1024 here - so **not** the case that pini reported (1024x768 max) -, and, I am pretty sure that even 1600x1200 would be possible with the proprietary driver. However the **kernel** stuff must match **exactly **to the (binary-only) NV driver - the warning in the installer program was not put there by pure luck. With the 3.18 I'm still happily using, the latest driver is not suitable.

---

### Post by Dave_Crowder on 2016-01-05
Just to add to this...  I tried Billy Martinez's method and could see that it had an effect but I was still freezing at the point where the message was previously displayed.  After a bit of toying around I found a setting in the bios which set the computer for the type of OS to be installed.  Windows or others... once set to 'others' and with the use of Billy's instructions I have finally managed to get to the installation (which is almost complete :) 

hope that helps!

---

### Post by lpdf on 2016-08-26
If you're like me you won't have the F6 option (I'm using Zorin, based on arch linux) ... you have to actually edit your boot loader script to default to software rendering until you get the proper (proprietary) video driver is loaded.

So you need to add a parameter to your kernel ...
[mostly likely this:]
 nouveau.noaccel=1
[but may be this:]
 nouveau.nofbaccel=1
[or this:]
 nomodeset

For Zorin I booted with the terminal option when it got the the repair menu I ran the "grub update" menu-item (gave me read/write access) then then "terminal access" menu-item.  At the terminal..
vi /etc/default/grub
 (newbies websearch "vi commands" for how to edit with vi)
Find the line starting with GRUB_CMDLINE_LINUX_DEFAULT and append the new parameter to its end. For example:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.noaccel=1"

Save the file and close the editor.
Then at the terminal prompt run:
sudo update-grub

[note this is for grub 2 bootloader, adding those parameters is different for old grub, syslinux, etc]

On the next reboot, the kernel should be started with the software rendering boot parameter.

I would try the first parameter ["nouveau.noaccel=1", above in the 2nd paragraph], then the 2nd, then the 3rd ... until you find one that gets you to the gui.  Then go into your system config dialog to install the needed proprietary video driver.  With Zorin this was quite easy.  Elementary OS should be as well, a bit harder with stock Ubuntu and harder with the more egg-head distros.

Once you have the right driver you can again edit your grub file to remove the addition you made, then sudo update-grub and then reboot.  Done.

---

