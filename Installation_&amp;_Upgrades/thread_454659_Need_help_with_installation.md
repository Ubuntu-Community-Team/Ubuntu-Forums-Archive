---
title: "Need help with installation"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by erod on 2007-05-25
I'm trying to install Ubuntu on an old computer.  The specs are as follows:
IBM Aptiva
Petntium III 450 mhz
224 MB Ram
40GB HD

So I burned the ISO to a CD and rebooted the computer.  The main menu pops up and I select the start installation option.  First it gives me a BIOS/ACPI error saying I need to enable force, or something like that.  But then it starts up with the Ubuntu logo and the status bar going back and forth.  After a little while the screen just goes blank.  I'm completely new with Linux.  Thanks for your help.

---

### Post by grgs on 2007-05-25
Did you try to put XUBUNTU? I believe this version is for olds hardware.

---

### Post by erod on 2007-05-25
I'll give it a try!  Thanks.

---

### Post by erod on 2007-05-25
Xubuntu did the same thing.  :(

---

### Post by confused57 on 2007-05-25
You might try adding boot options when you boot the live cd, you'll need to press one of the F keys(I can't remember which..F2, F6?) & you can add boot parameters, such as:
acpi=off
noapic

then try to boot the live cd...

You could try these 2 for starters, there's a list of cheatcodes on the Knoppix wiki:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

---

### Post by southernman on 2007-05-25
Are you using the live... or the alternate cd?

---

### Post by erod on 2007-05-26
Looks like the alternate cd did the trick....sorry I should have done a search earlier.  Thanks for your replies!

---

### Post by southernman on 2007-05-26
No worries erod. confused57's approach would have worked for you also.

Welcome to Linux and happy Ubuntu-ing! :D

---

