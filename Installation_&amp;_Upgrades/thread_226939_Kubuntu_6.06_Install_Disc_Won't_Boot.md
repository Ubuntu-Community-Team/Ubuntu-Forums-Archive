---
title: "Kubuntu 6.06 Install Disc Won't Boot"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by HalNineThousand on 2006-07-31
I have a friend who has a Fujitsu Series A Lifebook laptop that currently is running Windows XP.  Ideally, she'd like to be able to use Linux.  (This is a non-technical person who is fed up with XP the nightmare of firewalls and virus checkers and other issues who just wants to use her computer without spending hours keeping it running.)  There are one or two applications she needs to use Windows for, so we're looking at doing the defrag-resize thing for her XP partition, then installing Kubuntu with grub pointing to that as the primary system.

Since this is a friend's system I have limited access.  When it comes time to do a full install, then she'll let me have it for a while to install it, but until then, it's under heavy use, so I can't do a ton of testing until I know what I'm testing for.

At this point, the install disk for Kubuntu 6.06 won't even boot.  The last message is:

* Starting Bluetooth services...
hcid sdpd

Then the system hangs.  When I try to reboot it, I get a few messages as some services stop, then:

* Stopping Bluetooth services

and it hangs again.  I have to power down and reboot to do anything after that.

I looked through the BIOS setup to see if it was possible to disable Bluetooth on the computer, but it isn't.  (She doesn't use Bluetooth, at least not at this point.)  I also tried adding "bluetooth=off" to see if that helped on the end of the line of kernel options, but it doesn't make any difference.

I'm concerned because, obviously, once I figure out how to make the CD boot, I will need to be sure it'll be as easy to fix the boot sequence on the actual install, too.  I have no problem editing Grub's menu.lst if needed to add more kernel options.  And, of course, once I get this issue fixed, I'll still need help with resizing the partitions.  I've heard that there are utilities that will resize NTFS partitions (after defragging), but I've never used one and don't know what works best.

Is there a way to disable Bluetooth when booting, or some way to just skip it if it doesn't work?

Thanks!

---

### Post by confused57 on 2006-07-31
You can press Ctrl+C when it hangs, it'll skip the step.
Do you have a USB device connected during bootup?

---

### Post by HalNineThousand on 2006-08-01
Thanks.

I think she may have had one or more ramdrives and I know the cordless USB mouse (not bluetooth) was connected.

So do I press ctrl-c as soon as it says "Starting Bluetooth" or just after the previous step is reported?

---

### Post by confused57 on 2006-08-01
Try it as soon as Starting Bluetooth services appears.
Some USB devices can cause problems during startup, may be the cordless USB mouse...I'm not sure.

---

### Post by HalNineThousand on 2006-08-01
Once we get it up and running (and installed), will there be any problem if I disable bluetooth?  Since she's not using it, there's no need of it, so I figure if that's the only issue, then we might as well nix it -- unless there's something other than obvious consequences.

And when you're asking about USB, do you mean that USB and Bluetooth specifically have issues?

Thanks again!

---

### Post by confused57 on 2006-08-01
> **HalNineThousand said:**
> Once we get it up and running (and installed), will there be any problem if I disable bluetooth?  Since she's not using it, there's no need of it, so I figure if that's the only issue, then we might as well nix it -- unless there's something other than obvious consequences.

And when you're asking about USB, do you mean that USB and Bluetooth specifically have issues?

Thanks again!
If you're not using a bluetooth device, there's no problem disabling it from loading at startup.  It may be that Ubuntu mistakenly thinks one of the USB devices(mouse?) is a bluetooth device...I couldn't tell you for sure.  I've just read that USB devices connected during bootup can cause problems?

---

### Post by HalNineThousand on 2006-08-01
I got it to boot up.  My friend loves the USB wireless mouse that she got from me, so I tried a few other things, but in the end, removed the mouse receiver and it booted fine.  I tried letting the drivers load, then removing the mouse before Bluetooth started, but that didn't work.  In the end, I just kept the mouse removed during booting and it was okay.

While it was working I tried to stop /etc/init.rd/bluez-tools (sounds like a kid's TV show, doesn't it?), the program just hung.  I've learned that on LIVE CD distros you often can't add apps or anything, but I tried apt-get remove bluez-utils to remove the bluetooth services, but I can't tell if it worked.  As part of the removal process it tried killing bluez-tools on its own, and it hung until I killed it.  I didn't have time to see if it had actually removed it before my friend had to leave.


When I get to doing the install (which I hope is in the next week), I plan to boot without the wireless mouse (or see if the PS/2 adapter works for it), set it all up, remove the Bluetooth stuff, and reboot.  If it's gone, I'll reboot with the mouse attached and see how it works.  I'll report my results here.  Now onto the NTFS shrinking issue.  I'll post elsewhere for that to not mix topics.

Thanks for the help!

---

### Post by confused57 on 2006-08-01
Glad to help & that you got it to boot up.
If you have a means to download SimplyMepis, you might want try it...it's actually uses Ubuntu repositories in the newest release, 6.0...may do a better job at configuring hardware.

---

