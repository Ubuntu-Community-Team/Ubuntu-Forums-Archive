---
title: "How to get Wifi working in Live CD in Chroot."
date: 2010-01-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-01-22
When I get to root in Live CD I do not get Wifi to download upgrades. I do not
know the code to accomplish this, Wifi working while in chroot that is. Thanks

---

### Post by cariboo on 2010-01-22
You're a little bit short on information, I'm going to assume you want to try wifi using the live CD, you're not clear on that either.

What chipset and driver does your device use?

---

### Post by Starks on 2010-01-22
Are you copying /etc/resolv.conf correctly?

[http://ubuntuforums.org/showthread.php?t=1326721](http://ubuntuforums.org/showthread.php?t=1326721)

---

### Post by garvinrick4 on 2010-01-22
> **cariboo907 said:**
> You're a little bit short on information, I'm going to assume you want to try wifi using the live CD, you're not clear on that either.

What chipset and driver does your device use?

Sorry I was did not explain more. When in Live CD and chroot ot either
karmic or lucid cannot get a wifi connection with laptop. Needed to see if 
there is code to fix this problem. Same if I go into recovery mode for Linux
if I go to a wired connection works, if I am on Wifi connection it does not 
work. I do not have problem right now but wish to know the salution before
I need to use this function to fix Lucid for one reason or another. 


02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
        Subsystem: Intel Corporation Device 1315
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at d3500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 306b
        Flags: bus master, fast devsel, latency 0, IRQ 27
        I/O ports at 2000 [size=256]
        Memory at d1410000 (64-bit, prefetchable) [size=4K]
        Memory at d1400000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at d1420000 [disabled] [size=64K]
:00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) The
rmal Subsystem (rev 03)
        Subsystem: Hewlett-Packard Company Device 306b
        Flags: fast devsel, IRQ 11
        Memory at d4504000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
Thanks for any help.

---

### Post by garvinrick4 on 2010-01-22
> **Starks said:**
> Are you copying /etc/resolv.conf correctly?

[http://ubuntuforums.org/showthread.php?t=1326721](http://ubuntuforums.org/showthread.php?t=1326721)

You know in chroot I looked at Lucid and Karmic and they are both an empty file.
etc/resolv.conf

I took what was in a file not in chroot and added it in to lucid (three lines) resolv.conf
and Lucid in chroot will now update and upgrade with no problems. Is this a fix that
is going to work without any problems in future? If it is, I am satisfied and Thank's for
input. If you know something else I should be doing please advise.

---

### Post by garvinrick4 on 2010-01-22
What I have copied and pasted into etc/resolv.conf  while in Live CD in chroot lucid
was my isp so when I am in different location using another wifi connection what will happen
then HMMM it works now but I believe there must be more to it than using this three line
fix in etc/resolv.conf. 

I have seen a few different code variations. Stark or Caraboo907 do you have code that
will do more than my temporary fix.

Edit: Using Live USB with persistence and it did not retain etc.resolve.conf so no problem with
different isp. File go's back to empty.

---

### Post by k64 on 2010-01-23
The OP was in chroot, which would explain it. Do NOT chroot into the Live CD.

---

### Post by garvinrick4 on 2010-01-23
> **k64 said:**
> The OP was in chroot, which would explain it. Do NOT chroot into the Live CD.
  
My object is to make sure I am capable of repairing Alpha and Beta when problems
arise, in which they will doing daily upgrades. If I do not use the chroot cmd to get into
a OS from a Live CD what would I use. I would also like the capabilities of running updates
and upgrades to possibly repair a system that needs it. That is what I am studying right now is the Live CD. If you know a way different than chroot or I am going about this wrong
please expand on the "DO NOT chroot into the Live CD".   Thanks.

---

### Post by ranch hand on 2010-01-23
I believe that k64 thinks you are trying to chroot into the LiveCD rather than from the LiveCD to an installed OS.

---

### Post by cariboo on 2010-01-23
I would concentrate on getting wireless to work with the live CD, if you have it working, it shouldn't make any difference what else you are doing. When running the Live CD waht do you get when you run:

```
sudo lshw -C network
```

the above command will allow us to see if your wifi device is detected and the driver loaded.

---

### Post by garvinrick4 on 2010-01-23
Thank you all for assistance while in chroot in either karmic or lucid I had to add isp to etc/resolv.conf  that was in live CD directory or by sudo cp /etc/resolv.conf edit/etc/
After shutdown and reboot all is removed from etc/resolv.conf in chroot OS so I imagine
I will just have to add the line everytime and with whatever wifi connection I have at the time.
Have no problem with that and seems logical. Thanks again.

---

### Post by garvinrick4 on 2010-01-23
> **cariboo907 said:**
> I would concentrate on getting wireless to work with the live CD, if you have it working, it shouldn't make any difference what else you are doing. When running the Live CD waht do you get when you run:

```
sudo lshw -C network
```the above command will allow us to see if your wifi device is detected and the driver loaded.
 
It did show my device and driver were installed thank you. I enjoy learning a new command.
"sudo lshw -C network"   nice to have available. Figured out my problem (previous post) and marked
as Solved.

---

