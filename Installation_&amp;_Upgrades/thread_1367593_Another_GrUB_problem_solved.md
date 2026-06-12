---
title: "Another GrUB problem solved"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by Tclarkie on 2009-12-29
cut a long story short i had thing in grub that weren't actually there anymore so i thought i should delete them. I open grub.cfg in a root gedit, and editted them out. It then would not let me resave so i save to root home and sudo cp'ed it over, which appeared to work. I didn't bother shutting down that night and then i had to reboot for something in the morning. To my suprize i was the dropped to a grub shell. In my need to do some stuff i then booted off this months lxf dvd (ubuntu 9.10) and forgoit about ity for two days. Out of fustration a nrelised that i could not boot off cd forever. When i tried to 
$ root@ubuntu:/media/c5b6c02e-ec44-4bae-a1a3-63f9ab873c23/root# cp grub.cfg /boot/grub/grub.cfg
and again it appeared to cp but when i checked it was the same results. I then opened the grub.cfg in sudo gedit and trie to save it to root@ubuntu:/media/c5b6c02e-ec44-4bae-a1a3-63f9ab873c23/root# cp grub.cfg /boot/grub/grub.cfg...

dont worry, should have run 
$ root@ubuntu:/media/c5b6c02e-ec44-4bae-a1a3-63f9ab873c23/root# cp grub.cfg ../boot/grub/grub.cfg

---

