---
title: "Lost Boot Splash Sceen After Second Distro Install"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2008-05-19
Hello Everyone,

This one has me stumped.  I wanted to install a second distro on my laptop where Hardy is my main OS, but is still not performing well.  I needed something I thought would be a little more stable until Hardy gets a little more mature.  So, I added an extended partion and install Slackware, never touching the partition that Hardy is installed on.

After the Slackware install, Hardy no longer has the famous moving bar (splash screen) during boot-up.  It boots up OK and gets me to the login screen, but totally in text mode.  It also shuts down in text mode as well now.  I really feel more comfortable having the splash screen, for both boot and shutdown.

Anyone have any ideas how to restore this?  The menu.lst still has the splash entry in the boot line.

Any replies appreciated.

Bob

---

### Post by Pumalite on 2008-05-19
How do you boot Slackware?

---

### Post by bobnutfield on 2008-05-19
Well, as a matter of fact, it is not booting, but I did not install a bootloder with Slackware and just edited the menu.lst file installed with hardy, which is the grub boot installed.  I haven't able to actually boot into Slackware, getting grub errors.

But the Hardy partition was never touched.  Have no idea how this could have happened

Bob

---

### Post by Pumalite on 2008-05-19
Maybe the problem is in the editing of your menu.lst

---

### Post by bobnutfield on 2008-05-19
Yes, I considered that, but it was first noticed when I first rebooted in Hardy to edit the menu.lst.  It was then that I found the boot splash screen gone, before I edited the menu.lst.  I checked to see if anything had changed in the menu.lst for Hardy's entry and all is the same as before.  Very strange.  I know of no where else that this boot screen options are found, and they haven't changed.

Bob

---

### Post by Pumalite on 2008-05-19
Do you have 'quiet splash' in your kernel line?

---

### Post by bobnutfield on 2008-05-19
Yes, this is the entry:

> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=41e116b8-8942-43b7-919c-724f30b65c68 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

Nothing changed.

---

### Post by Pumalite on 2008-05-20
Post:
cat /boot/grub/menu.lst

---

