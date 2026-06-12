---
title: "A few questions before installing if it's ok"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by SheppeyRed on 2008-10-28
Hi all,

First post for me here in over 2 years. \\:D/

So on to the matter at hand.

I want to install Ubuntu - obviously ;) - and have a few questions:-

1) SATA HDs and DVD-RAMs

I have these installed on my PC and don't have any IDE drives. Currently I have 1 x Samsung 80Gb SATA HD and 2 x 500Gb Samsung SATA HDs plus 2 x Samsung SATA Lightscribe DVD-RAMs. Is this likely to cause me any issue? I'm assuming not but best to ask now **before** I install Ubuntu! ;)

2) My proposed setup

OK, for my HDs and DVDs I have the following setup with what I have them set to and what I would like them to be:-

Drive:-

C: Windows Vista 32 bit Home Premium Edition (80Gb HD)
D: DVD-RAM
E: DVD-RAM
F: Proposed location for Ubuntu (126Gb partition of 1 HD)
G: Data storage (500GB HD)
H: Program storage (338Gb Partition of 1 HD)

Is this likely to cause me any issues? I hope not but, again, best to ask now.

3) Dual booting

I obviously want to dual boot Vista and Ubuntu. I don't know what things are like now with Linux as I last used Mandrake Linux v7 for my last Linux Distro. I want to dual boot and would like to have it so that I can choose which OS I want to boot at Startup with 1 set to auto boot if I don't make a decision within x time. Can this be done? If so, can I select the OS that is the default to boot?

4) Hardware compatibility

While Mandrake Linux was the last Linux Distro I used, I did try and install Debian Linux on one of my PCs but never got it working due to hardware compatibility issues. Are there any resources available where I can check my hardware setup for compatibility with Ubuntu or is my only recourse to either read through lists of supported hardware or post my hardware setup here and get feedback on any likely issues, if any?

Many thanks for your time and sorry if these questions have been asked before but I did read a fair few pages before posting and saw no thread similar to mine.

SR

---

### Post by dstew on 2008-10-28
1. Ubuntu loves SATA disks, but sometimes the grub boot loader has trouble getting the disk order correct. When you install, grub is fed the order determined by the Live CD Linux system. However, when grub boots, it determines the order from the system BIOS. Sometimes these two don't agree. You can always fix it, but sometimes it makes people a bit crazy.

2. Your setup is fine overall. You need to use the Linux drive and partition names though. I like to partition before installing, so I have the Linux partitions ready to go. Sometimes if you partition in the middle of the installation, and make a mistake, lots of problems arise. You can partition before installing using the Gnome Partition Editor (gparted) from a Live CD boot.

3. You can dual-boot using the grub boot manager. Sometimes there can be grub installation issues. The grub installer may not get the disk order right, but it usually works OK. If it does not install correctly you can usually fix it. Post here if you have problems. And, you can always restore the Vista booter (if you have a Windows recovery disk) if you need to. You can even set up the Vista booter to dual-boot Linux, but it is harder to do than using grub.

4. Check hardware [here]("https://wiki.ubuntu.com/HardwareSupport/").

---

### Post by SheppeyRed on 2008-10-28
Well - I hit my first issue it seems. The BIOS doesn't recognise my keyboard while the boot manager loads so I can't select Ubuntu from the list of 2 OSs I have and Windows gets loaded each time. :(

It's a Saitek Eclipse USB keyboard and none of the keys work **until** Windows has loaded.

Not sure how to resolve this tbh.

---

### Post by bpalone on 2008-10-28
Is USB turned off in your BIOS?  

Do you have access to another USB Keyboard to see if it is the keyboard?

My first guess would be the BIOS, but with Vista all bets are off as it sure broke a lot of hardware.  And, some Vista hardware may not play well outside of vista.

My $0.02 worth of thought.

---

### Post by JordanLeach on 2008-10-28
i sometimes have the same problem with my saitek eclipse, but i find if you use a different keyboard while in the bios then just switch back to it while in the o/s then it should work.

---

### Post by SheppeyRed on 2008-10-29
Hi all,

Thanks for the replies.

Hmmmm, so the Saitek keyboard can be an issue then? Just as well that mine developed a fault last week (space bar is playing up, as is the shift key) and that I'm looking at changing it to a Logitech one. ;)

I'll let you know how I get on when I get the new keyboard.

Cheers,

SR

---

