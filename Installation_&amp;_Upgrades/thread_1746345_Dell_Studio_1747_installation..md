---
title: "Dell Studio 1747 installation."
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by californium on 2011-05-01
I was previously using ubuntu 10.10 amd64 on my notebook. 
I used the  upgrade option to update to 11.04 and let it ran overnight. It was  pretty much finished by morning. However, upon the subsequent reboot, my  notebook would no longer boot. It would get stuck on the loading  screen. (the dots would move for a bit and then just a total freeze.) I  rebooted a few times and once I even let it sit for 2 hours thinking it  was still doing something. Nothing happened...

Since mine was an  upgrade, I had options in my grub menu of loading previous kernels.  Luckily for me, loading an older kernel worked! I was now able to login  and get to the desktop.

I was now running into issue of the  system being slow and sluggish. I tried both Unity and Classic mode. I  even installed Gnome3 Shell but ran into graphical glitches.

So  figured what I needed was a fresh install... I decided to use Kubuntu.  (Unity or Gnome3 shell didn't feel like its right for me)

I  downloaded Kubuntu 11.04 amd64...  Total Failure... I could not get the  liveCD to work. It would freeze on the loading screen with the dots. The  check disk option stated the CD was fine. Memtest gave no errors. After  multiple reboots, I was still running into the same problem....

I  downloaded Kubuntu 11.04 amd64 (Alternate CD)... Almost Worked... using  the text installer, I was able to get the OS loaded. I was pretty  pumped thinking I now have a working notebook again after 2 days.....   After it ejecting the installer CD and rebooting, it once again hangs at  the loading screen with dots. It gave some type of error involving  cryptswap. knowing that I selected the option to encrypt my home folder,  this error might have been the result of that.

I proceeded to do  another fresh install. This time with no encryption.. another  disappointment awaits. Once again, freezing on the loading screen with  the damn dots. Since these were a fresh install, I no longer have  options to load a previous kernel under grub. 

I tried the  recovery options on the disks. I tried to read the /var/logs. I tried  recovery mode, but no go.. After searching through this forums and not  finding any answers, I was dejected and disappointed. I contemplated of  going back to either Ubuntu 10.10 or Win7.
until.... I found out that  during the boot process, you can hit the <esc> key and it would  show you what it is doing during loading up.

I found out it would freeze up around when it was loading the networking modules.
I  proceeded to disable my blutooth, LAN and WLAN under the bios. Rebooted  and it now friggen WORKS! I was able to get to kdm and log in. I now am  able to get to a desktop, albeit no networking but i'm one step closer  to a working installation. I confirmed a few times that it was able to  boot to the desktop with no issues. I went back in to the bios and  enabled my blutooth, LAN and WLAN.... and.... my installation still  WORKED!! No graphical issues, KDE looked nice and clean.

But I  still wanted my /home directory encrypted. So I proceeded to do another  reinstall. This time I went back and used the regular Kubuntu LiveCD. I  spammed my <fn>+<F2> button while the live CD was booting.  (<fn>+<F2> is the hardware buttons to disable/enable my  networking)
The LiveCD took a bit to boot up into the desktop and I  proceeded to install.. BAM!!! The installation gui would crash and I had  to start over. I was pulling out my hair by now. Thinking the LiveCD  environment was not fully loaded I started the install again.
After the 4th gui crash I said screw it and used the Alternate CD.

(Are you still reading this?)
Alternate CD installation fine. I now have a functional notebook with Kubuntu 11.04
Only  took me like 3 days to install but it works. My quick thoughts is that I  like it. I'm not too sold on Unity or Gnome3 shell just yet. I'll  probably use test it out sometime again in the future but I'll be using  KDE as my main desktop.

---

### Post by californium on 2011-05-01
TL;DR version

Dell Studio 1747 install.

Use the Kubuntu Alternate CD (amd64) to install. 
(The LiveCD version gave kept crashing on me during gui install)

Reboot.
If you are experiencing freezing during the loading process, disable your networking in the bios. 
After successfully getting to the desktop and confirming you're able to get to the desktop with reboots, you can go back in and enable the networking in the bios.

If you did not disable the networking in the bios, you can also just spam networking hardware button during the load process. <Fn>+<F2>
(only need to do this on the first reboot after install)

Once you get to the desktop, it should be fine from there.

Lan and wireless works fine for me out of the bat.
Audio needs to be reconfigured.
[http://ubuntuforums.org/showthread.php?t=1395682](http://ubuntuforums.org/showthread.php?t=1395682)  (post #7)

---

