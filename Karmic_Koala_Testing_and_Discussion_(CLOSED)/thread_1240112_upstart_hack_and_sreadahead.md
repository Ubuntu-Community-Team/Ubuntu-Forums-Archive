---
title: "upstart hack and sreadahead"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-08-14
anybody tried to hack the new upstart.. i found some how-to on old upstart which uses /etc/event.d but quite a lot changed since 0.5 to 0.63....

also anybody using sreadahead instead of readahead? if so did you spot any improvement?

---

### Post by MacUntu on 2009-08-14
I used the information in this thread: [http://ubuntuforums.org/showthread.php?t=727224](http://ubuntuforums.org/showthread.php?t=727224).

I followed the steps in the lower part of this posting to create the jobs: [http://ubuntuforums.org/showpost.php?p=6158642&postcount=38](http://ubuntuforums.org/showpost.php?p=6158642&postcount=38)

Just changed some dependencies as you can see in my depchart (you can find a link to the depchart script at the end of that thread):

[[img]http://img.xrmb2.net/315719.jpg[/img]](http://img.xrmb2.net/images/315719.png)

You need to change the line 
```
f=open("jobs.d/"+item.name,'w')
```
in upconv.py to
```
f=open("jobs.d/"+item.name+".conf",'w')
```
as jobs now need to have the conf extension.

Same thing goes for
```
self.name=name.replace("-","_").replace(".","_")
```
in depchart.py which I changed to
```
self.name=name.replace(".conf","").replace("-","_").replace(".","_")
```
if you wanna create such a depchart image.

Jobs then need to go into /etc/init (back up that directory, create a new one and copy all the scripts needed from the backup). I've removed the "2" from the runlevel list in rc.conf (start on...), removed rcS.conf and rc-sysinit.conf and that's it.

Result: some seconds saved during boot but this conversion feels very hacky/incomplete. And I lost my terminals (F1-F6). :D

Not played around with sreadahead a lot. First runs on a HDD are disappointing (+6s for GRUB2 -> desktop) but that's WIP.

**Edit**:
Make sure you don't run sreadahead in the foreground (I added "--no-fork" to the exec-line in /etc/init/sreadahead.conf - no SSD here, so running it in the background wouldn't make much sense) when you don't have a file list (/var/lib/sreadahead/pack) or else your system won't boot anymore. :D

---

### Post by rednus on 2009-08-14
> **MacUntu said:**
> I used the information ...
Thanks MacUntu... I will have to give this a go..

---

