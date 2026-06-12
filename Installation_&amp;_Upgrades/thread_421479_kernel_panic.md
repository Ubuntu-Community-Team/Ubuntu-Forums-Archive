---
title: "kernel panic??????"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by concer on 2007-04-24
hi, i hawe downloadet the new ubuntu 7.04

when i try to boot from the cd i get the boot loader screan, tehn select install ubuntu and then i get a error message "kernel panic" and everithing stand still.......
 please help a total linux beginner....

---

### Post by kidders on 2007-04-25
Hi there,

This is unfortunate. :-(

A kernel panic is the result of an unexpected combination of circumstances that the Linux kernel (the layer of software that sits under the operating system) can't deal with. If there is nothing the kernel can do to recover, the whole computer often locks up. Examples of the kind of thing I'm talking about might be your CPU telling Linux that 2 + 2 = 6,944.75 ... or a low-level buffer overflow ... or badly written software ... or the contents of memory changing for no reason. What it's likely to be depends on what was happening immediately before the panic.

Could you post the following:

[LIST]
[*]A description of your hardware
[*]Whether the CD you are using is a release version of Feisty
[*]Whether this problem occurs with other Linuxes
[*]What (in as much detail as you can) Ubuntu does before the panic
[*]Whether the panic has ever _not_ happened
[/LIST]

I know this is a lot to ask for, but the more information you can provide the better. Essentially, anyone who tries to help you will be interested in...

[LIST=1]
[*]Ruling out hardware faults (such as an overheating CPU or bad RAM).
[*]Trying to find a reason to blame the error on faulty code (eg a driver being loaded at boot-time).
[*]Checking for known issues with your specific motherboard, PCI cards, or other devices.
[/LIST]

Because kernel panics are such low-level errors, their cause can be quite difficult to pin down. In the meantime, you might like to try a different Ubuntu release (or perhaps a distro from another company). Since you're new to Linux, you'll no doubt be interested in learning the platform as quickly as possible ... but don't worry ... Linux skills are very transferrable between distros. If you *do* decide to try another CD, try to use one that _does not use the same kernel release_ as the one you already have, especially if the panic occurs early in the boot process. If a software bug is to blame for your problem, this precaution could help eliminate it.

I hope that helps a little.

---

### Post by concer on 2007-04-29
1. ok, i am trying to instal ubuntu 7.04 on an
 IBM Thinkpad 600 Laptop
233 MHz MMX PII
256 MB RAM
20 GB HDD

2. i downloaded the iso of ubuntu 7.04 (kubuntu) from the ubuntu site 


3. the kernel panic apeares right after i select the install or start ubuntu from the boot screen

4. ubuntu does nothing, it just boot from the CD to the boot menu and when i select the first option (install or boot ubuntu) the kernel panic message apeares

5. the message apears everi time i try to instal ubuntu 7.04

now i hawe found an older version, ubuntu 5.04.  the install is sucessfull, no error messages.


is there a way to update (upgrade) to 7.04 without installing the hole system again???

---

### Post by kidders on 2007-04-29
Hey again,

> **concer said:**
> now i hawe found an older version, ubuntu 5.04.  the install is sucessfull, no error messages.Excellent. :-) The panic is probably due to a feature that has been added to the Linux kernel since 5.04 that is incompatible with a computer as old as yours. Either that, or it's a bug in Feisty.

> **concer said:**
> is there a way to update (upgrade) to 7.04 without installing the hole system again???You can upgrade your Ubuntu in stages, if you'd like to ... ie Dapper -> Edgy -> Feisty. There are a few things worth mentioning though...

[LIST]
[*]There is no way to be certain that the boot-time kernel panic won't reccur if you do.
[*]Since it's so old, using very new versions of any OS will be a drag on your laptop's performance.
[*]Many of the new features introduced into Ubuntu since Dapper (most notably the UI improvements) won't work on your laptop anyway, so upgrading may not be worthwhile.
[*]Dapper is the most stable of all Ubuntu releases.
[/LIST]

Whether to upgrade is entirely up to you, but do bear in mind that you can't *down*grade again without reinstalling Ubuntu.

Regarding the kernel panic, it's almost always the case that kernel problems with laptops are caused by power management issues. This is particularly true of older laptops, that very often have faulty ACPI implementations, for instance.  If you want to, you could try temporarily disabling all power management features in your BIOS *and* in Ubuntu. Switching off other non-essential BIOS features would also be worthwhile. You never know ... Feisty might suddenly decide to work for you, in which case, working out where the problem is would be a simple matter of elimination.

---

### Post by concer on 2007-05-11
You said 
"You can upgrade your Ubuntu in stages, if you'd like to ... ie Dapper -> Edgy -> Feisty."

How???

---

### Post by kidders on 2007-05-11
There is detailed upgrade documentation available at ubuntu.com.

---

### Post by medina32 on 2007-07-25
I have the a problem with the kernel too here is what happends

I'm trying to install ubuntu in a 

compaq presario sr1020nx
celeron 2.8ghz
512 of RAM
70 GB of hard drive memory

and when i tried to lunch the live cd it puts a blank screen that in the bottom displays this:

Int 14: CR2 df800000 err00000000 EdP c020c384 CS 00000000
Stack: c00f8050 c03f129 c037d8c 00000002 c00f8050 00000000 00000000
:confused:

I've tried to initialized using the comand "boot: linux acpi=off" and its start loading and then it displays this:

[46.929320] VFS: Cannot open root device "<NULL>" or unknown-block(104,1)
[46.929393] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

:confused:
can any one help me i'll like to get rid of xp and install ubuntu

---

### Post by kDDs on 2007-11-12
having exactly the same problem..... any soloution? i can get a 64-bit version of ubuntu to work without problems... just not 32!!! i get that error message when i boot with "noapic"

---

### Post by kDDs on 2007-11-16
ok a soloution i found was to boot with "noapic" in safe graphics mode.

---

