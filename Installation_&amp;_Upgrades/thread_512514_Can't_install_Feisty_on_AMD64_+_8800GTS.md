---
title: "Can't install Feisty on AMD64 + 8800GTS"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by six on 2007-07-29
I've got 7.04 32-bit running OK on my laptop.

But I'm having trouble getting anywhere with the 64-bit installation CDs for my SN25P.

The graphical install, safe mode and check CD all hang (to a black screen) after a couple of minutes.

The alternate 64-bit CD worked up to being 75% installed, then hung on "configuring wvdial".

Anybody got any ideas? (The 64-bit variants of Fedora 7, Sabayon 3.4 and OpenSUSE 10.2 have all installed on the same PC without any problems).

There's no fault with the CDs - they all check out on the laptop. Kubuntu 64 does the same thing. I haven't tried Xubuntu 64, as I guessed it used the same installer.

Is there any other vga mode apart from "xforcevesa" I could try? I've seen "vgamode=normal" or "vgamode=0x314" on other distros' kernal parameters).

I installed Dapper successfully, both Ubuntu and Kubuntu 64-bit a year or so ago on the same PC.

I've searched the forums, but can only find people having Nvidia problems *after* installing.

---

### Post by aavesta on 2007-07-29
Hey six, I have the same system as you! Nvidia KN9-SLI Mobo and an 8800GTS (AMD 64 processor) and I am too having the same problem, I will hit install and it will give me a blank screen after loading! I'm downloading the alternate CD as I type this and I will let you know how that goes for me.

---

### Post by six on 2007-07-30
I (re)validated Ubuntu and Kubuntu 32-bit on the laptop. Both of them have installed on the AMD64/nForce 4/8800GTS machine.

I read all the function key help screens last night, and tried every combination of noapci, nolapic etc. Nothing would work. But the default parameters are just the same on the 32-bit variants, and they worked.

For some reason, the 64-bit graphical installer just doesn't like my CPU/Chipset/GPU.

I'm rather disappointed. I had Dapper 64-bit working on the same PC when I had a 7900GTX.

---

### Post by dabl on 2007-07-30
When you say "hang to a black screen", did you try to Alt-F1 or Ctrl-Alt-F1 at that point?  If you do that and get a text prompt, there's hope. :)

---

### Post by six on 2007-07-30
Thanks, dabl - I've made a note of those key combinations for future reference(!)

By "black screen", I meant what a lot of other AMD64 users seem to be experiencing; that is, selecting "Start or install", or "Start or install safe mode", or even "Check CD for errors" would immediately blank the screen, and instead of seeing the orange/blue progress bar, all you'd get is a completely black screen. Sometimes with the monitor shutting off due to no signal.

I've been doing a *lot* more searching and reading in the forums, today. It's not an easy thing to pin down what's going on. I made a long list of things to try, after going through the popular suggestions of checking md5 sums, burning slowly etc. (I found you can't verify 64-bit CDs on a 32-bit machine).

For my 1st attempt, I let it carry on for a good long while - over 20m or so. Despite seeing nothing but a black screen, the optical drive still occasionally whirred into life. But in the end I had to reboot as the drive eventually wound down and stopped doing anything.

On my 2nd attempt, I got lucky. I thought I'd try a combination of removing the word SPLASH from the boot options, and adding NOAPIC NOLAPIC... and it worked! Instead of the black screen, I watched text appear on screen instead; "kernel alive", "kernel direct mapping tables", "loading, please wait",  checking off services with "[OK]" before changing to a light blue screen (for Kubuntu) and an X. Then came the graphics for setting up & initializing. And at long last... it was up and running, and I could click on the Install to HDD icon.

For anyone else having this problem, press F6 to see the boot options at the menu, then edit the line to make sure it looks like this:

```
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet -- noapic nolapic
```

edit: or maybe even just this-

```
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet -- 
```

(I guess you should replace "ubuntu" with "kubuntu", "edubuntu" or "xubuntu" as appropriate.)

This problem was especially maddening, as it doesn't affect the 32-bit variants, despite being installed on exactly the same hardware! (Could it be something to do with the 64-bit kernel's supposedly superior SMP handling, as opposed to the 32-bit?)

My installation (of Kubuntu 64-bit) completed successfully, but wouldn't quite shut down properly. When it prompted me to press ENTER, it would only echo ^M^M^M^M. I had to switch the PC off at the PSU to reboot.

The Grub menu appeared as expected, but when I attempted to boot into the installed Kubuntu, all I got was the familiar black screen again. So I rebooted and pressed "e" to edit the kernel parameters. It had carried through NOAPIC and NOLAPIC, and also SPLASH. I removed just the SPLASH and booted successfully this time.

I quit out and rebooted again, this time removing all three; SPLASH NOAPIC NOLAPIC so the right-hand portion of the kernel parameters merely read;

```
ro quiet
```

So all this trouble must just be down to the single SPLASH parameter. Next time, when I try booting the Ubuntu 64-bit live CD, I'm going to leave NOAPIC and NOLAPIC off, and just remove the SPLASH parameter. I'll post an update if it boots OK and installs as well.

*Never surrender!* :guitar:

EDIT: It is just the **splash** parameter that's causing all the trouble. I've just successfully booted up the Ubuntu 64-bit live CD by removing it.

I also tried removing it from the "Check CD" option, but instead of validating the CD, it just booted into the live CD instead!

---

