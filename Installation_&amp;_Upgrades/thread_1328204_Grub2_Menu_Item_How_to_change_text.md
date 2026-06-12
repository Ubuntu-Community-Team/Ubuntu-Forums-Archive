---
title: "Grub2 Menu Item: How to change text?"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by PeggySue on 2009-11-16
In Grub 1 it was possible to change the text shown at boot up.  E.g. I could change it to "Windows XP for Memory Map" and "Ubuntu; Use this one for everything else".
Grub 2 generates info like "Karmic 9.10 on sda6".  This is meaningless to my users.  Short of hacking grub.cfg, is there an approved way of changing the menu item text?  Previous threads are littered with changes to grub.cfg but not the menu text (as far as I can see).

Grub 2 is really slow to boot.  Is there a safe way back to Grub 1?

Any ideas appreciated.

PeggySue

---

### Post by PeggySue on 2009-11-17
Anyone any ideas?

---

### Post by drs305 on 2009-11-17
I wrote a guide on tweaking the G2 menu, but I have to caution: GEEK Alert! It can *look* a bit overwhelming and complicated. Here is the link:
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

The alternative to changing the scripts is to create a custom menu (usually /etc/grub.d/40_custom) in which you can make the title anything you want. The disadvantage is that the menu won't update as changes are made to your system - you have to go in and make them yourself. You can also name it 06_custom to have the custom menu entries appear at the top of your menu.

If you want to try adjusting the scripts and have questions, it might be best to ask them within the Tweaks thread. I'll continue to monitor both threads.

---

### Post by PeggySue on 2009-11-17
That's great.  Thank you so much.  I have changed the Microsoft references but it took a couple of goes!  (Silly mistakes on my part.)

I have a few more tweaks to make but just wanted to say thanks.  That's a really usefull peace of work.  It should be part of the GRUB2 HowTo.

I did search the forums but failed to find your thread.  I spent hours trawling through the threads on colors and backgrounds etc. but couldn't find anything on titles.  Hey ho!!

---

### Post by drs305 on 2009-11-17
> **PeggySue said:**
> I did search the forums but failed to find your thread.  I spent hours trawling through the threads on colors and backgrounds etc. but couldn't find anything on titles.  Hey ho!!

I have a shortcut on my FF bookmarks bar:
[http://www.google.com/advanced_search?q=site:ubuntuforums.org&hl=en&lr=&tbo=1&num=30&tbs=qdr:m]("http://www.google.com/advanced_search?q=site:ubuntuforums.org&hl=en&lr=&tbo=1&num=30&tbs=qdr:m")

It opens a page to enter terms and then searches the Ubuntu forum entries for the past month. 

I've added "grub2" "grub 2"  and "title" as tags for the post, although they are in the title of the thread.

Glad you found the post useful.

---

