---
title: "Asus M3N extremely slow after 10.10 install [10minutes bootup]"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by marisdembovskis on 2011-01-14
Hello. 
I tried Ubuntu 10.10 live CD. Everything was fine. 
Installed. And problems started. 

Boot up time is 10 minutes long. 
PC is extremely slow! I got Asus M3N portable pc. apt-get upgraded was done.
Also errors I got when I'm logged in. ( Attached screenshot)



Before I was using Ubuntu 8.10 for 3 years. When I installed 8.10 3 years ago, pc was also extremely slow. I add ipw2100-modules-2.6.18-6-486_2.6.18+1.2.1-4+etch3_i386.deb package, which require linux-module-2.6.18. It was installed automatically. After those 2 packages everything was fine. For me it seems that linux-module did the trick and not ipw2100 package. 

So how to get now 10.10 working on my notebook?
a) I somehow get linux-module-2.6.18 (which is not available on Debian servers, at least, I could not find it) and add ipw2100 package. Don't know yet how to do this.
b) Forum people help to find out some other way, how to get my pc working!


Any help will be appreciated!

---

### Post by dino99 on 2011-01-14
10.10 comes with its own kernel(s), latest is 2.6.37-12, so cant understand why you still look at oldish one.

the errors shown on your screenshot are only about applets, nothing to worry about.

I suppose you always have made dist-upgrade to have such mess in your config. As everything & everywhere, cleaning can help.

Times to times, a fresh install is a good idea. Then logs let you know about errors and misconfiguration.

By the way, if that laptop have not much ram, then choose a light distro: Lubuntu rather than ubuntu, for example, or netbook rather than desktop.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by marisdembovskis on 2011-01-14
Thanks for replay. 
1. It is fresh 10.10 install. Everything is up to date, clean ...
2. I don't care about applets, I care about speed of working system. It is not normal. Bootup is 10 minutes. Firefox starts 1 minute. Terminal 2 minutes. Alt + Tab takes 5 seconds. Awful to work. Now I'm typing from Live CD session. I don't use installed system, because it is toooo slow. 
Notebook has 1 GB RAM. 
Slow system is not related with old pc. 10.10 should work on this pc, but not so slow. I don't expect my laptop to be like i5, but also not like this. 

3. Is there a way, how to write LIVE CD to HDD? That could be good solution.

---

### Post by marisdembovskis on 2011-01-14
What else hav noticed is that slow process starts from GRUB. 

For example. 
I start from hdd, if i want to edit boot lines, it takes minutes to do that. It' s hanging. 

I start from cd, it takes seconds to edit boot lines. 


I'm thinking it would be great:
1) edit grub, which is on hdd to say, that it should use dir, where is extracted live CD files. So that it could boot the same as from CD, but reading HDD files. 

just don't know how exactly accomplish this.

---

### Post by marisdembovskis on 2011-01-14
Solved in 2 ways:

a) 

1. create new partition. and do dd if=livecd.iso of=/de/newpartion
2. bootup with cd then before startup take edit comand, (Try ubuntu version) file=/cdrom/..... changed to file=/dev/sda5 worked like charm. Booted up live cd from hdd. 


b) searched forums for asus. 
and stupid it is or not, but trick was with:

1) editing Grub before bootup (add pci=nomsi mem=1000M nosplash noapic nolapic
2) sudo su
cd /etc/default
gedit grub

find the line 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
changed to
GRUB_CMDLINE_LINUX_DEFAULT="quiet pci=nomsi mem=1000M nosplash noapic nolapic"

save.
3)last command in terminal: update-grub
reboot.


Of course, the most natural and easy way was way b.
Thanks forum. 
Lots of stuff can find here and learn! 
:)

Ubuntu 10.10 rocks! Even on my trashy M3N. :)

---

### Post by banago on 2011-02-16
I have EXACTLY the same problem on a Comapaq Presario F700 but this line does not save my problem:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet pci=nomsi mem=1000M nosplash noapic nolapic"

Do I need other configuration for my case?

---

