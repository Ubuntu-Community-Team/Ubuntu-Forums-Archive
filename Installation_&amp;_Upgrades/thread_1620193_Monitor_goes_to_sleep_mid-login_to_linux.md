---
title: "Monitor goes to sleep mid-login to linux"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by InTheMarket on 2010-11-12
_***(SOLVED)***_

My monitor falls to sleep when I get to the Grub Menu and choose "Ubuntu". It will get to the purple-ish loading screen to a minute before the monitor falls asleep. I am using 10.10, and this is my first experience with Linux.
[B]
As much details as I can think of:[/B]
I recently installed Ubuntu 10.10 after playing with it on a live CD. I chose to install it alongside Windows 7. The install was quick and smooth, and booted up as it should. When I get to the GRUB menu, I had more choices than I thought I would (I figured I could nix them later.)
[B]
These options were:[/B]
Ubuntu Linux
Ubuntu Linux (recovery mode)
Memory Check
different Memory Check 
Windows 7

I chose windows 7, to make sure ol' semi-reliable, slow, and resource hogging OS worked. As expected, it ran through some stuff white-text-black-screen stuff to make sure all it's files were there (probably due to the fact I had to give some of my hard drive space to ubuntu). As far as I could tell, this did not modify any files, and it checked out with windows. I restarted using windows at this point.

I left the computer go while I made dinner, and when I came back, it completed the countdown and automatically chose Ubuntu Linux. And my monitor was sleeping and did not wake up when I pressed the keyboard or mouse. I hard-rebooted and got the same thing. I rebooted again.
This time I chose recovery mode, which brought me to a menu, I selected to repair damaged packages. It took like 10 minutes, and it repaired alotta stuff. After this, I chose to update GRUB (or something like that), it didn't update anything. Back to the menu, I chose to "run as normal" or something. This brought me to a terminal-like screen. I told it to reboot. It told me to login as root. I tried to tell it to go to root. It said the root stuff wasn't installed, and it took up a whooping 154mb of stuff installing root (which did nothing). I tried to login as su into root. It asked for a password. I tried my login password for linux, didn't work. I tried a few more times and gave up, and rebooted.
I tried once again to login to Ubantu as normal with no success. At this point, I took to the internet. I found a source from here[ (this tutorial), ]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")changed what it said (even though I have an ATI graphics card). No such luck. I hard rebooted again after the monitor fell to sleep. I tried vainly a few little things that did nothing, and discovered that ctrl +alt + delete + delete brought me back to the GRUB menu. 
I checked, windows 7 still works flawlessly. But no such luck in Linux.

_**Specs**_ (sorry they are unspecific, but they shouldn't matter cause they worked fine on live CD Ubuntu, and I used those same files to install it to the hard drive)
Computer itself is a Dell desktop Inspiron 546
Mobility ATI gpu (A laptop card, dell are cheapstakes, but I've been told ATI and Linux are hommies)
A stellar Quad Core AMD processor
4GBs of DDR2 RAM (shipped with 1x2GB, bought a second identical 1x2GB so Windows could run more than one program at once. 
320GB hard drive
DVD-RW CD-RW with nothing in it.
No other storage devices attached.
Primary OS is 64 bit Windows 7 premium. 
It may be slightly relevant that I tried to make some virtual drives a few months back, but it declared war on windows 7 and I uninstalled it.

I'll dig up any additional info I can find, I'll do anything, I loved every 120 minutes of the time I spent on Ubuntu. 
I lots have experience with terminal and package installing from my time as an iOS jailbreaker and developer, so I'll probably understand what you'll say, lay on the nerdspeak.

Any help is welcome, and I will name my computer or second child after you if you get this to work. Unless you have a really messed up name. I'll think of something else in that case.

Thank you for your time
- Market.

---

### Post by InTheMarket on 2010-11-12
UPDATE/BUMP:
I was able to boot her up in "bad graphics mode". I recalled from the live CD that the driver wasn't totally right, and it gave me the option to update it, which I did. I did the same thing here on bad-graphics mode. It didn't just say "Blahblah old/bad driver" it said "no proprietary drivers", but luckily ATI gifted me with a driver and it's installing now. Wish me luck, 3 people who viewed this :D

EDIT:
Thank you 3 people!! :D Works fine now. /solved :)

---

