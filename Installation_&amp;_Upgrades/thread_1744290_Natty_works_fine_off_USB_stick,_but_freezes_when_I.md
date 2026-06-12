---
title: "Natty works fine off USB stick, but freezes when I try to install"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by MacMouse on 2011-04-30
Hi there,

I'm running Natty 11.04, booting from a USB stick. It works well. I have network access. Everything's fine. Until I try to install it. Then it freezes.

My machine: Asus EeePC 901

My EeePC has never been modified, so it has 4 gigs of RAM.

Any ideas?

thanks.

---

### Post by Rubi1200 on 2011-04-30
How many primary partitions are currently on the drive?

If you can post a screenshot of GParted from the LiveUSB that would really help.

---

### Post by MacMouse on 2011-04-30
Hi Rubi1200,

Thanks for your reply. Screen shot below.

I want to erase everything on the computer. I was hoping the Natty installer would guide me through partitioning, but it didn't get that far. It froze when going from the first screen to the second screen.

[IMG]http://img10.imageshack.us/i/screenshotunledwindow.png/[/IMG]

Link to screenshot:
[http://img703.imageshack.us/i/screenshotlx.png/]("http://img703.imageshack.us/i/screenshotlx.png/")

---

### Post by Rubi1200 on 2011-04-30
Did you choose the option to erase and use entire disk?

If you are planning on a complete fresh start anyway, try deleting all partitions with GParted leaving everything as unallocated and then start the installer again.

You will need to turn the swap partition off with right-click > Swapoff before trying to delete anything.

I assume you have enough RAM?

Is this a GPT disk by the way?

I hope you first backed up all important data.

---

### Post by MacMouse on 2011-04-30
I previously had the MeeGo OS on this computer. Thought I'd go back to Ubuntu. There is no valuable data on the computer.

Tried using GParted. It failed. Error message as follows:

[B]1 of 3 operations completed
>Delete /dev/sda1 (ext3, 250.00 MiB) from /dev/sda[/B]  [COLOR="SeaGreen"](it shows a green tick, operation succeeded)[/COLOR]
**>Delete /dev/sda2 (btrfs, 3.26GiB) from /dev/sda** [COLOR="Red"](it shows a red icon, operation failed)[/COLOR]
**Delete /dev/sda3 (linux-swap, 256.00 MiB) from /dev/sda**  [COLOR="Silver"](it shows no icon, operation not yet attempted)[/COLOR]

---

### Post by Rubi1200 on 2011-04-30
GParted should have a log with the messages of what went wrong. If you didn't save it, try the operation again and this time post the details here.

Must admit, though, it is a bit odd that it failed.

---

### Post by MacMouse on 2011-04-30
Thanks again, Rubi1200, for all your help.

I didn't save GParted's fault report. Instead, I went through each partition separately, and somehow managed to delete them all.

Then I rebooted off the USB stick. And now the installer is working, and has moved past the first screen (it is still installing as I speak.)

But at least that freezing problem is now gone.

Yes, it was odd. Both the installer and GParted froze when confronted with the partitions on my computer. Maybe there's a bug there somewhere.

Interesting that the installer found an old version of Ubuntu on my machine (I didn't know it was there), which must have co-existed with MeeGo. Both are erased now.

Sounds a bit like a bug to me. Anyway, thanks again for your help.

---

### Post by Rubi1200 on 2011-04-30
No problem, you are more than welcome :-)

Please post back if all goes well with the install and then you can also mark this Solved using the Thread Tools near the top of the page.

Good luck and enjoy!

---

### Post by srs5694 on 2011-04-30
/dev/sda2 (the partition that caused GParted to fail) uses Btrfs, which is brand-new and not yet ready for widespread use. My hunch is that your version of GParted simply lacks Btrfs support, or perhaps that support is still buggy. There's very little point to a 3.26 GiB Btrfs partition, BTW; that's too small for a full Ubuntu installation, and Btrfs's most important advantages over other filesysstems are in handling larger files and partitions.

---

