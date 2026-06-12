---
title: "Test drive hangs my Gateway machine"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by rghines1 on 2009-12-08
Heard raves about Ubuntu and wanted to give it a try but having no luck. First tried the Live CD boot before attempting installation.

During initial boot get a message about not able to enumerate USB 1-4.

Goes on to boot to the desktop but the keyboard and mouse do not respond. Mouse is on PS/2 and keyboard on USB. Mentions needing drivers for more efficient operation that are available for purchase but wasn't more specific. Guessing it might be the Nvidia drivers.

The led is blinking on the power switch like the computer is asleep.

Did verify the burned CD's integrity.

I'm using a Gateway 64-bit desktop that's less than a year old.

Richard

---

### Post by u.b.u.n.t.u on 2009-12-08
Hi and welcome to Ubuntu community.

What version of Ubuntu?

Have you got Ubuntu installed?

---

### Post by rghines1 on 2009-12-08
New version 9.1

Install attempt fails too with keyboard and mouse not responding at the language selection screen.

Richard

---

### Post by u.b.u.n.t.u on 2009-12-08
Going with the obvious here, are you able to test with a different keyboard and or mouse?

---

### Post by rghines1 on 2009-12-09
No. However my Gateway system is less than a year old. Richard

---

### Post by u.b.u.n.t.u on 2009-12-10
Is your computer a desktop or a laptop?

Check your BIOS settings. The keyboard and mouse should work by default with Ubuntu 9.10. If you are unable to test an alternative keyboard and mouse (for a desktop PC), then perhaps try Ubuntu 9.04 and see if that works.

---

### Post by rghines1 on 2009-12-16
Thanks for everyone replying. This is a desktop already running Vista and was going to try Ubuntu in a dual boot configuration as a fun learning experience. Since Ubuntu clearly does not like my hardware I'm going to let this project die.

Richard

---

### Post by phillw on 2009-12-16
Odd - I have a Gateway and Ubuntu Loved it, out of the box !!

Before you pack up & give up - are you using the 64 Bit version of Ubuntu ? If not - try it, as you have 64Bit machine. If you are trying it - Give the 32 Bit one a try.

As allways, before you do anything - check the md5 checksum on the cd you're booting from.

As you are having problems getting the boot cd to see your keyboard / mpouse - the attached has how to do this from Win.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Ensuring the burn speed of a prospective cd is at 4X speed, or even slower - Is also highly recommended if you are having a proble.

Regards,

Phill.
A happy Ubuntu & Gateway user

---

### Post by rghines1 on 2009-12-17
Hi Phill,

Odd indeed!

Followed the link's instructions on verifying the MD5 checksum with _Winmd5sum _on the ISO file. That verified OK  The integrity check on the boot CD passed too. Confident my boot media is good at this point. Have 64 bit machine so trying to get the 64 bit version to work first. Also booted the 32 bit version with mouse and keyboard freezing up again.

It was suggested to try an earlier Ubuntu version but prefer not to go to earlier version.  And to check Bios settings. Looked around in bios w/o seeing anything of interest to change that might make a difference.

I have a Gateway DX4720 64 bit desktop machine that less than a year old.

Richard

---

### Post by The Real Dave on 2009-12-17
I'm gonna go with what been said already, check the BIOS. Its a common source for such a problem. Looking for something like USB support, the actual title varies. What BIOS type have you? 

Also, are you using a generic keyboard and mouse, or something else? Does the mouse or keyboard have any special buttons, or is it bog standard?

How far along the boot process do you get? Try booting into the recovery console?

---

### Post by rghines1 on 2009-12-20
Hi Ubuntu devotees,

Had some time this weekend to try some things but failed miserably!

Another keyboard and and mouse did not help. Both still hang on me. Went into the USB bios settings and set keyboard and mouse legacy support to disabled, has been enabled all along. Tried a Microsoft keyboard and a Dell mouse. My originals were both Gateway devices.

Do get all the way to the GUI desktop but with keyboard and mouse frozen can't go any further.

Someone inquired about my bios. Its an American Megatrends v2.61

Tried unplugging the USB plug from the external hard drive, no change.

There was mention of trying recovery console but didn't see that option from Ubuntu CD.

Richard

---

### Post by phillw on 2009-12-20
> **rghines1 said:**
> Hi Ubuntu devotees,

Had some time this weekend to try some things but failed miserably!

Another keyboard and and mouse did not help. Both still hang on me. Went into the USB bios settings and set keyboard and mouse legacy support to disabled, has been enabled all along. Tried a Microsoft keyboard and a Dell mouse. My originals were both Gateway devices.

Do get all the way to the GUI desktop but with keyboard and mouse frozen can't go any further.

Someone inquired about my bios. Its an American Megatrends v2.61

Tried unplugging the USB plug from the external hard drive, no change.

There was mention of trying recovery console but didn't see that option from Ubuntu CD.

Richard

Seriously puzzled@phill .... Gateway use 'bog-standard' stuff in their computers - I am mystified.

As a sort of 'last throw of the dice' - Can you try grabbing the alternate CD image for 64 bit (It's marked as AMD64 - but don't worry) - That drops to CLI (Command line) and not GUI - I'm just real curious as to why it is not seeing your keyboard & mouse.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

9.10 is still new, but I've never heard of any OP with this issue. It may be worth trying 9.04.

9.04 is still fully updated for 18 months and can be upgraded to 9.10 easily
[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

TBH, I'm at a bit of a loss. I've never had problems with 9.04, 9.10 or the Alpha Release of 10.04 that I'm running now. 

Regards,


Phill.

---

### Post by efflandt on 2009-12-20
Check any alternative settings for USB in CMOS setup (at the Gateway splash screen before anything else loads).  Try alternative settings to see if one of the other USB settings works (legacy or auto or whatever).

We just got a refurbished Dell at work that has no PS/2 ports, and initially even WinXP has to run for awhile before it figures out where the USB mouse and keyboard are.  Although, it probably remembers on subsequent boots, unless things are moved to different USB ports.

---

### Post by max packer on 2009-12-20
This happens on my built machine as well.  9.04 works fine though so I have that installed, but 9.10 freezes at the login screen, no mouse, no keyboard.

mobo is a MSI k9a2 platinum.

ATI 4850

Phenom @ 3ghz

Logitech usb mouse

Enermax usb keyboard

---

### Post by rghines1 on 2009-12-27
Hi Ubuntu devotees,

Hope everyone had a wonderful Christmas!

The mystery is solved! 

The breakthrough was understanding the blinking power button. Research led me to the ACPI feature in the motherboard bios. The frozen keyboard and mouse were side effects.

In the bios there is a menu named "Power Management Setup" that has an option "ACPI Aware O/S" set to "Yes". Toggle it to "No" and Ubuntu live CD boots fine without the freeze ups. Go ahead and install Ubuntu 9.1 on the hard drive in a dual boot with Vista. 

Tested the boot into Vista and thinks the system files are damaged. Did not think  Ubuntu could have hurt the Windows files. Back into the bios to toggle ACPI back to "Yes" and Vista boots fine again.

Did more research on getting Ubuntu to boot with ACPI set to Yes in the bios. Found the following link that explains how to turn off ACPI in Unbuntu's boot.cfg file. The config files read like programming code but found exactly the info needed and got through it.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Should be well on my way to learning more about Ubuntu.

Thanks for pushing me not to give up!
Richard

---

### Post by phillw on 2009-12-27
Congratulations on your perseverence. I'd not have thought at looking at acpi as the offender. Well, hopefully, it will all be plain sailing from now on.

Regards,

Phill.

---

### Post by fortis24 on 2010-07-11
> **rghines1 said:**
> Hi Ubuntu devotees,

Hope everyone had a wonderful Christmas!

The mystery is solved! 

The breakthrough was understanding the blinking power button. Research led me to the ACPI feature in the motherboard bios. The frozen keyboard and mouse were side effects.

In the bios there is a menu named "Power Management Setup" that has an option "ACPI Aware O/S" set to "Yes". Toggle it to "No" and Ubuntu live CD boots fine without the freeze ups. Go ahead and install Ubuntu 9.1 on the hard drive in a dual boot with Vista. 

Tested the boot into Vista and thinks the system files are damaged. Did not think  Ubuntu could have hurt the Windows files. Back into the bios to toggle ACPI back to "Yes" and Vista boots fine again.

Did more research on getting Ubuntu to boot with ACPI set to Yes in the bios. Found the following link that explains how to turn off ACPI in Unbuntu's boot.cfg file. The config files read like programming code but found exactly the info needed and got through it.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Should be well on my way to learning more about Ubuntu.

Thanks for pushing me not to give up!
Richard

This post helped me to fix a problem I've been dealing with for the last few days, I just had to register and say thanks richard, many many thanks :D

---

