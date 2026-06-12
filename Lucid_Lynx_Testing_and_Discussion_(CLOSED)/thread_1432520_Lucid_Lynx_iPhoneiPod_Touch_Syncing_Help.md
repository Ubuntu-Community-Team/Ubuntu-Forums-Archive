---
title: "Lucid Lynx iPhone/iPod Touch Syncing Help"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xVehemencityx on 2010-03-17
Hi, so, I installed 10.04 alpha, and I was very surprised to see that it supports iPods without having to install anything different. I was able to plug it in and view (and play) my songs in Rhythmbox.  Only problem is I can't figure out how to sync it.  I installed gtkpod, and all of the other plugins I can think of, reading every guide I can find.  When I try to mount my iPod through gtkpod, it says 

```
Could not find iPod directory structure at '/media/iTunes_Control/Music'.

If you are sure that the iPod is properly mounted at '/media/iTunes_Control/Music', it may not be initialized for use. In this case, gtkpod can initialize it for you.

Do you want to create the directory structure now?
```


So I click Create Directory Structure, and it tells me to select iPod mountpoint and model.  I know what my model is, but how can I tell what the mountpoint is when it automatically mounts it?

---

### Post by overdrank on 2010-03-17
Moved to Lucid Lynx Testing and Discussion

---

### Post by xVehemencityx on 2010-03-17
Thanks for moving it.  I couldn't find the subforum.

---

### Post by ndefontenay on 2010-03-17
I've read an article about that in OMG! Ubuntu just 2 days ago.

Maybe this works fine with lucid lynx. I was thinking they did that for us already and we wouldn't have to toy around with it though :(

[http://www.omgubuntu.co.uk/2010/03/sync-iphone-and-ipod-touch-in-ubuntu.html](http://www.omgubuntu.co.uk/2010/03/sync-iphone-and-ipod-touch-in-ubuntu.html)

---

### Post by xVehemencityx on 2010-03-17
Thanks for the guide.  I followed it to the T, and when I started up my computer, it gave me this error.

```
DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered
```

---

### Post by xVehemencityx on 2010-03-19
Any ideas?  Basically I just need to figure out where my iPod is mounted, I think.  How do I do that?

---

### Post by xVehemencityx on 2010-03-19
Okay, I found the mountpoint of my iPod, put it in, and gtkpod is frozen.  It still hasn't responded.  Been at least 3 minutes, and I think that's plenty long enough for my computer.  It's not a slow pc by any means.

---

### Post by cyberkilla on 2010-03-19
I can't wait for this stuff to be stable enough that I can use my iPod Touch 1G fw3.1 without rebooting into Vista:p

---

### Post by xVehemencityx on 2010-03-19
I agree completely, haha.  I think I'm going to have to install VirtualBox with XP so I can just use iTunes (bleehhh).  Hopefully I don't have too much trouble with that.

---

### Post by GoGoGulliver on 2010-03-20
My iPod Touch lives in ~/gvfs/ which I agree is not a very user friendly place to put it. 

In gtkpod, point it to there, and it should be able to find it.

I also had to run the following command (from [http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html]("http://fatbuttlarry.blogspot.com/2010/01/ipod-touch-iphone-3g-ubuntu-910-in-5.html")) to make it work:

$ sudo adduser "$USER" fuse; echo -e "\n\nPlease type the name of your ipod:"; read ipod_name; mkdir -p "$HOME/.gvfs/$ipod_name/iTunes_Control/Device/"; ipod-read-sysinfo-extended `sudo lsusb -v | grep 'iSerial' | awk 'length($0)>=68' | awk '{print $3}'` "$HOME/.gvfs/$ipod_name/"

---

