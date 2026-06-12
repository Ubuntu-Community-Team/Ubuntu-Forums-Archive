---
title: "Kubuntu won't boot!"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by galactus1 on 2008-01-10
Last year I attempted to learn linux through a duel boot setup with windows.  Everything was going fine.  I successfully step up a dual boot machine and was well on my way to learning linux.  After a few months and loading beryl onto my kubuntu 6.10 everything was looking great.  Then I think I tried to load a new version of beryl or something and it crashed my kubuntu.  When I try to boot i get this error message:
[HTML]Starting up...
.
Decompressing Linux... done.
booting the kernel.
[   0.000000] ACPI: Unable to locate RSDP
Ubuntu 6.10 username-desktop tty1
username-desktop login:_ [/HTML]
I don't know enough to use the command line to fix my linux. Rescue mode doesn't seem to help either.  I get this error message that tells me to use the 'noapic' kernel parameter, whatever that is...
What little I did know about linux I have unfortunately forgotten since this happened last year.  I threw up my hands in frustration after reading this error message and I am just now wanting to give it another shot.  So.. Any help?
By the way, I also forgot how we post code.  I hope I did it right!

---

### Post by Partyboi2 on 2008-01-10
When you get to the grub menu highlight the kernel you are going to boot into and press "e" then highlight the line that starts with Kernel and press "e" again then at the end of the line add ```
noapic
``` then press enter then "b" to boot
If that works you will need to add it to your grub menu.lst so that it uses it everytime you boot ubuntu. If that is the case post back and someone will be able to tell you how to do it.

---

