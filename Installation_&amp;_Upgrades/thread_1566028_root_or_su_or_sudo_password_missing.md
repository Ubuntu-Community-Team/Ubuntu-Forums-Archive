---
title: "root or su or sudo password missing"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by rejean on 2010-09-01
Hi all!
I upgraded from Super Ubuntu 2008.11 to Ubuntu 10.04.1 online ( my mistake ). Now I can boot into Ubuntu 10.04 with 2 kernel options and a failsafe. However I can only boot as a user ( rejean ) and not as su or sudo. 
My other problem is that I don't have a gui. 
I would like to do a 
```

sudo dpkg-reconfigure xserver-xorg
```

but there is no password that works.
What should I do?
I am posting from mandriva and can mount the ubuntu partition no problem if that can help.

---

### Post by lsmobrian on 2010-09-01
I'm a little confused at what you meant by boot as su or sudo? So previously rejean was a sudoer? and after the upgrade rejean could no longer run a command as sudo with rejean's password? 


If you need root access and can't get it through logging in as root or using su or sudo, you can boot into single user mode, from there you can do whatever you'd like.

The failsafe option in grub should do that for you, if not edit the  grub entry you'd normally use and on the line that has words like 'quiet ro splash' etc... add the word 'single' and boot that entry.

this will bring up a root prompt and you can do whatever you needed to do as sudo or su,  run your dkpg-reconfigure command and reboot and see if X is back(the word single will have disappeared from grub if you did need to edit before)

---

