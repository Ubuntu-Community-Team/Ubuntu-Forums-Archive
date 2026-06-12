---
title: "Grub doesn't recognize usb or ps2 keyboard"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by scardien on 2011-06-13
hey guys - i just upgraded my desktop from an old version of linux mint based on ubuntu 8.04.  my comp is a dual boot linux/xp, and i didn't have any problems with GRUB before the upgrade.  since upgrading to ubuntu 11.04, however, GRUB doesn't recognize my keyboard at all, regardless of whether i use a usb keyboard or a ps2 keyboard.  i can still use the keyboard during boot to access my bios, and it's fine once i boot into ubuntu.  i tried enabling and disabling usb legacy support in the bios to see if that did anything when plugged usb, but it didn't work.  

i've searched the forums but couldn't find anyone else who had the same problem.  not sure what else to do.

---

### Post by dcstar on 2011-09-16
> **scardien said:**
> hey guys - i just upgraded my desktop from an old version of linux mint based on ubuntu 8.04.  my comp is a dual boot linux/xp, and i didn't have any problems with GRUB before the upgrade.  since upgrading to ubuntu 11.04, however, GRUB doesn't recognize my keyboard at all, regardless of whether i use a usb keyboard or a ps2 keyboard.  i can still use the keyboard during boot to access my bios, and it's fine once i boot into ubuntu.  i tried enabling and disabling usb legacy support in the bios to see if that did anything when plugged usb, but it didn't work.  

i've searched the forums but couldn't find anyone else who had the same problem.  not sure what else to do.

There are many posts that a Google search reveals that say that setting the "Legacy" USB option in your BIOS fixes issues like this.

---

### Post by scardien on 2011-09-16
thanks for the reply, but as i said in my original post, i've tried changing the legacy usb support option in my bios and that hasn't worked.

right now, i don't even have a decent workaround, so any ideas are appreciated.

---

### Post by xpucto on 2012-11-04
I had the same problem after BIOS update -  i could access the bios just fine but stuck at the grub screen. Well, let's say i was stuck 9 out of 10 times and occasionally   working which is really annoying. I read you tried to disable "Legacy Usb support" in the bios which didn't help,but you also mentioned that you tried  usb keyboard. Maybe disabling it using usb didn't work,but i did the same on my ps/2 keyboard and now it works like a charm.  Just sharing,so my apology if it doesn't help you,but maybe somebody else will find it usefull.** If using ps/2 keyboard explicitly disable "Legacy usb support" in the bios. **

---

### Post by danielnmnsantos on 2013-02-24
On my computer bios there is a "USB in DOS" option.  I enabled the option and it worked fine.

---

