---
title: "No boot splash in Lucid Lynx on system with ATI graphics card"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Alvin Chiu on 2010-05-07
I have been unable to get the fancy purple bootsplash (plymouth) since I installed Lucid Lynx on my ThinkPad T43. The bootsplash would up when I had booted off of a Live CD, but all future instances post-install only shows the blinking terminal cursor, followed by the GNOME log in screen.  This has occurred after upgrading from Karmic, and after attempting a fresh installation of Lucid.  Here's what I've tried so far without success:


[LIST=1]
[*]comment out "[FONT=Courier New]GRUB_HIDDEN_TIMEOUT=0[/FONT]" in the grub file
[*]tried running [FONT=Courier New]echo FRAMEBUFFER=y > /etc/initramfs-[/FONT][FONT=Courier New]tools/conf.[/FONT][FONT=Courier New]d/splash
update-initramfs -u[/FONT]
under su but it did not work because my conf.d directory doesn't contain a file called "splash", but only one file called "resume".
This fix was taken from [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801.](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801.)
[/LIST]
A Google search showed that a lot of users with this problem have NVIDIA cards; however I'm running ubuntu on a system with an ATI card.

Thanks in advance for any help.

---

### Post by bdw on 2010-05-10
Hey there! :)

Which ATI card or chipset are you running and are you using the proprietary ATI fglrx drivers?

-- Brian

---

### Post by Iskaros on 2010-05-10
I have the same problem!
ATI Radeon x1200

---

### Post by Alvin Chiu on 2010-05-21
Hi bdw,

I have a 64MB ATI Mobility Radeon X300.   I used the X.org video driver that was installed by default by Ubuntu.

-A

---

### Post by Alvin Chiu on 2010-06-20
bump

---

### Post by HeadHunter00 on 2010-07-01
EDIT: Oh! never mind, i fixed my problem with your step 2. but, i had to enable plymouth in bum first. to do that, install bum using synaptic, open bum (system-->administration-->bootup-manager), and then enable plymouth.

---

### Post by Alvin Chiu on 2010-07-26
> **HeadHunter00 said:**
> EDIT: Oh! never mind, i fixed my problem with your step 2. but, i had to enable plymouth in bum first. to do that, install bum using synaptic, open bum (system-->administration-->bootup-manager), and then enable plymouth.
Installed bum and checked off plymouth, plymouth-log, plymouth-splash, and plymouth-stop.  Applied changes and then restarted.  I still get the blinking cursor when I boot up.  Looks my computer is being very stubborn.

---

### Post by HeadHunter00 on 2010-07-26
sorry dude, i didnt have any experience with ati cards, only nvidia and intel.

---

