---
title: "help me to upgrade carmic to lucid please..."
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by psudheera on 2010-06-10
[FONT=Georgia]hi.. i'm sudheera new to linux and still trying to learn about it.

ok.here's the problem.i'm currently using ubuntu 9.10 carmic and need to upgrade to 10.04 .
I have downloaded the iso and burned into a cd and the cd working perfectly (i have installed it my friend's computer ).when i'm trying to upgrade carmic, i insert the cd and nothing appeared. and i hit alt+f2 and enter [/FONT]gksu "sh /cdrom/cdromupgrade"[COLOR=#000000][FONT=Times New Roman][I][FONT=Georgia][SIZE=2]then appear a window to enter  password, and when the password entered nothing happened.[/SIZE][/FONT][SIZE=2]i have no idea about what's going on.please can any one help me.[/SIZE]
[/I][/FONT][/COLOR]

---

### Post by dvlchd3 on 2010-06-10
That is extremely odd.  Does the computer have an Internet connection?  If so, try to upgrade via command line:

Applications -> Accessories -> Terminal
```

sudo apt-get dist-upgrade

```
Type in your password if prompted.

---

### Post by Elfy on 2010-06-10
Did you download the alternate iso - you need that to upgrade from.

It should also offer the upgrade when the cd is inserted from memory.

---

### Post by psudheera on 2010-06-10
thanks for your reply,but I have slow Internet connection.Is there any other ways??

---

### Post by sidzen on 2010-06-10
> **psudheera said:**
> thanks for your reply,but I have slow Internet connection.Is there any other ways??
Please go here and study the dd command:
[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

A clean install is your best option.  If you need to backup first, it will tell you how.
Prepare your hard drive for the clean install by wiping it with zeros first.  It tells you how with
[PHP]#  dd if=/dev/zero of=/dev/hda conv=notrunc[/PHP]uncomment by removing the # to make the command usable from the command line.

If you need help, come back here.  Someone will be here to assist, if not me. (Probably not me)

Best wishes.

---

### Post by psudheera on 2010-06-10
thanks for all of you...I also think the best option is a clean install.thanks again..

---

