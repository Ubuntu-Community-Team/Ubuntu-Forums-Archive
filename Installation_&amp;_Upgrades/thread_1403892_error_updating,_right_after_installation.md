---
title: "error updating, right after installation"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by rlfny1 on 2010-02-10
I am brand new to Linux. Successfully installed Ubuntu 8.04 with dual-boot: Linux or Windows XP.  After installing, I was prompted to install over 400 updates. After installing about half of them, I got the error message: "failed to check for installed and available updates.  This is a major factor of your software management system.  Please check for broken packages with synaptic.  Reload the software information with 'sudo apt-get update' and 'sudo apt-get install -f'   Also, if I try to run update manager, after starting the attempt to download/install the remaining 278 updates, the process stops and I get the message: An error occurred.  E:dpkg was interrupted.  You must manually run 'dpkg--configure -a' to correct the problem.  E:_cache>open() failed, please report.  I also get the same error message trying to use Synaptic Package Manager.  I tried to run the requested commands, using a window I opened via the alt + F2 key combination, but to no avail.  Please help.  I wish I knew more about Linux; I am a beginner who knows a good bit about Windows, but not Linux, yet.

---

### Post by northrup on 2010-02-10
Try running the first two in a terminal (Applications > Accessories > Terminal), then type in the first commands you were prompted to run ("sudo apt-get update" followed by "sudo apt-get install -f").  Copy down the information both commands spit out and post it here.

If that doesn't work, try rebooting and selecting "recovery mode" at the GRUB menu.  I don't remember whether or not 8.04 has a recovery menu with an ability to repair the APT repository.  But, if not, you can try running those commands again, along with "sudo dpkg --configure -a".  It's worth a try.

Otherwise, the only really "easy" solution is to re-install Ubuntu.

---

### Post by pastalavista on 2010-02-10
You need to run 'gnome-terminal' [Applications|Accessories|Terminal] and then enter the command```
[COLOR="Red"]sudo[/COLOR] dpkg --configure -a
```. 
You'll be asked for your password. When you type it won't show but hit 'enter' annyway. Then enter```
sudo apt-get update
```and try update-manager again.

---

### Post by Sef on 2010-02-10
> Successfully installed Ubuntu 8.04 with dual-boot: Linux or Windows XP.   After installing, I was prompted to install over 400 updates.

Where you using 8.04.4?   You should not have that many updates for it, unless you were using something like 8.04.0.

---

### Post by rlfny1 on 2010-02-11
Thank you all for your advice.  Success!  I was able to enter "recovery mode" in the GRUB menu, and ran the various commands I was advised to run. One of them triggered a lengthy process which, when concluded, resolved ("fixed") my problem.

---

