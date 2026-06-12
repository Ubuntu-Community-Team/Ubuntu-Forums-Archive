---
title: "Stuck trying to replace Mint with Ubuntu"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by eGyEm7R on 2013-09-26
Searched the forum, probably don't know how to ask the question so here goes.

I have a dual boot with Win 7 and Mint, would like to replace Mint with  Ubuntu but when I select "something else" and continue I'm lost.

Note: I*'*m a relative newbe so English would be appreciated........ :p

---

### Post by Kirboosy on 2013-09-26
Welcome to the forums! :D

Ok, so when you select something else you will want to select that partition that currently holds Mint. (It will be an EXT4 format most likely). There should also be a SWAP partition and you will wanna make sure to  select to use that as well. Reformat it to SWAP that way Ubuntu knows to  use it.

Now, **please** make sure that you backup any important data from Mint before you reinstall to Ubuntu. It will delete everything on the Mint partition and that can get messy trying to recover data. 

Hope that helps!
~Caboose

---

### Post by eGyEm7R on 2013-09-26
> **Caboose885 said:**
> Welcome to the forums! :D

Ok, so when you select something else you will want to select that partition that currently holds Mint. (It will be an EXT4 format most likely). There should also be a SWAP partition and you will wanna make sure to  select to use that as well. Reformat it to SWAP that way Ubuntu knows to  use it.

Now, **please** make sure that you backup any important data from Mint before you reinstall to Ubuntu. It will delete everything on the Mint partition and that can get messy trying to recover data. 

Hope that helps!
~Caboose

I saw all that, don't know how to do it, guess I'm looking for a step-by-step, I'm a visual type of person.  As for the Mint OS, could care less, nothing there I need.

---

### Post by Kirboosy on 2013-09-26
Can you provide me with a screenshot of your screen when you click "Something Else"?


Thanks!
~Caboose

---

### Post by eGyEm7R on 2013-09-26
> **Caboose885 said:**
> Can you provide me with a screenshot of your screen when you click "Something Else"?


Thanks!
~Caboose

I'll get back to you on that one, when I figure out how to take a screen shot when loading a new OS.

---

### Post by oldos2er on 2013-09-26
> **eGyEm7R said:**
> I'll get back to you on that one, when I figure out how to take a screen shot when loading a new OS.

Hitting the printscreen button should work.

---

### Post by Kirboosy on 2013-09-27
Here is a quick guide I made. I threw together a VM with a Mockup of  what I think your drives should be similar to. (I'm using a VM so my  hard drive probably isn't as big as yours)

[ATTACH=CONFIG]246536[/ATTACH][ATTACH=CONFIG]246535[/ATTACH][ATTACH=CONFIG]246537[/ATTACH]

That should give you a rough idea of how to do it. (The FAT drive is my "Windows" The EXT4 is my Mint install)


Hope that helps!
~Caboose

---

### Post by sandyd on 2013-09-27
> **eGyEm7R said:**
> I'll get back to you on that one, when I figure out how to take a screen shot when loading a new OS.

When starting up from the livecd, choose Try Ubuntu instead of Install Ubuntu - then click on the install icon on the desktop
Then you can take screenshots

---

### Post by eGyEm7R on 2013-09-28
> **Caboose885 said:**
> Here is a quick guide I made. I threw together a VM with a Mockup of  what I think your drives should be similar to. (I'm using a VM so my  hard drive probably isn't as big as yours)

[ATTACH=CONFIG]246536[/ATTACH][ATTACH=CONFIG]246535[/ATTACH][ATTACH=CONFIG]246537[/ATTACH]

That should give you a rough idea of how to do it. (The FAT drive is my "Windows" The EXT4 is my Mint install)


Hope that helps!
~Caboose
That just answered my question.

My partitions are:

/dev/sda1 nfts
/dev/sda2 nfts
/dev/sda5 ext4
/dev/sda6 unknown

I assume the unknown is the swap file. Thanks!

---

### Post by eGyEm7R on 2013-09-28
So far so good, the install went without a hitch, Win7 still works normally and I'm configuring Ubuntu now.  Thanks again! :D

---

### Post by Kirboosy on 2013-09-30
Glad to be of assistance and help. If you could mark the thread as solved that would be awesome! (Under "Thread Tools" at the top of the first post)

Thanks!
~Caboose

---

