---
title: "Four Ubuntu Installations -- ALL FAIL"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by rbronson1976 on 2005-09-10
Hello all, I am new to Ubuntu and Linux in general. I heard good things about Ubuntu so I wanted to try it. Unfortunately I can't get past the install.

I have an AMD 64 Athlon machine with 1GB RAM. The motherboard is MICRO-STAR MS-7145. This machine is not exotic. It's a relatively new eMachines T6520, straight out of the box. Please don't laugh at eMachines. BTW, this machine works great w/Windows -- zero problems.

I have tried to install four different Ubuntu distributions and they all hang.

Here are the four installations I've tried:
5.10 "Breezy Badger" for AMD64
5.10 "Breezy Badger" for i386
5.04 "Hoary Hedgehog" for AMD64
5.04 "Hoary Hedgehog" for i386

In all four cases I am doing the default installation, not the "server" installation.

First, I'd like to describe the problem I see with the v5.04 installations. Both the AMD64 and the i386 releases have the exact same hang behavior:

The installation starts out fine. Then, I see the following message:

     ohci-hcd: already loaded
     ohci-hcd: already loaded
     ehci-hcd: already loaded
     ohci1394: already loaded
   pci      [success]
ohci_hcd 0000:00:13.1 Unlink after no-IRQ?  Different ACPI or APIC settings may help.

That's it, nothing else happens -- there's CD or hard drive activity. It just hangs.

Now, I should also mention that I also tried the boot option, 'noapic nolapic', and that seemed to get by this hang problem, but then I had problems with DHCP so I just gave up.

Incidentally, I don't think 'noapic nolapic' is a "solution" to the hang problem. Why should I have to cripple the operating system?

---------------------

Now for the 5.10 "Breezy Badger" installations. Both the AMD64 and the i386 releases have the exact same hang behavior:

The installation starts out fine. Then, I see the following message:

Running /etc/hotplug/scsi.rc
   scsi     [success]
[   40.229618] ACPI: CPU0 (power states C1[C1])
[   40.229642] ACPI: Processor [CPU0] supports 8 throttling states}
Starting system log daemon: syslogd, klogd

That's it -- no hard drive activity, no CD ROM activity, nothing. It just hangs. 

Why must it be this way? Does anyone have an idea of what could be wrong? Obviously, to a newbie, the messages on the screen are useless. I am in the midst of trying other distros. I know SuSE 10 is fine -- no problems at all -- it allows me to connect to the Internet.

This is not the first Linux distro I've had problems with. It's really frustrating -- I try to like this OS, I sincerely want to like it and use it, but it's so hard to use. Even though you probably hate Microsoft at least they don't require their users to know about APIC settings or a myriad of other acronyms. Windows just works, very unlike Linux. I'm ready to give up. I know there is probably some weird set of options I should try when I Ubuntu but why should I have to? Why can't it just work like Windows? Why can't you detect my hardware and do the right thing?

BTW, I will say you have a very nice web site.

Thanks very much.

---

### Post by Mez on 2005-09-10
what do you have attached via USB?

---

### Post by pizzach on 2005-09-10
Just set the comp down for a moment (or the night) and come back to it in the morning.  Okay.  I'm still pretty newbie to linux too so take what I say with a grain of salt.  

You said you started from the cd with "noapic nolapic".  Did the lack of DHCP effect occur after the installation, or just when the computer tried to update itself during installation.  For some reason right now I'm thinking that changing how the cd boots doesn't change the install procedure.  If the DHCP problem was just during the installation time, then try updating when you're actually in the OS.  If it was in the OS, have you tried looking up ethernet drivers?

Keep in mind, how Windows runs has no corelation to how well linux will run.  A lot of times new special drivers are included with brand new PCs needed to make even xp function correctly.  With out them it would suck about the same as linux but they tend to be included with the computer on separate cds or even preinstalled on an image cd you people don't even notice because everything is pre-setup.  My laptop runs better on vanilla Ubuntu than Vanilla Windows XP.  It would be nice if there were little stickers on computers that said "Made for Linux" much like there are "Made for XP" stickers nowadays.  But that is another digression. :cool:

---

### Post by rbronson1976 on 2005-09-10
[QUOTE=Mez]what do you have attached via USB?[/QUOTE]

No, there was nothing attached to any of the USB ports.

---

### Post by rbronson1976 on 2005-09-10
[QUOTE=pizzach]Just set the comp down for a moment (or the night) and come back to it in the morning.  Okay.  I'm still pretty newbie to linux too so take what I say with a grain of salt. [/QUOTE]

Set it down? I'm ready to blast the dang thing. 

[QUOTE=pizzach]You said you started from the cd with "noapic nolapic".  Did the lack of DHCP effect occur after the installation, or just when the computer tried to update itself during installation.  For some reason right now I'm thinking that changing how the cd boots doesn't change the install procedure.  If the DHCP problem was just during the installation time, then try updating when you're actually in the OS.  If it was in the OS, have you tried looking up ethernet drivers?[/QUOTE]

The DHCP problem occurred during installation. Specifying "noapic nolapic" just allowed the installation to progress a bit further than it had.

As I said, I don't want to specify "noapic nolapic". That just dummies down the computer. Ubuntu can't figure out how to handle it so I basically tell Ubunto, "that's okay, just ignore APIC and move on."

Ethernet drivers? Why does this have to be such a manual process? I guess I'm starting to understand why Linux only owns a whopping 3% of the desktop market. The Linux people need to take a lesson form Microsoft Windows..oh, excuse me, I mean, "Micro$oft Windoze".

The more I learn of Linux the more I hate it. It's like going back to stone knives and bear skins. I'm going back to civilization. You guys can keep your pathetic "hobby OS".

---

### Post by jfsanchez on 2005-11-16
Pop your box open and unplug the cable on the motherboard that connects the memory card readers.  This should help, but I think you will still have to work through getting x server to work properly.  There is a thread on that if you search for emachines

---

### Post by dmxubuntu on 2005-11-25
> 
The more I learn of Linux the more I hate it. It's like going back to stone knives and bear skins. I'm going back to civilization. You guys can keep your pathetic "hobby OS".


Don't take out your frustration on people who are just here like you, looking into an alternative to the monopoly. Of course, everything is geared to work under Windows and not anything else! Just stick with MS if you like. Nobody will throw flak at you for it.

:(

---

