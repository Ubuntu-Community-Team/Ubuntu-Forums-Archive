---
title: "Install to CF with 9.xx - NO GRUB!"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by bpan123 on 2009-12-21
I've been trying to install 9.04 or 9.10 - ubuntu and xubuntu.  To no avail!
Best bet is to stop it from trying to format as ext4 and use ext3.

Even so, I still have not been able to get grub onto the MBR.
I've tried all the tricks and work-arounds I could find links to, but still, I have a fully installed xubuntu 9.10, with NO GRUB.

[SIZE=5]NO BOOT.[/SIZE]

And so far nobody seems to have a working solution.
Am I the only one?  (based on my searches... prolly not...)
What's going on here?!?!

somebody must have a clue!

bp

---

### Post by drs305 on 2009-12-21
You are going to have to provide more information for detailed responses.

What happens when you try to boot?

There are links in my signature line on Grub 2 - "GRUB2" is the community doc. REview it if you haven't already seen it, especially if you get a "grub" or "grub-rescue" prompt.

It would help to have the results of the bootinfo script:
Download from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
```
cd ~/Desktop && chmod 755 boot_info_script042.sh && sudo ./boot_info_script042.sh
```

Post the results here.

---

### Post by bpan123 on 2009-12-21
In fact, I've been trying for days now.
D945GCLF w/ 1MB DRAM, 8G266x (udma enabled) CF.

I've driven myself silly trying to find solutions to getting this thing to boot (boots windows just fine!) but apparently ubuntu variants are not able to fix a MBR....

... or so it would appear.

Yes, I'm huffed.  I'm appalled that there must be hundreds (if not thousands) of users out there that are suffering the same issue as well.

I'm not a noob.  

But I'm very frustrated by an otherwise awesome OS that simply can't do something as simple as install itself onto a CF card.

'Nuff said.

Brian

---

### Post by bpan123 on 2009-12-21
@drs305: I've read all the grub2 info and recovery info - and tried all the "tricks" to no avail.  I'm still sitting here with a fully loaded CF with no GRUB.

It would seem that GRUB WILL NOT INSTALL.  PERIOD.

I've tried alternate install CD's.  Live CD's with lots of mods, all of the mods on the GRUB2 page, and I'm still sitting here with a box that won't boot Ubuntu.

I've seen all the prompts - from Grub-rescue to grub-file not found.

Still no GRUB that will actually boot ubuntu.

D945GCLF w/ 1GB DDRAM; 8GB CF, w/Marvell 88SA8052 based SATA adapter, booting from either an IDE or USB attached CDROM.  

This needs to be addressed immediately!

There ARE problems with ext4 and CF media!

Even ext3 doesn't allow updating the MBR...

ADDRESS THIS ISSUE NOW!

I've spend too much time trying to fix this - and found no useful responses here.

---

### Post by PRC09 on 2009-12-21
[http://www.thinkwiki.org/wiki/Compact_Flash_boot_drive](http://www.thinkwiki.org/wiki/Compact_Flash_boot_drive)

---

### Post by presence1960 on 2009-12-21
> **bpan123 said:**
> @drs305: I've read all the grub2 info and recovery info - and tried all the "tricks" to no avail.  I'm still sitting here with a fully loaded CF with no GRUB.

It would seem that GRUB WILL NOT INSTALL.  PERIOD.

I've tried alternate install CD's.  Live CD's with lots of mods, all of the mods on the GRUB2 page, and I'm still sitting here with a box that won't boot Ubuntu.

I've seen all the prompts - from Grub-rescue to grub-file not found.

Still no GRUB that will actually boot ubuntu.

D945GCLF w/ 1GB DDRAM; 8GB CF, w/Marvell 88SA8052 based SATA adapter, booting from either an IDE or USB attached CDROM.  

This needs to be addressed immediately!

There ARE problems with ext4 and CF media!

Even ext3 doesn't allow updating the MBR...

**_*ADDRESS THIS ISSUE NOW!*_**

I've spend too much time trying to fix this - and found no useful responses here.

Maybe if you would follow drs305's suggestion and run the boot info script instead of your fingers we may be able to help you. I reiterate:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB w/ CF inserted. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

