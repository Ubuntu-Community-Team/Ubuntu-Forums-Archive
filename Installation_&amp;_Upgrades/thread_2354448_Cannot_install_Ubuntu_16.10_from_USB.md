---
title: "Cannot install Ubuntu 16.10 from USB"
date: 2017-03-02
forum: Installation &amp; Upgrades
---

### Post by noahsutter on 2017-03-02
Hi Ubuntu Forums. First post here, and I'm new to Ubuntu and the Linux World in general.

I'm having an issue with installing Ubuntu 16.10 and 16.04.2 LTS. I am able to download the ISO, burn it to a USB (From a Windows Device), boot from the USB, but once I get past the GRUB menu, I get a blank screen and my Monitor is unable to detect a display.

I do have an external GPU - Nvidia Geforce 970.

What's odd to me is that not only does 16.10 and 16.04.2 have this problem, but 16.04.1 did not have this problem. From a 16.04.1 installation, I am able to get past the GRUB menu and install/use Ubuntu just fine. Also, other Distros that I have tried recently, like Mint KDE and Manjaro, have not had this problem.

Please note that I have also tried "try without installing" and I was unable to get that to work, either.

I have tried alternating between Ubuntu versions, with 16.10 and 16.04.2 not working and 16.04.1 working with other flavors of Ubuntu, such as Kubuntu and Ubuntu Gnome.

I have also tried installing 16.04.1 and then doing an in place upgrade to 16.10, and after the installation and initial reboot, the same thing happens.

In the real world, I'm a Windows PC Tech, but this Linux thing has me stumped! Which is too bad because after distro-hopping, I think I have finally found a Linux home. And I have learned to love the Gnome DE.

Thanks in Advance for your time and help!

---

### Post by dajavex71 on 2017-03-02
I seen something similar on an older machine. Try the following on the ubuntu bootup screen, select F6 Other Options - highlight acpi=off(press space to select), then repeat for noapic.

---

### Post by noahsutter on 2017-03-02
I will install 16.04.1 LTS (which I know works), do an in-place upgrade to 16.10, and see if that works. I don't have that option from an installation USB, though, unless there is something I'm missing. I can't get past GRUB on anything last 16.04.1 without my monitor unable to detect a display. I'll get back to you.

---

### Post by yancek on 2017-03-02
I wouldn't bother upgrading to 16.10 because support for it ends in July of this year.  Use 16.04 which will have four more years of support.

---

### Post by noahsutter on 2017-03-02
My worry is, though, is that these newer versions of Ubuntu are coming out and I won't be able to install it on my main machine (which, by the way, isn't a slouch or an older machine in anyway) and miss out on all the cool new stuff.

---

### Post by noahsutter on 2017-03-02
Hi dajavex, I was unable to get that to work, since I can't get to a splash screen. My display gives up after grub.

---

### Post by ubfan1 on 2017-03-02
If you're booting in UEFI mode, the options need to be edited into the linux line of the grub selection.  Instructions at the bottom of the grub screen, type "e" to edit, then try adding nodeset in place of the "quiet splash" on the linux line.  Then boot (ctrl X) and see if that helps.  When running, from the software updater/settings/additional drivers, add the tested Nvidia driver.  nomodeset is the first thing to try for Nvidia problems, but there are many other options which may be necessary.

---

### Post by noahsutter on 2017-03-02
ubfan1:

I attempted, in UEFI mode, to replace "quiet splash" with nodeset. That had no change in my results.

I did get somewhere, though.

Going back to Dejavex's suggestion, I was able to boot into non UEFI mode and make those changes - highlight acpi=off and noapc. I also tried nomodeset.

This, however, DID get to the splash installation page, where I tried to install Ubuntu onto one of the three hard drives on my computer, one of them I dedicate to Linux.

When I got to the DE, I noticed that the resolution was low, which was obviously due to no Driver's present. This is normal and I have experienced this in installing other Distros, like CentOS and Fedora.

After trying to do a fresh install onto my Linux drive, it however hangs when it tries to create a GRUB menu, and I get an error stating that GRUB could not be installed, and I get a message saying to "install in another partition" or or "skip installing grub" or "cancel installation", for which none of the options actually work and I'm forced to force my PC off. What I noticed when it error'd on GRUB, that it actually tried installing it on a different drive - which was my native Windows drive.

I then reboot and went into my BIOS, turned off the SATA ports that had my 2 other drives and my DVD drive, and only left the one drive available for Linux to install. I tried again, booting into non UEFI and using nomodeset, and the installation actually completed.

However, when I restarted and tried going into the new Linux Drive, it gives me a black screen, stating that it's scanning my drive and 23674/9873497 files clean (this is a linux command, not Windows chkdsk function, mind you), or something along those lines. Then it just freezes, and nothing happens. So that's where I'm stuck, at this point.

Ugh >.<

---

### Post by dajavex71 on 2017-03-02
When it gets to the 
> [COLOR=#000000] Then it just freezes, and nothing happens. So that's where I'm stuck, at this point.[/COLOR]

Try hitting ALT-F1, this should take you to a console prompt.
The problem I think is related to the window manager being unable to load. so chances are it just looks frozen.

logon at the console prompt.
> sudo ps -e | grep dm

Result will vary, though something like the following should appear:
2577 ?        00:00:00 lightdm

Replace with the PID of your results:
> sudo kill 2577 

Then try to reload it:
> sudo service lightdm start

If all goes well, this will likely load, and automatically deposit you to the graphical logon.
If not, try pressing ctrl-alt-F7.

---

### Post by cwmoser2 on 2017-03-03
I too are having this same problem.
Try Ubuntu worked just fine - but the install failed.
Several attempt to install Ubuntu on my replacement PC failed - system hanged with Grub.
My solution was to just move to Linux Mint 18.1 Serena - everything went smooth and uneventful.
I think there is something buggered up with Ubuntu installations.

---

### Post by ubfan1 on 2017-03-03
Oops, my typo, that should have been nomodeset, not nodeset.

---

### Post by ubfan1 on 2017-03-03
Oops my typo, should have been nomodeset.  You need nomodeset on the first boot of the installed system too, then in software updater/settings/additional drivers, install the (tested) proprietary driver.

---

### Post by noahsutter on 2017-03-03
Dajavex:

I tried using that method. When I did, I got a "lightdm" was not installed. So, I installed it by going sudo apt install lightdm. Then it gave me an option for lightdm and gdm3, for which I picked gdm3. I was able to get to the lock screen (oddly enough, the regular Ubuntu log in screen, although I was on Ubuntu Gnome).

I also tried going back into UEFI installation on the USB, change to "nomodeset", and I was able to get Ubuntu to install without any kind of display driver. After booting into an installation and downloading/installing the Nvidia drivers through the Driver utility, after a reboot the screen becomes stuck on the hard drive scan that looks like Windows's chkdisk, and after I try the Dajevex's suggestion, at that point nothing happens and I can't get a display. Running init 5 doesn't either :/

I have also tried doing this from a fresh installation and a direct upgrade from 16.04.1...I can get Ubuntu to boot to desktop and install using nomodeset, but what I'm stuck on now is that I can't get it to go to the desktop without any kind of real display driver, whether it's nouveau or Nvidia drivers.

So close yet so far away :( I wonder what change is so huge between 16.04.1 and 16.10 that my machine simply hates?

And personally, I'm not a fan of Mint/Cinnamon...it's not a far enough departure from the Windows world :P

---

### Post by sudodus on 2017-03-04
> **yancek said:**
> I wouldn't bother upgrading to 16.10 because support for it ends in July of this year.  Use 16.04 which will have four more years of support.

+1

To be precise, I recommend that you install ***Ubuntu 16.04.1 LTS***. It is supported for 5 years from the release date, so until April 2021. See these links,

[http://old-releases.ubuntu.com/releases/xenial/](http://old-releases.ubuntu.com/releases/xenial/)

[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

### Post by noahsutter on 2017-03-15
Just circling back - I was able to get Ubuntu 16.10 installed using the "nomodeset" fix at start up. This worked with the Flagship Ubuntu - the reason I made this thread was that I was having a tough time getting Ubuntu GNOME to install, which I couldn't hack and I have given up on. Since I'm a Ubuntu hopper, I don't mind going with the latest and greatest to see what's available.

Thank you everyone that put time into this to help me out.

---

### Post by sudodus on 2017-03-16
Thanks for sharing your results :-)

---

