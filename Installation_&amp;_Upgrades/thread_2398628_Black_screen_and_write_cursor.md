---
title: "Black screen and write cursor"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by comonda2 on 2018-08-15
[COLOR=#242729][FONT=Arial]the situation likes this:

 [IMG]https://i.stack.imgur.com/6FHwa.gif[/IMG][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]i added that commmands to grub file:[/FONT][/COLOR]
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
[COLOR=#242729][FONT=Arial]After I restarted my laptop, it gave the black screen which same as picture. I hope you know a solution.[/FONT][/COLOR]

---

### Post by dinkidonk on 2018-08-15
Did you issue a "sudo update-grub"? Can you post your entire /etc/default/grub file? [https://askubuntu.com/questions/1036091/how-to-set-grub-timeout-to-0-on-ubuntu-18-04](https://askubuntu.com/questions/1036091/how-to-set-grub-timeout-to-0-on-ubuntu-18-04)

---

### Post by comonda2 on 2018-08-15
no i didnt .when i got black screen, i deleted added lines with liveusb but no changing.i will post it.

---

