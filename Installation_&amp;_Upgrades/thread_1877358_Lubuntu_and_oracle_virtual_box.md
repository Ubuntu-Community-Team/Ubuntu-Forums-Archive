---
title: "Lubuntu and oracle virtual box"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by rishi_singh on 2011-11-08
I tried to instal lubuntu 11.1 inside virtualbox. But it gets stuck at "using the entire XX gb of vdi hard disk". I cannot continue to actual installation. Virtualbox installs lubuntu from a virtual drive. Please help me to solve this problem.

---

### Post by spcwingo on 2011-11-08
Have you tried partitioning yourself using the "something else" option?  If that fails, there's something else you can try.

Although there is not an alternate installer specifically for Lubuntu, you can still use the alternate ISO to get Lubuntu installed, like so:

After booting from to the alternate installer, select your language, and then press F4 for "mode".  Next, select "command line install" and then from the main menu select "Install Ubuntu".  Follow the on-screen instructions to install an Ubuntu command line system.  When prompted, reboot your virtual machine.  After the reboot (to the fresh command line install) you may have to switch to a virtual terminal (if the boot splash is still displayed) by pressing ALT+F1 (or F1-F6).  Login and issue these commands:

```
sudo apt-get install lubuntu-desktop
```

```
sudo apt-get clean
```

```
sudo reboot
```

If all went well, you should now be at your LXDM login screen.  :)

EDIT:  I guess it probably would have helped if I had remembered to put in a link to the alternate installer.  Anyways, here it is:  [clicky]("http://releases.ubuntu.com/11.10/")

---

### Post by rishi_singh on 2011-11-08
I did not see the install by command line option. But this time it installed when i unselected the download updates option. Strange. Thanks for helping.

---

### Post by amjjawad on 2011-11-08
> **rishi_singh said:**
> I tried to instal lubuntu 11.1 inside virtualbox. But it gets stuck at "using the entire XX gb of vdi hard disk". I cannot continue to actual installation. Virtualbox installs lubuntu from a virtual drive. Please help me to solve this problem.

Have you used Live-CD to do that? Have you checked MD5SUM before you create your Live Media? there are some points to consider before installation is made.
What is the size of your virtual HDD?

---

### Post by amjjawad on 2011-11-08
> **spcwingo said:**
> Have you tried partitioning yourself using the "something else" option?  If that fails, there's something else you can try.

Although there is not an alternate installer specifically for Lubuntu, you can still use the alternate ISO to get Lubuntu installed, like so:

After booting from to the alternate installer, select your language, and then press F4 for "mode".  Next, select "command line install" and then from the main menu select "Install Ubuntu".  Follow the on-screen instructions to install an Ubuntu command line system.  When prompted, reboot your virtual machine.  After the reboot (to the fresh command line install) you may have to switch to a virtual terminal (if the boot splash is still displayed) by pressing ALT+F1 (or F1-F6).  Login and issue these commands:

```
sudo apt-get install lubuntu-desktop
``````
sudo apt-get clean
``````
sudo reboot
```If all went well, you should now be at your LXDM login screen.  :)

EDIT:  I guess it probably would have helped if I had remembered to put in a link to the alternate installer.  Anyways, here it is:  [clicky]("http://releases.ubuntu.com/11.10/")

The correct link is: [http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/)

Find more stuff: [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

---

### Post by spcwingo on 2011-11-08
I'm glad that you got it going.  Happy Ubuntuing!  :popcorn:

---

### Post by spcwingo on 2011-11-08
> **amjjawad said:**
> The correct link is: [http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/)

Find more stuff: [http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Wow, I never knew that ya'll had an alternate installer for Lubuntu.  That's awesome news.  I've been doing it the hard way.  This will save me a bunch of time.  Thanks for the heads-up.

---

### Post by amjjawad on 2011-11-08
> **spcwingo said:**
> Wow, I never knew that ya'll had an alternate installer for Lubuntu.  That's awesome news.  I've been doing it the hard way.  This will save me a bunch of time.  Thanks for the heads-up.

A lot was going on lately ... check my thread - Lubuntu One Stop Thread. Isn't Lubuntu great? :D

You welcome :)

---

### Post by rishi_singh on 2011-11-08
**One problem - **I removed lubuntu because i was unable to instal guest additions for it. :(
I need that for getting full screen. Can anyone tell me how to solve this problem ?

---

### Post by amjjawad on 2011-11-08
> **rishi_singh said:**
> **One problem - **I removed lubuntu because i was unable to instal guest additions for it. :(
I need that for getting full screen. Can anyone tell me how to solve this problem ?

Hi,

You didn't answer my previous Qs and I'm not sure what do you mean by what you posted above?

---

