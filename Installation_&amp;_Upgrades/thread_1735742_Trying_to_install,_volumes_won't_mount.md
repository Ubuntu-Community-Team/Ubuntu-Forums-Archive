---
title: "Trying to install, volumes won't mount?"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Kirasa on 2011-04-21
I got a new computer today, a Compaq Presario CQ56, with Windows 7 preinstalled, and I want to dualboot with Ubuntu, but I'm having some problems. I'll explain what I've done so far, in case I did something wrong.

When I popped in my 10.10 Live CD, I was surprised to see there was not\ "install alongside existing operating system", which I thought I remembered from the last time I installed Ubuntu, but I chose manual partitioning and continued. I'd never done this before, so I quickly learned I  had to first create a (couple) partition(s). 

After freeing up a large amount of space and rebooting twice as recommended, I booted off the Live CD and opened GParted, intending to create a Ubuntu system partition, one for swap, and one for my home folder. When I right-clicked on my unallocated space, I got the error message "It is not possible to create more than 4 primary partitions". After a little googling, I found I had to eliminate one of my primary partitions and create a new extended partition, which I could then partition further. Noticing I had a partition that didn't seem important, HP_TOOLS, I googled and found [COLOR=Blue][this]("http://ubuntuforums.org/showthread.php?t=1400095"). [/COLOR]

When I inserted my flash drive, it didn't automount. When I tried to mount by right-clicking and clicking "Mount", nothing happened.  I also cannot mount the HP_TOOLS partition, nor any other. They don't mount when I click on them in the Places menu, and they don't mount when I right-click and choose Mount.

My main question is "Help! How do I install Ubuntu?", but I think if I can create these partitions, which requires mounting the drives (I think), I can figure the rest out.

A screenshot of my GParted window is attached, if that helps. (I couldn't see how to insert it without a URL)

Thanks!

---

### Post by Hedgehog1 on 2011-04-21
Kirasa,

Here is my 'HOW TO' guide.  This is based on removing the larger 'HP_RECOVERY' partition, so you can do the same or swap /dev/sda3 for /dev/sda4

Once you have resolved backing the partition you, follow this basic flow:


When all four primary partitions are taken (the HP install)

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete':[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create you sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-04-21
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Select this during the install:[/COLOR][/SIZE]
[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

### Post by Kirasa on 2011-04-21
Awesome, thank you! I have RECOVERY and HP_TOOLS though, and my understanding is the RECOVERY partition is equivalent to a recovery disk, and I don't want to delete that. Am I wrong?

---

### Post by Hedgehog1 on 2011-04-21
> **Kirasa said:**
> Awesome, thank you! I have RECOVERY and HP_TOOLS though, and my understanding is the RECOVERY partition is equivalent to a recovery disk, and I don't want to delete that. Am I wrong?

What we suggest is that you create 2 sets of recovery DVDs using the Windows 7 software that dose that, store them in a safe place and and then re-use the partition.

Computer Manufacturers stopping including ready-made disk to save money, and added the 'RECOVERY' partition instead.


***The Hedge***

:KS

---

### Post by Kirasa on 2011-04-21
Okay, thanks. This may be a silly question, but is it safe to assume that I will still have mounting issues after I install?

---

### Post by Hedgehog1 on 2011-04-21
> **Kirasa said:**
> Okay, thanks. This may be a silly question, but is it safe to assume that I will still have mounting issues after I install?

That is hard to say.  The drive you were trying to mount - can you see it using the Ubuntu Disk utility?  Do other USB drives mount?

**Were you using a USB 3.0 port?** (you cannot boot from USB 3.0 ports in Ubuntu yet, and I don't think you can mount from them unless you have installed on the disk and have a more recent kernel running).

Try those variations first from the LiveCD/LiveUSB.


***The Hedge***

:KS

**EDIT: **Just checked the data sheets your PC - they are USB 2.0 ports, so it is not that...

---

### Post by Kirasa on 2011-04-21
Actually, this time I am having no problems mounting anything. I don't know what the issue was the first time. I guess I can follow your guide now, and I'll hopefully be all set! (The recovery disks took a very long time) Thanks for all your help. (I'll mark as solved when I know I was successful.)

---

### Post by Kirasa on 2011-04-21
Actually, one more question. In your guide, when sda5 is setup, should I mark it for formatting? It doesn't look like it in the screenshot of the "Change..." window, but it's marked afterward, and when I press Install Now I am asked if I want to mark it for formatting.

EDIT: Well, I did it, with partitions for /home, /boot, and /. I formatted all three, it remains to be seen if that was correct. Worst case scenario I reinstall I guess. Thank you!

---

### Post by Hedgehog1 on 2011-04-22
> **Kirasa said:**
> Actually, one more question. In your guide, when sda5 is setup, should I mark it for formatting? It doesn't look like it in the screenshot of the "Change..." window, but it's marked afterward, and when I press Install Now I am asked if I want to mark it for formatting.

EDIT: Well, I did it, with partitions for /home, /boot, and /. I formatted all three, it remains to be seen if that was correct. Worst case scenario I reinstall I guess. Thank you!

Congrads on installing Ubuntu!!!

I will have to make a fresh set of install screen captures Natty/11.04, so I will be sure to correct the graphic then, thanks for the feedback.

The Hedge

:KS

---

