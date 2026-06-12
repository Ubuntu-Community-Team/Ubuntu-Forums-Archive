---
title: "Ubuntu does not turn off completely !"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by s.maciek on 2008-09-01
Hello!

I have read a lot of about my problem but nothing has helped me yet. The issue is really simple. When I try to turn off/reboot/re-log/log computer off typing it from menu, all applications get closed instead of system. Only my desktop is available and nothing more, just the wallpaper is visible. Theres nothing on it, icons, any bars, even Metacity is closed. I can move my mouse but I can't do anything else. Waiting if it will change something wouldn't help aswell ( 2 hours waiting :/ ).  I have been looking for some help on [www.forum.ubuntu.pl]("www.forum.ubuntu.pl") ( Polish forum for Ubuntu users ), but no one knew how to help me. 
Now I must turn of my laptop by pressing Start button. But then session is not saved and when I turn computer on Ubuntu loads session before the problem appeared. There are some programs running on which I do not use any more and it drives me crazy when I have to close them over and over again. Saving session do not help, tried it many times.

I already have tried to fix it these ways, none have helped :

- I've added to /boot/grub/menu.lst ```
acpi=force lapic
```
- I've added to /etc/modules ```
apm power_off=1
```
- When I type ```
sudo shutdown -h now
``` it turns computer as same as it turns by pressing Start button, so it do not help me
- As same as above, but other command```
sudo halt
```
- When I typed in console ```
apm power_off=1
```
then appears " No apm support in kernel ". Someone told me it could help ...

Please, I really need your help. Because I can't set anything and save it. Everything just restart because I turned Ubuntu off in the wrong way ( pressing start button or those two commands I've listed above). PLEASE HELP !

I'm sorry if you have had some problems with understanding my post, my English is not so well as I wanted it to be ;).

---

### Post by s.maciek on 2008-09-01
Maybe some process stops system ? How can I check which one ??

---

