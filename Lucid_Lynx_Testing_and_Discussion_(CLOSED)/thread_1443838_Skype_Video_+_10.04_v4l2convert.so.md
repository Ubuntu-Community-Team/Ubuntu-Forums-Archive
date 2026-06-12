---
title: "Skype Video + 10.04 v4l2convert.so"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 0004tom on 2010-03-31
Does anyone know how to force skype to load the v4l2convert.so when you lunch skype from the aplications menu?

I've pointed the luncher to a simple script

```
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype
```

I've even tried the full location for skype, /usr/bin/skype but it just doesn't work. It won't show my video. But if I run the command from terminal it works. Does anyone know a work around that works? I've tried tens of example for the same problem on from the net but nothing works for me. :(

---

### Post by xc3RnbFO8P on 2010-03-31
Try:
> #!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

---

### Post by Scott82 on 2010-03-31
I had the same issue with the camera, command also worked for me, what i ended up finding to get it to do it automatically was actually from the opensuse forum (other places had really lame methods, none of which worked for me) here's what it was:

opened up a terminal and did:
```

sudo mv /usr/bin/skype /usr/bin/skype.real  
sudo chmod 755 /usr/bin/skype.real
sudo gedit /usr/bin/skype

```
in the new file opened by gedit:
```

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

```
saved that file, then in the terminal did:
```

chmod 755 /usr/bin/skype

```
then skype worked fine either starting it in startup apps or from the gnome menu.

source of info: [http://en.opensuse.org/Skype_HOWTO](http://en.opensuse.org/Skype_HOWTO)

note: i dono wtf i'm doing at all, but hey.... it works... i'd guess that this would have to be done again each time i install a new version of skype though, but on the other hand the linux versions seem to be released every what? 50 years? (sorry for the sarcasm :D )

---

### Post by 0004tom on 2010-03-31
Thanks so much Scott88 that did the trick, I guess I didn't look at that as it was for opensuse.

---

### Post by Scott82 on 2010-03-31
glad it helped ya, i think it really isn't much different than what you did though so i dono why it works so much better, maybe it's the chmod thing, whatever that is that really made it work.

I didn't really expect to find the answer on the opensuse forum either, it was just one of the sites the almighty google gave me :D

---

