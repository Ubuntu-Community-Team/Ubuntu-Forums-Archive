---
title: "Lucid boot extremely slow"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lucasart on 2010-04-18
Hello everyone,

Contrary to what was announced I found Lucid much much slower to boot. Technically the boot untill the login/password is fast, but from that point to actually showing the desktop, it seems to freeze for a good 20/30 seconds before doing anything.

Does anyone else have the same problem ?

---

### Post by tokyobadger on 2010-04-18
what USB devices do you have attached?

---

### Post by wilee-nilee on 2010-04-18
> **lucasart said:**
> Hello everyone,

Contrary to what was announced I found Lucid much much slower to boot. Technically the boot untill the login/password is fast, but from that point to actually showing the desktop, it seems to freeze for a good 20/30 seconds before doing anything.

Does anyone else have the same problem ?

I have had it boot faster and slower at various times during this testing cycle. I have been using it since the first available ISO. It is a beta still, so 
I guess we will see in the end.

---

### Post by lucasart on 2010-04-18
> **wilee-nilee said:**
> I have had it boot faster and slower at various times during this testing cycle. I have been using it since the first available ISO. It is a beta still, so 
I guess we will see in the end.

Thanks, at least I don't feel alone with that problem :) It is probably something to do with my hardware and the bug wouldn't affect everyone. I'm npot sure exactly if it has to do with X11, the Window Manager, or the GNOME desktop.

I am currently testing Lucid Lynx beta 2 for amd64.

To tokyobadger: I have nothing plugged into any USB hole nor a CD in it when I boot. USB works fine for me, the real problem is the regression that Lucid has introduced with UDF DVDs (they dont mount and /etc/fstab is simply missing the /media/cdrom line, and in fact this directory doesn't exist). I can start using Lucid (other than on another partion for testing only) when these showstopper bugs have disappeared.

---

### Post by Khakilang on 2010-04-18
My Lubuntu Lucid Lynx boot at about 15 sec on my old machine but of course after many updates. No bad for an old machine.

---

### Post by fedexnman on 2010-04-18
mine boots slow almost a minute, where karmic was fast as all get out.  its slo with the noveau driver and the nvidia driver

---

### Post by gmck on 2010-04-20
Also having boot problems with Lucid.

I see it in two phases: a delay of about 1 minute between power on and getting the log-in prompt (kdm) and then about 30 seconds delay between logging in and getting into kde.  In 9.04 there was no issue.

Seems to be related to USB and hdparm. I get lots of messages in my log files about the USB card reader (see Bug #452519 on Launch Pad).  After a lot of searching, I tried adding the flag "nohdparm" to the kernel line in grub. This eliminated both of the delays, but the card reader does not auto-detect an inserted card.

---

### Post by jeppo on 2010-04-21
> **gmck said:**
> Also having boot problems with Lucid.

I see it in two phases: a delay of about 1 minute between power on and getting the log-in prompt (kdm) and then about 30 seconds delay between logging in and getting into kde.  In 9.04 there was no issue.

Seems to be related to USB and hdparm. I get lots of messages in my log files about the USB card reader (see Bug #452519 on Launch Pad).  After a lot of searching, I tried adding the flag "nohdparm" to the kernel line in grub. This eliminated both of the delays, but the card reader does not auto-detect an inserted card.
Adding the flag nohdparm fixed the X-server load delay for me.

My question is: are there any issues that could arise from adding this flag?  Because I don't want to fix this problem and break something else.

Thanks,
Chris

---

### Post by gmck on 2010-04-21
> **jeppo said:**
> 
My question is: are there any issues that could arise from adding this flag?  Because I don't want to fix this problem and break something else.


I have the same question.  What are the possible side effects of having "nohdparm" in the kernel boot flags?

---

### Post by philinux on 2010-04-21
> **lucasart said:**
> Hello everyone,

Contrary to what was announced I found Lucid much much slower to boot. Technically the boot untill the login/password is fast, but from that point to actually showing the desktop, it seems to freeze for a good 20/30 seconds before doing anything.

Does anyone else have the same problem ?

From GDM to desktop has been consistently ~5 seconds.

Try disabling compiz.

---

### Post by philinux on 2010-04-21
> **philinux said:**
> From GDM to desktop has been consistently ~5 seconds. Does bootchart show anything odd?

Try disabling compiz.
.

---

### Post by cornelis1 on 2010-04-21
I had the same problem: after login it took almost 30 seconds to show a complete desktop. From another thread I found the following solution: disabling floppy drive in BIOS. Now desktop shows almost immediately.

---

### Post by philinux on 2010-04-21
> **cornelis1 said:**
> I had the same problem: after login it took almost 30 seconds to show a complete desktop. From another thread I found the following solution: disabling floppy drive in BIOS. Now desktop shows almost immediately.

Thats interesting as my rig has no floppy.

---

### Post by cornelis1 on 2010-04-21
> **philinux said:**
> Thats interesting as my rig has no floppy.

Mine hasn't either, but my BIOS still supports floppy drives, as I suppose most motherboards still do. By default floppy support was enabled. Changing setting to 'disabled' made all the difference. I have an ASUS m3n78-em motherboard. I'm using Lucid 64bit.

---

### Post by lucasart on 2010-04-21
> **cornelis1 said:**
> I had the same problem: after login it took almost 30 seconds to show a complete desktop. From another thread I found the following solution: disabling floppy drive in BIOS. Now desktop shows almost immediately.

Thanks for that !
it worked like a charm

in my experience nothing is immediate though. It's more like 10 sec instead of 30, but that's very acceptable.

---

### Post by kwokyinc on 2010-04-24
> **lucasart said:**
> Thanks for that !
it worked like a charm

in my experience nothing is immediate though. It's more like 10 sec instead of 30, but that's very acceptable.

The BIOS fix works for me too, though I don't have a floppy drive at all. It now even boots slightly faster than 9.10.

My boot time (from grub to working desktop)
9.10 -- 47sec
10.04 (before fix) -- 70sec
10.04 (after fix) -- 44sec :P:P

---

