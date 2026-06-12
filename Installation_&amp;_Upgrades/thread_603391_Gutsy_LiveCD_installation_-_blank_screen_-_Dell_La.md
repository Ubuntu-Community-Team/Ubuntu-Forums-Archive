---
title: "Gutsy LiveCD installation - blank screen - Dell Latitude c800"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by jbrid on 2007-11-05
I have read several posts about the GUI not appearing during installation. I have tried nearly everything:

Different Boot Options (in safe graphic mode):
noapic
nosplash
vga=771
noapic irqpoll noirqdebug
noapic acpi=noirq nolapic

What is bothering me is that I can't get to command line. I have tried hitting CTRL-ALT-F1 in at various points and it never works. If I could get to the command line I could at least continue to try other possible solutions that I have read on other posts. My next step is to try 7.04 LiveCD and see what happens. I am assuming that is must be related to the VGA.

If anyone has any other suggestions, I am all ears! Thanks!

Here's the details about my old laptop:

Dell Latitude c800
Windows Pro 2000 SP4 on other partition working properly
Pentium III 800 MHz
128 MB RAM
20 GB HD
VGA: ATI Rage Mobility M4

---

### Post by dysolve on 2007-11-05
I had the same issue, feisty was fine but gutsy had issues, all i did was boot the liveCD with basic VGA and all was good..

---

### Post by deusxechelon on 2007-11-05
My dell inspiron 5100 did the same thing. I was not able to resolve the issue, had to use feisty.

---

### Post by michaelzap on 2007-11-08
I'm also unable to boot from the LiveCD on a Dell inspiron 5100. It actually seems to boot fine (I even hear the welcome sound), but the screen goes black right about when Gnome should be launching and stays that way. Has anyone resolved this?

---

### Post by Padakwaak on 2007-11-09
I'm not sure if you have the similar problem to what I've had:

After I've clean installed Ubuntu 7.10 via the Live DVD on my HP omnibook 6000 laptop with a ATI mobility graphics card, my Ubuntu booted up for the firsts time and after the first Ubuntu loading screen with the progress bar was done my screen gone completely black and the PC froze.

Then I reset the PC and then it also went passed the loading screen with the progess bar and the brown background appeared and the loading/busy mouse cursor, but it froze completely once again.

I found a solution to this by turning off the APM and ACPI within GRUB boot loader.
See [http://ubuntuforums.org/showthread.php?p=3737043](http://ubuntuforums.org/showthread.php?p=3737043) for the original post where I got my solution from.

---

### Post by Padakwaak on 2007-11-09
The solution I found which I gave in my previous post resulted in no working sound within Ubuntu.

Then I can across these parameters that fixed my sound too, which I appended to the kernel line in the grub boot loader menu.lst: noapic nolapic pci=noacpi acpi=off

---

### Post by jbrid on 2007-11-20
Solution:

1. Install 7.10 Alternate-CD in text mode
2. At first boot screen is distorted and split into 3 columns
3. CTRL-ALT-F1 to drop to command line
4. Edit /etc/X11/xorg.conf according to Step 1 of Post 5 in this thread:
[http://ubuntuforums.org/showthread.php?t=167670](http://ubuntuforums.org/showthread.php?t=167670)

Add these two lines in the 'Section "Monitor" stanza:
```

	HorizSync	  31-82
	VertRefresh	40-110

```

5. Reboot

---

### Post by Aktariel on 2007-12-29
I also have a Dell Inspiron 5100 that I want to convert to Ubuntyu 7.10... will this fix also work?

Most excellent.

I will say, as a note for anyone who may be interested, that Sabayon Linux 3.4f booted fine - no graphics problems, just a little slow (it can be kinda bloated.)

---

