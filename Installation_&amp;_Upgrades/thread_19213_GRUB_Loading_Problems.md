---
title: "GRUB Loading Problems"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by kepardue on 2005-03-10
Hello all.

I've been having trouble getting Warty installed on a PC.  The Ubuntu CD (for AMD 64 architecure) recognises fine, installs fine, but when it gets to the GRUB screen, will freeze up, saying, "Loading GRUB Stage 1.2" (or something to that nature).  Problem is, after this I can't get back into Windows, unless I pop in an Ubuntu Live CD and boot to the Windows partition.  I can't reinstall windows, because the screen goes black just after the "Detecting your hardware" notification.  I finally had to get an old Windows 98 boot disk and format the MBR.  I've gone through the process several times, and it's proven to be a real pain getting Windows back up.

I've tried other distributions briefly: if I install Suse (9.1) BEFORE attempting to install Ubuntu, it seems to work.  If I try to install it AFTER attempting to install Ubuntu, I don't even get to the "Lilo Loading" text... it consistently freezes up after the "L".

I'd be very interested in trying the new Hoary release, reading about the new multimedia features in GNOME 2.10, but I really can't say that I have the patience to struggle with keeping my system afloat; like most people, I've got too many other things going on to spend half my days trying to get my computer to work, a fact which has immensely turned me on to Ubuntu's "just works, TM" philosophy.

Here are my computer's specs:
AMD Athlon 64 3000+
Asus K8VX
1GB DDR Corsair RAM (PC3200)
60GB IDE (Primary Drive)
250GB SATA (Secondary/Storage Drive)

---

### Post by kepardue on 2005-03-15
Bump.  Would really like some help here.

Kenneth

---

### Post by ryanrad on 2005-03-16
Oh crap, I thought you had the same problem I did until I reread the end of your post.  However, this may still help you (reversed) or someone else so I'll post it anyway.

Hey kepardue,

I don't know if this will help at all, but I just got hoary installed on a similar setup.    I've got and IDE storage drive and just installed an SATA Raptor for my OS's.

Every time I installed Ubuntu with both drives connected, it automatically loaded GRUB onto my IDE drive while it correctly installed Hoary on the Raptor.  Ubuntu booted fine from GRUB on the IDE, but Windows errored out every time.

Here's what I did:

Step 1:
Unplug SATA drive
Use Windows disc to FIXMBR on IDE drive.

Step 2:
Unplug IDE drive
Plug SATA drive back in
Install Ubuntu - Grub will now install properly on SATA drive

Step 3:
Plug IDE drive back in
Go into your BIOS setting and make sure SATA drive is 1st priority boot harddrive.
On my MSI mobo, this is in a completely different section than the normal device boot priority.

Hope this helps.

---

