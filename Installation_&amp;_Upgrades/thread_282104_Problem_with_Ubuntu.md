---
title: "Problem with Ubuntu"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Tasadduq khan on 2006-10-22
Hello,

I have just installed Ubuntu 6.06 , which I got a few days ago by ubuntu (their free shipping method). 

Everything went normally, I installed it to one of my harddrives (Hard drives not partition). Logged in normally but when I tried to run .exe files (except the few ones already installed like broswer etc) none worked. I can't even open the media player installed by ubuntu as well. When I click on .exe file it says "can't locate the file". Also I can't install any kind of software.

Could any one help me solving this problem.

Thank you

PS: Sorry if this isn't the right catagory to post in.

---

### Post by Najand on 2006-10-22
well, Linux does not support usuall windows applications which has .exe extensions. There are some emulators like wine which allow to use that, but they are not very complete, still... You can install wine by typing this in the terminal (Terminal can be found at: Application->Accessories->Terminal)

```

sudo aptitude install wine

```
and press ENTER; then enter your passwrod... 
And then try to run your file using:
```

wine <PATH>/<FILENAME>.exe

```

---

### Post by Tasadduq khan on 2006-10-22
Thanks for the hint.
But I am having problem with their own Movie player. Also what if I want to install some software? Though I have to download some software for linux.

---

### Post by Kateikyoushi on 2006-10-22
To install software use the synaptic package manager.
System >> Administration >> Synaptic Package manager.

This guide might help you in understanding the basics. [LINK]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Tasadduq khan on 2006-10-22
Hello,

YOu might be right. I am going to check this but I can't understand why movie player isn't working at all? :(

Sorry to sound to dumb but I am totaly new to linux side.

---

### Post by Kateikyoushi on 2006-10-22
Which movie player do you mean ?
The one in Applications >> sound and video ?
Linux does not use .exe extension to mark executeable files.

---

### Post by Tasadduq khan on 2006-10-22
I am talking about the program which is built in by Ubuntu. I am not sure about the name but I didn't try to install my own (Coz it isn't letting me install other software :) , But I am going to try the method you just mentioned).

I simply double clicked my media files and it says " can't locate ...... " or "something like that". 

BTW can I install normal software on Ubuntu (Like the ones I use with Windows XP, Guessing not?)

Thank you

---

### Post by Kateikyoushi on 2006-10-22
You can try to use wine to run Windows software in linux, but out of the box no.

---

### Post by Tasadduq khan on 2006-10-22
umm
Still having no success with "Administration >> Synaptic Package manager" method.

Thanks mates for helping me out. Lets see what other people have to say.

Thank you
Tasadduq Khan

---

### Post by ashenrose on 2006-10-22
You may find the add/remove option easier. Go to Applications> Add remove and have a look around it. It has some useful things on there. 

If you post the error message you are getting with the ubuntu movie player, someone may be able to help you a bit better. :)

---

### Post by Peepsalot on 2006-10-22
I'm guessing the error is because you are missing a **codec** for whatever file type you want to play.
See this thread for some more info:
[http://www.ubuntuforums.org/showthread.php?t=182902&highlight=codec](http://www.ubuntuforums.org/showthread.php?t=182902&highlight=codec)

---

