---
title: "[SOLVED] update to 8.04.1?"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by ajgreeny on 2008-07-07
Can I assume that a fully updated original Hardy 8.04 is now the same as a new install of the new iso 8.04.1 and that there is no need to reinstall?  I have looked everywhere but not been able to find an answer to this, but presume this to be the case.

---

### Post by dje on 2008-07-07
Has done for me, i haven't reinstalled. I've just done normal updates and i have 8.04.1 ;)

---

### Post by rolnics on 2008-07-07
> **ajgreeny said:**
> Can I assume that a fully updated original Hardy 8.04 is now the same as a new install of the new iso 8.04.1 

I would assume that. I noticed the other day that my conky setup states 8.04.1, so it must be, don't ask me how it's know though!

---

### Post by jw5801 on 2008-07-07
Please check the stickies before posting.

---

### Post by ibutho on 2008-07-07
> **ajgreeny said:**
> Can I assume that a fully updated original Hardy 8.04 is now the same as a new install of the new iso 8.04.1 and that there is no need to reinstall?  I have looked everywhere but not been able to find an answer to this, but presume this to be the case.

There is no need to reinstall. If you have kept up to date with updates for hardy, then you are running 8.04.1. You can check by running "cat /etc/lsb-release. The DISTRIB_DESCRIPTION should be Ubuntu 8.04.1.

---

### Post by ajgreeny on 2008-07-07
OK jw5801, I'll do that - if you can tell me how to find the stickies on the forum.  I can find no link to them at all, but perhaps I just don't understand how to get to them.

---

### Post by Pumalite on 2008-07-07
If you have kept up with the updates; you have it. Check your menu.lst. Your first entry should read: Ubuntu 8.04.1

---

### Post by Rocket2DMn on 2008-07-07
Here is the sticky - [http://ubuntuforums.org/showthread.php?t=849915](http://ubuntuforums.org/showthread.php?t=849915)
It is the second sticky post at the top of the page on this forum area.  There are Sticky Threads and Normal Threads.

---

### Post by abn91c on 2008-07-07
to check your ubuntu version type this in a terminal:
 sudo lsb_release -a

---

### Post by jw5801 on 2008-07-08
> **ajgreeny said:**
> OK jw5801, I'll do that - if you can tell me how to find the stickies on the forum.  I can find no link to them at all, but perhaps I just don't understand how to get to them.

The stickies for each subforum go at the top of every page. If you open the page for the [Installation & Upgrades](http://ubuntuforums.org/forumdisplay.php?f=333) subforum, you'll see the two stickies right at the top of the list.

---

### Post by ajgreeny on 2008-07-08
OK, Thanks folks.  The reason I don't see them is simply the way that I access the forum, using the RSS feeds on a bookmark toolbar in FF.  I seldom if ever go to forum home pages, but will do so in future occasionally.

Just a quick edit to avoid confusion to other users.  I do now definitely have 8.04.1 as shown by **sudo lsb_release -a** in terminal, but the menu.lst still shows 8.04.  Presumably it is just new installs of the new iso which change the menu.lst entries. or perhaps when a new kernel appears that will do it.

---

