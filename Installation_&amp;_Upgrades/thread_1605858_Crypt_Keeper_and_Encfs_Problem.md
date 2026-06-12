---
title: "Crypt Keeper and Encfs Problem"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by lmp321 on 2010-10-25
Hi,

I upgraded to 10.10 on my Asus netbook 10.10 a few weeks ago. I have a separate ntfs partition with my data on it. One of the directories on that partition was encrypted using Cryptkeeper on when my netbook ran 10.04. I've tried to import the encrypted folder with Cryptkeeper, but the program doesn't see the encrypted directory, even though I can see it if I undo the hide function in nautilus. If I tell the file to open using Cryptkeeper, it just shows another encrypted folder on my system. I'm not sure what to do as the directory contains my previous years tax information!

Thanks!

---

### Post by globalmac on 2010-11-09
don't know if this will help you but I was having a similar problem when I did a clean install of 10.10 and restored everything back with mondo.  when I would try to import my encrypted folder it would give me an error.  what I found is that the hidden folder with the name (.xxx_encfs, where xxx is the name of your folder) was not restored.  I restored this folder and pointed cryptkeeper at this, hidden folder when importing and now I got it back.  God bless.

---

