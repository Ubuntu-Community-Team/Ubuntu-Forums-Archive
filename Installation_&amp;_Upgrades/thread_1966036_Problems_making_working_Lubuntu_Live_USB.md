---
title: "Problems making working Lubuntu Live USB"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Paideuma on 2012-04-26
I've been able to successfully download and install Ubuntu (AMD64) 12.04. I did so by (1) booting Ubuntu (AMD64) 11.10, (2) downloading the 12.04 ISO, (3) using the Startup Disc Creator to make a Live USB, (4) booting Ubuntu 12.04 from Live USB, and (5) using the Live USB's "Install Ubuntu" wizard.

I wanted to do the same thing for Lubuntu (AMD64) 12.04, but I've hit several problems.

FIRST PROBLEM
Ubuntu (AMD64) 12.04's Startup Disc Creator won't create bootable Lubuntu (AMD64) 12.04 Live USB. The SDC appears to run just fine, but when I boot from this Lubuntu Live USB, I get a pure black screen with a flashing white underscore cursor in the upper left.

I left it on this screen for >10 minutes (wondering if things were happening in the background), but nothing happened. When I removed the USB and rebooted, the machine booted back into Ubuntu 12.04. I ran an md5sum check on the Lubuntu ISO, just in case, but it passed.

SECOND PROBLEM
After hitting the forums, I downloaded UNetbootin and used it to recreate my Live USB. Because 12.04 came out today, UNetbootin didn't have it as a preconfigured option. So I manually pointed it to the Lubuntu ISO I'd previously downloaded.

When I boot from the Live USB, I get to a menu (progress!) that gives me several options. However, selecting any option except the top one ("Default") just causes my machine to reboot and reload the menu. Selecting "Default" launches a Live USB version of Lubuntu (progress!), but I don't understand why I couldn't just select "Install Lubuntu" from the original boot menu...

THIRD PROBLEM
While running the Live USB version of Lubuntu (AMD64) 12.04, the "Install Lubuntu" wizard fails when it attempts to copy the bootloader. (I think that's what it said. I'll try it again and report the exact error.) This happens after my previous Ubuntu 12.04 build has been wiped and after about 10 minutes of downloading/installing files.

This leaves my machine without a working OS. I had to reinstall Ubuntu 12.04 to write this post.

Any suggestions?

---

### Post by nosredna on 2012-04-26
I'm exactly at the point where you're at. I tried to make a bootable USB stick with Unetbootin, and it acted the same way for me. Whichever option I chose, it just left me stuck at a black screen which disappears and reboost back to the same menu if I press a button.

Then I tried usb-creator and the install worked fine, but when the installation was finished and it was time for reboot, I ran into the ever-blinking underscore as well. This is after I changed boot order and removed the USB stick. However, the fresh install of Lubuntu will boot normally if you leave the USB stick connected - don't remove it or change the boot order. But this is not very comfortable, I don't want to have the USB stick connected for ever.

What are we going to do, install 11.04 and upgrade instead?

Edit 1: Seriously. We're both unable to even install the new release. It's very silly. What computer do you use?
Edit 2: I just filed a bug report, you should do the same.

---

### Post by slumbergod on 2012-04-26
Neither usb-creator nor unetbootin produced a bootable live usb installer for me. I tried several times for each and all of them gave me a "boot error". 

So I concluded that 12.04's Xubuntu iso doesn't like my system. 

Then I tried making a live CD. First attempt failed so now on second run. 

It's very strange. I haven't had issues installing Xubuntu for the last 4 or 5 releases. Now even making a bootable installation disc is not working.

---

### Post by techsupport on 2012-04-26
> **slumbergod said:**
> Neither usb-creator nor unetbootin produced a bootable live usb installer for me. I tried several times for each and all of them gave me a "boot error". 

So I concluded that 12.04's Xubuntu iso doesn't like my system. 

Then I tried making a live CD. First attempt failed so now on second run. 

It's very strange. I haven't had issues installing Xubuntu for the last 4 or 5 releases. Now even making a bootable installation disc is not working.

Install Ubuntu and then add the Xubuntu Team PPA and install Xubuntu Desktop Environment. And then remove Ubuntu desktop with Synaptic Package Manager.

You don't need to use the Xubuntu boot disc to install the Xubuntu Desktop Environment. Same thing with Lubuntu.

---

### Post by nosredna on 2012-04-27
> **techsupport said:**
> Install Ubuntu and then add the Xubuntu Team PPA and install Xubuntu Desktop Environment. And then remove Ubuntu desktop with Synaptic Package Manager.

You don't need to use the Xubuntu boot disc to install the Xubuntu Desktop Environment. Same thing with Lubuntu.
Good tip, didn't think of that. So I don't have to do anything else than download Ubuntu 12.04, apt-get install lubuntu-desktop, then apt-get remove ubuntu-desktop? Things get very easy when all of these children distros are based on Ubuntu.

Edit: I'm burning a Live CD now, maybe that'll work.

---

### Post by nosredna on 2012-04-27
I didn't want to waste a piece of plastic so I installed Lubuntu 11.10 through USB and then upgraded manually to 12.04, works like a charm. So I would recommend you to do that as well Paideuma if you want the latest release of Lubuntu. It seems safer than downloading Ubuntu and install LXDE on top of that as a desktop environment. But they should really fix this .iso problem, we're already three that hasn't made it with the live USB, I bet there's a lot more out there.

---

### Post by Paideuma on 2012-04-27
Thanks for all your posts, nosredna! Too bad we haven't been able to get this solved via the forums yet, though I'm still hopeful.

> **nosredna said:**
> What computer do you use?
I'm on a Lenovo ThinkPad R61.

> **nosredna said:**
> I just filed a bug report, you should do the same.
Good suggestion! Where would I file it, though? From what I understand Lubuntu devs look in a different place than Ubuntu devs do.

> **techsupport said:**
> Install Ubuntu and then add the Xubuntu Team PPA and install Xubuntu Desktop Environment. And then remove Ubuntu desktop with Synaptic Package Manager.

You don't need to use the Xubuntu boot disc to install the Xubuntu Desktop Environment. Same thing with Lubuntu.
I didn't realize that the only difference between Ubuntu and Lubuntu was the desktop. Thanks for that. However...

> **nosredna said:**
> So I don't have to do anything else than download Ubuntu 12.04, apt-get install lubuntu-desktop, then apt-get remove ubuntu-desktop?
I tried this, but now I'm in a weird hybrid place. I ran:
```
sudo apt-get install lubuntu-desktop
sudo apt-get remove ubuntu-desktop
```
Now, when my machine boots up or shuts down, I get the Lubuntu "splash screen" (the screen with the dots that change colors from white to blue), but when my GUI loads, it's Ubuntu's (Unity?).

> **nosredna said:**
> I didn't want to waste a piece of plastic so I installed Lubuntu 11.10 through USB and then upgraded manually to 12.04, works like a charm. So I would recommend you to do that as well Paideuma if you want the latest release of Lubuntu. It seems safer than downloading Ubuntu and install LXDE on top of that as a desktop environment.
Yeah, I was afraid I'd have to do that. I agree with you on the safety comment, but I don't know enough about what's going on to be confident in my safety assessment. As I showed above, though, what I tried didn't pan out.

> **nosredna said:**
> But they should really fix this .iso problem, we're already three that hasn't made it with the live USB, I bet there's a lot more out there.
Agreed. Unless I'm mistaken, that means the only way to install Lubuntu 12.04 is via upgrade. This is concerning.

---

### Post by silentstone on 2012-04-27
> **Paideuma said:**
> I tried this, but now I'm in a weird hybrid place. I ran:
```
sudo apt-get install lubuntu-desktop
sudo apt-get remove ubuntu-desktop
```Now, when my machine boots up or shuts down, I get the Lubuntu "splash screen" (the screen with the dots that change colors from white to blue), but when my GUI loads, it's Ubuntu's (Unity?).


@Paideuma, it sounds like you need to change the default desktop that loads for GUI from Unity to LXDE.   Also, why is there enough of Unity remaining on the system to run after it was uninstalled via "apt-get remove ubuntu-desktop"?  What was removed/changed with that command?

---

### Post by marinara on 2012-04-27
i can verify "PROBLEM SECOND" on my PC.

for "PROBLEM THRID"  we'll need an error message, or the stage where ubiquity locked up.

I can also suggest using the alternate installer if you would like to try Lubuntu again.

---

### Post by SlasherIT on 2012-04-28
Installing the Lubuntu 12.04 iso to my USB using Startup Disk Creator on Ubuntu 12.04 keeps failing at 93%, saying wrong checksum or something like that, although I am sure it is the right checksum though...

---

### Post by Dennis N on 2012-04-28
> **silentstone said:**
> ... Also, why is there enough of Unity remaining on the system to run after it was uninstalled via "apt-get remove ubuntu-desktop"?  What was removed/changed with that command?

ubuntu-desktop is a meta package - essentially a list of other packages it causes to be installed by specifying them as dependencies or recommended packages. If you just discard the list only (that is, remove ubuntu-desktop), the packages in the list remain behind. (It's like throwing away your shopping list after shopping and putting the items away on the shelf. Discarding the list doesn't make the items disappear from your shelf.) 

For reference: Packages installed with ubuntu-desktop:

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

---

