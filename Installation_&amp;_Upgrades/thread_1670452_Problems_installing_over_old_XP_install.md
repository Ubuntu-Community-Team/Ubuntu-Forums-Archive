---
title: "Problems installing over old XP install"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by hc803 on 2011-01-18
I'm installing 10.10 on another laptop (after successful and enjoyable install on previous laptop) but am running into some snags:

-Inserting 10.10 disc I got in the mail from Ubuntu, laptop boots from CD as it should, logo pops up and install begins.
-Start getting a string of error messages, most of which are the "SQUASHFS" errors.

Is this an issue with my XP configuration?  Would I be better suited to format the HD and erase XP and start from there?  I didn't have any issues on my other HP laptop, which is only about 1 yr younger than the one I'm having issues with now.

NOTE: computer is an HP Pavilion ze4805us.

---

### Post by garvinrick4 on 2011-01-18
#No it is working off of the CD not the HDD which XP is on.
#Does Ubuntu work when you choose Try Ubuntu instead install on CD?

---

### Post by Laysan_A on 2011-01-18
Hi,

I'm not technically advantaged, but I think it would help if you could be more specific about the errors you're getting, and what exactly it is you're doing when you get them. From what I understand, squash is the protocol used to compress and decompress the files on the cd. Perhaps you should run the "check the cd for errors" routine, to see if it's all right (might be called verify, or something like that, I don't recall). 

It's also possible there's a problem with your ram. If I'm correct, the live cd is trying to create a ramdisk to begin the installation with? Do you have enough ram, and is what you have working?  There should also be a routine for that. 

More information will likely get you more help.

Edit: 
Garvinrick4 will certainly be of more help than I...

---

### Post by hc803 on 2011-01-20
ok, ran memtest on it, no issues there.
i believe the problem is the cd drive itself.  i'm attempting to boot off an external CD/DVD burner drive but having issues getting it into the boot order: it comes on, spins, then that's it and i'm left at a blinking text entry dash.  ideas?

---

### Post by Laysan_A on 2011-01-23
Hi hc803,

Sorry I didn't get back to you, I thought garvinrick4 was going to help you. 

I don't get it. You got errors from the cd before, now you say it doesn't get read? What did you change?

I see that you did the memtest, but you didn't mention verifying the cd. You should do that. Even mass-produced cds get garbled sometimes, or have bad spots.

Is this the live cd or the alternate install cd?

The settings for boot order are in your system bios. If it's a usb drive it shouldn't be a problem, as far as I know.

Edit:

I don't know if you've given-up on this thread, but just in case...

I re-read your last post, and I think I understand - your built-in cdrom might be bad, so you're trying to get an external to set as the boot device, but can't. I can't help you with that, but if you have access to a working system, have you thought about installing from a usb stick? Take a look at [this thread](http://ubuntuforums.org/showthread.php?t=831332), especially the last post. Seems pretty straightforward.

---

