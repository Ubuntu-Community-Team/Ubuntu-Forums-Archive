---
title: "Kernel Panic (?) and nothing happens when installing ubuntu"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by a_b2 on 2014-07-20
Hello everyone!

I am new to Ubuntu with only a little computer experience and am trying to install Ubuntu 14.04 (trusty tahr) on a 2004 Presario V2000 (it used to run Windows XP, yes it's very old). The computer had ~90GB of free space and 2GB of RAM, so I was installing the 32-bit 14.04 version. I burned the ISO file on a DVD on another computer, then put it in the CD drive and started up the computer. It took me through set-up, and I chose to wipe Windows XP from the computer, then went through the selection process (wifi, choosing options, account setup) and it was in the middle of loading something when the screen switched to black and there was a frightening error message.

I can't say what the message was because I had a knee-jerk reaction and forced a shut down. I remember the first line was something like "Kernel panic - not syncing: attempted to kill init!". But every reboot since then has given me a blank screen with a small blinking rectangle at the top left.

I know I can access the "Setup Utility" menu by pressing F10, but I don't really understand anything about the menu and I'm not sure how to even diagnose the problem from here.

---

### Post by coffeecat on 2014-07-20
Welcome to the forum and to Ubuntu! A few thoughts.

When the kernel panics, you don't have to! :wink:

The first thing to check is that your installation medium is OK, both the downloaded ISO and the burnt DVD itself. Here is how you check the integrity of the downloaded ISO:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And you can check that the DVD has been burnt OK by starting to boot it, but tap the spacebar or any key when you see the purple screen with two small icons, a keyboard and stick figure, near the botton of the screen, very shortly after the DVD starts the boot process. That will take you to a text menu after a language choice. The DVD integrity check is about third or fourth on the list. That is, so long as the kernel doesn't panic before you get to the menu. Try that and let us know how you get on.

Next thing to look at is the specifications of your 10-year old machine. Most people would say that Ubuntu itself is too heavy for such a machine, and would recommend a lighter variant such as Lubuntu or Xubuntu but you say you have 2GB of RAM which would be enough for Ubuntu. However, the specifications I found online for “Presario V2000” say 256MB, and although I expect that was upgradeable, the ability to upgrade to as much as 2GB would be surprising. Is 2GB correct? So - let's check your machine specifications before we get sidetracked by suggestions for one of the lighter Ubuntu variants.

Please confirm CPU (speed), RAM and, very importantly, graphics type. The specs I found say Intel 82852/82855 which is ancient, and can give problems. I have no recent experience with old Intel graphics and it's possible that you may need special kernel boot parameters to be able to work with that, but let's see if that is what you have got first. The Ubuntu desktop, Unity, needs beefy graphics, so again we might be back to recommending a lighter variant, but let's check all that first.

Also – 90GB? That's a lot for a 10-year old machine. Does it have a replacement hard drive?

---

### Post by a_b2 on 2014-07-20
Thank you for replying so quickly!

1. I used md5sum to check the downloaded file and the hash was what it should be.

2. I don't think I am able to check that the DVD was burnt. On startup, the computer goes to the Compaq logo (and I can hit F10 to access the Setup Utility), after which it goes to the black screen with the flashing grey bar. Pressing spacebar (or any key other than F10) doesn't stop that from happening.

3. The specs came with the box that I had the laptop in.  I think I read something wrong on the computer the first time. Here is the list of things that seem relevant
> [B]Compaq Presario V2335US
[/B]
[LIST]
[*]Intel Pentuim M Processor 750 (1.86 GHz)
[*]100GB (4200RPM) Hard Drive
[*]1024MB DDR SDRAM
[*]Up to 128MB Video Memory (shared)
[/LIST]


A look at the Setup Utility (using F10 on the boot screen) confirms these numbers, which means I'm definitely wrong about the RAM. I found it in the Control Panel on the Windows XP software before I tried to install Ubuntu, but I must have seen something else. I'm not sure how to find the graphics type, because it's not on the list of specs and I can't see anything in the Setup Utility.

---

### Post by coffeecat on 2014-07-21
There's an inconsistency in the way your computer is behaving with the Ubuntu DVD here:

> **a_b2 said:**
> I burned the ISO file on a DVD on another computer, then put it in the CD drive and started up the computer. It took me through set-up, and I chose to wipe Windows XP from the computer, then went through the selection process (wifi, choosing options, account setup) and it was in the middle of loading something when the screen switched to black and there was a frightening error message.

> **a_b2 said:**
> 2. I don't think I am able to check that the DVD was burnt. On startup, the computer goes to the Compaq logo (and I can hit F10 to access the Setup Utility), after which it goes to the black screen with the flashing grey bar. Pressing spacebar (or any key other than F10) doesn't stop that from happening.

First time around you seem to have been able to get a working installation wizard during which a kernel panic occurred. Your later attempt, you can't get beyond the Compaq BIOS POST screen. My instincts tell me that could be a problem with your optical drive, or perhaps with the DVD. Try cleaning the DVD - gently! - in case some dust is on it. Try cleaning the optical drive with an optical drive cleaner. It's like a CD with a brush on it. That might be difficult now you have no operating system to run it from. Try burning another DVD. If all that fails, it's possible that the optical drive itself is failing.

> **a_b2 said:**
> 3. The specs came with the box that I had the laptop in.  I think I read something wrong on the computer the first time. Here is the list of things that seem relevant
> [B]Compaq Presario V2335US
[/B]
[LIST]
[*]Intel Pentuim M Processor 750 (1.86 GHz)
[*]100GB (4200RPM) Hard Drive
[*]1024MB DDR SDRAM
[*]Up to 128MB Video Memory (shared)
[/LIST]


1 GB of RAM is enough to run Ubuntu in, but it will always be a sluggish, particularly with that leisurely CPU. Notwithstanding my earlier comments, I think it would be a good idea to try a Lubuntu ISO. You can get one here:

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

That will give you an opportunity to try a different DVD - or CD in the case of Lubuntu - and will help in case you ran out of RAM in the first instance. Since you hadn't installed Ubuntu yet, you had no swap partition, and that's a possibility that is worth considering.

I think that's enough to be going on with. Two things that still might need attention are:

1 - The graphics.

2 - If you do manage to get Lubuntu to run from the live session or install it, there's a bug that means that the network manager applet sometimes doesn't appear on the desktop. That shouldn't stop you from connecting wirelessly in the installer, but it will be something to fix if you do install Lubuntu. That's easily done, and I can point you to a relevant howto if you get that far. 

One tip: if you do manage to get a working installer and start the installation off, I suggest you forego the update while installing option. That always takes too long, in my experience. I simply install and then run an update as soon as I have rebooted into the fresh installation.

---

### Post by Richard_Fleming on 2014-07-21
I had the same type of kernal panic when trying to boot Lubuntu. I was able to install Xubuntu on my machine (Shuttle SK41G with Athlon XP 3200+).

---

