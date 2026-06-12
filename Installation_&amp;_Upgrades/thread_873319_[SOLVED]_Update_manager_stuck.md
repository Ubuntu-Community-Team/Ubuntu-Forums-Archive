---
title: "[SOLVED] Update manager stuck?"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by alayahlan on 2008-07-28
While performing the recommended updates, the update manager seems to have stuck for the last 10 minutes or so on one particular update. This is the first time I've had anything hang up...so I really wasn't sure what I should do. I attatched a screenshot. I have no closed the update manager or anything yet.

---

### Post by alayahlan on 2008-07-28
Okay...so after no response from here (or a few of my friends I was waiting on) 40 minutes of hang time got to me and I attempted to reboot. This was apparently a BAD idea because now after the initial login screen I'm stuck at a nice gradient peach blank page. Nothing....

HELP!

---

### Post by Pumalite on 2008-07-28
Try to get in Recovery Mode and do:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get diat-upgrade

---

### Post by alayahlan on 2008-07-28
How do I get to recovery mode?

I can choose to change sessions before the login screen and can select from:

()Last Session
1.Run Xclient script
2.GNOME
3.Failsafe_GNOME
4.Failsafe_Terminal


Do I want the failsafe_terminal to run that?

---

### Post by alayahlan on 2008-07-28
> **Pumalite said:**
> Try to get in Recovery Mode and do:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get diat-upgrade

first command attempts to reinstall the update that got stuck....but it continues to hangup in the same place on the terminal screen. How do I get past this update or skip/remove it?

it says:
Setting up language-pack-fr-base (1:7.10+20080205)
Generating locales...
  fr_BE.UTF.8...

---

### Post by alayahlan on 2008-07-28
A call to Ubuntu support solved. :)

---

### Post by a0u on 2008-07-28
I'm glad to see the that problem is solved.

Just FYI...

> **alayahlan said:**
> How do I get to recovery mode?

When you boot the computer, there is a GRUB screen that appears after the BIOS.  Press **Esc** to enter the GRUB menu; there should be a recovery mode option in the list.  But remember, if you do not have a dual-boot system, you have only three seconds to press Esc before the normal Ubuntu starts.

---

### Post by alayahlan on 2008-07-29
That's exactly what Ubunutu support had me do.

---

### Post by gstanley on 2008-07-29
> **alayahlan said:**
> That's exactly what Ubunutu support had me do.

What exactly did they have you do?  I tried to run the "dpkg --configure -a" from the recovery console and it still hangs trying to setup up the "fr" package.

---

