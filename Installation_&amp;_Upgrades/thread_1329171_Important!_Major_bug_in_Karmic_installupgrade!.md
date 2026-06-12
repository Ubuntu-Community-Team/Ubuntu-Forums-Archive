---
title: "Important! Major bug in Karmic install/upgrade!"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by HuaiDan on 2009-11-17
Can I get a mod's opinion on this please?

Many, if not most, of the bugs that arise from upgrading to or installing karmic seem to be kernel related, particularly those involving sound and video. The correct kernel that most karmic installs should be running is 2.6.31-14-generic. You can check this at a terminal with 
uname -r
This should also be reflected in the grub boot menu.
This suspected flaw has to do with the installation of grub2 which occurs during the upgrade from jaunty to karmic.
I don't know if this happens in every case, but the grub2 upgrade occurred in my case along with many others.
During the upgrade, grub-pc (presumably) presents the hard disks it found in the system to which it can install grub2.
!!!It is VERY easy to click through this dialogue without selecting any drives!!!!!
If this happens, it seems to default back to the legacy menu.lst which loads the old kernel!!

This can be fixed by editing the menu.lst to load the correct kernel ( run sudo update-grub to get info on kernel versions installed).
I did this initially, but suffered from slow boot times. Then I dug a little deeper into grub2.

I took a leap and removed grub pc
sudo apt-get remove --purge grub-pc

DO NOT reboot at this time!!!

Run

sudo apt-get install grub-pc
If it asks you for a blank command line, just select ok. STOP when you have check boxes for your installed hard drives. Check off the hard drives on which you want to install grub2. a's always good, check b too if you have it.  Finish the install and shut down and restart the computer. Do not reboot: shut down hard and restart.  Your grub menu might look a bit different. You can change the look with startupmanager (synaptic, sudo apt-get install can get you a GUI startupmanager)

Check the kernel with  
uname -r
if it's 2.6.31-14-generic (as of this 17th day of November 2009) in both your boot menu and uname -r, you should be well on your way to fixing many of the bugs that became apparent after the upgrade to karmic.


I personally think the fact that the wrong kernel is loading might be responsible for many of the problems coming about after upgrades.

---

### Post by bluenova on 2009-11-17
I am not upgrading to 9.10 for other reasons, but I read in Karmic pre-release notes that GRUB2 would only be used for fresh installs, upgrades would continue to use GRUB. Is this not the case?

---

### Post by HuaiDan on 2009-11-17
Not sure. The facts I'm aware of are that I first became aware of the presence of grub2 troubleshooting a sound issue, and found it was already installed on my system, and that my menu.lst was loading the wrong kernel. Fixing grub to load the correct kernel has resulted successfully for many users. This lend evidence to the proposal that my experience may not be unique.

Another thing I am ignorant of is the exact relationship between grub-pc and grub2. Can grub-pc run without grub2, and how would this affect the boot behavior?

---

### Post by bluenova on 2009-11-17
I'm not entirely sure, as I haven't upgraded myself, but I think if your menu.lst is effecting GRUB then you are using GRUB legacy because GRUB2 uses grub.cfg instead of menu.lst from what I understand.

---

### Post by HuaiDan on 2009-11-17
That's exactly my point. If a drive isn't selected during setup (none are selected by default), then grub really isn't updated when karmic is installed. Thus, the old kernel loads.
Simply disallowing a null response or having a default selection could mitigate a lot of headaches.

---

