---
title: "Restoring GRUB2 Defaults"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ScripterJR on 2010-04-30
Hey guys,

I just upgraded to Ubuntu 10.04 LTS and decided to make my boot pretty but I did something I shouldn't have and now it boots weirdly and it also closes weirdly. I wanted to know if there is a possible way to restore the default settings of GRUB2. If so, could you please tell me :P

Oh, I forgot to mention, I didn't edit grub.cfg, I only edited 10_linux.

 Thank you.

---

### Post by oldfred on 2010-04-30
You can always totally uninstall grub2 and reinstall it. Do not reboot in between as you may never get back in.

You may want to back up the grub directories:
 GRUB 2 has three main parts:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

Make sure you reinstall to the correct directory probably sda.
purge old and reinstall new to sda
sudo apt-get purge grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by ScripterJR on 2010-04-30
> **oldfred said:**
> You can always totally uninstall grub2 and reinstall it. Do not reboot in between as you may never get back in.

You may want to back up the grub directories:
 GRUB 2 has three main parts:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

Make sure you reinstall to the correct directory probably sda.
purge old and reinstall new to sda
sudo apt-get purge grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

Im stuck at sudo apt-get install grub-pc grub-common. Won't let me choose which device to install GRUB on.

---

### Post by oldfred on 2010-04-30
Are you getting an error message or what screen are you seeing?

---

### Post by oldfred on 2010-04-30
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

That link is for converting grub2 to old grub but has a warning about some servers not having all the packages. You might try changing servers (system, admin, software sources) and see if that makes any difference.

---

### Post by ScripterJR on 2010-04-30
[IMG]http://img30.imageshack.us/i/screenshotmfa.png/[/IMG]http://img30.imageshack.us/i/screenshotmfa.png/

It simply won't let me choose. I tried almost every key on my keyboard.

---

### Post by oldfred on 2010-04-30
I thought I had a screen like that when I installed beta. You should only select sda. But I thought I just put an x in the box?? I worked for me. If you can skip this screen then you can manually install it, which I think the commands I already gave did.

If grub & grub common installed ok and it is just running the update exiting should be ok but then you still have to manually install:

sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

---

### Post by ScripterJR on 2010-05-01
That did the job thanks a lot :P I still think GRUB2 should have a command to restore defaults :D

---

