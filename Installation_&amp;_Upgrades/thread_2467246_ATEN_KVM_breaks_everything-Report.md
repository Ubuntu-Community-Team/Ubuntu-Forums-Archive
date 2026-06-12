---
title: "ATEN KVM breaks everything-Report"
date: 2021-09-21
forum: Installation &amp; Upgrades
---

### Post by vector on 2021-09-21
This is a strange tale but I'll keep it short. 
Over the past year or so I have been having weird problems. Ubuntu Studio various versions.

Randomly very long boot ups. ~~Just sits on the Bios logo for eons.
Randomly long shutdowns.
Problem mounting USB drives and card readers. ~~Sometimes will not mount newly inserted. Reboot normally fixed it.
Unable to switch users ~~It just locks up when I switch back.
fdisk -l can take ages to finish. ~initial burst while it finds HDs and then (with little todo/left to find? it just sits there.)
Randomly locking up. Seemed to be in sync with when I go to move the mouse.


Some time back I got given a minimac. I converted it over to run linux.(works well BTW as does a n iMac) In order to keep the desk simple. 
I purchased an **ATEN KVM cubiQ CM0264** to "simplify" the desk. The iMac went elsewhere far too big for my patch.
I often have other PCs come n go like a laptop during lockdown to work from home so i had a spare set of leads from the KVM to plug things into.

The basic need was to switch the keyb,mouse and screen over to these other devices.

It seemed to be doing the job well and I didn't notice at the time these various problems. Occasional lock up or reboot is just one of those things we live with.
Recently the issues were getting worse(or was it that I was simply pushing its buttons more often) I have been doing a lot of HD and USB card(photos) reading and re organising.
I noticed a few problems with fdisk and was getting worried the HD was on the way out.
I had another PC I hooked up to the "spare leads". Idea was to install a new linux(been a while since this machine was fresh install anyway).
I had numerous problems getting the new PC to boot, to accept the usb start drive, to create the usb drive in the first place. I had all kinds of issues with CD drive not reading or failing halfway thru. My PC was getting worse and I couldn't even burn a new one. The ubuntu studio install seemed to take eons when it did take. Then crashed after install.
Nothing made sense..

In desperation I took the new old pc to the shed plugged in an old screen, keyb n mouse. It all, started working.
Even the simplest thing of initial screen splash were halting when the PC was plugged into the ATEN, as though it was messing with the video.
I know I didn't believe any of this either and hence why it took so long to dawn on me that the KVM was the issue.
(I must add here that all this was not helped by old HD bittlocker issues and BIOS passwords. I guess thats what ya get when picking up throw outs)
Even the internet was against me when I tried to grab the official iso. (that still is a problem I just tried it)

> Not Found
The requested URL was not found on this server.
Apache/2.4.29 (Ubuntu) Server at cdimage.ubuntu.com Port 443

Found an older iso and burnt it. So a new install on the new old box I went back into the office. Networked and updated it.
Finally with my desk upturned and the two machines side by side I started to copy across files.
New box did the same thing...went missing in action....fdisk -l did had the same slow response.
With a bit of desk clearing I plugged a monitor ,keyb,mouse direct. Removed the HD from the dodgy machine placed it in a HD to usb dock and finally started copying files.

Whilst sitting there watching bits transfer it finally struck me that the problem must be the KVM.
I ripped it out, put the HD back in the dodgy machine, direct feeds to peripherals and booted.
Quick boot, no delay. fdisk -l reported quick and as expected.
I wonder?...., tried switching users a few times, no dramas. Checked various USBs in and outs, audio gear, drives etc, all good.
And so far no locks up.

BTW I did try some  ATEN commands to for eg 
disable mouse emulation. made no diff
disable keyboard emulation...wouldnt even let me do this, command never stuck

So just in case anyone else is in the same boat and still has some hair left. Remove the KVM.

---

### Post by ActionParsnip on 2021-09-21
I suggest you test the RAM as a good starting point.

---

### Post by rbmorse on 2021-09-21
KVM and Linux have had issues since the early days of the Republic. I got burned with this issue (almost same process you experienced) when I was on Mandrake Linux back in '04.

---

### Post by TheFu on 2021-09-21
If the KVM you have is the problem, get a replacement or remove it from the path. Also, check all the cables. Swap them around to see of the issue follows a cable.  Some KVMs are finicky.

I've been using a KVM switch since the 1990s. Next to zero issues in all these years.  

Around 2002, I switched KVMs to a Belkin 4-port thing.  It is VGA and PS2 for the keyboard and mice.  Using it right now and it works beautifully.  I have USB-to-PS2 "Y" adapters on the each computer side.  That means never having to figure out with PS2 port is for the mouse and which is for the keyboard.  I wasted far too much time over that 20 yrs ago.  $4/ea for the "Y" adapters.  My IBM 101M keyboard and 2000-ish mouse are PS2 and plug into the KVM directly with 10ft extension cables for each.

Can't remember any Linux related issues.  I just have to enable "legacy USB support" in the BIOS for computer.

Once there was a problem with a Logitech C-Series mouse due to MS-Windows. The only fix was to buy a new mouse.  I'm using that same mouse today.  Whenever there seemed to be a mouse issue - it was during the 6 months when I switched to a cordless mouse - I'll never do that again - or because the mouse sensor/ball needed cleaning.  All my mice have those rubber balls still. Ain't broke, so I won't be fixing it.

The KVM I use is a Belkin Qube. Don't think those are available anymore.

Just a few days ago, I added an HDMI 4K@60hz video-only 4x2 matrix switch (~ US$50) to the setup to replace a 4x1 HDMI 1200p (max) switch for the 2nd monitor.  So far, there's only been 1 surprise where the video output from the 2nd connection to a laptop (MS-Windows) wasn't seeing the 1080p-ness of the 2nd monitor and insisted on sending 800x600 resolution.  In the end, the answer was to switch to a different 1080p source, then directly switch to the Windows machine as a source.  To be far, the Windows laptop is 11 yrs old and hasn't been patched in years or rebooted in about 260 days.

I've been unable to get the 2nd video output working from an nvidia 1030 GS GPU.  Last weekend, the 470.x driver was released and got installed (I didn't see that coming), but I haven't rebooted the system yet.  Reboots are for the weekends here. I don't reboot on weekdays. Saturday morning, I'll try to get the 2nd monitor working with the nvidia GPU.

---

### Post by MAFoElffen on 2021-09-22
I have good luck with both Belkin and Dell KVM switches with my servers, all going to an HP 1U Rack Mount Console TFT Display/Keyboard w/ touchpad. 

I have noticed with Graphical Desktops, that with HWE kernels, that I lose the mouse intermittently on some machines, that are running newer than 5.8.xx Kernels (5.11.0 Series Kernels), if sitting for a long time switched to that same machine and idle. But if I switch to another and switch back, then it's good. It may have something to do with the polling/keep_alive of the USB device. But since it always comes back for me, I haven't taken the time to report it. It doesn't happen when I am am connected to these same as headless/remotely. (which would be IP, not physically through the KVm switch.)

---

