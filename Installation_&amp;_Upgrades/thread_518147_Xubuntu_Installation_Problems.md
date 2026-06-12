---
title: "Xubuntu Installation Problems"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by amgupt01 on 2007-08-05
[FONT=Arial]Hi everyone.  This is my first thread, so don't flame me too much :).
I'm having problems installing Xubuntu on my old PC.

It's a Dell Dimension XPS D233 with: 
[/FONT][LIST]
[*][FONT=Arial]233 MHz Pentium II processor[/FONT]
[*][FONT=Arial]630 MB of RAM[/FONT]
[*][FONT=Arial]70 GB Hard Drive[/FONT]
[*][FONT=Arial]DVD drive[/FONT]
[*][FONT=Arial]CD drive[/FONT][/LIST][FONT=Arial]At first, it always displayed
```
[FONT=Courier New][       0.000000] ACPI: Unable to locate RDSP[/FONT]
```[/FONT][FONT=Arial]But after reading a few threads, I managed to get the Xubuntu Alternate Install CD to boot by appending
```
[FONT=Courier New]acpi=off apm=on[/FONT]
```[FONT=Courier New]to the boot parameters of the installer.
It got the farthest that it had ever gotten before, up to the step "Install the Base System" when an error message came saying:
```
An error was returned while trying to install the kernel into the target system.

Kernel Package: 'linux-generic'

Check /var/log/syslog or see virtual console 4 for the details.
```[/FONT]I checked the md5 hash of the .iso file and I burned it at the 1x speed in order to try to prevent write errors.

I would appreciate it if anyone could help.
My email address is
[email]amgupt01@gmail.com[/email]
Thanks in advance,
amgupt01

[/FONT]

---

### Post by merlinus on 2007-08-05
Are you installing xubuntu on the entire hard drive, or wanting to dual-boot with windows?  If the latter, what version?

Are you using the xubuntu live cd or the text-based alternate?  Did you check the cd for errors at the startup menu?

What did you select at the partitioning menu?  What is your video card?

-merlin

---

### Post by jnorthr on 2007-08-05
Just a thought - can you run the cd as a 'live' cd without doing an install ? If it does run as a live cd,  then we know that the video, keyboard etc. are working correctly.  If you have access , you may want to research here : [https://answers.launchpad.net/ubuntu/+addquestion](https://answers.launchpad.net/ubuntu/+addquestion)
but i could not see anything particularly about your hardware. It is an older model but the spec looks ok so it should work. What are your BIOS settings for acpi, apm and hard disk access ? Dunno if acpi=off apm=on conflicts with the current BIODS settings.

---

### Post by amgupt01 on 2007-08-05
I'm using the Alternate CD to install Xubuntu on the entire 70 GB Hard drive.  It is version 7.04.  I can't check the cd for errors because it doesn't boot the display correctly and  is not legible.  The graphics card is an old Texas Instruments [SIZE=2]TVP3026-220PCE.[/SIZE]
Sorry for not being specific,
amgupt01

---

### Post by lgambett on 2007-08-05
Do you have checked the message in virtual console 4 ? (by pressing Ctrl+Alt+F4). You can check also Ctrl+Alt+F1. It could narrow the search for the problem.

---

### Post by amgupt01 on 2007-08-06
@lgambett
Thanks for the keyboard shortcuts!
I didn't know how to access the Virtual console 4.
Ill post my results soon.

---

