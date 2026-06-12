---
title: "Ubuntu on VMWare 5.0?"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by dude2425 on 2005-04-25
Would it be at all possible to install Ubuntu Hoary on VMWare 5.0? I wanted to test something out, but when I tryed to install it, the installation menu's were unbarably slow, and it hang at 75% at one point after instalation, and then I rebooted the virtual Ubuntu, and all I got was the word GRUB. Am I doing something wrong or something, or is Ubuntu just not installable on VMWare. I'm gonna try again later. I might be able to figure it out later.

---

### Post by sonicintuition on 2005-04-26
I installed it flawlessly on VMware 5.0. Here is what I did - 

[list]
[*]Created a new VM with default settings
[*]Created the VM as "Other Linux 2.6 Kernel" in the dropdown
[*]Allocated all disk space (used 20 gigs) immediately
[*]Went with Network Address Translation (NAT) for networking
[*]After machine was created and ready to boot, I went into the settings for it and pointed the cd-drive emulation at the ISO for the ubuntu installation ISO
[*]Booted up the machine, installation started immediately there-after.
[/list]

This should work, as long as you go with default settings in VMware. If you still have problems after this little guide, feel free to email me at [email]sonicintuition@adelphia.net[/email] for any further questions. Good luck!

-Sonic

---

### Post by dude2425 on 2005-04-26
That was exactly the same thing I did. I'm gonna have to try it again and see what I get.

EDIT: Problem resolved. I think my dad must have unpluged the router again while I was checking apt-get sources durring install or something (he does that sometimes.)

It installed it just fine now, so I'm playing with Ubuntu in Ubuntu lol.

---

