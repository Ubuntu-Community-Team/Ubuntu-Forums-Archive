---
title: "strange boot problem"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by nickless on 2005-07-12
My Ubuntu needs 3 restarts until it boots completely. (Except sometimes :? ...)
It just stops. while loading modules. When I restart the same happens when hot-plug system should be loaded. 
I have no idea why. I actually messed a bit in menue.list, trieing to get a grub splash screen, but I don't see what I could have done wrong  ](*,)

---

### Post by mingus on 2005-07-12
[QUOTE=nickless]
I have no idea why. I actually messed a bit in menue.list, trieing to get a grub splash screen, but I don't see what I could have done wrong  ](*,)[/QUOTE]

Reading various posts re adding the grub splashimage, or even much more so installing splashy, apparently a number of folks have had boot problems as a result.  I can see why this could easily happen with splashy, although I was surprised that just adding a background image would also be a problem.  But apparently for some it has.  Why don't you back out whatever you did, then do a $sudo update-grub to regenerate menu.lst, see if that fixes it.

---

### Post by nickless on 2005-07-14
[QUOTE=mingus] Why don't you back out whatever you did, then do a $sudo update-grub to regenerate menu.lst, see if that fixes it.[/QUOTE]
Because I didn't knew this command thx :D
I'll try that.

---

### Post by crashd on 2005-07-26
[QUOTE=nickless]Because I didn't knew this command thx :D
I'll try that.[/QUOTE]
I have the same problem but this command don't work for me. 
Any ideas to solve?

---

### Post by mingus on 2005-07-27
[QUOTE=crashd]I have the same problem but this command don't work for me. 
Any ideas to solve?[/QUOTE]

We need more of a description of the problem.

If you do eventually get into Ubuntu, *immediately* open a terminal and do:
$dmesg | more
and look for any error messages.  Also you can try:
$cd /var/log
and then look at the logs, for example:
$more syslog
$more messages
$more Xorg.0.log

---

