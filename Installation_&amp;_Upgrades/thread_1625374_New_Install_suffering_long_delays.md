---
title: "New Install suffering long delays"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by Peter Bell on 2010-11-19
I'm running ubuntu on an i5-650, Intel H55 mobo system.  I have 4GB RAM.

I was running Lucid (AMD64) very happily, but then had a severe failure of the Samsung HD502HJ hdd (the smart report is showing more than 1000 bad sectors, increasing everytime I try to access the disk).

I have replaced that drive with a Seagate ST3500418AS.  Using ddrescue I was able to recover all but 9MB of the drive content.  However, with my /etc, /proc and /opt directories having gone missing, I decided that attempting to recover the installation was a lost cause so I went ahead and installed Maverick onto the new drive.  As part of this process I created a separate partition for my /home directory (recovered from the old drive).

Now, having installed only a few 'essential' packages (eg autofs5), I've realised that a lot of actions are taking well in excess of a minute to take effect.  For instance, clicking on 'Places->Computer', it takes approximately 100 seconds before the Nautilus window appears.

According to System Monitor, there is nothing using any significant resource during this time - it's as though something is waiting for a timeout to complete before actioning my command.

If I look at the processes in System Monitor during this time, I can see that the Nautilus process is showing 'autofs4_wait'.

Is anyone able to suggest what is likely to be causing this, and how can I fix it.

---

### Post by Peter Bell on 2010-11-19
Okay, I think that I have found the answer.

Because I had preserved my old home directory, my nautilus bookmarks had been retained.  Some of my bookmarks related to nfs shares, using the machine name ... a machine name which had been defined in hosts.  However,  I hadn't yet recreated the hosts file, so the name was not resolvable..

Now, for some strange reason, every time a nautilus window is opened, it seems that every bookmark is accessed ... because the host name couldn't be resolved for the autofs mounts, each one had to wait to timeout.

It seems, to me, that this is unhelpful behaviour!

---

### Post by dino99 on 2010-11-19
let say that you should not always trust what smart report says. Check for errors by loading gparted or similar, and run fsck on next boot:

sudo shutdown now -R

on your new hdd you'd better to make a fresh install instead of tweaking as you have your data in a safe place (/home)

---

### Post by Peter Bell on 2010-11-19
Thank you for the words of counsel!

I am, of course, simply using the smart report to confirm what had been experienced in use - the drive became write-protected because of the high incidence of read errors, and the system would not reboot because the etc, proc and opt directories had become inaccessible.  In addition, ddrescue experienced significant difficulty in copying the drive contents - as I said, 9MB remained unrecovered when the mains power went off during the block splitting phase.

Yes, I also concluded that, with the exception of recovering my home directory, a fresh install was the only sensible recovery route.

---

