---
title: "Can't install with disk mirroring"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by AlexBooton on 2011-10-22
Hi,

I've been trying every which way to install 11.04 with disk mirroring using two 2tb drives.

I set up mirroring in the BIOS.  I've actually done this with two different mother boards.  One of them quite recent.  That appears to work OK.

But when I try to install U11.04 from a USB stick I get to the screen that asks me if I want to use the entire drive.  I say yes.  Then it just goes into a wait state... forever.

I've also tried allowing U11.04 to run from the USB stick (as opposed to just asking for a direct install).  And then I select the install option from the U11.04 gui.

Again pretty much the same thing happens except I get a message that Ubiquity closed unexpectedly and them I stuck.

Is there any way to do this?

Thanks

AB

---

### Post by masgeeks on 2011-10-22
I've had issues on a server of mine where I had to use software raid instead of hardware raid - never did figure out what was wrong, but software raid 1 had been working fine, I even tested by disconnecting on drive and it booted ok...

---

### Post by AlexBooton on 2011-10-22
> **masgeeks said:**
> I've had issues on a server of mine where I had to use software raid instead of hardware raid - never did figure out what was wrong, but software raid 1 had been working fine, I even tested by disconnecting on drive and it booted ok...

Thanks for the feedback.

Where do I look for info on software raid?

Thanks,

AB

---

### Post by AlexBooton on 2011-10-22
> **AlexBooton said:**
> Thanks for the feedback.
Where do I look for info on software raid?
AB

I marked this thread as solved but truthfully, many questions remain.

Well, amazingly, I finally got it to work.  It wasn't easy and I can't relate all the steps.

I found [this doc]("https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html") and tried to follow it; but it's incomplete.  

The first problem I ran into was where the doc said:

"As with the swap partition, select the "Use as:" line at the top, changing it to "physical volume for RAID".  

I could find no such setting.

Anyway here's a brief outline of what I did.
1. I had previously attempted hardware raid and that may have left some artifacts that prevented U11.04 from using them.

I used Hiren's boot CD to re-partition the drives.

2. Next I ran U from the USB Stick and used gparted to partition the drives with a 32gb swap partition at the end and a 2tb main partition.

I first tried with both drives connected but ran into problems so I did it one at a time.

On both drives I used the "flags" feature of gparted to mark them as raid.

3.  Finally, with both drives installed I ran the installation from the USB stick.  It worked!

I satisfied myself this was working by creating a small text file.  I then booted one drive at a time and that text file was there on both drives!

I ended up with mirrored drives, which was what I wanted but don't know how it knew that.  I set the raid flag but never saw a way to select the level of raid I wanted.

Oh well.  The important thing is that it's working.

AB

---

