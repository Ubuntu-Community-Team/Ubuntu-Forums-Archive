---
title: "Dropbox not working"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by orduek on 2009-03-24
I have installed nautilus Dropbox from the PPA jaunty repository but for some reason its not working.
I get the icon and I try to Start dropbox but then it stops and do nothing.
any ideas as to why?

---

### Post by HavocXphere on 2009-03-24
Did it ask for username & pwd?...Cause its supposed to on first launch.

Also, try running it from a terminal and see what it outputs.

---

### Post by lvlo on 2009-03-24
Try to install latest version: [http://forums.getdropbox.com/topic.php?id=7717&replies=35#post-49353](http://forums.getdropbox.com/topic.php?id=7717&replies=35#post-49353)

Works for me :)

---

### Post by orduek on 2009-03-24
I installed the new version and now i get "Waiting to be linked to an account..." ofcourse I haven't put my username and paswword yet (It didn't ask me too).

---

### Post by binbash on 2009-03-24
It is working at my jaunty box.

---

### Post by jfernyhough on 2009-03-24
The official version of nautilus-dropbox for Intrepid works fine. I'd suggest you try that first.

---

### Post by puccaso on 2009-03-24
the intrepid version doesnt work in jaunty
i think because of the python changes

it used to work, but stopped working after the python upgrade

---

### Post by Technoviking on 2009-03-24
How-to get Dropbox working in Jaunty.

1. Download and install Dropbox deb (32 or 64 bit) for Intrepid. (Note: Don't restart Nautilus)
[https://www.getdropbox.com/downloading?os=lnx](https://www.getdropbox.com/downloading?os=lnx)

2. Download experimental build of Dropbox
x86: [http://dl.getdropbox.com/u/17/dropbox-lnx.x86-0.6.491.tar.gz](http://dl.getdropbox.com/u/17/dropbox-lnx.x86-0.6.491.tar.gz)
x86_64: [http://dl.getdropbox.com/u/17/dropbox-lnx.x86_64-0.6.491.tar.gz](http://dl.getdropbox.com/u/17/dropbox-lnx.x86_64-0.6.491.tar.gz)

3. Extract experimental build of Dropbox
```
$ rm -r .dropbox-dist/
$ tar xzf dropbox-lnx.x86-0.6.491.tar.gz # or x86_64
```

4. Restart Nautilus
```
killall nautilus
```

5. Connect Dropbox to your Dropbox account.

---

### Post by | MM | on 2009-03-24
It doesn't work for me... I just get a 'Start Dropbox' contenxt menu, which when clicked tries to connect but can't because it does not know my login credentials...


EDIT: This may help:
```
matthew@matthew-desktop:~$ /home/matthew/.dropbox-dist/dropboxd
Traceback (most recent call last):
  File "__main__dropbox__.py", line 3, in <module>
  File "arch/__init__.py", line 33, in <module>
  File "arch/linux/startup.py", line 11, in <module>
  File "ui/wx_core.py", line 7, in <module>
  File "wx/__init__.py", line 45, in <module>
  File "wx/_core.py", line 4, in <module>
  File "wx/_core_.py", line 14, in <module>
ImportError: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: XRRGetScreenResourcesCurrent
```

---

### Post by orduek on 2009-03-25
OK, I worked it out. 
Thank you.
I tried to install the nautilus-fropbox from a jaunty PPA and that didn't work.
What worked was installing it from the website (I guess its the intrepid one) and then adding the new build (as mentioned above).
Notice that you should delete all the .dropbox folders before doing so.

---

### Post by tom56 on 2009-03-25
> **Technoviking said:**
> How-to get Dropbox working in Jaunty.

1. Download and install Dropbox deb (32 or 64 bit) for Intrepid. (Note: Don't restart Nautilus)
[https://www.getdropbox.com/downloading?os=lnx](https://www.getdropbox.com/downloading?os=lnx)

2. Download experimental build of Dropbox
x86: [http://dl.getdropbox.com/u/17/dropbox-lnx.x86-0.6.491.tar.gz](http://dl.getdropbox.com/u/17/dropbox-lnx.x86-0.6.491.tar.gz)
x86_64: [http://dl.getdropbox.com/u/17/dropbox-lnx.x86_64-0.6.491.tar.gz](http://dl.getdropbox.com/u/17/dropbox-lnx.x86_64-0.6.491.tar.gz)

3. Extract experimental build of Dropbox
```
$ rm -r .dropbox-dist/
$ tar xzf dropbox-lnx.x86-0.6.491.tar.gz # or x86_64
```

4. Restart Nautilus
```
killall nautilus
```

5. Connect Dropbox to your Dropbox account.

That worked great for me, thanks!

---

### Post by | MM | on 2009-03-25
> **orduek said:**
> OK, I worked it out. 
Notice that you should delete all the .dropbox folders before doing so.

Yep i didnt do that.  Now all is fine!  Thanx!

---

### Post by odysseusjak on 2009-03-28
It worked for me!

Thanks.

---

### Post by binbash on 2009-04-02
Dropbox was working perfect after upgrade from intrepid but it does not work after clean install.But with the tricks it is working fine again.

---

### Post by viduliya on 2009-04-02
That did the trick and now Janty is 100% usable for me.  Thanks Technoviking!!

---

### Post by bLaCkMeTaLL on 2009-04-09
that's it! Thanks technoviking, testing ubuntu 9.04 and now dropbox working.
Note I don't even needed to install the standard dropbox, I just took the experimental build, deleted .dropbox-dist and uncompressed it inside my home, then logout/login done the trick.

---

### Post by DJ_Peng on 2009-04-12
> **lvlo said:**
> Try to install latest version: [http://forums.getdropbox.com/topic.php?id=7717&replies=35#post-49353](http://forums.getdropbox.com/topic.php?id=7717&replies=35#post-49353)

Works for me :)
Thanks for posting this. I, too, lost use of my Dropbox once I updated to Jaunty but that link did the trick.

/me wonders when the hell we'll get our Thank You buttons back so I can use the damed thing here

---

### Post by Mud.Knee.Havoc on 2009-04-16
Dropbox just released a package with a fix for Jaunty.  It's got some more features, too!

[https://www.getdropbox.com/downloading?os=lnx](https://www.getdropbox.com/downloading?os=lnx)

From the [official announcement]("http://forums.getdropbox.com/topic.php?id=8470&replies=12#post-53870"):

> We've been keeping this secret for some months while Megabuild (0.6.507) was in development. Now it's finally ready! Here is the newest Linux package for Dropbox. In this package you can expect the following enhancements:

    * Dropbox CLI (man dropbox at your prompt :)
    * New Nautilus emblems (spiffy ones you see on the latest Mac and Windows builds)
    * Dropbox no longer autostarts for every user from Nautilus, you can now start Dropbox from your applications menu!
    * Jaunty compatibility out of the box (finally!)

 
For you Jaunty users out there who can't stand a single level of indirection here are some direct links:

    * Ubuntu 9.04 (64-bit)
    * Ubuntu 9.04
    * The Source

 
Enjoy! 

---

### Post by nandemonai on 2009-04-20
The standard Dropbox Jaunty repo version works fine here.

```
nautilus-dropbox:
  Installed: 0.6.1
  Candidate: 0.6.1
  Version table:
 *** 0.6.1 0
        500 http://linux.getdropbox.com jaunty/main Packages
        100 /var/lib/dpkg/status
```

---

