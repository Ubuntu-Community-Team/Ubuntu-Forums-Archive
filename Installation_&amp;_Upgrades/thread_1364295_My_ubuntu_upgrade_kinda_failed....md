---
title: "My ubuntu upgrade kinda failed..."
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by kog6 on 2009-12-25
So ya that pretty much says it all right there, my computer froze up during the upgrade and, luckily, i can still log on but i cant do much else... can anyone help me? i cant get to the update manager or the add/remove programs or the ubuntu software center... atleast not through the desktop... 
noob speak plz xD any help would be much appreciated!!!

---

### Post by phillw on 2009-12-25
> **kog6 said:**
> So ya that pretty much says it all right there, my computer froze up during the upgrade and, luckily, i can still log on but i cant do much else... can anyone help me? i cant get to the update manager or the add/remove programs or the ubuntu software center... atleast not through the desktop... 
noob speak plz xD any help would be much appreciated!!!

Hi & welcome to the Ubuntu Forum.

Were you upgrading from 9.04 -->  9.10 ?
Did you take any backups of your system before you did the upgrade ?

We're going to have to drop to the command line for some of this stuff, It's under Applications --> Accessories --> Terminal   Or, more quickly, the little black rectangle icon with **>_** in it. Don't worry, it's a case of copy and paste.

To Copy **from** a code selection in a post, triple click it to highlight it, then hold down the Ctrl key and press **C**  then in the terminal window hold down Shift and Ctrl and then press **V**

The one below is entirely safe - just be aware of this thread

[http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)

```

sudo apt-get moo 
```It will ask you for your password, if it all works - you'll be greeted with a match-stick drawing of a cow

Regards,

Phill.

---

### Post by kog6 on 2009-12-25
Haha thanks for the post about the thread i'll keep an eye out
wats the next step? The command line works fine

---

### Post by kog6 on 2009-12-26
ooh nvm i got it all cleared up!
i used the script 
```
sudo dpkg --configure -a
```

---

