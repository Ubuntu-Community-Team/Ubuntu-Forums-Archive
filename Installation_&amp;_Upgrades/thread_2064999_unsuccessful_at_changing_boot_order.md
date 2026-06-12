---
title: "unsuccessful at changing boot order"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2012-09-30
So I have followed the instructions to change the default OS (I would like to boot into Win7 by default - don't shoot me, this is my work computer).

When I restart, the boot order remains as it was before I edited the Grub file.

I did run update after editing and saving Grub.

What am I missing.

This is a new 12.04 install.  Previously, I had downloaded a GUI to accomplish this after having the same problem that my edited changes did not take effect.

Advice would be appreciated.

Thanks.

Caruso

---

### Post by darkod on 2012-09-30
What exactly did you try to edit, /etc/default/grub or maybe grub.cfg?

You need to edit /etc/default/grub and then run the sudo update-grub.

Any change directly in grub.cfg is lost.

Also make sure the position of windows doesn't change, and if it does you will have to adjust /etc/default/grub again. If you use the title of the menuentry and not the posititon, it should be OK even if the position changes in the future. But you need to use the exact menuentry name.

---

### Post by carusoswi on 2012-09-30
Here is what I did:

sudo cp /etc/default/grub /etc/default/grub.bak

gksu gedit /etc/default/grub

Then, I changed Grub_Default=0 to Grub_Default=5 (that's my Win7 entry position)

After saving and closing the file, I ran

sudo update-grub

Then, I rebooted.  Nothing changed - not the order of the entries in my list nor the default (which currently is Ubuntu 11.10 - I loaded that earlier today to overcome a bad installation of 12.04 that trashed my Grub on that installation).

I can reopen my grub file, and the change is still there - 5 is the default.

So, what am I missing?

Thanks for your reply.

Caruso

> **darkod said:**
> What exactly did you try to edit, /etc/default/grub or maybe grub.cfg?

You need to edit /etc/default/grub and then run the sudo update-grub.

Any change directly in grub.cfg is lost.

Also make sure the position of windows doesn't change, and if it does you will have to adjust /etc/default/grub again. If you use the title of the menuentry and not the posititon, it should be OK even if the position changes in the future. But you need to use the exact menuentry name.

---

### Post by darkod on 2012-09-30
The default doesn't reorder the OSs in the menu. They are always in the same order, as detected automatically.

What it does is change which entry it will boot if you don't press anything. At the moment it should boot the 6th entry (not the 5th) because it starts counting from 0.

So, 0 is the first line in the grub boot menu, 1 is the second line, etc.

Count the position of windows again, and readjust if needed.

It should work.

PS. You can create different order of the menu, but that involves using the /etc/grub.d/40_custom file and disabling the automatic /etc/grub.d/30_os-prober.

---

### Post by carusoswi on 2012-09-30
I believe I did things correctly.  Counting from 0, my Win7 entry would be number 5.  If I change the default, should not new default be highlighted when the grub menu list appears?  

I used that GUI prevviously, and that is what happened.  The order of the list did not change, but when I would boot up, the Win7 entry would be highlighted and that is the OS that would load.

Today, even though I have changed the default= number, the top entry (#0) remains highlighted when Grub appears.

I must be doing something wrong, but cannot figure out what.

Thanks again for your help (and patience!)

Caruso

> **darkod said:**
> The default doesn't reorder the OSs in the menu. They are always in the same order, as detected automatically.

What it does is change which entry it will boot if you don't press anything. At the moment it should boot the 6th entry (not the 5th) because it starts counting from 0.

So, 0 is the first line in the grub boot menu, 1 is the second line, etc.

Count the position of windows again, and readjust if needed.

It should work.

PS. You can create different order of the menu, but that involves using the /etc/grub.d/40_custom file and disabling the automatic /etc/grub.d/30_os-prober.

---

### Post by darkod on 2012-10-01
Yeah, it should be highlighted. I thought you expected the order to be changed.

Something is not working as it should obviously.

Open the file /boot/grub/grub.cfg and take a look (don't edit, just look) what the default value is in there. I can't tell you right now where exactly to look since I don't have an ubuntu machine at hand.

The default value should be adjusted in grub.cfg after you ran update-grub. The boot menu uses grub.cfg so if the change didn't apply there as supposed to, maybe that's why you are not seeing it in the boot menu.

---

