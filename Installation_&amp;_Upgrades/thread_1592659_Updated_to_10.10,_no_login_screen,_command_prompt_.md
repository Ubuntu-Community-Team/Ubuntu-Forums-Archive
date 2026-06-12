---
title: "Updated to 10.10, no login screen, command prompt only"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by cuderanch on 2010-10-10
Of 2 upgrades from 10.04 to 10.10, one went swell but the other went south. The one that went south ended up being a partial upgrade. It completed and computer rebooted. Instead of the login splash screen, I was presented with 'texty" Ubuntu 10.10 screen then a

 "computer name here" login:

I logged in as administrator, and got a screenful of system information statistics. Following some advice on another thread I entered "startx" and got a bunch of error messages regarding nvidia, e.g., "No drivers available", and "no screens found".

Please help

---

### Post by drober05 on 2010-10-10
I have had a virtually identical experience.  Upgraded two home desktop computers from 10.04 to 10.10.  One went flawlessly while the other one experienced the exact problem described above.

The computer having the problem has been running Ubuntu for over 2 years and has gone through other upgrades without a hitch.  Now all of the sudden the screen is not recognized.  It is an old Dell Dimension 4400.

Any suggestions on how to fix?

---

### Post by mionescu on 2010-10-10
Did you have installed before the nvidia driver? If so, try first to use the open source driver. One way to do this is to rename the Xorg.conf using sudo and boot the comnputer again. If it works, you can try to reinstall the nvidia drivers using "Hardware Drivers" from the system menu.

---

### Post by GBrogan on 2010-10-10
Same problem here. Have been able to get my desktop back by wiping out the Xorg.conf and loading the generic driver, but still can't get my nvidia drivers activated and loaded.

---

### Post by cuderanch on 2010-10-10
> **mionescu said:**
> Did you have installed before the nvidia driver? If so, try first to use the open source driver. One way to do this is to rename the Xorg.conf using sudo and boot the comnputer again. If it works, you can try to reinstall the nvidia drivers using "Hardware Drivers" from the system menu.

Hmm, I can't even get to Xorg.conf... Seems like I've been relegated to a user directory and get out?

---

### Post by Naoko15 on 2010-10-11
I've got exactly the same problem. Help please  :(

---

### Post by mionescu on 2010-10-11
You did say that you managed to login as an administrator, right? Try to type the following:
cd /etc/X11
mv xorg.conf xorg.conf_backup

then reboot the calculator. I hope this will work.

---

### Post by psic on 2010-10-11
Same problem here. Renaming xorg.conf worked, but I can't install the nvidia drivers or setup thecorrect resolution...

---

### Post by cuderanch on 2010-10-11
Thank you. I was able to rename xorg.conf, but it didn't help. Is it the nvidia drivers? How would I update them?

---

### Post by mionescu on 2010-10-11
What happens now when you try to start X (startx)? There is no difference after moving the xorg.conf file? Did you try to boot from the live cd to see if it works that way? If it does, you might want to do a fresh install.

---

### Post by Naoko15 on 2010-10-11
I'm in the same place. I am able now to boot the system but can't use Nvidia drivers. Obviously, screen resolution etc is all wrong. 

Startx now says:

```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
```

How can i configure Nvidia drivers?

---

### Post by dnewkirk on 2010-10-11
When upgrading one of my current installs, I noticed that the kernel headers had not been installed prior to loading the nvidia driver, and hence the driver installation failed. You can get x to start  using something similar to the previous suggestion:

cd /etc/X11
sudo mv Xorg.conf Xorg.conf.failsafe

(you can ls in the folder to make sure that file exists!).

---

### Post by sunyata_nn on 2010-10-11
try ps -ax look for gnome, or similar, and kill the proces. 
also you can try
sudo service gdm start

---

### Post by cuderanch on 2010-10-11
I tried all of these suggestions, but unfortunately none worked. I ended up pulling the graphics card (nvidia GeForce 4 Ti 4800 SE) and was able to get to Ubuntu using the motherboard graphics. I redownloaded the nvidia driver (version 96) and reconfigured startx. After reboot, I was back to square one.

RIght now, the only way I can run is without the video card (motherboard works), and without startx.

Any ideas? Is it the old card? Is it startx? Do I need to get away from nvidia altogether?

---

### Post by phuxed on 2010-10-12
I was able to fix it like everyone else by wiping out xorg.conf but it does present a problem in that I can't access the accelerated graphics

---

### Post by GavinP on 2010-10-12
Same issue with standard Intel netbook graphics as well:

[http://ubuntuforums.org/showthread.php?t=1594122](http://ubuntuforums.org/showthread.php?t=1594122)

Thanks

Gavin

---

### Post by Xoanan on 2010-10-12
Same issue here;  I am currently running in low graphics mode.

---

### Post by mionescu on 2010-10-12
Unfortunately, Nvidia does not officially support older graphics card like the one you have. That's why Ubuntu has so many different versions of their driver. But there is not much they can do without Nvidia's help. You might have to go back to 10.04 in order to use 3d effects on your card or but a new one.

---

### Post by cuderanch on 2010-10-12
Thanks. It sounds like I'm not alone. I agree that I'll have to search for a newer card.

---

### Post by WhoSayIn on 2010-10-13
im also facing the exact same problem, but however i dont have an Xorg.conf file in /etc/X11, but there's xorg.conf.failsafe

i also tried to rename xorg.conf.failsafe to xorg.conf.ff and rebooted my laptop, but still the same problem. i have an on board intel graphic card.

any suggestions?

---

### Post by Velophile on 2010-10-13
Think there are two problems floating around.

First one is that older cards aren't supported by the new xorg server, it's a known issue, which is in the release notes (available at [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Graphics%20and%20Display)). Specifically:

* The new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers. Bug 626974

****************************************************************

Second one, that's troubled me, lets me update and boot to the logon screen but there's no signal going to the VGA/Monitor, I get the 'no signal'/black screen on my monitor.  I know it's got to the logon screen because I can hear the 'tom-toms'.  I can get to a tty/shell (CTRL+ALT+F1) and logon ok.

I've got an NVidia 8300GS and it appears to not work with the drivers included in the Maveric release.  To get a working (but low graphics) desktop:

sudo apt-get purge nvidia-current
sudo rm /etc/X11/xorg.conf

reboot, it should be working in low graphics mode..in which case good, we know it's the NVidia drivers.  To get the NVidia card working in non-low graphics mode I've downgraded to older drivers by:

Download the older nvidia-current package from this page [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973340:](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973340:)

wget [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973340/+files/nvidia-current_256.53-0ubuntu3_i386.deb](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973340/+files/nvidia-current_256.53-0ubuntu3_i386.deb)

then install it:

sudo dpkg -i nvidia-current_256.53-0ubuntu3_i386.deb

and configure xorg:

sudo nvidia-xconfig

Interestingly if I go to the NVidia site to download their driver install package for my card it's the 256.53 one's it recommends as the latest appropriate version, not the 260 ones in the maverick repos'.

Hope that helps.

---

### Post by rjakiel on 2010-10-13
Same here.  I have the same exact problems where it will boot and hang on the splash screen.  I press ctrl+alt+F2 and then login through console and startx manually.  I am NOT running a nVidia card just the embedded Intel chipset in my HP desktop.

---

### Post by liedele on 2010-10-13
I'm also seeing the same problem , with a stock hp dc7600, was running 10.04 upgrade to 10.10 and it does not like the intel 945G graphics anymore, will only run failsafe.

---

### Post by jocefus on 2010-10-14
I have a fairly new discrete card (gt240) and since recent upgrades to lucid my machine (amd64) boots fine to tty1 then seems to hang for some time (30-40sec) before finally loading gdm. I have upgraded to maverick and am still experiencing the issue. Also the GRUB_GFXPAYLOAD_LINUX argument in /etc/default/grub seems only  affective with onboard nvidia graphics chipsets (atleast on my machine).  However, I can force splash and tty resolution using uvesafb.

---

### Post by Bloemetjesgordijn on 2010-10-15
Same problem here.

First tried to upgrade ended in a command line interface
Secondly tried a clean install....no avail.

System: KUbuntu 10.10 64 bits
ATI graphics 3450

Cheerz

Bloemetjesgordijn

---

### Post by GavinP on 2010-10-15
Why has this been marked as solved ?

It certainly is not with the Intel chipset !

Thanks

Gavin

---

### Post by mionescu on 2010-10-15
I guess it was marked as solved because the original message was related to Nvidia drivers and not the Intel ones. You might want to create a new thread to make sure you receive answers to your questions. The problem and solution are probably different.

---

