---
title: "PCI issues on Gutsy kernels"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by starglimmered on 2007-10-15
I upgraded to Gutsy on my Toshiba Satellite Pro P100 laptop yesterday, everything went smoothly. There are a just a couple of issues:

(1) Using either of the 2.6.22 kernels (386 or generic) gives these warnings on boot:

```

Oct 14 19:44:23 europa kernel: [    0.261439] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
Oct 14 19:44:23 europa kernel: [    0.261441] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
Oct 14 19:44:23 europa kernel: [    0.261443] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Oct 14 19:44:23 europa kernel: [    0.261445] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
Oct 14 19:44:23 europa kernel: [    0.261448] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
Oct 14 19:44:23 europa kernel: [    0.261450] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
Oct 14 19:44:23 europa kernel: [    0.261452] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
Oct 14 19:44:23 europa kernel: [    0.261454] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
Oct 14 19:44:23 europa kernel: [    0.261456] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2

```

Sound no longer works and I suspect these PCI issues are the problem.
Booting from the Gutsy 2.6.20-generic kernel does not have these errors and sound works fine. However, on the 2.6.20 kernel, X video does not work properly and each time X is started it prompts me to reconfigure the X server, which I do (nvidia driver, 1440x900 screen and resolution) but I can only ever get it to start in 1024x768.

The graphics problems are not present when booting from the 2.6.22-generic kernel.

(2) The ipw3945 wifi kernel modules are not included in the 2.6.22-386 build, only the 2.6.22-generic build. This is a shame because the -386 build is enabled by default. 

Other than that, great work on the Gutsy release. Can anyone help with the PCI issues? 

Kind regards,
Carl

---

### Post by xircius on 2007-10-18
I also have the Cannot Allocate message... I am on Gutsy 64-bit. I plan to re-install from a disk for a fresh start and see if that works. I will post results here after I do so. Anyone else have this shortly after bootloader?

---

### Post by barthel on 2007-10-21
I have the same messages and no sound with the 2.6.22-14 generic kernel.. (My Toshiba is a P105-S9339). I can also confirm that sound works with the 2.6.20-16 generic kernel.

However, I have the buggy 3.30 BIOS, so when I first upgraded to gutsy, the sound card was not recognized at all. I did an 
```
update-initramfs -u -k $(uname -r)
``` to patch the buggy DSDT table for the new kernel and the sound card was available on the next reboot, although I still had the PCI messages noted above. (Under Fesity, that was sufficient to get sound working correctly for me.)

I can also confirm the "low resolution graphics" purgatory when using the 2.6.20 kernel instead. ARGH!!!

I haven't had any success yet with using the latest ALSA drivers, as suggested in other threads.

Oh. One other odd thing about my gutsy upgrade: it installed a 386 kernel -- which is completely inappropriate for a Centrino Duo processor...

Is there an official bug report on this yet? Or has all the discussion been limited to these forums?

---

### Post by lespaul_rentals on 2007-10-21
I have EXACTLY the same problem with the same Toshiba model, except it can't allocate memory to "4" instead of 7/8/9.  It displays a black screen for about 45 seconds, then the login screen comes on.  Overall, I've noticed a **huge** increase in bootup time and an overall bloated feeling.  7.10 has disappointed me so far.  :(

---

### Post by lyndaj70 on 2007-10-21
I have the same problems on allocating resources on bootup....

A long delay, then those same messages, plus one about a bios bug, but I'm not sure where to locate the file to post it....

Also, when the login screen appears, it is normal, but when you type your username and password, the font is HUGE... and at first when you login everything in incredibly large, like it's trying to fit everything in a 200X200 display resolution (just a random number guess there, but it is really big -- a single word will take up almost a third of the screen).

Does anyone know if there is a fix for this?

And if anyone knows where to find the log with the errors on bootup, please contact me with the location and I will post them..

Thanks,
Lynda

---

### Post by PaulFr on 2007-10-21
With my Satellite P105-S6084 and upgrade to Gutsy (2.6.22-14-generic), I can confirm:

1. The PCI errors for 7|8|9.

2. Sound did not work. For Feisty, I had to fix with a custom DSDT and then it worked. For Gutsy, I have got sound working with "acpi=off". Not an ideal solution, but works for now.

3. Graphics resolution on one reboot was 1024x768, but I got it back to 1440x900 by repeating what I did in Feisty: install "915resolution" package, then set up as per **[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)** with the i810 driver in xorg.conf.

---

### Post by barthel on 2007-10-22
I've verified that, on my system at least, the PCI messages are not related to failure to recognize the sound card.

[LIST=1]
[*]00:1c:0-2 are the PCI Express ports (00:1b:0 is the sound card)
[*]The PCI messages still appear even though I got the sound card recognized (although still no sound)
[/LIST]

By searching for 82801G, I found that others with the same audio controller (not just Toshibas) have had success restoring sound by using module assistant. Although I don't yet have working sound, at least the device is recognized and the mixer controls are responding--one step closer.

The steps for the module assistant fix are:
> **holodad said:**
> 
*  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings


While it didn't work completely for me, it did get the sound card recognized by ALSA, so it's definitely a step in the right direction.

---

### Post by lespaul_rentals on 2007-10-22
> **lyndaj70 said:**
> I have the same problems on allocating resources on bootup....

A long delay, then those same messages, plus one about a bios bug, but I'm not sure where to locate the file to post it....

Also, when the login screen appears, it is normal, but when you type your username and password, the font is HUGE... and at first when you login everything in incredibly large, like it's trying to fit everything in a 200X200 display resolution (just a random number guess there, but it is really big -- a single word will take up almost a third of the screen).

Does anyone know if there is a fix for this?

And if anyone knows where to find the log with the errors on bootup, please contact me with the location and I will post them..

Thanks,
Lynda

I have EXACTLY the same problem!

---

### Post by gene6482 on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There's already a bug filed.

---

