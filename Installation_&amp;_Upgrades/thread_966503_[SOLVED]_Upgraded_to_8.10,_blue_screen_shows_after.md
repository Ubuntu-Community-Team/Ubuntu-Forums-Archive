---
title: "[SOLVED] Upgraded to 8.10, blue screen shows after login"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Irishpolyglot on 2008-11-01
Hey guys!! I've checked around and a couple of people are having the same problem as me, but I tried their solutions to no avail!!

After upgrading to 8.10 (and confirming each time to allow it to upgrade particular files), now when I boot up after logging in I just have a blank blue screen. The mouse works fine and the keyboard lets me access the terminal. CTRL+ALT+F1 shows the following messages (transcribed as I look at the laptop from an Internet cafe):
> Starting up ...
Loading, please wait ...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/c***LOTSOFNUMBERS***) = dec(8,5)
kinit: trying to resume from /dev/disk/by-uuid/c906ffa1-***LOTSOFNUMBERS***
kinit: No resume image, doing normal boot...

Based on recommendations in similar threads, I ran ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
``` and rebooted and also tried ```
sudo dpkg-reconfigure xserver-xorg 
sudo /etc/init.d/gdm restart 
``` (after backing up the original, and then restoring it again when this didn't work).
I'm still staring at a blue screen! Any advice hugely appreciated. I'm on a DELL Inspiron 9400 with Nvidia 256MB GeForce Go 7900 GS PCI Expressx16 Graphics Card. Everything was working fine in 8.04 before upgrading.

I'm sure a kind soul will point out something simple that I can try so I can have my computer back and get to check out 8.10 :D
Thanks for any help!!

---

### Post by ajgreeny on 2008-11-01
It may not help at all but could be worth trying.  Boot up in recovery mode, the second choice in your grub menu.  You will get to a menu choice which should include xfix (at least that is what I remember it to be).  Choose that, and the system should go through the detection as if a new install, and may sort out the problem if it is as simple as your graphics card and driver.  If that is no help you will need someone better than me to help further.

---

### Post by Irishpolyglot on 2008-11-01
Thanks for the suggestion! I tried that too and it didn't help. Any other ideas guys? Thxs!

---

### Post by Irishpolyglot on 2008-11-01
I've found a temporary work around!! :)

When on the log-in screen (or if it logs in automatically, press CTRL+Alt+Backspace) click "Options" then "Failsafe Gnome" and then log in as normal and it should work!

When inside I see that it needs to update the NVIDIA Hardware Drivers. I tried to select this option, but the update goes to 0% and does not go beyond it, then the update screen disappears. It's a separate issue I'll solve tomorrow. For the moment I have full access to the OS and everything else seems to be working as long as I'm in Failsafe Gnome! :)

---

### Post by gulch on 2008-11-01
Quote:
Originally Posted by jerrylamos View Post
Might be the same black screen problem I've been getting with Intel graphics since Aug 13. Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects. If you want to try compiz again, install with Synaptic.

Jerry
[http://ubuntuforums.org/showthread.php?t=965478&page=2](http://ubuntuforums.org/showthread.php?t=965478&page=2)

please reference, why not try in this way?

---

### Post by Irishpolyglot on 2008-11-01
Gulch, I appreciate the help but you really should read people's posts fully. I tried removing compiz (after having read the thread you referenced) and showed that in my initial post. It was an NVIDIA driver conflict and I have a temporary work around as I suggest above.

---

