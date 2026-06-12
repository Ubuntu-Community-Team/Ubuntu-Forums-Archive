---
title: "ubuntu X server doesn't start after upgrade to ubuntu 10.04"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by vikashiiitdm on 2011-06-14
hiii all, 
recently i upgraded my laptop from ubuntu 9.10 to 10.04 but alas! after the upgrade i don't get anything, just the 10.04 boot up screen and my cursor after some time. when i run it in recovery mode and tried to startx from there , it gave me a message " no protocol defined " now i can only access my system in failsafe x mod. please help.

my system specifications are:-
interl core2 duo 2.0ghz, 2.0mb l2 cache
nvidia 8200mg 512mb graphic card
 and a fairly high internet connect of 8.0 mbps

---

### Post by mörgæs on 2011-06-15
Can you run 10.04 in a live boot?

---

### Post by MAFoElffen on 2011-06-15
> **vikashiiitdm said:**
> hiii all, 
recently i upgraded my laptop from ubuntu 9.10 to 10.04 but alas! after the upgrade i don't get anything, just the 10.04 boot up screen and my cursor after some time. when i run it in recovery mode and tried to startx from there , it gave me a message " no protocol defined " now i can only access my system in failsafe x mod. please help.

my system specifications are:-
interl core2 duo 2.0ghz, 2.0mb l2 cache
[COLOR=Red]nvidia 8200mg 512mb graphic card[/COLOR]
 and a fairly high internet connect of 8.0 mbps
1. Check your blacklist files in directory " /etc/modprobe.d/ ."   Look for a name similar to " nvidia-graphics-drivers.conf ".  Please post this. When posting this file, please use the " # " icon in the forum posting toolbar and paste the text within the CODE tags.

2. Another thing to check is your /var/log/xorg.0.log to see where is is erroring out.  Please post this file.  When posting this file, please use the " <> " icon in the forum posting toolbar and paste the text within the HTML tags.

3.  Is this NVidia 8200MG chipset an integrated video chipset (not PCI...)?

4.  If Yes to number 3, is it a Dell Latitude or Inspiron equipped with a UXGA UltraSharp TFT Samsung display?  (There's a bug with these and 10.04, with a particular workaround).  If not, there's 2 other workarounds for things that may show up in items 1 and 2...

EDIT- Please post your /etc/X11/xorg.conf... Theres something in that file that goes along with those 3 bugs and this chipset.

EDIT2: Sorry, Guess you would need to run in failsafe mode, or reference the first 3 posts of the sticky below to be able to boot into a Text Console mode or a LiveVD:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
To be able to see and copy those files to post them here.

---

