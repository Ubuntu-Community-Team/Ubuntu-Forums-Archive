---
title: "Cannot boot into LiveCD (10.4)"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Elbelion on 2010-04-29
Greetings,

Whenever I try to boot from my freshly burned Ubuntu 10.4 CD (my goal is to complete a Ubuntu installation from scratch, no upgrade), I see three things :

- first, a purple screen with two pics on the lower side (looks normal) ;

- then an "Ubuntu" waiting screen with five dots blinking alternatively (still looks normal) ;

- and last, a strange screen featuring black & white "staircase" lines. The installation process remains stalled at that point (looks abnormal).

I'm fairly new to "fresh" Ubuntu installations, so please could anyone enlighten me about what happens. Any help will be greatly appreciated.

Best regards

---

### Post by phillw on 2010-04-29
Hi and welcome to the forums,

the first thing I would do is to run the self test on the CD to make sure it has burned okay.

If the CD checks out ok we can look at other things, but if the CD has an error you're on a losing streak.

Regards,

Phill.

---

### Post by Elbelion on 2010-04-29
Thank you for the answer &#8722; and sorry for the disturbance... The CD is OK. But after one more try, it looks like when the purple screen appears, I have to *press a key* to open the language-choice menu and start the installation process for good. Is that key-pressing-first requirement normal ? I'm asking this because I also tried with a 9.10 distro, and then the language-choice menu automatically opened...

Best regards,

---

### Post by scpatl4now on 2010-04-29
Check to see if your motherboard mftg has a BIOS update.  I was having a similar problem and after 4 disks I updated BIOS and now have 3 spare copies...and they all work

---

### Post by cuberts on 2010-04-29
> **Elbelion said:**
> Greetings,

Whenever I try to boot from my freshly burned Ubuntu 10.4 CD (my goal is to complete a Ubuntu installation from scratch, no upgrade), I see three things :

- first, a purple screen with two pics on the lower side (looks normal) ;

- then an "Ubuntu" waiting screen with five dots blinking alternatively (still looks normal) ;

- and last, a strange screen featuring black & white "staircase" lines. The installation process remains stalled at that point (looks abnormal).

I'm fairly new to "fresh" Ubuntu installations, so please could anyone enlighten me about what happens. Any help will be greatly appreciated.

Best regardsFirst I would check the CD itself, and it might have not been burned right. Also what CD burning software did you use?
If you use k3b I know that you wont have any problems, please tell me then I will do something to try to help you

---

### Post by raven809 on 2010-04-29
Im having almost the same problem, The last version of ubuntu that worked on this laptop was 9.04. I tried this 10.04 disk and it starts to load but freezes on the Ubuntu screen with the 5 dots. Tried the windows installer and when i rebooted it froze on the same screen. is there a log file i can check to see whats holding it up?

---

### Post by jjloupe on 2010-04-30
Same issue. If you press Esc. Key you can see the terminal lines, and it says something about username issue? Cant do a screenshot...

I tried mounting the iso and running it from there, but it seems all the files are either inf files or unknown. 

I also tried the "alt+f2 trick, but even though it starts running from the iso, it tries to download files from the internet.

Why is this so f'ed?

---

### Post by Gene_J on 2010-04-30
I am having a similar issue. I can install any other OS (Mint7, Ubuntu9.10, etc), but not 10.04. After several minutes of the 5 dots it pops up a splash screen that says: "The installler encountered an unrecoverable error".
 
I am running an Intel D845 MB with a P4 2.66GHz 533MHz FSB.
 
Thanks for any help...

---

### Post by Orographic on 2010-04-30
Yes, this seems to be a bug. I've installed Ubuntu with no problems on this same machine since Hardy but got this error below with the Lucid live CD:

'The installler encountered an unrecoverable error'

I could finally get to the live CD desktop after this message but for those that can't, try this, it worked in the RC:

As soon as you see the CD loading up, press any key, then choose language, then press F6 then select nomodeset. That worked for me anyway.

After I installed Lucid I got a FSCK on reboot and then after boot I have a blank screen with just the cursor for thirty seconds before the desktop fully appears. I reported this bug in Beta One but due to the other problems with Lucid, they were unable to fix it, apparently.

Its sad that my same system that has run Ubuntu so well has problems with Lucid. Seems it may be related to Plymouth which is hard to remove I understand?

My system is:

Gigabyte 945GZM-S2 motherboard with intel onboard graphics.

PS: I did a MD%SUM and all is well with the iso for the live CD as it was in RC and Alpha and Beta versions when I also had this bug.

---

### Post by ceefour on 2010-04-30
I have similar experience as thread starter, but I can never get past purple screen with two icons.

Using Toshiba Satellite U305-S2806, the LiveCD hangs on boot, while the two icons (keyboard + human) are showing at bottom screen. I haven't been able to resolve this problem.

Using my other Zyrex laptop, the installation process was flawless.

---

### Post by bluenova on 2010-04-30
Do any of you have more than one monitor attached? If so try removing them so you only have one monitor attached...

---

### Post by BitProcessor on 2010-04-30
Same problem here - trying to install 10.04 on a Lifebook E4010 - cd starts booting, I'm getting the Ubuntu logo with the blinking dots but after that : blank screen + freeze !

:(

---

### Post by itdoesnot on 2010-04-30
[http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng)

this might be the issue^

i was having the same problem.
running the live CD, i couldn't get to the desktop
and using the alternate install (i386) i could install it, but not boot into ubuntu

i'm using a Gateway 7330gz. P4 mobile 3.06ghz, and dual-booting Windows 7

---

### Post by ceefour on 2010-04-30
> **bluenova said:**
> Do any of you have more than one monitor attached? If so try removing them so you only have one monitor attached...

Ironically, my Zyrex with external monitor attached installs Ubuntu 10.04 with LiveCD just fine.

The Toshiba one is not attached to external monitor, doesn't even boot LiveCD properly.

Note that the same Toshiba boots & installs Ubuntu 9.10 LiveCD just fine.

---

### Post by Onesimus on 2010-04-30
Have you read the release notes ?

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Desktop%20installer%20sometimes%20crashes%20on%20startup]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Desktop%20installer%20sometimes%20crashes%20on%20startup")

---

### Post by raven809 on 2010-04-30
OK after getting to the screen with the 5 dots I hit escape and it shows the error that seems to be holding the whole thing up.

(process:281): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
stdin: error 0

The disk wont go any further, cant load into the live cd mode and wont run the installer. any ideas on what to do?

---

### Post by peppers on 2010-04-30
> **raven809 said:**
> OK after getting to the screen with the 5 dots I hit escape and it shows the error that seems to be holding the whole thing up.

(process:281): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
stdin: error 0

The disk wont go any further, cant load into the live cd mode and wont run the installer. any ideas on what to do?

Exactly the same problem here!

---

### Post by BitProcessor on 2010-04-30
> **BitProcessor said:**
> Same problem here - trying to install 10.04 on a Lifebook E4010 - cd starts booting, I'm getting the Ubuntu logo with the blinking dots but after that : blank screen + freeze !

:(

FYI : to be sure, I downloaded a copy of 9.10 (Karmic Koala) and installed it on the same laptop : everything runs flawlessly out of the box !!!

Koala - Lynx : 1 - 0 To bad :(

---

### Post by TwiceOver on 2010-04-30
Same issue here.  Tried nomodeset and it just made the screen flicker a bunch.

Willing to wait, just wanted to check compatibility with my laptop: Acer 4810tz.

---

### Post by Gene_J on 2010-04-30
> **Gene_J said:**
> I am having a similar issue. I can install any other OS (Mint7, Ubuntu9.10, etc), but not 10.04. After several minutes of the 5 dots it pops up a splash screen that says: "The installler encountered an unrecoverable error".
 
I am running an Intel D845 MB with a P4 2.66GHz 533MHz FSB.
 
Thanks for any help...
 
After pressing any key at the first screen, I finally got the Live CD to boot. The systray immediately started filling up with instances of "Starting File System" and wouldn't stop. I started the install and after much delay it finally did install, albeit quite slowly. After a forced restart, it has booted normally and appears to be running.

---

### Post by deathblossom on 2010-05-01
> **peppers said:**
> Exactly the same problem here!

Me too! Also, I get a lot of "sudo: unknown user: ubuntu" following that. It's like 1.5gb to download for an upgrade, so I would really rather a clean install...

---

### Post by sonourous on 2010-05-01
I have the same problem like the thread starter! Is there no solution to it? Anybody? :(

---

### Post by Dalek Draco ON LINUX on 2010-05-02
I am experiencing similar issues.   I have to press enter when the Da Vinci sign and the keyboard symbol show up, and then I can navigate between boot options, but pressing enter doesn't do anything.   I have tried booting from a USB as well with no luck, and Wubi installer doesn't work as an alternative either.

---

### Post by Dalek Draco ON LINUX on 2010-05-02
UPDATE:  After some research it seems that quite a few people are suffering from installation issues. Someone has suggested that a corrupt .iso might be responsible.   Thus, possible fix will be to download a new .iso (preferrably from a different mirror/torrent). I will attempt this tomorrow and report my findings if no one else has posted beforehand.

---

### Post by a2800276 on 2010-05-02
> **BitProcessor said:**
> Same problem here - trying to install 10.04 on a Lifebook E4010 - cd starts booting, I'm getting the Ubuntu logo with the blinking dots but after that : blank screen + freeze !

:(


Exact same problem with a lifebook e4010. Bootup starts, ubuntu typescript with 5 blinking dots and then blank/frozen. This is definitely not a corrupt iso problem, it also happened when I upgraded to 10.04 (from a perfectly functional 9.1) using "Update Manager".

---

### Post by SteveDee on 2010-05-02
Similar story here.

I downloaded the iso this morning and tried to run LiveCD (& USB) on Dell Inspiron 500 laptop. After 5dots all disk activity stops and I get a blank screen. Tried "nomodeset" also.

Also tried to boot my fleet of Compaq D510s with similar results. The common factor is probably Intel hardware.

My iso checks out OK, and it does actually work on an AMD powered desktop mongrel. But I'm reluctant to install at this stage...

...somebody wake me up when they've got all the bugs out.

---

### Post by Dalek Draco ON LINUX on 2010-05-02
Downloaded a new .iso image from the optusnet mirror. Still same problem.  I'll wait a few days and see if a fix pops up.

---

### Post by groovomata on 2010-05-02
I've got the same problem in that when I try to boot with the install cd, I wait until I see the keyboard and little man icons a then press a key and I can see the menu however anything I select only produces a sort of purple screen with a white line down the middle. So I can't test to see if there's a problem with my disc, but my download checked out fine with md5sum.

My computer is a Dell 6400 laptop, intel processor and nvidia video card.

I actually had started my own thread on this too:
[http://ubuntuforums.org/showthread.php?t=1468687](http://ubuntuforums.org/showthread.php?t=1468687)

Best,
Erik.

---

### Post by Dalek Draco ON LINUX on 2010-05-03
Just out of curiosity is everyone using the 64-bit version? Because I haven't tried to install the 32-bit (got 4gb of RAM so it would be silly to use the 32-bit).

---

### Post by Joe on 2010-05-03
I've tried both 64 and 32 bit versions and they both have this problem on my system (Core i3 with integrated Intel HD graphics).

Edit: Ok I just tried something that worked.  When you see the logo and man at the bottom, hit spacebar and hit F6 to go into options.  I set acpi=off and noapic and I was able to boot into the LiveCD!

---

### Post by mrcsft on 2010-05-04
> **BitProcessor said:**
> Same problem here - trying to install 10.04 on a Lifebook E4010 - cd starts booting, I'm getting the Ubuntu logo with the blinking dots but after that : blank screen + freeze !

:(

The same for me, can't boot using 10.04 32 bit final live CD version on my Dell Latitude D505 (CD checked and OK) also tried some different booting options but no success.
I've tried Ubuntu Lucid Lynx from first beta, no problem booting till version 2.6.32-20 of the kernel.
Problem appeared with kernel version 2.6.32-21

One note: whatever kernel version I use, I have to set the output video to X Window without Xv (running gstreamer-properties from command line) otherwise (using default output) xorg crashes. My system is based on an Intel 855GM

---

### Post by dkdias on 2010-05-04
> **raven809 said:**
> Im having almost the same problem, The last version of ubuntu that worked on this laptop was 9.04. I tried this 10.04 disk and it starts to load but freezes on the Ubuntu screen with the 5 dots. Tried the windows installer and when i rebooted it froze on the same screen. is there a log file i can check to see whats holding it up?

I am having the same problem with a desktop Dell Dimension 8100 P4. 10.04 Ubuntu won't boot, but 9.04 Ubuntu will boot? 9.10Ubuntu won't boot either? I thought it was the beta version I had because I downloaded it on 4/26, so last night I downloaded the newest release of 10.04, but it did the same thing. Please help!!

---

### Post by shashikm on 2010-05-04
i have same problem here is explanation:

live CD boot stops at ubuntu purple screen with five dots blinking red and white for ever.
when I press control+alt+backspace, I see a text screen with several error messages please see attached image.
md5sum check is okay.

---

### Post by Joe on 2010-05-04
Did you guys try booting in with acpi=off and noapic?

---

### Post by dkdias on 2010-05-04
> **Joe said:**
> Did you guys try booting in with acpi=off and noapic?

I don't know how to turn acpi off and noapic.  Please tell me how to do this and I will try it?  Thanks!

---

### Post by ruipedrovpa on 2010-05-04
i have the same problem, i press enter when logos apeares and than select language, after that enter key do not do nothing :S

Anyone have a solution for that?

---

### Post by Joe on 2010-05-04
> **Joe said:**
> Edit: Ok I just tried something that worked.  When you see the logo and man at the bottom, hit spacebar and hit F6 to go into options.  I set acpi=off and noapic and I was able to boot into the LiveCD!

Just follow these steps.

---

### Post by ruipedrovpa on 2010-05-04
> **Joe said:**
> Just follow these steps.


Hi, a try what you said, and don't work for me. :S :S

Anyone knows when ubuntu update .iso with this error/bug solved? 

I want new ubuntu but it don't want me :( :s

---

### Post by kai_kan on 2010-05-04
Chalk up one more...

I get the install menu, but none of the options appear to do anything (except spin the CD). 

-Running the Desktop AMD 64 iso (downloaded today)
-On Dell Studio XPS 1645 with Core i7
-Tried acpi=off and noapic to no avial

Eagerly awaiting a fix!

---

### Post by ruipedrovpa on 2010-05-04
welcome to the club :s

I love ubuntu but this realy sucks :s

---

### Post by vytman on 2010-05-04
> **Joe said:**
> I've tried both 64 and 32 bit versions and they both have this problem on my system (Core i3 with integrated Intel HD graphics).

Edit: Ok I just tried something that worked.  When you see the logo and man at the bottom, hit spacebar and hit F6 to go into options.  I set acpi=off and noapic and I was able to boot into the LiveCD!

It worked for me.

I'm installing ubuntu 32-bit with a Windows 7 64-bit installed.

I previously had ubuntu 64-bit with Windows 7 64-bit and the installation went with any problems, I don't know if it's a 32/64-bit incompatibility....hope that helps.

---

### Post by ruipedrovpa on 2010-05-04
anyone knows other solution to try? thanks

---

### Post by NijelMcTavish on 2010-05-05
I can't help with booting the liveCD, but I upgraded my D505 from 9.10 to 10.4 and got the same symptoms when booting with the new 2.6.32 kernel.  I could, however, choose the old karmic 2.6.31 kernel and boot fine.

I downloaded and installed the latest release candidate kernel and headers from 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/") and using the new kernel it all seems to works fine.

---

### Post by Rubi1200 on 2010-05-05
See this post:

[http://ubuntuforums.org/showthread.php?p=9239795#post9239795](http://ubuntuforums.org/showthread.php?p=9239795#post9239795)

Hope it helps.

---

### Post by kai_kan on 2010-05-07
Nothing in Rubi's link worked for me, but I tried the 64-bit Desktop iso of 9.10 and was pleased to find it ran fine. From there I ran a full install, then updates, and finally the 10.04 upgrade. 

Messy, but it got me up and running...

---

### Post by RJARRRPCGP on 2010-05-07
> **deathblossom said:**
>  "sudo: unknown user: ubuntu" 

Ow, that error reminds me of pre-Gutsy. :( 
IIRC, with Breezy, Hoary or Dapper, I would get "sudo: unable to" error messages sometimes. :(  (or bug me with an error message claiming the machine host name is unknown)

---

### Post by samcoinc on 2010-05-07
Is there a reason why you went with the 32 bit version?  (I had a brain fart and installed the 32bit version on my i7 quadcore.  Wondering if I should reinstall using the 64bit version....  (it installed and is running great)

sam

> **vytman said:**
> It worked for me.

I'm installing ubuntu 32-bit with a Windows 7 64-bit installed.

I previously had ubuntu 64-bit with Windows 7 64-bit and the installation went with any problems, I don't know if it's a 32/64-bit incompatibility....hope that helps.

---

### Post by jemmrich on 2010-05-13
I just wanted to add that I have created a usb live thumbdrive in the 10.04 live cd environment using usb startup disk creator and had the following errors when trying to boot using the thumb drive:

(process:320): Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

stdin: error 0
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr1: No medium found
/init: line 7: can't open /dev/sr1: No medium found
stdin: error 0
stdin: error 0
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr1: No medium found
/init: line 7: can't open /dev/sr1: No medium found
stdin: error 0
stdin: error 0
stdin: I/O error

The partition on the usb drive was formated to fat32, was set up for persistence and was made in the 10.04 live cd.

During boot of the usb drive I turned acpi=off worked great and the boot process was nice and fast thanks!

---

### Post by mrcsft on 2010-05-14
I found this solution for owners of Dell Latitude D505 and more generally for all those who have had problems with graphics chipset Intel 8xx.

Here you can find the bug in launchpad:
[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/575103"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/575103
[/URL]

and here the solutions proposed:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

*Workaround A: Re-enable KMS* worked for me :)

---

### Post by CHFFriday on 2010-05-14
Robi1200,

That link worked for me on an Acer TravelMate 4500

I hope they get this fixed.

BIG THANKS

CHFFriday

---

### Post by dkdias on 2010-05-18
> **Rubi1200 said:**
> See this post:

[http://ubuntuforums.org/showthread.php?p=9239795#post9239795](http://ubuntuforums.org/showthread.php?p=9239795#post9239795)

Hope it helps.

I don't get the purple screen.  Basically when the 10.04 cd is in and I boot it, I get "Press F1 to reboot or Press F2 for boot options".  If I press F2 it goes into the bios.  All my bios settings are correct for booting off the cd.  I have removed the floppy boot option and that makes no difference at all. When I press F1 it just reboots to the same message to press F1 or F2?  Ubuntu 8.04 boots from CD and 9.04 boots, but not 10.04?  Please help! Thanks!

---

### Post by ReformedRobotMan on 2010-09-10
Intel Core2Quad Q6600 4x2.4GHz
2048 MB DDR2
4GB Memory, 8MB cache
2x 1.5TB Samsung 154U
BIOS version V1.10B1
 
Hi,
 
Same problem here.
Had 9.10 (32) and previous versions on my system, without any problems.
After upgrading to 10.04, i couldnt boot after restarting.
Used 9.04 LiveCD to reinstall, upgraded to 9.10 and then tried to upgrade to 10.04 again; same results.
Tried 10.04 LiveCD (burned version of yesterday), but cannot boot into CD.
Same with 10.04 on USB stick.
 
Tried booting in with acpi=off and noapic (F6 options), but always got stuck in purple screen with 5 dots.
Also tried (after hitting F6 and Esc) replacing 
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**
with:
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**
but after a few seconds (of data flashing by), the screen just goes black.
(also tried q6600 instead of i915; just in case)
 
Now i finally cannot even boot in the 9.04 / 9.10 LiveCDs anymore...
and i cannot use the old kernels either...
 
Maybe somebody can help me?
 
Thank you!

---

### Post by Rubi1200 on 2010-09-10
The link I gave was for users with Intel graphics chipsets.

What graphics card do you have installed?

---

### Post by ReformedRobotMan on 2010-09-10
Thank you for replying!
 
XFX GeForce 9600GT 512MB DDR3 DVI PCI-E

---

### Post by Rubi1200 on 2010-09-10
> **ReformedRobotMan said:**
> Thank you for replying!
 
XFX GeForce 9600GT 512MB DDR3 DVI PCI-E
Ok, so let's try this: follow the instructions as above (where you used F6 Esc etc),
but this time use the nomodeset parameter.

So, the boot line will change from this
> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**to this
> **file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**Then Enter.
Let us know if this works and if not what happens.

---

### Post by ReformedRobotMan on 2010-09-10
Thank You!
 
At least i got a little further...
Lots of data flashes by, including:
...reading package indexes, writing sew source list, skipping nonexistent binary-i386/packages,
setting ubiquity favourite for UNE, no volume set set for (key) favourites list...
 
Until these last few lines:
 
```
Begin: running /scripts/init-bottom ...
done.
init: unreadahead-other main process (1243) terminated with status 4
init: unreadahead-other main process (1244) terminated with status 4
* setting sensor limits
```
 
Then the lights on my keyboard for "Ä" and 'the arrow down' keep flashing simultanuously,
and im stuck.

---

### Post by Rubi1200 on 2010-09-10
Did it stop there completely or did you wait to see if it would go further?

Take a look here and see if there is something that might help:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)

Barring that, what about trying 9.10, the previous release, and see if that works for you on your system?

---

### Post by ReformedRobotMan on 2010-09-11
Thank you.
 
> **Rubi1200 said:**
> Did it stop there completely or did you wait to see if it would go further?
 
It stopped there, and still was there many hours later
 
> Take a look here and see if there is something that might help:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)
 
Thank you. I will check it out.
 
> Barring that, what about trying 9.10, the previous release, and see if that works for you on your system?
 
After the 10.04 upgrade failed for the second time, I cannot boot in any LiveCD version anymore.
Is there some way to restore/fix the boot section?
Maybe by installing Win XP first?

---

### Post by nebjak on 2010-09-11
This helped me:

F6 -> acpi=off , nomodset, noapic

after that I booted live sesion from usb, and instaled Lucid

---

### Post by ReformedRobotMan on 2010-09-12
Thank you. 
I tried it, but doing that using the LiveCD, i got stuck in the same purple screen with the 5 red dots again...
Anyone else?

---

### Post by Rubi1200 on 2010-09-12
I don't like giving up; try this combination as you boot the LiveCD (F6 then Esc and edit):
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa noapic noapci nosplash irqpoll --**

---

### Post by ReformedRobotMan on 2010-09-12
> **Rubi1200 said:**
> I don't like giving up
 
Im glad that you dont!!
 
> ; try this combination as you boot the LiveCD (F6 then Esc and edit):
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa noapic noapci nosplash irqpoll --**
 
I will.
I guess i have to wait a little and let my system cool down a bit, as i probably have been trying too many combinations, as currently i cannot even get into my BIOS. (my system) gets stuck before that)

---

### Post by ReformedRobotMan on 2010-09-13
> **Rubi1200 said:**
>  try this combination as you boot the LiveCD (F6 then Esc and edit):
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa noapic noapci nosplash irqpoll --**
 
Unfortunately, some data flashes by and then the screen goes black,
and it stays that way...

---

### Post by imnotrich on 2010-09-13
Elsewhere on the net I have seen this issue blamed on incompatibilities with many Intel, Nvidia and ATI video cards. In my experience I have never known a mainstream distro to not have video support out of the "box" with hardware from common video card manufacturers. This is quite odd. I've tried it on several machines here, 32 bit and (where appropriate) the 64 bit version. Same bug. After about 3 weeks of struggling, I went back to Debian on my primary desktop. Debian at least knows what a video card and sound card is (though printing and scanning remains problematic in Debian).
If you can get 10.04 or 10.04.1 to recognize your keyboard, some people have suggested tinkering with nomodeset or acpi options but I have tried on three different machines with no success. It may be a clue that Puppy 5.10 and 5.11 fail in a similar fashion so it's got to be a bug that both distros have in common. If I figure it out I will happily share the solution.

---

### Post by Rubi1200 on 2010-09-14
> **ReformedRobotMan said:**
> Unfortunately, some data flashes by and then the screen goes black,
and it stays that way...
Have you tried turning off (I think that is the setting) AHCI in BIOS and then trying? Clutching at straws here, but you have a SATA drive and I seem to recall they can cause issues sometimes. It might be worth a try at this stage.

---

### Post by ReformedRobotMan on 2010-09-15
> **imnotrich said:**
> Elsewhere on the net I have seen this issue  blamed on incompatibilities with many Intel, Nvidia and ATI video  cards.

Yes, ive read that too.

> If I figure it out I will happily share the solution.

Please do so..., thank you!

> **Rubi1200 said:**
> Have you tried turning off (I think that is the setting) AHCI in BIOS and then trying? Clutching at straws here, but you have a SATA drive and I seem to recall they can cause issues sometimes. It might be worth a try at this stage.

Yes, everything is worth a try at this stage.
Unfortunately, it didnt work either...
At least i have been able to boot into the 9.04 LiveCD again, so that ive now (after upgrading) 9.10 installed.
Naturally, i would still like to install 10.04, but thats not an option right now,
because upgrading always gives me the same problem (cannot boot into system anymore)
and a clean install from the 10.04 LiveCD is not possible currently.

Thank you for your time Rubi1200!

---

### Post by Rubi1200 on 2010-09-15
You are more than welcome :)

If 9.10 is working then stick with it for the moment (supported until April 2011).

It seems that 10.04 has caused issues which are often difficult to track down even for users with the same or similar specifications.

I would wait until 10.10 is released in October then try it as a LiveCD to see if it works with your setup. You could then consider installing it.

---

### Post by ReformedRobotMan on 2010-09-15
Thank you. My idea exactly.
Im just contemplating upgrading my BIOS, as ive read that this may help.
After that i will see if i can boot into the 10.04 LiveCD.
If not, i still have my perfectly functioning 9.10 system.
(which is not the case when i upgrade with update manager)

If that works, it may help for others as well.
And if not, no harm done.

---

### Post by ReformedRobotMan on 2010-09-15
Nah, im not sure [what type/version](http://global.msi.eu/index.php?func=downloaddetail&type=bios&maincat_no=1&prod_no=1695) i need, so forget about that...

---

### Post by cacedilla on 2010-10-02
if livecd does not successfully boot to installation, shutdown the computer. turn on the computer after a while. if livecd crash again on boot, shut down the computer again. turn on on the computer after a while. the livecd will successfully boot ton installation after the second power on

---

### Post by Jolicoeur on 2010-10-02
> **BitProcessor said:**
> FYI : to be sure, I downloaded a copy of 9.10 (Karmic Koala) and installed it on the same laptop : everything runs flawlessly out of the box !!!

Koala - Lynx : 1 - 0 To bad :(

Me too, 9.10 works great, can't intall 10.04, black screen.

---

### Post by ReformedRobotMan on 2010-10-05
> **cacedilla said:**
> if livecd does not successfully boot to installation, shutdown the computer. turn on the computer after a while. if livecd crash again on boot, shut down the computer again. turn on on the computer after a while. the livecd will successfully boot ton installation after the second power on

Unfortunately, that doesnt work for me, 
no matter how many times i try.

> **Jolicoeur said:**
> Me too, 9.10 works great, can't intall 10.04, black screen.

Same here.
So i will wait for 10.10

---

### Post by Rubi1200 on 2010-10-05
Waiting for 10.10 might not be a bad idea. The new kernel seems, at least in my testing with Intel chipsets, to be less problematic than it was in 10.04.

Just a few days to go now; yay!

---

### Post by olafurg on 2010-10-10
I'm running a Dell Latitude D505 with the 855gm chipset. Had the same situation with going from 9.10 to 10.04 because of the issues with the chipset. See [here]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes"). 

So I always got back to 9.10. 

Then today installed 10.10 and works ok-ish ... no graphical effects and a CPU spike every ~10 seconds that seems to be because of some kslowd000 process. Don't know where to go ... getting close to going back to 9.10 :(

---

### Post by ReformedRobotMan on 2010-10-20
> **olafurg said:**
> ... today installed 10.10 and works ok-ish ... no graphical effects and a CPU spike every ~10 seconds that seems to be because of some kslowd000 process. Don't know where to go ... getting close to going back to 9.10 :(

Same here, so i went back to 9.10
The only thing that worries me now is that 9.10 is supported until April 2011.
Will we get a proper new release before that time?

---

### Post by olafurg on 2010-10-20
@ReformedRobotMan!

I got it working properly after I contacted Stefan Glasenhardt and asked about possible solutions. Short story short: It worked! And now I'm running 10.10 smoothly with full graphics and all. The mail is a few weeks old so there might be some tweeks required. Start with the xorg.conf file at least. 

Here's the response that fixed everything:

> 
The developers disabled the driver-autoloading mechanism in the Xserver
for some graphics chips, namely i830, i845 and i855. When the Xserver
detects one of these chips, only the framebuffer driver is loaded. This
driver does not support any special features (No 2D accel, no OpenGL and
so on).

To re-activate the normal driver, you have to create/modify a
"xorg.conf"-file and put in the following content :

Section "Device"
  Identifier     "Intel "
  Driver         "intel"
EndSection

But there is a second problem with the Ubuntu-kernel :

After re-activating the intel-driver, you can no longer see the
mouse-cursor. This is a kernel-bug and a at the moment the only thing
you can do is using a newer kernel-version e.g from the mainline-PPA :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/)

or

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-rc7-maverick/)

The bug in the Ubuntu-kernel should be fixed when the devs rebase the
Maverick kernel-image on a newer vanilla kernel-version. The bug was
introduced in kernel 2.6.35 and was fixed in 2.6.35.6. The Ubuntu
kernel-version 2.6.35-22 is based on 2.6.35.4.

Hope this helps!

---

### Post by ReformedRobotMan on 2010-11-05
Thats fantasic, good job!
Re-activating the normal driver went fine.

> 
After re-activating the intel-driver, you can no longer see the
mouse-cursor. This is a kernel-bug and a at the moment the only thing
you can do is using a newer kernel-version e.g from the mainline-PPA :

This, however, i dont know how to do that...
So, once again im back at 9.10 and im hoping everything is resolved in the next version...

---

### Post by Rubi1200 on 2010-11-05
I have something to add:
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

The fix for 10.10 is more or less the same as for 10.04!

See my post here:
[http://ubuntuforums.org/showpost.php?p=10067580&postcount=7](http://ubuntuforums.org/showpost.php?p=10067580&postcount=7)

Caveat: Compiz will not work even with this fix, but the CPU spikes mentioned above are a thing of the past.

Hope this helps.

---

