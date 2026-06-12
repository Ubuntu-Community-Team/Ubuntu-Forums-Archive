---
title: "boot hangs w/ 2.6.20-16"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by sztorok on 2007-09-07
First, my chipset is not detected correctly - it's P35 (GA-P35C-DS3R m/b), not G33.

The second problem is, whichever kernel I am loading from grub I am having those weird USB error messages all the time, flooding my VT, it's almost impossible to work while pressing
Ctrl-L every two seconds.

I am running 64 bit 7.04, so I could see this message in restricted mode only:

----- BEGIN -----
* Reading files needed to boot...

* Setting preliminary keymap...

* Preparing restricted drivers...

usb 8-3: device descriptor read/64, error -71

usb 8-3: new high speed USB device using ehci_hcd and address 3



* Starting basic networking...

* Starting kernel event manager...

* Loading hardware drivers...

r8169: eth0: link up

r8169: eth0: link up

usb 8-3: device descriptor read/64, error -71

agpgart: Detected an Intel G33 Chipset.

Bad page state in process 'modprobe'

page:ffff81012fd1ad90 flags:0x0000000000000000 mapping:00000000000000000 mapcount:1 count:0

Trying to fix it up, but a reboot is needed

Backtrace:



Call Trace:

modprobe [3984]: segfault at 00000000000000000018 rip 00002b293a7d7090 rsp 00007fff70562d48 error 4

----- END -----

After this my only option is a hard reset; Shift-PgUp or Ctrl-Alt-Del doesn't work.
I am thinking about downloading the latest kernel from kernel.org and recompiling.
But before that I need to know if this is a known issue and if the newest kernel will solve it?
Any insight much appreciated.
Szilard

---

### Post by reckless2k2 on 2007-09-07
what about 2.6.20-15? my one pc is so buggy with -16 that i can't use it but -15 is fine.

---

### Post by Pumalite on 2007-09-07
Your problem is chipset P35. Research it.

---

### Post by sztorok on 2007-09-07
> **reckless2k2 said:**
> what about 2.6.20-15? my one pc is so buggy with -16 that i can't use it but -15 is fine.

yes, 15 works, but only in restricted mode.  The annoying USB error messages are now not flooding the text console, maybe b/c I changed some bios settings.

BTW:
It would be really great, to be able to see the boot messages w/ the 64 bit version!
How hard it is to re-enable them?

---

### Post by merlinus on 2007-09-07
Press e at grub menu, arrow down to the kernel you are booting from, and delete "quiet" from that line.  You may have to press e again to do this.

Then press b to boot.

-merlin

---

### Post by sztorok on 2007-09-07
> **Pumalite said:**
> Your problem is chipset P35. Research it.

It sounds like the best way to go is to build a shiny new 2.6.22.6.
I am new to Ubuntu. Any known pitfalls or distribution-specific docs out there on
rolling your own kernels? TIA

---

### Post by Pumalite on 2007-09-07
If you can do it; great, but if I were you I would get a motherboard with a different chipset (If you want to run Ubuntu full blast without problems). I use Intel D975XBX. Good luck.

---

### Post by sztorok on 2007-09-07
> **merlinus said:**
> Press e at grub menu, arrow down to the kernel you are booting from, and delete "quiet" from that line.  You may have to press e again to do this.

Then press b to boot.

-merlin

Thank you merlinus!

---

### Post by merlinus on 2007-09-07
You are welcome.  Glad to help, and hope that the scrolling boot-up messages can shed some light on your situation.

-merlin

---

### Post by sztorok on 2007-09-07
> **Pumalite said:**
> If you can do it; great, but if I were you I would get a motherboard with a different chipset (If you want to run Ubuntu full blast without problems). I use Intel D975XBX. Good luck.

Thank you for the reply pumalite. The badaxe is a great board, especially tempting is its stability in the reviews, but for me it's not an option (penryn, ddr3 with the p35). It's easier to change the kernel then the m/b and then I need to reinstall my other OS & apps - it took me two weeks to set things up as I wanted...
I googled some guides re kernel upgrade though, I will give it a try and give you guys an update.

[http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html](http://www.ubuntugeek.com/howto-upgrade-kernel2622-9-generic-in-feisty-fawn.html)
[http://phoenix-ani.blogspot.com/2007/08/howto-upgrade-kernel2622-9-generic-in.html](http://phoenix-ani.blogspot.com/2007/08/howto-upgrade-kernel2622-9-generic-in.html)

---

### Post by Pumalite on 2007-09-07
You are welcome. I hope it all goes well for you.

---

### Post by sztorok on 2007-09-07
Update: the kernel upgrade went without problems. I think even the tv tuner card is now recognized correctly, but I didn't tested it yet.
Regarding making the boot messages visible: in /boot/grub/menu.list removing both 'quiet' and 'splash' is required.
Thanks to everyone who helped.

---

### Post by musicinmybrain on 2007-09-11
> **Pumalite said:**
> Your problem is chipset P35. Research it.

What an idiotic response. When a kernel update breaks your previously functioning system, obviously the problem is you have the wrong hardware and you should buy a new motherboard. Or not.

For the record, 2.6.20-16 gave me the same issue on a Gigabyte GA-P35-DS3R. Everything was working perfectly on 2.6.20-15. I downgraded to the older kernel version for now, but I did try a Gutsy Tribe 5 live CD and the newer kernel works as well.

---

### Post by sztorok on 2007-09-11
> **musicinmybrain said:**
> What an idiotic response. When a kernel update breaks your previously functioning system, obviously the problem is you have the wrong hardware and you should buy a new motherboard. Or not.

For the record, 2.6.20-16 gave me the same issue on a Gigabyte GA-P35-DS3R. Everything was working perfectly on 2.6.20-15. I downgraded to the older kernel version for now, but I did try a Gutsy Tribe 5 live CD and the newer kernel works as well.

Same experience w/ the kernels here. I actually installed 2.6.22 and now at least I have a choice. The two things not working are an old tuner card (it's not working in xp either) and compiz (my video card is too new). None of that is the M/Bs fault - I really like my DS3R, I just wish I have more time for Linux!

---

### Post by Pumalite on 2007-09-11
> **sztorok said:**
> It sounds like the best way to go is to build a shiny new 2.6.22.6.
I am new to Ubuntu. Any known pitfalls or distribution-specific docs out there on
rolling your own kernels? TIA

[http://ubuntuforums.org/archive/index.php/t-470786.html](http://ubuntuforums.org/archive/index.php/t-470786.html)

---

### Post by musicinmybrain on 2007-09-11
In case anyone is curious regarding the regression from 2.6.20-15 to 2.6.20-16, I am using the GA-P35-DS3R in AHCI mode.

---

### Post by Pumalite on 2007-09-11
Good for you.

---

### Post by sztorok on 2007-09-11
> **Pumalite said:**
> [http://ubuntuforums.org/archive/index.php/t-470786.html](http://ubuntuforums.org/archive/index.php/t-470786.html)


Thank you for the link Pumalite. My setup is a bit different; RAID0 and RAID1, both on ICH9R (it's set to RAID mode in BIOS) and JMB363 (AHCI in BIOS) is used for eSATA at the moment (if I will need more space, I plan to use it as a port multiplier, for external RAID). This works nicely in XP.
In Linux however even w/ the latest kernel and the dm drivers I can only see the RAID1 volume, but not the stripe. I think the kernel is actually ok, but DM needs a couple more dev. cycles to be there (?).

I can live w/ this, since I can access my data from the Mirror under any OS - and have a dedicated swap partition for Linux anyway - while using the stripe (in XP) for pagefiles, Photoshop scratch, ripping, etc.

P.S.: My original, boot-hanging problem was solved by installing the latest kernel.

---

### Post by Pumalite on 2007-09-11
You are welcome. Glad you made it work.

---

### Post by gummih on 2007-09-27
> **sztorok said:**
> First, my chipset is not detected correctly - it's P35 (GA-P35C-DS3R m/b), not G33.

I am running 64 bit 7.04, so I could see this message in restricted mode only:

agpgart: Detected an Intel G33 Chipset.

Bad page state in process 'modprobe'

page:ffff81012fd1ad90 flags:0x0000000000000000 mapping:00000000000000000 mapcount:1 count:0

Trying to fix it up, but a reboot is needed

Backtrace:



Call Trace:

modprobe [3984]: segfault at 00000000000000000018 rip 00002b293a7d7090 rsp 00007fff70562d48 error 4

----- END -----

After this my only option is a hard reset; Shift-PgUp or Ctrl-Alt-Del doesn't work.
I am thinking about downloading the latest kernel from kernel.org and recompiling.
But before that I need to know if this is a known issue and if the newest kernel will solve it?
Any insight much appreciated.
Szilard

I've been having this  exact issue. 2.6.20-15 worked fine, upgraded to 16 and it worked fine for a while too - then after some upgrades all was ruined. A clean install of 15 works fine, but even adding just the supported upgrades breaks the system (I haven't had time to eliminate which one it is)

So I guess I'll just install 15 once more and then wait for the 7.10 release

---

