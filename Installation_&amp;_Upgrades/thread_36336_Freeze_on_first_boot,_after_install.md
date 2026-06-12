---
title: "Freeze on first boot, after install"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by TestDummy! on 2005-05-22
Hello again, I've been trying to install Ubuntu (Hoary) onto another one of my computers, which is..

Celeron 400MHz
ASUS P3V4X 
256MB RAM
20GB Hard Drive
ATi Rage Pro video (If I recall..) 
Generic PCI sound

I install it and the install seems to go on fine, then it gets to first boot, says the stuff about loading the kernel, gets to the part where it says 

**Starting Ubuntu..** 

Then it just stalls, nothing... 

If I start it in Recovery Mode, it gets past that, but then gets caught up in trying to probe drive IRQ's for drives that don't even exist in the computer (The computer only has one hard drive and one CDROM yet it's trying to check for ones past hda, hdb and hdc). I dunno what's up. Warty worked, but this doesn't. 

Shame too, it seems my main computer is the only one Hoary seems to work well on :( 

Any ideas?

---

### Post by TestDummy! on 2005-05-24
I know it's kinda rude of me to bump this, but I've tried a lot of things, but nothing seems to work. I don't know what else to do, or why it's stalling. 

I've also asked on #ubuntu, but I personally think it's WAY too busy there. Nice community, but just really, really busy. 

But I'm still stuck. Warty worked somewhat on there, but Hoary has been a butthead on all but one computer for me :| . I don't know what really is up with this thing.

---

### Post by lafnlab on 2005-05-24
I'm installing Kubuntu for the first time and had a similar problem. I've used Slackware in the past and decided to try out Kubuntu on my new/refurb IBM T23 laptop (Pentium 3).

After a few fits trying to install it, I finally got it to the point where I could boot, but the system seemed to hang. I hit the power button, then hit the ESC key when GRUB came up. I tried the recovery mode, which seemed to work (I didn't have the problems with IRQs and such), but it got to the root prompt. 

Firts thing I tried to enter was gdm, which didn't work, and neither did startx. I typed ls and it only howed a couple of files. I typed login, then logged in as a user. However, when I typed ls there, nothing came up. I typed exit to get out of user space, then typed exit again to see if I could get out of root. 

It started to act like it was going to shut down, then it started unpacking a bunch of files. I'm guessing these files are necessary to make the regular kernel work, as opposed to recovery mode.

Hope this helps... and I hope it works for me as well - it's still unpacking. :-\"

---

### Post by theerga on 2005-05-26
I had issues  booting because of my video card at first. i got it working using dpkg-reconficure xserver-xorg and then selecting the aproiate driver and the right pci bus. i would recomend going through that selecting the ati driver in tesdummy's case dont know about you lafnlab and then trying to use gdm. i dont know about the irq problem, but if gdm fails to load read those messages carefully and look for where it says wich bus has the right video card for that driver

---

### Post by TestDummy! on 2005-05-26
[QUOTE=theerga]I had issues  booting because of my video card at first. i got it working using dpkg-reconficure xserver-xorg and then selecting the aproiate driver and the right pci bus. i would recomend going through that selecting the ati driver in tesdummy's case dont know about you lafnlab and then trying to use gdm. i dont know about the irq problem, but if gdm fails to load read those messages carefully and look for where it says wich bus has the right video card for that driver[/QUOTE]
 I don't get what you mean.

If it's about the bus, it's an AGP card. But I cannot get to even a command line either way.

---

### Post by TestDummy! on 2005-05-30
I'm still stuck with this and I'm out of ideas.

It's not giving me any output or reason on why it's freezing, it just gets to starting and locks up, does nothing. I do not know why. I do actually want to get this to work, but nothing wants to work for me ;| 

I just don't understand why it's locking up...

---

### Post by mingus on 2005-05-30
Just to be sure I'm clear, you successfully installed, including the second stage?  And then is it hanging at your first post-install boot, just after the grub handoff?

Or is it hanging when it reboots into the second installation stage, and the installation is not complete?

And when you first booted the installation, what arguments did you pass to the kernel?  From the chip and HDD, appears this is older hardware; did you disable both acpi and apic?

---

### Post by TestDummy! on 2005-05-30
This is after the first part of the install is done, and it wants to boot for the first time without the cd and finish the install. 

I haven't tried disabling either of those things, but I actually do not know how anyway.

---

### Post by mingus on 2005-05-31
Then a few things you can try:

At the installation boot colon, add the following to your entry line:

noacpi acpi=off noapic

and if that doesn't work, the same with the additionof:  pci=biosirq

it is not uncommon for the BIOS on older hardware to conflict with newer power management (acpi) or irq assignment (apic) technologies.

Also consider going into BIOS setup and disabling all power management if you can, including apm (the predecessor to acpi).

---

### Post by TestDummy! on 2005-05-31
[quote="mingus"]At the installation boot colon, add the following to your entry line: ....[/quote] 

Where?? I don't really know where that is, and if it's where I think it is, it doesn't work.  :-? 

The power management in the BIOS was already disabled.

---

### Post by mingus on 2005-05-31
sorry I wasn't more clear . . .

when you boot from the install CD, there is a prompt.  You can type "linux" or just hit enter which effectively does the same thing.

to add kernel arguments, you type "linux" followed by the arguments.  For example:

:expert noacpi acpi=off noapic pci=biosirq vga=normal apm=off

then hit return

the vanilla install is "linux", but I would use "expert" so you can see and control better what is going on

(btw, this is the same technique you can use after installation at your boot menu prompt but hitting 'e', and then you can add an argument to that line.  However, once you've figured out what argument you need, you will want to add that to your boot loader control file (grub => menu.lst, lilo => lilo.conf) so that it's done for you each time)

the arguments above are the most commonly used to disable power mgmt, dynamic irq assignment, and the vesa frame buffer

when you reboot into the second stage of the installation - and for that matter, each time afterward - whatever kernel arguments you used at first have been passed to the boot loader control file.  It is possible that the kernel handled your first install boot without arguments, but after it has been set up, chokes the next time around without those arguments

I would concentrate on the fact that you are using older hardware.  Any number of things could be hanging you up besides the most common above, such as misreading the amount of RAM, failing to activate the swap partition, choking on a weird old floppy driver, etc.
   
So if the above doesn't work, you may have to do some homework and trial and error.

Your best sources of documentation probably are:

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/index.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/index.html)
[http://www.debian.org/releases/stable/i386/install.en.html](http://www.debian.org/releases/stable/i386/install.en.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO-1.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO-1.html)

these are the installation manuals for Ubuntu and Debian, and a library of kernel arguments

good luck

---

### Post by TestDummy! on 2005-06-02
[QUOTE=mingus]sorry I wasn't more clear . . .

when you boot from the install CD, there is a prompt.  You can type "linux" or just hit enter which effectively does the same thing.

to add kernel arguments, you type "linux" followed by the arguments.  For example:

:expert noacpi acpi=off noapic pci=biosirq vga=normal apm=off

then hit return

the vanilla install is "linux", but I would use "expert" so you can see and control better what is going on

(btw, this is the same technique you can use after installation at your boot menu prompt but hitting 'e', and then you can add an argument to that line.  However, once you've figured out what argument you need, you will want to add that to your boot loader control file (grub => menu.lst, lilo => lilo.conf) so that it's done for you each time)

the arguments above are the most commonly used to disable power mgmt, dynamic irq assignment, and the vesa frame buffer

when you reboot into the second stage of the installation - and for that matter, each time afterward - whatever kernel arguments you used at first have been passed to the boot loader control file.  It is possible that the kernel handled your first install boot without arguments, but after it has been set up, chokes the next time around without those arguments

I would concentrate on the fact that you are using older hardware.  Any number of things could be hanging you up besides the most common above, such as misreading the amount of RAM, failing to activate the swap partition, choking on a weird old floppy driver, etc.
   
So if the above doesn't work, you may have to do some homework and trial and error.

Your best sources of documentation probably are:

[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/index.html](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/index.html)
[http://www.debian.org/releases/stable/i386/install.en.html](http://www.debian.org/releases/stable/i386/install.en.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO-1.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO-1.html)

these are the installation manuals for Ubuntu and Debian, and a library of kernel arguments

good luck[/QUOTE]
 Well, I just tested out of curiosity, since I have both a install disc for Hoary and Warty...

Warty worked, oddly, without any trouble, I just went though the install as normal, and it was cool.

But Hoary doesn't, for some reason.

I've noticed this one computer here is the only one that smoothly updated from Warty to Hoary, all the others have some problem :( 

I still don't get what you mean very well.

---

### Post by mingus on 2005-06-02
What I mean is . . . it is possible that the kernel is finding something in the hardware that it doesn't know how to handle.  Or there is a conflict between *how* the hardware bios handles a function (for example, irq's) and what the kernel wants to do.  This happens in particular with old hardware like yours.

The kernel in Warty is different than in Hoary.  Usually the newer the kernel the better, but it is possible for something to work in an older kernel that is now a problem in the new version.

The kernel "arguments" that I gave you earlier are the most commonly used across Linux distributions to tell the kernel not to do certain things.  When you get the grub menu, press 'e' and add to the end of the line:

acpi=off noapic pci=biosirq vga=normal apm=off ide=nodma

That will turn off the 6 most common reasons for lock-up.  It's worth a try.

---

### Post by TestDummy! on 2005-06-02
None of those arguments seem to work. 

I know you keep on saying I have older hardware, and I know that, but I don't really have any unusal part in there, I don't really see why it'd screw up.

The BIOS isn't really all that old. Says 2001 ish. I know a lot probably has chaned between 2001 and now, but it isn't terribly old.

---

### Post by mingus on 2005-06-03
it would seem that I am wasting both your time and mine . . . so best of luck  O:)  . . .

--mingus

btw, your mobo dates 3/2000, the BIOS date is just an update.  *All* the technology in that box has changed *significantly*.  Both Windows and Linux have had major enhancements to be able to manage the conflicts between the old and new technologies.  A good job has been done making this transparent to the user, so you don't see it - but the conflicts are there, just the same.  You entered arguments above for 6 of them.

---

### Post by wolovids on 2005-06-15
[QUOTE=TestDummy!]I install it and the install seems to go on fine, then it gets to first boot, says the stuff about loading the kernel, gets to the part where it says 

**Starting Ubuntu..** 

Then it just stalls, nothing... 

If I start it in Recovery Mode, it gets past that, but then gets caught up in trying to probe drive IRQ's for drives that don't even exist in the computer (The computer only has one hard drive and one CDROM yet it's trying to check for ones past hda, hdb and hdc). I dunno what's up. Warty worked, but this doesn't. 

Shame too, it seems my main computer is the only one Hoary seems to work well on [/QUOTE]Wow, I am having the exact same issues with my older PII machine.  My PIII machine works like a charm.  The installation disk booted up fine and seemed to install correctly.  It asked me to remove the installation disk and reboot to finish installing the packages and it gets to "Starting Ubuntu ..." and just hangs.  I disabled APM and sent in noacpi boot parameters and it still does not boot.

NOTE: My Mepis installation prior worked well.

---

### Post by mingus on 2005-06-17
wolovids -

The boot process off the installation CD is not identical to after the installation is done.

Usually if the boot hangs right at the start, the problem is with the video.  The "Starting Ubuntu" simply means the kernel has been called.  The kernel then checks cpu and RAM and then loads the video framebuffer so that it can display messages about what it's doing.  It then looks at everything on the PCI bus and assigns IRQ's; here there can be 4 or 5 potential types of conflicts most of which are due to an older BIOS or older power management.

These problems can occur on one version of the kernel but not on another.  Either because of changes in how the kernel handles something, or because of how the kernel has been built by the distro.

If the framebuffer driver (vesafb) cannot communicate with the firmware on your video card, there will be no display and the system will usually lock.  Or, if the resolution is read wrong, there can be a problem.

Unfortunately, the solution is not always simple.  It depends on the video card.

First thing to try is to add the kernel argument:  "vga=ask".  This tells the kernel to prompt you for a video resolution to use.  It will offer you a "scan" option; when you do that it will try to read the card and tell you what it finds.  If this works, choose a low resolution for now, like 640x480.

Second thing to try is to disable the framebuffer driver.  Use this kernel argument:
video=vga16:off
be sure this is at the end of the kernel arguments.

If this doesn't work, google the boot arguments howto and look in the Ubuntu & Debian manuals for commands to disable all the power management and default irq assignment.

---

### Post by newtimes on 2005-07-17
[QUOTE=mingus]Then a few things you can try:

At the installation boot colon, add the following to your entry line:

noacpi acpi=off noapic

and if that doesn't work, the same with the additionof:  pci=biosirq

it is not uncommon for the BIOS on older hardware to conflict with newer power management (acpi) or irq assignment (apic) technologies.

Also consider going into BIOS setup and disabling all power management if you can, including apm (the predecessor to acpi).[/QUOTE]
 this helped me thanks....

---

