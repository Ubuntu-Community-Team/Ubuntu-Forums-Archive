---
title: "warty install fails installing initrd-tools"
date: 2004-11-11
forum: Installation &amp; Upgrades
---

### Post by MarcDM on 2004-11-11
This message also posted to the ubuntu-users mailing list (awaiting approval)

I have been trying like crazy to get the Warty Warthog on a K62-500MHz
PC that I have wtih 128MB RAM and a 10GB drive.

Using the installer defaults, the installation process executes
error-free until it gets to the point where it starts installing the
kernel.

At this point, it fails when trying to install initrd-tools. 

I have verified the md5sum of the ISO and the CD and they check out ok.
I have tried 4 different CD-ROM drives and 3 different CDs (burned on
different machines) but it still fails in the same place. In 1 case I
used the same burner that burned the CD.

I tried the expert installation method, hoping that it would allow me to
not-install initrd-tools (no avail).

I spent the entire night in the IRC channel, tried everything suggested.
Nothing. It fails in the same place.

I assume that this is happening because I had slackware 10 on the
machine previously with LILO installed to the MBR. And yes, I did make
the mistake of removing the lilo files before uninstalling it. However,
I have since booted with a DOS floppy and executed fdisk /mbr. I know
that this only rewrites the boot sector and not the partition table. I'm
not sure how to fix the latter (ubuntu installer partition tool does
this?).

but still... I try to install and it goes through... all the way to :
"Installing initrd-tools" and fails. On virtual term 3 there are no real
descriptive messages, it just says the same thing. "Initrd-Tools install
failed."

Can anyone help?

---

### Post by MarcDM on 2004-11-12
Finally, the warthog got installed. 

There are 2 things that I did differently than all the previous failed installations. 

1. I used a tool named ZAP (from IBM) to overwrite the first part of the disk with 000s. When the warty installer started, it saw the disk as a new disk with no partition table and a blank MBR.

I believe that it's the remains of the Slackware/Lilo install that was causing the install to fail.

2. Upon inspection, I noticed that the heat-sink and fan were not touching the cpu. The clip that holds the heat-sink to the cpu had broken. Maybe the install was failing because of an overheating processor.

But wouldn't it fail at random points in the install if this were the case?

Anywho... I got it installed. I have 1 more HDD to install it on. This one, too, had Slackware 10 installed. I'm not going to zap the disk before I perform the install. I'm going to try a vanilla install before I zap it. 

More info as that progresses. 

MDM

---

### Post by Billy Anachronism on 2005-02-03
I can't believe this.. but I have a k2-500mHz and I'm having exactly the same issue. I have no idea why .. I can't even guess how we'd both be experiencing this problem.
I'm going to read your solution again but at first glance they seemed very unrelated to the actual problem. 

Anyway, nice to see someone else is experiencing this. Possibly an obscure bug of some sort and it would be nice to have it flattened out.

The console 3 only really reports that initrd-tools is already a newer version than what is trying to be installed. Also that there are unmet dependancies for it but they aren't going to be installed.

This is so bizarre...

Billy

---

### Post by Nichotin on 2005-02-12
First, sorry for the bump.


I had the exact same problem with my k6-2 400mhz.
What did the trick was simply to put a fan on the heatsink. This confirms that this has something to do with the heat.

The solution is simple: Get adequate cooling.

---

### Post by pohara on 2005-03-10
My k6-2-550mhz, kept giving the initrd-tools message and all seemed to fall apart thereafter. I decided to look at the fan (after reading these threads) ... and Yep it was full of dust. Once cleaned (quick method: just rub it a bit with something (aint got no vacuum/air-spray)) I rebooted ... and IT WORKed!!

Lessons learnt: dust sucks, these forums are very useful, try DIY b4 you buy.

---

