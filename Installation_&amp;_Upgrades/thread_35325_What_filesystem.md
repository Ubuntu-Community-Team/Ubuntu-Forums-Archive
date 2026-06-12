---
title: "What filesystem?"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by BorO on 2005-05-18
Hello!

I wonder wich filesystem I should use. Which one is fastes?

---

### Post by tread on 2005-05-18
More than fastest, get a journalling file system. Reiserfs/ext3 come to mind.

---

### Post by Redbaron on 2005-05-18
Yeah, either go with EXT3 or ReiserFS.  In the end it doesn't really matter which one you choose. Both are great.  The only thing about ReiserFS that is better than EXT3 is how it deals with very small files < 4k .  But realisticly you are not going to notice any performance difference as a general user.

---

### Post by BorO on 2005-05-18
Thank you!

I have installed my Ubuntu on Ext3...Works fine but I have problem with my Refresh Frequens. It's on 60Hz all the time. How xan I fix that? I can't choose any other...

---

### Post by Rodrigo on 2005-05-18
Personally I like RaiserFS more :p

---

### Post by bored2k on 2005-05-18
[QUOTE=BorO]Thank you!

I have installed my Ubuntu on Ext3...Works fine but I have problem with my Refresh Frequens. It's on 60Hz all the time. How xan I fix that? I can't choose any other...[/QUOTE]
 sudo dpkg-reconfigure xserver-xorg

---

### Post by bored2k on 2005-05-18
EXT2 is the fastest, but it comes with a price: a hard reboot could and probably will render your *machina* unconscious. ReiserFS/ext3 is the way to go.

---

### Post by BorO on 2005-05-18
> Personally I like RaiserFS more 
Personally I don't know much about this  :| 

>  sudo dpkg-reconfigure xserver-xorg 
Works fine now! Thanks..


My last problem for now is that it feels like the GUI is slow. I run Ubuntu Live yesterday and it worked very well. GUI was fast and responsive.

What can it be?  :|

---

### Post by matid on 2005-05-18
I use ReiserFS for my / disc, and for /home, etc. I use ext3.

---

### Post by BorO on 2005-05-18
When I push the logout button the screen is slowly starting to be darker. This transformation was going smothly running UbuntLive, but now it's not running so mothly..

---

### Post by jdong on 2005-05-18
ok, reiserfs is indisputably faster than ext3 at all tasks, but that speed comes at a price of possible DATA corruption after a hard reset (ext3 keeps more information in its journal than reiserfs).


Ext3 is a very sound choice, unless you have a _REALLY GOOD_ reason why you need that extra performance from reiserfs.



Don't use XFS. It makes many risky assumptions (i.e. no IDE drive writeback cache) that lead to almost guaranteed filesystem corruption after a bad shutdown!

---

