---
title: "Samsung Alt-CD 12.04... login problem after installation"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2014-02-07
Bought a samsung laptop. Tried to install  kubuntu 12.04. without installing windows inside it. Failed, tried again with different bios (uefi) options and failed again. Asked someone to install it for me. He refused because cd was not licensed, but he accepted to bring the laptop into a state where I could install kubuntu myself.  (a friend said, he continuously pressed F10 (is this the magic to make bios allow linux?)) Had problems twice, once because power was lost, and ended up with grub rescue..........ANYWAY, it worked 3rd time (after F10 trick). Typing encryption key works. Then I login with user account. It fails, but not because of wrong pw. I'm sent back to login screen after correct login........Then I try console login. It works. I do  sudo apt-get update ,... it shows a long list of failures. No problem with internet connection itself. For some reason this installation likes giving errors, and refusing to fix them. Another thing I try: boot with recovery mode. Then I try fsck, dpkg,..no idea what they are. They mostly give errors or do nothing...............Maybe there is a command which will magically fix all problems. It doesn't make sense that there are problems with this installation, because everything seemed to be ok until I login with user info. ...

---

### Post by bjngchn on 2014-02-10
Any ideas?

---

### Post by mastablasta on 2014-02-10
have you read this?: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

also why not try ver. 13.10 first if computer is new?
furthermore did you check the iso after download and the DVD disk after burning the image to DVD?: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

1 bit is wrong and all can go to hell.

---

### Post by bjngchn on 2014-02-10
Thanks, I will check those links. There must be an easy way to fix this using command line, root access, and internet (don't have anything else).  13.10 doesn't have alt-cd.  Probably no problem with md5. Are alternate (encrypted) kubuntu's not allowed anymore. If so, copies of old alt-cd's should be priceless.

---

### Post by bjngchn on 2014-02-10
12.04.3 doesn't work as explained above (and noone knows how to fix it?). Then tried to install 12.04.04 alt-cd on the same computer.  Somewhere (after typing passwords, selecting  encrypted lvm), it gives and error. Nothing can be done. So I try another version. 11.10 alt-cd. Everything works until the last moment. Then screen gets dark. Nothing happens, nothing can be done. Then I shut down the computer. Turn it on, choose the one at the top in grub menu. Screen gets dark. Nothing happens.  .................So in one case I can't login, in another case I can't install, in another case I get dark screen. If you can suggest a solution for either version, I can install them again and fix it by following your advice.

---

