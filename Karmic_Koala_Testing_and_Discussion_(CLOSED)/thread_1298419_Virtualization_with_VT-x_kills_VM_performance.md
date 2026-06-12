---
title: "Virtualization with VT-x kills VM performance"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by HotShotDJ on 2009-10-22
Has anybody succeeded in getting ANY virtualization software (such as VirtualBox, KVM) working properly under Karmic with VT-x enabled?  I've tried VirtualBox 3.08 PEUL & OSE versions and kvm.  Only by disabling VT-x will VirtualBox run XP.  KVM was a total loss.  I could improve performance by setting it to only 1 cpu, but it was still so slow as to be unusable.

I suspect that I'm missing something important here -- at least that is my hope.

---

### Post by novafluxx on 2009-10-22
Well, what kinda hardware are you running?

---

### Post by HotShotDJ on 2009-10-22
> **novafluxx said:**
> Well, what kinda hardware are you running?I suppose that WOULD be useful information ;)

System76 PanP5
P8700 (Core 2 Duo)
4 Gig DDR2 RAM
NVidia G105M Graphics
320 GB 7200 RPM HDD
Karmic Beta AMD-64 Desktop

Also, VirtualBox 3.0.8 PUEL w/ VT-x enabled worked flawlessly under Jaunty.

---

### Post by novafluxx on 2009-10-22
That CPU should certainly be able to handle the virtualization. I'm not sure what the issue is. Try enabling nested paging as well, and turn IO APIC OFF, unless you installed Windows with it enabled.

Never know, it may be a bug in VB 3.0.8, even if it did run well in 9.04.

How much RAM is set aside for that Windows XP virtual machine? I'd hope at least 1GB out of your max of 4.

I'm curious if is due to running 64-bit...is the Windows install also 64-bit? Are you using the 64-bit VirtualBox as well or 32-bit?

---

### Post by HotShotDJ on 2009-10-22
> **novafluxx said:**
> Never know, it may be a bug in VB 3.0.8, even if it did run well in 9.04.

How much RAM is set aside for that Windows XP virtual machine? I'd hope at least 1GB out of your max of 4.I've given the VM 1.5 gig.  I thought initially that there was a bug in VB 3.0.8 under Karmic until I tried it using KVM and had the exact same symptoms.  I'll have to do a reinstall of Windows under VirtualBox in order to test your IO APIC hypothesis.  IIRC, you can't enable VT-x without also enabling IO APIC... but I could be wrong about that.

Have you successfully used VT-x enabled virtualization under Karmic?  If so, that will at least give me hope.

EDIT:  You added to your post while I was answering... I'm using 32 bit Windows XP.  Again, this shouldn't be a problem (and worked fine with VB 3.0.8 under Jaunty).  Because I'm having the same symptoms with KVM and VirtualBox, I strongly suspect something changed in Karmic that has broken hardware virtualization.  But for the life of me, I can't think of what that might be.  I wonder if it has something to do with the move from HAL to DeviceKit and if so, how to make hardware virtualization work with it.

---

### Post by novafluxx on 2009-10-22
Unfortunately my Ubuntu machine is a laptop. The CPU doens't support hardware virtualization! My desktop machine is a Windows 7 64-bit box and I have an AMD CPU and I can do it there, but I don't have Ubuntu installed on my desktop.

I know IO APIC can slowdown the system, and I don't believe it is required to install/run Windows XP in VBox, so try turning it off and reinstalling.

---

### Post by HotShotDJ on 2009-10-22
> **novafluxx said:**
> I know IO APIC can slowdown the system, and I don't believe it is required to install/run Windows XP in VBox, so try turning it off and reinstalling.I just tested it out (sort of). Without IO APIC, I can only have one virtual CPU in the VM.  BUT, that might not be a big deal.  I'll try a reinstall w/out IO APIC this weekend.

---

### Post by novafluxx on 2009-10-22
> **HotShotDJ said:**
> I just tested it out (sort of). Without IO APIC, I can only have one virtual CPU in the VM.  BUT, that might not be a big deal.  I'll try a reinstall w/out IO APIC this weekend.

Don't see it being a big issue either, depending on what you plan to do in that XP VM, you may only need 1 CPU.f

Also, you can create two identical VMs, except one with hardware virtualization, one without, and just benchmark them.

As of VBox 3 I believe they've enabled hardware virtualization by default, because its matured enough (in their opinion) to be more efficient/faster then their software implementation. This may not be true in some cases.

It also, possibly, may be a CPU defect, just throwing that out there on the table for consideration, however, I seriously doubt that's the case.

Let me know what happens in a PM. I may not check this thread again after its lost, and I'm eager to hear how it plays out.

---

### Post by HotShotDJ on 2009-10-22
> **novafluxx said:**
> It also, possibly, may be a CPU defect, just throwing that out there on the table for consideration, however, I seriously doubt that's the case.If that is the case, then Karmic broke my CPU!  It worked under Jaunty. :lolflag:

---

### Post by novafluxx on 2009-10-22
> **HotShotDJ said:**
> If that is the case, then Karmic broke my CPU!  It worked under Jaunty. :lolflag:

Haha, true. I don't have enough experience running VBox under Ubuntu to tell you, and as I stated previously, my craptop CPU doesn't support virtualization.

Best of luck mate, let me know how it goes!



On a side note, I've been running Arch Linux in a VM here on my craptop, and its noticeably slower then on my desktop. I don't even have a desktop installed on that thing, yet!

---

### Post by Longinus00 on 2009-10-23
Virtualbox works great for me using VT-x. This is on my desktop with an e8400 on karmic x64.

---

### Post by HotShotDJ on 2009-10-23
> **Longinus00 said:**
> Virtualbox works great for me using VT-x. This is on my desktop with an e8400 on karmic x64.Thats good to know.  What settings have you used?  What guest OS are you running?

---

### Post by bobince on 2009-10-23
I've been using hardware virtualisation on Virtualbox for several versions with no problems at all. Core 2 Q9300 on G45 (Shuttle SG45H7); guests including Jaunty, Slax, XP, Vista, Win7, Win98...

Maybe a BIOS problem?

---

### Post by HotShotDJ on 2009-10-23
> **bobince said:**
> Maybe a BIOS problem?That was my first thought as well, and I updated my BIOS to no effect.  I'm going to try reinstalling my guest with IO APIC disabled, as suggested by novafluxx.  Something else of note: with kvm, ACPI is completely broken on the guest OS.  I'm thinking these issues are related to each other and to the move from HAL to DeviceKit.  But not being a programmer, I can't be sure.

---

### Post by HotShotDJ on 2009-10-23
Ok.  I tried one more thing before reinstalling the guest with IO APIC disabled.  I enabled VT-x but left the number of virtual CPU's at 1.  *Et voilà*!  I now have Windows XP running in VirtualBox at near-native speeds using hardware virtualization.

---

### Post by novafluxx on 2009-10-23
Excellent! I didn't know what would have anything to do with it, but disabling IO APIC would have had the same effect! ;-)


Wonder why adding MORE CPU's made the VM incredibly slow.


Try doing the same with more then 1 CPU with another OS like Ubuntu or openSUSE and see if they have the same slowdowns with multiple CPU's

---

### Post by HotShotDJ on 2009-10-23
> **novafluxx said:**
> ...disabling IO APIC would have had the same effect! ;-)Yes, it would have.  In fact, that is what gave me the idea to try just setting the number of CPU's to 1.  For some reason, that never even crossed my mind until you mentioned disabling IO APIC (and I got a good night's sleep).  And NOW, I don't have to do yet ANOTHER re-installation of WinXP -- where that internet meme that it is LINUX that is hard to install came from is beyond me!
> **novafluxx said:**
> Try doing the same with more then 1 CPU with another OS like Ubuntu or openSUSE and see if they have the same slowdowns with multiple CPU'sThat's a good idea.  I'd also like to find out if this is a Windows specific issue or not.  Hmmmm... I think I may have saved a Windows Vista VM that I had been experimenting with awhile back. I deleted it from my old laptop... but it might be in one of my backups.  I'll check that out as well if I can find the image.

---

