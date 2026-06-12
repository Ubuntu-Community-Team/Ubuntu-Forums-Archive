---
title: "Installation issues"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by URNotMega on 2007-02-28
I'm finally attempting to get linux up and running, and of course my newb self is running into installation issues.

Specs:
soltek mobo
amd64 3000+
ati radeon 9600XT
120gb IDE hdd
1gb ddr400 corsair
sony dvd rw
norcent cd rw

So... I downloaded the 64 bit dvd version, burned it, booted from dvd.  The starting menu comes up, looks fine, so I try to start the install.  After a short pause, the next screen I see has a grey ubuntu logo (not the nice orange as before), and the progress bar is a glitchy grey bar that moves left and right... After about 5-10 minutes of it doing that, the screen will clear and begin scrolling with error after error.  It moved extremely fast through the errors until it's done, then pauses/freezes.  One of the more unique error lines I see when I can finally read them is "status error: status=0x58".  

So I went with this error... threads/articles i found on this suggest it could be a faulty disk drive, faulty burn, or faulty cd.  I try it three more times, all at 2x burn speeds (can't burn at 1x), using something called "Burn My Files" and also Nero.  All 3 of these disks did the same thing, giving the same errors.

Next I re-installed my old cdrw, downloaded the 64bit cd version, and burned it.  This gives me the same error.

Next I switched IDE slots, using the slot and cord my HDD was previously using with my dvdrw and cdrw.  Reburned both a dvd and cd, both are doing the same thing.

Found some more threads... one suggested I do the following:
remove "slash --"
wait, skip reports of xserverfail, type some stuff

Well... I remove splash, and now I get to see some text scroll as it's trying to do something, then I get to this error:

udevd_event[1594]: run_program: '/sbin/modprobe' abnormal exit

from here, I can type stuff, but nothing seems to work... so I ctrl+alt+delete it which reboots my machine.

Next I try to install in text mode... this gives me some error popup about not being able to read the cd... tried this with both my dvd and cd, and with the cd in both the dvdrom and cdrom.

My next urge was to look at more threads for the next 18 hours until I figure it out, or break my computer, but I decided instead to make a new post :)

So, any ideas?

Thanks for any help...

-Tommy

---

### Post by actuary286 on 2007-03-01
Just need a little more information:

Have you tried using the Check CD option in the boot menu to make sure you have a good disc?

How did you download the file? 

Did you check the file's MD5 sum to make sure the file is correct?

Have you tried downloading it again?

Have you tried using the "alternate" install CD?

---

### Post by URNotMega on 2007-03-01
> **actuary286 said:**
> Just need a little more information:

Have you tried using the Check CD option in the boot menu to make sure you have a good disc?

How did you download the file? 

Did you check the file's MD5 sum to make sure the file is correct?

Have you tried downloading it again?

Have you tried using the "alternate" install CD?

I've tried using the check cd option, but it just ends up doing the same thing that using the install options does...

downloaded the file from ubuntu.com .

I've downloaded the 64bit dvd version, 64bit cd version, and now the 64bit alternate version.  I'm guessing even if one of them was corrupt, one of the others should be ok...

as for the alternate install cd, I downloaded that today and tried it.  I get a bit farther, but now I get stuck on "detecting cd-rom", and at the bottom it's 6% and says "loading module trm290 for ide chipset support".  I let it sit like that for about an hour with no progress.  I read some posts that suggested I do stuff like adding linux acpi=off noapic nolapic , tried a bunch of different versions of that along with irqpoll, etc etc... I usually get a kernel panic error when I do something like that. 

*sigh*

any idea?

---

### Post by ebichuhamster on 2007-03-01
Is that grey Ubuntu symbol normal for the 64bit cd version? cause im getting it too, im also getting the glitched progress bar which then turns green.

Check this out, I did a disk diagnosis from the setup, and after 84 minutes Ubuntu actually got to the window manager, but as I was installing, it completely froze at 15%.  Now it wont even get pass the green progress bar.  

Tried another disk check without succes. 

This is the first thread I have read where they mention the grey Ubuntu, so thats why im posting here, if Im supposed to get help elsewhere please let me know.

---

### Post by xsist10 on 2007-03-25
I'm getting a similar error with the i386 version of Feisty Fawn - Herd 5 (feisty-desktop-i386.iso)
I deliberately didn't go with the 64 bit version.

Installation goes as follows:
[LIST]
[*] Boot to CD
[*] Select Install or Run Live CD
[*] Ubuntu loader screen (full colour)
[*] 1% loaded and it drops to text mode with this error:
xxxx - varies (e.g.: 2040, 2041)
udevd_event[xxxx]: run_program: '/sbin/modprobe' abnormal exit
[/LIST]

Critical system specs are as follows:
AMD Athlon 64 X2 Dual
Core Processor 4200+
2.21 GHZ, 2.00 Gb of RAM
GeForce 6800GT
SATA HDD


Is there a log dump of the install attempt anywhere that I can post?

Thanks

p.s.: CD's checked with MD5. Couldn't run the Ubuntu CD check as the same problem as above occurs.

---

### Post by a1437053 on 2007-04-28
Similar issue: i386 Feisty Fawn

Installation goes as follows:
[LIST]
[*] Boot to CD
[*] Select Install or Run Live CD
[*] Ubuntu loader screen (full colour)
[*] almost immediately it drops to text mode with this error:

usbcore: registered new device driver usb
ohci_hcd: 2006 August 4 USB 1.1 'Open' Host Controller (OCHI) Driver
udevd-event[1511]: run_program: '/sbin/modprobe' abnormal exit

 . . . .

starting system log daemon: syslogd, klogd.

IT TAKES FOREVER.


I can't check CDs from the LiveCD, I've re-downloaded .iso files, re-burned CDs . . . 

Sigh, back to MS Windows?



Jose

---

### Post by a1437053 on 2007-04-28
Next attempt:
Similar text mode comment ending with "abnormal exit".
WAITED and it continued installing. Detected keyboard settings.
Slows down again at "Detecting hardware, please wait" . . . 


6%
"Loading module 'trm290' for 'IDE chipset support' . . .

STALLED OUT THERE

Jose

---

### Post by a1437053 on 2007-04-28
SO . . . here was my workaround (all-the-way-around):

1. Install KUBUNTU. Appears to work great so far!
2. Install UBUNTU-DESKTOP from one of the CDs that I had . . . 


So far so good!


Jose

---

