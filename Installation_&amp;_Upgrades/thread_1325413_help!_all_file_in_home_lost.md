---
title: "help! all file in /home lost?"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by duckling9 on 2009-11-13
Hello
I just upgraded from hardy, via intermediary step to karmic.
 
I was having problems with the boot (as I'd kept my menu.lst as was - but then fixed that)
I now have a much much worse problem - that karmic seems to have overwritten my /home with something entirely of its own creation - and wiping out my files? is this true?
 
I have /home as a separate partition... please, please tell me it didn't just do what it seems to have done....
any help gratefully received. off for a strong cup of tea.

---

### Post by doas777 on 2009-11-13
show us 
```
sudo fdisk -l
```

---

### Post by oldfred on 2009-11-13
Also print a copy of /etc/fstab so we can see if it is mounting your separate /home or not.

---

### Post by duckling9 on 2009-11-13
aaah. thanks guys, for coming with some suggestions. 
After calming down with some tea, and dinner, i was able to realise that it would all still be there, on a partition, so have now mounted that on a new mountpoint.... phew!
 
but what's with this default new /home. Can I get rid of it? how? What do i lose if I do?
thanks in advance!

---

### Post by doas777 on 2009-11-13
you could, just merge them, while running off a live cd session. or just replace the new with the old. most things that need a .file configuration, will create it if not present.  every two or three versions, I back up my content out of the home, and have it create a new one for me, just to clean out the cruft.

for next time, when you are installing ubuntu, and you get to the partitioner, edit the home partitions entry to give the correct mount point and fs type. just make sure that the "format" box is NOT checked. then the system will use your home partit by default from the first boot.

---

### Post by duckling9 on 2009-11-13
thanks. .. but i seem still not to get this - the new version (which was an upgrade, not a new install) now seems to insist on a /home somewhere else, rather than on the mount point I have created. I'm not sure how this arose or how to get rid of it...

I could just delete the new /home and hope that it now mounts my /home. Will it?

---

### Post by doas777 on 2009-11-13
is the new home already mounted to /home?

---

### Post by duckling9 on 2009-11-14
yes, the new home is mounted on /home (created by upgrade apparently), and my old home, is on, well, /oldhome

---

### Post by doas777 on 2009-11-14
fraid you'll have to swap them arround. just changing your fstab is probably enough

---

### Post by oldfred on 2009-11-14
You have done most of work of moving home, but if you want detailed instructions starting from scratch.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

