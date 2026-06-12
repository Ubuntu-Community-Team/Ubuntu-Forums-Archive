---
title: "How to change the boot drive after installing Xubuntu?"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by gigacoasterfan on 2013-05-23
Hello forums,

I recently attempted to install xubuntu viz usb to my computer as a dual boot to windows 7. Everything was going smoothly, I had a C:/ partition, but I accidentally selected my windows 7 boot drive as my ubuntu boot drive. Both boot files are there and visible, but windows 7 is unable to boot. I was wondeing if there was a way to change the boot drive?

---

### Post by ohnonot on 2013-05-24
hmm.
you waited 13h for a reply, so i guess it doesn't harm if i take the initiative, although i know little about your particular problem.
but, since you said "...accidentally selected my windows 7 boot drive as my ubuntu boot drive...", i hate to be pessimistic, but to me it sounds like you accidentally deleted files crucial for windows to start.
if you think that is not the case, you will have to give us more precise information about what you see in the current boot process and what you accidentally did earlier.

---

### Post by Bucky Ball on 2013-05-24
Boot into Ubuntu and open Gparted. Is there a Windows partition there (it will be NTFS)? If there is, do this:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The problem you explain isn't really a problem because Grub should be in sda and will pick up the Win bootloader so something else has gone awry by the sounds. Win bootloader may have been damaged in the process. Boot Repair will tell you more. Install and run.

---

### Post by gigacoasterfan on 2013-05-24
Well, I ran boot repair, as it seems as though windows boot files were still there, but I am still getting errors.
[URL="http://paste.ubuntu.com/5697901/"]
Here[/URL] is my pastebin of boot repair.

EDIT: More info:

Windows boot loader is now functional. I can see linux, two tests, and two very strange options.

One is Windows Boot UEFI loader

Another is Windows UEFI bkpbootmgwf.efi

Both when clicked yield the same error after roughly 3 seconds-

error no such device: 7A85-54BF

---

### Post by Bucky Ball on 2013-05-24
Ah, the old UEFI nightmare! Now we are heading down a different path. I suggest you start doing some research on that. oldfred is our resident expert on all things install and boot but he's on holiday. Do a search for some of his threads regarding UEFI installs. They are a strange beast. Good luck.

(I think you can change UEFI boot to something else (GPT?) in the BIOS but I'm no expert on this, have a bit more of a dig, as suggested.) One thing I do know is both OSs need to be installed the same way, both UEFI or GPT or something ... sorry, not V helpful. ;(

* This might give you a start:

[http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=oldfred+uefi&ql=](http://www.dogpile.com/info.dogpl.t8.1/search/web?fcoid=417&fcop=topnav&fpid=27&q=oldfred+uefi&ql=)

---

