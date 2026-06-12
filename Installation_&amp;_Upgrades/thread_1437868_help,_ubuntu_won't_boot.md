---
title: "help, ubuntu won't boot"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by goosethebus on 2010-03-24
Im completely new to linux so please excuse my noobyness. Ive been using it for a few days and it kept reminding me to update some files. (about 200mb worth) after it finished installing i rebooted but it won't show me a login screen. it only shows me a commmand line. it allows to 'exit' and then it boots windows. Please help.

---

### Post by neo unplugged on 2010-03-24
login at command line prompt and try the following:

service gdm start
And reply your output

---

### Post by goosethebus on 2010-03-24
it doesn't recognize the command 'service'

---

### Post by neo unplugged on 2010-03-24
try
/etc/init.d/gdm start

---

### Post by oldfred on 2010-03-24
Is this a grub command line or a terminal after grub boots? Is this a standard install or wubi? 

I think the only way you get windows to boot is if it is wubi?

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by goosethebus on 2010-03-24
does not recognize '/etc/init.d/gdm'

---

### Post by neo unplugged on 2010-03-24
my bad... should have asked if u r in grub command line. refer to oldfred's post

---

### Post by goosethebus on 2010-03-24
I tried using the link and i replaced the file but it made no difference

---

### Post by goosethebus on 2010-03-24
when i try to boot i get the "grub:sh>" prompt

---

### Post by neo unplugged on 2010-03-24
I am not good at at Grub prompt but check out the link below maybe of some use, (looks like a similar problem)
[http://ubuntuforums.org/showthread.php?t=1437214](http://ubuntuforums.org/showthread.php?t=1437214)

---

### Post by goosethebus on 2010-03-24
i used the commands from the thread and it looked like it was about to boot, but then it said error does not exist and it dropped to a shell

---

### Post by neo unplugged on 2010-03-24
its good that you got to a shell prompt rather than just the grub...
whats the exact error?? also, do you have access to internet on this system?

---

### Post by goosethebus on 2010-03-24
I only have access when i boot to windows obviously, but normally i would have internet access on ubuntu. I can't copy the exact error but ill try again and write it down

---

### Post by goosethebus on 2010-03-24
waiting for root file system 

gave up waiting for root device

alert! /dev/sda1/ does not exist dropping to a shell

---

### Post by goosethebus on 2010-03-25
should i just reinstall ubuntu?

---

