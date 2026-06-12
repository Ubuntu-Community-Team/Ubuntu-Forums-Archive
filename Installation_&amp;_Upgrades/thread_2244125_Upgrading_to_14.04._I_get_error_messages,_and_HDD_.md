---
title: "Upgrading to 14.04. I get error messages, and HDD keeps running"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by eadwacer on 2014-09-13
Upgrading my wife's five year old System 76 PC to 14.04. Install went fine. On restart I got a couple of "Problem detected, would you like to submit a report" messages, but no details. After that, and on a subsequent restart, I get three "can't find file"s, followed by a "hit any key to continue". Then get a "scanning for Btrfs files" for a minute or so.  At that point I get my usual home screen. The few programs I've checked seem to work. However, the HDD keeps seeking, irregular pattern, for five or ten minutes before settling down. System Monitor shows low CPU use, low swap, low network. Highest activity process is the System Monitor.

To be honest, I don't know what file system I'm using -- it's the Ubuntu default. This is a vanilla install, with normal updates. We were running 12.04 until earlier this year, when we upgraded to 13.04 in preparation for this move. 

So, what's my next move to troubleshoot this?

---

### Post by grahammechanical on 2014-09-13
At what point in the loading process do you get this "can't find files" and "hit any key to continue" message? And what files can the loading process not find? That would give a clue.

We get the "scanning for btrfs files" message if we have installed on to a btrfs file system. If you open the Disks utility you will see your partition layout and what file systems you have.

With the btrfs file system we can take a snapshot of the OS or parts of the OS and then if we need to we can revert the OS back to the point the snapshot was taken. I am wondering if this System 76 PC came with some utility that let you or your wife do a system restore. It may have been using the btrfs file system to do that and now the machine cannot find the files that it was expecting to find.

The continued operating of the hard disk is most likely due to some instruction trying to complete and failing and then trying several more times before giving up.

Regards.

---

### Post by eadwacer on 2014-09-13
Thanks for the quick response.

1. On startup I get the Sys76 logo along with the 'hit <F10> for BIOS etc' messages. That holds for a second or so then the 'can't find file' message quickflashes on a black screen, and is immediately replaced with a purple screen with the same message repeated on three lines, with no mention of the filename, and right underneath it is the 'hit the any key'.  Hit a key and I get a black screen with flashing cursor, then the btrfs message. After a bit comes a purple screen with the typical Ubuntu .... in white, then black screen with same .... in yellow, then my home screen. 
2. I'm not aware of any system restore utilities, and I've owned three different System 76 PCs (that doesn't mean they aren't there). Disks says my main partition is Ext4.
3. Other anomalies, which might or might not be diagnostic, include loss of workspaces, and auto-activation of Anthy in Japanese mode. I'll worry about them later.

---

### Post by eadwacer on 2014-09-16
So, I went back to the "...and now I have this problem" thread and followed the "sudo apt-get clean...etc" instructions. No errors.
Power-cycling the PC gave me the same uninformative "can't find file" messages

Also got a purple screen with two "Error calling EVIOCSKEYCODE". They flash by so fast that even when I know they are coming, and where on the screen to look, I can't read more than half a word. I think they might be"
[ 11.232646] systemd-udevd[490]: Error calling EVIOCSKEYCODE: Invalid argument
...but I can't vouch for the numbers.

So, is this a systemd issue?

---

