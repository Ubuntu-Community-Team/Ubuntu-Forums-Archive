---
title: "ubuntu 13.02 to 14.04 install password not working on first boot!"
date: 2014-09-13
forum: Installation &amp; Upgrades
---

### Post by mrezstreet on 2014-09-13
I got my laptop working again and found that the 13.02 was not supported so I moved to 14.04. I put the same password in as old version, and when I go to login on, screen blinks and them comes back to login again. I have rebooted, went to change root pw but i get errors in command lines about not mounted. I am not super ubuntu buff, but have tried all kinds of stuff to fix password to no avail. In grub I changed boot line from ro to rw , but after that I can not move forward....

I m sorry for my lack of cool factor...but my laptop with a ton of pictures is dead in the water. It has just ubuntu on it but I have half the hdd portion and free.

---

### Post by Bashing-om on 2014-09-13
mrezstreet; Hello;

Could be a number of things at fault here,
What pops to mind is 2 things.
a) You do not have authority to access the GUI;
What returns from terminal commands ( at the login screen key combo ctl+alt+F1, to get a console terminal);
```

ls -al .Xauthotity
ls -al .ICEauthority
ls -al /home
ls  -al /home/<user_name_  ##where <user_name is your actual login name##

```

b) When you upgraded you had a proprietary graphics driver in use, and it got broke in the process;
What returns:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
Starting this ball rolling, and a place to begin the process of fault isolation.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mrezstreet on 2014-10-05
The info I got said cache data failed

---

### Post by Bashing-om on 2014-10-05
mrezstreet; Hi !

Information out of context has little relevance as we can establish the relevance.
Please post the commands requested and the outputs for our inspection.
Will poke at it 'till we find a reasonable cause.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mrezstreet on 2014-10-05
I may have misunderstood. At login I did ctl+alt+F1 and got that I will get on a laptop and attach picture of the screen. I could have missed something.  Thanks from your patience.

---

### Post by Bashing-om on 2014-10-05
mrezstreet; I have a failure to understand .

All I am requesting is that you get to a terminal, execute those 6 commands from post#2, and provide the outputs for our inspection. Unil such time as I see those outputs, I have nothing to base any notions on.

[INDENT][INDENT]knowledge is power
[/INDENT][/INDENT]

---

### Post by mrezstreet on 2014-10-05
I got that message after I did ctl+alt-+F1. I didn't understand to put codes after that. Thanks Will get the info and reply.

---

