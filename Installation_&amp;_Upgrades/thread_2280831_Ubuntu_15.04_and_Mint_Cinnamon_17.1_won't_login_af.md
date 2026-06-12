---
title: "Ubuntu 15.04 and Mint Cinnamon 17.1 won't login after Nvidia driver install"
date: 2015-06-02
forum: Installation &amp; Upgrades
---

### Post by Lemonz on 2015-06-02
Hi everyone, I am completely new to the forum and this is only my second attempt at linux distros.

I'm trying to install nvidia graphics drivers for my Asus X550LN  (Nvidia GeForce 840M for the GPU) and when I try to login after the install, I get a login loop where ubuntu sends me to the login screen and after I type my password, it refreshes the login screen instead of going to the desktop.

Note: I'm 99.9% sure it's my fault.

What I've been doing is...

Install nvidia software for 840M, 64 bit linux
software  downloads to /home/lemonz/Downloads
I then run terminal
>sudo service lightdm stop           (to get out of x server)
[ctrl] + [alt] + [f1]
>cd /home/lemonz/Downloads
>sudo sh NVIDIA-Linux-x86_64-346.72.run     (file name)

it runs the installer and everything installs...then I restart my computer and boot linux and everything is normal, but when I try to login, I get the login loop I was talking about.
something similar happened when I attempted to run it on Linux Mint, but instead of a login loop it said cinnamon crashed or won't start so my solution so far has been to reinstall the operating system but then I obviously lose the driver.

Could y'all help me? I'm VERY new at this so simple terms would be greatly appreciated. Thank you!!!

---

### Post by ubfan1 on 2015-06-03
I'm experiencing the same problem with fresh install of Ubuntu 14.04 on a machine with the older Nvidia Geforce 6150.  No real solutions yet.  The noveau driver worked, but was very slow, so after the Nvidia driver inst, I got the login loop.  I tried removing all the hidden directories, and tried the guest login.  I tried the ```
ppa:xorg-edgers/ppa
``` repository, but the version was 125 just like the regular installs, and that did not help.  I did get it out of the login loop, but then it just produced either a screen with just a background, or a black screen (or a background which turned black after a few seconds).  I tried dropping back from unity, to xfce, and found the same black screen on login.  HOWEVER, xfce did work with the original kernel version from the install, not the latest from the updates.
  When I was just getting the background (unity), I could run a virtual terminal and export DISPLAY=:0, then run things on the X server on vt7.  ran ccsm and turned on the unity plugin and all the other stuff it required, then maybe that got me to the blank/black
screen.  nvidia-settings offered no insite.  Still working though the "blank screen" problems in askubuntu ([http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)) without much help.  I removed the xorg-edgers ppa, but  haven't tried the standard packages again yet.  There was another ppa, the ubuntu-x-swat/x-updates to try, and I still have another disk to install with the original working  14.04 on it to see how that was set up.

---

### Post by RobGoss on 2015-06-03
I'm thinking there must me something wrong with the install not sure if it's the way you created it or what. I have installed just about every distribution and grant you this, not all of them go smoothly especially on my older machines that have that [COLOR=#000000]Nvidia driver. Depending on your specs you might try a lighter version of Ubuntu it might work better.


[/COLOR]

---

### Post by Lemonz on 2015-06-03
I believe I solved the driver install issue. Under system details my graphics card use to show up as intel haswell, but now it is showing up as "GeForce 840M/PCIe/SSE2" so I'm assuming (maybe incorrectly) that I've successfully installed it.

How I did it is:
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get install nvidia-346
sudo reboot
```

For the way I did this, I didn't install the driver beforehand. To get the correct driver for your card, go to the nvidia drivers website, fill in the information about your card and find out what driver they want you to install. They wanted me to install "NVIDIA-Linux-x86_64-346.72.run", so I used "346" as my driver version.

I used these 2 pages to help me out:
[http://askubuntu.com/questions/412141/uninstall-nouveau](http://askubuntu.com/questions/412141/uninstall-nouveau)
[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

OKAY, just to remind you, I'm a complete noob at this...can someone tell me how to check to make sure I actually installed the Nvidia Drivers? Also if you can see something clearly wrong with what I did, please let me know.

Thanks everyone!

---

### Post by Lemonz on 2015-06-03
Sorry, I lagged and multi-multi post.

---

### Post by Lemonz on 2015-06-03
[COLOR=#222222][FONT=Verdana]Sorry, I lagged and multi-multi post.[/FONT][/COLOR]

---

### Post by Lemonz on 2015-06-03
[COLOR=#222222][FONT=Verdana]Sorry, I lagged and multi-multi post.[/FONT][/COLOR]

---

### Post by Lemonz on 2015-06-03
[COLOR=#222222][FONT=Verdana]Sorry, I lagged and multi-multi post.[/FONT][/COLOR]

---

### Post by Lemonz on 2015-06-03
[COLOR=#222222][FONT=Verdana]Sorry, I lagged and multi-multi post.[/FONT][/COLOR]

---

### Post by Lemonz on 2015-06-03
[COLOR=#222222][FONT=Verdana]Sorry, I lagged and multi-multi post.[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-06-03
Ah, but you have still to solve the issue of repeat postings. :)

If something is saying Haswell and also Nvidia I would not be surprised if you have hybrid graphics. Does this machine have Nvidia Optimus technology?

@Ubfan1

Make sure those latest Nvidia drivers you are trying to install support that graphic adapter. The latest proprietary video drivers often drop support for old graphic adapters. I have Nvidia GT220 and Nvidia 346 driver does not support it. So, I am using what Additional Drivers call "legacy binary driver" 304.125.

You can find out here

[http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk)

Regards.

---

### Post by ubfan1 on 2015-06-04
@grahammechanical
Oops, I had left off the driver (which was the 304 one) when I was talking about versions.  I took your suggestion to try Lubuntu and that performs acceptably with the nouveau driver.  My old Ubuntu 14.04 installation upgraded to kernel .,.. 39 and Nvidia 304.117 when it "started smoking".  Thought it was the motherboard, but eventually put new cpu thermal paste and tried the new install.  The old one I tried again immediately overheated with a burning insulation smell,so I stopped that and went to Lubuntu.  The new 304.125 does not overheat as fast as the older 304.117, but the machines was always marginal for running Unity (Ubuntu 12 would only run Unity 2d).  Anyway stock Lubuntu runs OK, thanks for the suggestion.

---

### Post by Lemonz on 2015-06-05
My gpu is supported by the 346 driver but no hybrid graphics.
Before I had the Nvidia drivers installed, the Nouveau couldn't read my graphics card, so it used the CPU's integrated graphics (Haswell from the name of the i7 processor). After I installed the right Nvidia driver though, my computer could read my GPU properly and now I see Nvidia 840m listed (correctly) as my graphics card.

---

