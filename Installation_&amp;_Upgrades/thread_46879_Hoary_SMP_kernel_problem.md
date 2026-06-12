---
title: "Hoary SMP kernel problem"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by pioni on 2005-07-06
I've tried to install Ubuntu on a dual processor (no Hyperthreading, two real processors) machine for a few days and I feel there's definitely something wrong with the stock kernels. If I do default install, switch to SMP kernel using Synaptic and reboot, one processor is almost always at 100% and the other works normally. If I change the SMP kernel version to a later one, whole system freezes right after login when the desktop should appear. The computer has old Matrox G200 graphics adapter, so I guess this isn't one of those Nvidia/ATI kernel/driver dependency problems I've read about. I think I've tried all SMP kernel versions Hoary has and none of them works as it should. Any ideas what I should try? Why doesn't Hoary install SMP kernel by default on a computer that has multiple processors?

Windows XP works and detects both processors correctly on the same computer, but I don't want to get 0WN3d, so that's not an option. I tried also CentOS 4.1, which used SMP kernel by default and did not the have same problems. So, it's most probably not a hardware problem.

---

### Post by cbare on 2005-07-08
I'm also having problems w/ SMP support on the Hoary 5.0.4. I'm trying to use the linux-686-smp kernel version 2.6.10-7. I can boot and log in, but the computer locks up requiring hard reset soon afterwards. Seems to do so during mouse moves. For the time before it hangs, I can open the system monitor and see normal 1-20% CPU loads.

My machine is a 2 x P3 (PIII) 733Mhz. ATI Radean 7000 VE graphics card. WinXP works w/ both processors as did suse 8.2 which I replaced with Ubuntu. This machine has some kind of issues with ACPI, so maybe that's part of the problem.

-chris

---

### Post by cbare on 2005-07-08
To update, I tried boot with acpi=off set in grub's menu.lst file. Didn't help at all.

With the SMP kernel, the computer freezes within a minute or so of logging in. It never seems to crash before logging in, and runs like a champ in text mode, so I guess it's something in Gnome or Xorg that's causing the crash.

The machine is perfectly stable using the single processor 386 kernel. Any Hints???

---

### Post by pioni on 2005-07-09
That's sort of funny, because the computer here has ACPI problems too, at least according to CentOS 4.1. It says "BIOS age (2000) fails cutoff (2001)" and says that I should use acpi=force kernel parameter to enable ACPI. If I press a in CentOS GRUB menu and add acpi=force to parameters, I get the same message and still no ACPI. The computer works correctly without ACPI though, even in SMP mode. Only nuisance is that it doesn't turn off in shutdown, because the lack of ACPI. 

My computer is perfectly stable in Ubuntu with the default single processor i386 kernel, though that's just like saying my car is runs perfectly but on 1st and 2nd gear only. Problems start after I try to switch to one of the SMP kernels. The oldest SMP kernel works, but one of the processor is always at 100%. All the others crash a few seconds after Gnome desktop appears. I can move mouse, but it freezes before the menus appear.

---

### Post by PMO6022 on 2005-07-09
Which smp kernels are you guys having lockup with?  I was having lockups within minutes of boot with the 2.6.11-686-smp kernel, on my P4 with hyperthreading.  I didn't do enough troubleshooting to determine that the kernel was the problem, but I've switched to 2.6.10-5-686-smp and haven't had a lockup.

---

### Post by cbare on 2005-07-09
I thought the ACPI issue was a red herring after that acpi=off didn't work, but who knows. My motherboard is an MSI w/ AMI bios release: 11/10/2000 S and the VIA 69X chipset.

I dunno if any of that is relevant, but it would be suspicious if we have the same bios version. I get this message during boot: ACPI: unable to locate RSDP. Aside from causing me to say, "I got your RSDP, <i>right here</i>!", I imagine this means the motherboard implements a preliminary version of ACPI that is not quite standard. Same deal, I have shut the computer of manually after shutting down the OS.

btw, the kernel I'm trying to use is linux-686-smp 2.6.10-7.
linux-386 2.6.10-7 works fine.

-chris

---

### Post by pioni on 2005-07-10
I have Award BIOS from 04/20/2000. The motherboard is an Abit BP6 with Intel 440BX chipset. 

I installed Fedora Core 4 and it detected both processors and used SMP kernel by default. ACPI didn't work though and after two hours I was deep inside RPM dependency hell, just reminding me to keep away from RPM distributions. So, after this reminder I decided to install latest stable Debian (3.1), which did not recognize SMP and did not use SMP even after switching the kernel manually. 

So far, the only 100% working OS has been Windows XP, except that it's Windows and I don't want to do weekly reboots. NTFS seems to have some sort of problem with directories that have tens of thousands of files (it works, but it's just so fscking sloooow), so for my purpose XP doesn't cut it. CentOS, Fedora Core 4, Ubuntu and Debian have all had problems with either ACPI or SMP, or both. I'm going to try my luck with FreeBSD next. 

If anyone has an idea what might be wrong with the SMP kernels in Ubuntu, I'd be very, very glad to know. Ubuntu is perfect except that it works with one processor only.  ](*,)

---

### Post by cbare on 2005-07-10
I decided to bang my head against this wall a little more today. Searching around I found a few candidate bugs:

There's an open bug in ubuntu's bugzilla that seems to cover this:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9123](https://bugzilla.ubuntu.com/show_bug.cgi?id=9123)

There's also an open bug in xorg regarding Radeon 7000 + SMP:
[https://bugs.freedesktop.org/show_bug.cgi?id=1912](https://bugs.freedesktop.org/show_bug.cgi?id=1912)

Then there's this xorg bug:
[http://ubuntuforums.org/showthread.php?t=39819](http://ubuntuforums.org/showthread.php?t=39819)

For what it's worth, I tried booting with the noinotify option to the kernel. Same lockup.

-chris

---

### Post by pioni on 2005-09-29
No messages in this thread lately, but anyway... I'm writing this just to inform that now the stock SMP kernel does work on the same unmodified computer and same install CD. I did a fresh install just like before and upgraded it to have latest everything with Synaptic. After that I added linux-image-686-smp to my configuration and let it install linux-image-2.6.10-5-686-smp version 2.6.10-34.6 to my computer. I rebooted and expected it to lock hard on first glimpse of Gnome desktop, but now the problem, whatever it was, is gone.
So, I'm not sure if anyone reads old threads like this, but even if nobody does, I must say something that should not be left unsaid: **THANK YOU!**

---

### Post by Antonio Ricardo Correia on 2005-09-30
I'm currently running Breezy but since Hoary t'ill now I don't manage to have a single smp kernel running. All freeze either at the grey screen before login or on the kde login screen.
It seems there is a problem with X, the mouse stops dead and the only way out is a hardware reset. I can't figure out what is going on, before I was running on Mandrake and the smp kernels worked fine.
Does any one have an idea of what is the problem?

Best regards,
Antonio

---

### Post by mb2k on 2005-10-17
Good Evening Ladies and Gents,

after installing Breezy Badger 5.10 on my 2 x 1,13 ghz SMP Server, I direclty upgraded to Linux-Image-2.6.12-9-686-smp, and I had the same lock up on KDE and Gnome. using either GDM, KDM or XDM doesn`t matter.

When I boot up the normal 386 Kernel everything runs like a charm...

Does anybody have some glue what is ???

I have an Dual P3 Board with an Via KT133 Chipset and a ATI Radeon 7000 Card inside ....:confused: 

It would be great to get some thoughts or feedback on this ... meantime I stick to the 386 kernel to work...

Many many thanks.

---

### Post by pioni on 2005-10-18
[QUOTE=Antonio Ricardo Correia]I'm currently running Breezy but since Hoary t'ill now I don't manage to have a single smp kernel running. All freeze either at the grey screen before login or on the kde login screen.
It seems there is a problem with X, the mouse stops dead and the only way out is a hardware reset. I can't figure out what is going on, before I was running on Mandrake and the smp kernels worked fine.
Does any one have an idea of what is the problem?
[/QUOTE]
I don't know what causes the problem, but I guess I too have ATI graphics adapter on that dual-CPU server. It's an old ATI Rage 128 or something, but does the trick as I don't have a monitor, keyboard or mouse on that computer anyway. I remember having tried different adapters when I tested Hoary and none of them made any difference. Gnome locked up exactly as you said above.

I tried Breezy on the same computer last weekend and the stock SMP kernel works without problems. I'm still running CentOS on it, but will install Breezy (or Dapper, if I'm lazy) later during the next service weekend a couple of months from now.

---

### Post by Antonio Ricardo Correia on 2005-10-18
I've tried with Breezy's 686/smp but the problem still remains. In the reboot logfile I could read that it finds two processors but at the same time it says that hyperthreading is disabled (wonder why).
It seems that the stock smp kernel only works with true bi-processor machines and doesn't take into account the smp possibilities of Pentium4 processors with hyperthreading but as I said before smp kernels in Mandrake did work flawlessly.
I hope the kernel development team at (K)Ubuntu will solve the problem sometime in the future.

Best regards,
A.Correia

---

### Post by pioni on 2005-10-18
[QUOTE=Antonio Ricardo Correia]It seems that the stock smp kernel only works with true bi-processor machines and doesn't take into account the smp possibilities of Pentium4 processors with hyperthreading but as I said before smp kernels in Mandrake did work flawlessly.
I hope the kernel development team at (K)Ubuntu will solve the problem sometime in the future.[/QUOTE]

I find it hard to believe that nobody else with Hyperthreading capable processor has this problem, if indeed HT is causing problems. I suppose HT processors are quite common nowadays, even though I don't have one (and probably never will). My guess is that SMP kernel is partly broken, i.e. works for some, fails for others. To my knowledge this happens only on Ubuntu, as other distributions have worked just fine in SMP mode here.

By the way, I found out only recently why Ubuntu does not "detect" SMP kernel during installation. I read from somewhere that since the CD is already full and having single CD installation is such a nice thing to have, they had to choose a kernel that works for all, i386. So now I know. :)

---

### Post by Antonio Ricardo Correia on 2005-10-18
[QUOTE=pioni]I find it hard to believe that nobody else with Hyperthreading capable processor has this problem, if indeed HT is causing problems. I suppose HT processors are quite common nowadays, even though I don't have one (and probably never will). My guess is that SMP kernel is partly broken, i.e. works for some, fails for others. To my knowledge this happens only on Ubuntu, as other distributions have worked just fine in SMP mode here.

By the way, I found out only recently why Ubuntu does not "detect" SMP kernel during installation. I read from somewhere that since the CD is already full and having single CD installation is such a nice thing to have, they had to choose a kernel that works for all, i386. So now I know. :)[/QUOTE]

Yes, it's really strange. I suppose that anyone with a Pentium4 or something else with hyperthreading should be having this problem (or at least a significant percentage among them) but I don't see many messages complaining about this. This comes from Hoary times, continues with Breezy and almost no one comes forward complaining. I submited a bug the 1st October and they told me to address it to the develoment team. Great help!

Best regards,
A.Correia

---

### Post by duffydack on 2005-10-24
I dont have the problem in hoary, just breezy
But my problem isnt crashing or locking up, its just general lag while using the OS, dragging windows around and stuff 
(Kubuntu breezy btw)
sorry i dont have anymore info to add..Im still waitin to read somewhere its been resolved.

---

### Post by Antonio Ricardo Correia on 2005-10-24
[QUOTE=duffydack]I dont have the problem in hoary, just breezy
But my problem isnt crashing or locking up, its just general lag while using the OS, dragging windows around and stuff 
(Kubuntu breezy btw)
sorry i dont have anymore info to add..Im still waitin to read somewhere its been resolved.[/QUOTE]

I've sent another bug request today regarding smp kernels on Pentium IV machines. Now let's wait and see what happens.

Best regards,
A.Correia

PS - You should probably send one too, because your problem is not exactly the same as mine.

---

### Post by duffydack on 2005-10-25
i just found out i got a bad stick of ram :'(   which might explain half the problems ive had with kubuntu.

---

