---
title: "Ubuntu Lucid Lynx Server 10.04.3 stops at GRUB2 Menu"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by ddouthitt on 2012-01-17
I have an Ubuntu Lucid Lynx 10.04.3 Server system that doesn't automatically boot; it stops at the boot menu and remains. No messages are seen and no errors displayed. When a key is pressed, it continues and generates a "error: no argument specified" and continues on.

I just upgraded the server to the most recent set of updates.

Other similar systems are not stopping at the menu, but are continuing on. I posted a message on the [Ubuntu Stack Exchange]("http://askubuntu.com/questions/96265/grub-1-98-error-no-argument-specified") but haven't heard anything yet - usually get responses right away. For the moment I'm assuming that people there don't know (I'll try to keep this thread updated if something comes up over there).

I did a Google search but can't find any answers to the ultimate question: *What makes the GRUB2 menu appear (possibly in spite of the menu configuration)?*

Can someone help? (I hope this question isn't out of place, but as Ubuntu SE hasn't responded...)

---

### Post by ddouthitt on 2012-01-17
I found that the version listed as the installed package (and installed software) and the version reported at boot-time in the GRUB2 menu were different: 1.98-1ubuntu12 for the former and 1.99~rc1-13ubuntu3 for the latter.

The system never had any Ubuntu version that uses 1.99~rc1-13ubuntu3; it had Red Hat Enterprise Linux 5 before, which uses GRUB Legacy.

The message "error: no argument specified" was seen before the menu (in bold) as well as after (normal text), with a "Press any key to continue..." after the second message. This prompt times out after about 5 seconds and continues on.

Gory details and research are at the StackExchange site.

---

### Post by ddouthitt on 2012-01-18
I created a script to check for differences between the files in /usr/lib/grub/i386-pc and in /boot/grub. The files in /usr/lib/grub/i386-pc are owned by the package, and those in /boot/grub are installed programmatically.

The problem system shows a wide discrepancy between the two. Reinstalling the Ubuntu package for grub-pc wiped out the differences; the configuration hasn't yet been tested in a system reboot.

All these details and more have been posted in an answer to the question on the Ubuntu StackExchange site:

[http://askubuntu.com/questions/96265/grub-1-98-error-no-argument-specified/96591#96591](http://askubuntu.com/questions/96265/grub-1-98-error-no-argument-specified/96591#96591)

---

