---
title: "Windows 8.1 not detected after uninstalling Ubuntu"
date: 2016-09-03
forum: Installation &amp; Upgrades
---

### Post by oonsay on 2016-09-03
Hey everyone.

First off, I'm sorry if this is in the wrong thread!

Here's what's going on: I configured a dual-boot between Windows 8.1 and Ubuntu 16.04.1 (I believe) a few months ago, with Ubuntu being the primary OS (the OS selection screen upon bootup wasn't the Windows one).

I eventually tired of alternating between operating systems and decided to use Boot Repair to delete it, as instructed by a tutorial. It deleted the Ubuntu OS, but also had me install grub on the Windows partition. I stopped that operation halfway through and used the OS Remover tool (from a similar package) instead as I thought it would be simpler, and I'm honestly blanking on how that turned out...

I did this all on a USB with Ubuntu installed.

When I restarted my computer and chose to boot to my HDD, I'm greeted with this message:

error: file '/boot/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue>

And I have no idea how to get Windows back. I can view all my files on that partition via the USB boot, so everything's intact, and I ran Boot Repair and the disk error checker from the USB without a solution. As of now, I have no usable operating system unless I have my USB...Does anyone know what to do?

---

### Post by darkeale on 2016-09-03
Hi,

When I've had this problem in the past I've done the following:

1 - Boot from Windows USB/DVD
2 - Select Repair Computer
3 - Advanced Options, Command Prompt (sorry, don't have it in front of me so not exactly sure, but there should be a way to get to a prompt).
4 - Run "bootrec.exe /fixmbr"
5 - Run "bootrec.exe /fixboot"
6 - Reboot

Hope I haven't missed anything out! Like I say, I don't have a machine to check so this is from memory!

---

### Post by oonsay on 2016-09-03
Thanks for that! I currently have only one USB drive that has Ubuntu on it, so I'd need to buy another and load Windows onto it.

However, I do have a spare, unopened copy of Windows 8.1 Pro that I'm never going to use. Would that work, or would that delete all my files as it's a new OS installation rather than repairing an old one?

---

### Post by darkeale on 2016-09-03
Afraid I haven't tried with a Windows 8 DVD, only with a Vista one, but with that I had the option to get to the repair options without the OS installation starting. I'm pretty sure that OS installation won''t kick off automatically so you'll have chance to abort if the "Repair" options aren't there.

---

### Post by oonsay on 2016-09-03
Alright, the Windows 8 disc gave me the option to repair it. However, /fixboot came back with the error message "Element not found."

I booted to Ubuntu again, opened GParted, and deleted all the partition reserved for Ubuntu, which was already gone. I'm still getting the same error, though, and /scanos tells me Windows is on D: instead of C:. Any ideas? :(

---

### Post by darkeale on 2016-09-03
Hmmm...in GParted, can you check that the Boot flag is set on the Windows partition? There should be a "Flags" column which shows which flags are set. If it isn't set you can right click on the partition, choose "Manage Flags", then set the Boot flag there. Then try the Windows bootrec steps again.

---

### Post by oonsay on 2016-09-03
I'll do that! I wanted to see if the automatic repairs option Windows gave would do anything, so I'm just waiting for it to finish. 

I really, really appreciate all your help. Thanks a ton :)

---

### Post by darkeale on 2016-09-03
You're welcome, happy to help! :) I've never had any luck with the automatic repairs tool but hopefully it's more successful for you!

---

### Post by oonsay on 2016-09-03
Haha, I don't expect much from it :P 
I also attempted to Refresh my PC before the automatic repair, which I had to do a few years ago when something was making it blue screen every boot. It's telling me the drive Windows is on is locked, now, though—is that a clue to solving this?

---

### Post by darkeale on 2016-09-03
Could be. Is that after the Automatic Repair or the bootrec commands? Did you try the bootrec commands again?

---

### Post by oonsay on 2016-09-03
Oh, the automatic repair is still in progress and I'm hesitant to force a shut down in case I lose files or damage the drive, unless you think it's harmless.
After the repair is done, I'll flag the Windows partition and retry the bootrec commands.

---

### Post by darkeale on 2016-09-03
Ah I see. Probably best to leave the automatic repair to do it's thing in that case.

---

### Post by oonsay on 2016-09-03
Agreed. It's nearly 1:00 a.m. where I am, so I think I'm going to head to bed and let my computer work until morning. If flagging the partition doesn't work, I'll be back here :P

Again, thanks so much for all your help, it's been invaluable. I hope you have a good night/day!

---

### Post by darkeale on 2016-09-03
No problem at all! :) If you do need more help let us know!

---

### Post by oonsay on 2016-09-03
I got it working!
The boot flag solved the grub problem, but my C: drive was still locked and I couldn't access it in diskmgmt or defragment it. The disk would also hang spontaneously, and indeterminately. Turns out, an SD card I put in my laptop for safekeeping was interfering with it—I removed it and everything seems to be in order. 
If something weird happens, I'll be back, haha. But until then, I couldn't have done this without your help. Thanks again, man!

---

### Post by darkeale on 2016-09-04
You're welcome, glad you got it working! :)

---

