---
title: "blinking cursor thread, again"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by rajan on 2011-05-26
I am sorry to have to post another blinking cursor thread since there are so many out there already, but none of their solutions have worked for me. Here's my problem:

I want to install ubuntu 10.04 lts 64 bit on a computer that i just got from a friend. 

CPU:  2 core opteron 64 bit
GFX: ATI radeon 2600xt

I tried booting from my old HD that I was running a 32 bit version of 10.04 with (everything other than the HD died on that system), but the screen went blank and probably had the blinking cursor, but my monitor wasn't adjusted properly to see it. Here's what I tried:

1. 10.04 live CD and USB startup disk, 32 and 64 bit, all produced blinking cursor.
2. 8.04 live CD, 32 and 64 bit, produced kernel panic of unknown type.
3. 5.10 live CD, kernel panic: unable to mount root fs on unknown block (0,0)
4. Knoppix live CD, same kernel panic as #3, but (1,3) instead of (0,0)
5. 11.04 USB startup disk, 64 bit, blinking cursor

When trying #1, I went through all the options under the f6 menu (acpi=off, noapic, nolapic, edd=on, nodmraid, nomodeset, free software only) and they all did almost the exact same. 

I can get the "boot:" prompt if I exit the graphical interface, but I'm not sure what to type in there. just hitting return sends me to a screen with "Ubuntu" on it but no progress after that. 

I don't know if this is a problem with my graphics card because most of the people that have had problems with theirs are describing a different problem. Thanks a lot for any help, I'm completely stuck right now.

---

### Post by rajan on 2011-05-26
tried 2 more things: 

1a. Fedora 15 32 bit
1b. Fedora 15 64 bit

Strangely, the two fedora discs seem to be actually doing something -- they boot up after bios has handled its business, but then blank screen (no blinking cursor). However, when I hit cntrl-alt-del, the comp restarts. None of the other OSs were responsive to any key combination.

I wonder, could it be my monitor? Samsung syncmaster 172N. 

Otherwise, time to switch graphics card tomorrow.....

Any ideas?

---

### Post by rajan on 2011-05-27
replacing ATI graphics card with nVidia 7900GS did not produce any more substantial progress with any of the live CDs i tried (Fedora 15, 32 and 64 bit, Ubuntu 10.04 64 bit). Super grub disk worked, but couldn't boot to anything due to HD not having anything to boot. Super grub disk worked previously too. 

i will see if anyone has a windows CD that i can try out and see if it's the whole comp that's dead. other than that, i'm stumped.

---

### Post by Quackers on 2011-05-27
I would imagine that the nomodeset option would be most likely to work with the Nvidia card.
How much ram is installed in the system?

---

### Post by rajan on 2011-05-27
thanks for the reply, it's been lonely in here. i tried nomodeset and the same things happened as with ATI card. i tried:

fedora 64/32 bit disks
ubuntu 10.04 32/64 w nomodeset
8.04 64 bit USB startup

in fact, in each case, the result was identical to the ATI card. it seems to me that this means the installation isn't even getting to the OS. are there any hardware problems that would lead to this? 

thanks again

PS system has 2 gb of RAM

---

### Post by rajan on 2011-05-27
11.04 booting from USB in text mode (using command at boot: /casper/vmlinuz) and from regular GUI mode both produce this error:

```
PANIC: early exception 0d rip 10:ffffffff81aecf4c error 0 cr2 f06fa1
```

here are other people with the same problem:

[https://bugzilla.redhat.com/show_bug.cgi?id=489933](https://bugzilla.redhat.com/show_bug.cgi?id=489933)
[https://bugzilla.kernel.org/show_bug.cgi?id=14487](https://bugzilla.kernel.org/show_bug.cgi?id=14487)
[http://ubuntuforums.org/showthread.php?t=1697904](http://ubuntuforums.org/showthread.php?t=1697904)

UPDATE: 
RAM!!!! I just read the bottom thread and I tried removing one ram module at a time, and there apparently was something wrong with one of them because now it goes to the ubuntu screen with the dots underneath "ubuntu" ... however it does hang, possibly due to low memory, and possibly because i'm too impatient to wait more than 4 minutes. 

UPDATE 2: 
RAM!!!!!!!! DAMMIT! going to 2 sticks of ram, i started the comp and a piece of the motherboard started on fire! I immediately killed the master power, but i guess i can mark this thread as "solved" since the comp isn't going to be useful to me. AAAAAAAAAAHHHHHHHHHHH!!!!!!!!

---

