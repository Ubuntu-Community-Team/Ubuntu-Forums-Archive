---
title: "NEW INSTALL, 10.10 &quot;cannot mount ISO during boot&quot; ??"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by chillcat34433 on 2010-10-29
I'm new to this forum. I have installed Ubuntu on my prior laptop (WITH CD Drive).
I currently have an ASUS Eee PC (NO CD DRIVE), using an external cd drive.

--downloaded the 10.10 version
--Mounted all files to cd-rw disk using ISO software (looks good!)
--Set Bios settings to Boot:USB
--restarted, Ubuntu begins, I hit [ENTER]
--Language option pops up, [English] 
--Then I click [INSTALL]
--it begins doing its thing, about 5 minutes, then goes to a screen with an error message.

[B](initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem:squashfs[/B]

I've been searching high/low for a fix to this and cannot get a straight answer or explanation of what is going wrong.  Please help ?

---

### Post by ajgreeny on 2010-10-29
After the language selection, if you hit any key a menu will appear with 5 options, one of which is to check the install media (CD) which is worth doing, as it sounds as if your burn may be faulty.

If any errors show, reburn the iso again to CD at a slow speed, and while burning don't use the machine for anything else.  I am assuming the iso file you used is also a good one.  You can check that with the published md5sum figures shown at
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) though I am not sure how you do it in windows, if that is all you have at the moment.

---

### Post by chillcat34433 on 2010-10-29
yeah I had done the cd check, memory check options in that Ubuntu menu section. I even reburned ubuntu onto a cd-r and its the same thing, gonna try the external cd player/and cd on my other laptop and see if I get the same results. I guess having an external cd player is more annoying it looks.

---

