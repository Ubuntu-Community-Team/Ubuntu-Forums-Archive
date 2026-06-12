---
title: "Can anyone else browse nautilus as root?"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joey-elijah on 2009-09-18
I noticed i had this problem in Alpha 5 - and now Alpha 6 - but i am unable to browse Nautilus as root.

Sudo nautilus gives me... 

```
joey@joey-desktop:~$ sudo nautilus

(nautilus:24028): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:24028): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
joey@joey-desktop:~$ 

```

Any ideas?

---

### Post by Starks on 2009-09-18
Why are you using sudo?

Use gksu or gksudo.

---

### Post by VMC on 2009-09-18
I've used both "gksu nautilus" and "gksudo nautilus". Sometimes it works first time, sometimes not. I just keep doing it and eventually I get nautilus as root. I vaguely remember following up on a LP report. Have to re-check.

---

### Post by dinxter on 2009-09-18
> **joey-elijah said:**
> I noticed i had this problem in Alpha 5 - and now Alpha 6 - but i am unable to browse Nautilus as root.

sudo nautilus works ok here, are you up-to-date? dbus among other things has had a few important updates as part of the boot changes

---

### Post by joey-elijah on 2009-09-18
> **dinxter said:**
> sudo nautilus works ok here, are you up-to-date? dbus among other things has had a few important updates as part of the boot changes

Yes updated an hour ago. Hmm...

> **Starks said:**
> Why are you using sudo?

Use gksu or gksudo.

Out of curiosity - why shouldn't you browse as sudo nautlius? It's helpful when people explain why you shouldn't do something rather then just tell you shouldn't. :)

Neither gksudo or gksu work either anyway.

---

### Post by LKjell on 2009-09-18
I think it is when you press alt f2 and type sudo <whatever> you are not prompt to enter the password.

---

### Post by ardchoille42 on 2009-09-18
Use sudo for cli apps and gksudo for GUI apps. [Here's]("http://www.psychocats.net/ubuntu/graphicalsudo") an explanation about the difference.

---

### Post by Seren on 2009-09-18
> **joey-elijah said:**
> 
Out of curiosity - why shouldn't you browse as sudo nautlius? It's helpful when people explain why you shouldn't do something rather then just tell you shouldn't. :)

Neither gksudo or gksu work either anyway.

I have never used nautilus so there might be safeguards, but the problem of using a GUI as root, is that you are one click away of destroying you system.

Imagine you have selected for whatever reason your /bin directory and your cat jumps on your keyboard and press the DEL key.

Or you can inadverdently drag and drop your /etc into your /home or something else..

This is somewhat less likely that your cat will jump on your keyboard and write 'rm -rf /bin'...

---

### Post by handaxe on 2009-09-18
It is a known bug: [https://bugs.launchpad.net/bugs/420841](https://bugs.launchpad.net/bugs/420841)

HA

---

### Post by dinxter on 2009-09-18
> **Seren said:**
> 
This is somewhat less likely that your cat will jump on your keyboard and write 'rm -rf /bin'...
if your dog did that it would be a miraculous accident, if your cat did it it would be cold and calculated revenge

---

### Post by joey-elijah on 2009-09-18
> **Seren said:**
> I have never used nautilus so there might be safeguards, but the problem of using a GUI as root, is that you are one click away of destroying you system.

Imagine you have selected for whatever reason your /bin directory and your cat jumps on your keyboard and press the DEL key.

Or you can inadverdently drag and drop your /etc into your /home or something else..

This is somewhat less likely that your cat will jump on your keyboard and write 'rm -rf /bin'...

Aaaah okay :) I'll consider myself learnt :P

---

### Post by som24 on 2009-09-18
> **ardchoille42 said:**
> Use sudo for cli apps and gksudo for GUI apps. [Here's]("http://www.psychocats.net/ubuntu/graphicalsudo") an explanation about the difference.
[COLOR="Olive"]thank you ard[/COLOR]

---

### Post by mdurham on 2009-09-18
To answer the question, I can use gksu nautilus ok without problems.
> Imagine you have selected for whatever reason your /bin directory and your cat jumps on your keyboard and press the DEL key.
this must be one of the silliest things I've read all week!
Cheers, Mike

---

### Post by handaxe on 2009-09-22
```
gksudo nautilus
``` now works as it should in nautilus 2.28, at least for me and according to the devs

HA

---

### Post by mdurham on 2009-09-22
> **handaxe said:**
> ```
gksudo nautilus
``` now works as it should in nautilus 2.28, at least for me and according to the devs

HA

I wonder what is meant by "works as it should"? Try running "gksu nautilus" and clicking on the "Browse all Local & remote disks" icon. You will get an error message. Is this how it "should" work? 
Cheers, Mike

---

### Post by handaxe on 2009-09-22
Yup, sloppily written by me, sorry. I meant of course the error preventing Nautilus running under gksu was done with.  "Computer" did not work for me under gksu before the bug in question.  This needs a separate filing I guess.

HA

---

### Post by mdurham on 2009-09-22
> **handaxe said:**
> Yup, sloppily written by me, sorry. I meant of course the error preventing Nautilus running under gksu was done with.  "Computer" did not work for me under gksu before the bug in question.  This needs a separate filing I guess.

HA

Ok handaxe, I see what you mean, thanks.

---

### Post by ranch hand on 2009-09-22
I am not having any trouble doing anything in nautilus.  I am glad to hear that some folks are.  I have felt, lately that all problems settled in my box.  Glad some have decided to give it a miss.

---

### Post by VMC on 2009-09-23
> **ranch hand said:**
> I am not having any trouble doing anything in nautilus.  I am glad to hear that some folks are.  I have felt, lately that all problems settled in my box.  Glad some have decided to give it a miss.

It's not just nautilus, its opening nautilus under root. Try Alt+F2 then "gksu nautilus". If it opens, then close and do it a few more times. Its hit or miss for me. Either way, if I try "gksudo nautilus" same results. Then do it under a terminal and you will see something along these lines:
```
** (nautilus:2200): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2200): WARNING **: No marshaller for signature of signal 'DownloadFinished'
```

---

### Post by ranch hand on 2009-09-23
I open nautilus with the terminal and have no problem.

---

### Post by juggarnatha on 2009-09-23
How do we noobs know that we've terminated a root-level nautilus session? I just tried this, it worked, and I've closed all the windows. I would *think* that that would automatically end any high-level privileges, but perhaps someone more seasoned knows for sure . . . yes?

---

### Post by VMC on 2009-09-23
> **juggarnatha said:**
> How do we noobs know that we've terminated a root-level nautilus session? I just tried this, it worked, and I've closed all the windows. I would *think* that that would automatically end any high-level privileges, but perhaps someone more seasoned knows for sure . . . yes?

Not to sound arrogant, but a noob shouldn't run nautilus as root.

But you bring up a good point. In another distro, whenever root is run under a gui file manager, a red info is displayed displaying elevated privileges.

---

