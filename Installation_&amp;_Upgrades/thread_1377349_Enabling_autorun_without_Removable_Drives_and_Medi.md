---
title: "Enabling autorun without Removable Drives and Media option"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by pipedreamer on 2010-01-10
Hi all,

I've just partitioned my hard drive with GParted so that I have space to install and run Windows OS based programmes such as Monkey Island (wine simply won't work) and other PC games.

I have the Windows XP SP2 Installation CD but my OS (Intrepid Ibex) won't allow me to autorun the CD and proceed to installation.

Now having hunted around the net  little, it seems the answer is System->Preferences->Removable Drives and Media. Problem is, I don't have a Removable Drives and Media option on this menu.

Is there a workaround for this? E.g., is there a way of using the Terminal to enable autorun, or is there another way I can do this?

As I'm pretty new to this thing, feel free to use short words and detailed explanations :D

Thanks all!

Rachel

---

### Post by Morbius1 on 2010-01-10
You don't install Windows through another operating system.

You place the Install CD in the CD/DVD player and reboot to the Install CD, just like you did when you originally installed Ubuntu.

It could be I don't understand your post. Are you maybe trying to Install WinXP into VirtualBox on Ubuntu?

---

### Post by pipedreamer on 2010-01-10
Hello!

The PC came with Ubuntu already installed, so that's maybe the info I was missing - thanks for the help!

Rachel

---

### Post by Morbius1 on 2010-01-10
Just so you're not surprised by this experience. When you install WinXP it will overwrite the Master Boot Record and you will not be able to boot into Ubuntu after that. It can be repaired and there are many howto's in this forum so perhaps VirtualBox is the better alternative.

---

