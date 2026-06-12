---
title: "how to make windows the default system?"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by rizzz on 2006-06-13
i installed the ubuntu in another hard drive. but every time i start my computer it goes straight to ubuntu. just before it goes to ubuntu, it gives me an option to go to windows. but I want my computer to go straight to windows instead of ubuntu. Basically i want my default operating system to be windows xp and not ubuntu. how do i do that?

---

### Post by Andykvakk on 2006-06-13
Go to a terminal. Write "sudo gedit /boot/grub/menu.lst". Find the line "standard 0" change this to the line corresponding with the line containing XP, you'll find it further down in the file. PS! When you are counting the lines, start at "0".

I guess default ubuntu install is:
Ubuntu
Ubuntu Safe mode
Memtest
Other operating systems
Windows XP

If you have this selection on boot then you should change the line to "standard 4".

Hope this helps you!

---

### Post by fredinator on 2006-06-13
[COLOR="red"]EDIT woops too late Andykvakk posted quicker and an easier way[/COLOR]
Open up applications->accessories->terminal and type ```
sudo gedit /boot/grub/menu.lst
```. The editor will pop up. In the editor, go down to the section that says ```
## ## end debian automagic kernels list ##
``` and cut and paste the whole section that says ```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
to under the section that says ```
## ## end default options ##
``` on a new line. after this put a hash (#) in front of the section that says ```
title           Other operating systems:
root
``` so it looks like ```
#title           Other operating systems:
#root
```

---

### Post by dabang on 2006-06-13
[COLOR="Red"]Ooops, too late for my answer... ;-)[/COLOR]

```
sudo gedit /boot/grub/menu.lst
```

Look for

```
default    0
```

and change it from "0" to "3" (if you have a default Ubuntu install with 2 kernel entries and the memtest) and the windows entry is the 4th. otherwise change appropriate.

or

copy
(should be at the bottom of the file and look something like this)

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1 
```

above this line:

```
### BEGIN AUTOMAGIC KERNELS LIST
```

And you should be set!

---

