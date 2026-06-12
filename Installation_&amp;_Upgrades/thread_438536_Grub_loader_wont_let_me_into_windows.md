---
title: "Grub loader wont let me into windows"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by skantflock on 2007-05-09
Hi guys, I recently started using ubuntu  on my laptop, I partitioned the drive half for ubuntu half for windows ,everything was working fine for about a month then I somehow messed up my ubuntu install real bad and it would'nt even load 

So I booted into windows and formated the second partition from there thinking that would get rid of the bust install so I could redo it, I had already planned to upgrade to 7.04 so this seemed a good plan

I restart my machine and instead of getting the option to boot to ubuntu or windows from the grub loader,or load straight into xp as it should have  I just get an error saying it cant find the grub loader and I cant get access to my windows partition anymore, I know you guys are thinking hey just press F8 but I tried it wont go past the grub loader error

Has anyone else had this problem or know of a fix as I need the stuff I have in windows and dont want to format the whole drive

---

### Post by confused57 on 2007-05-09
If you want to be able to boot Windows, you can reinstall Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you're going to reinstall Ubuntu, then just install Feisty on the partition(s) that you previously had Ubuntu and you should then be able to boot Windows or Ubuntu...without having to restore Window's IPL code to the mbr.

---

