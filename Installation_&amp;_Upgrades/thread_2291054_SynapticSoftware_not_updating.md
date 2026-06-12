---
title: "Synaptic/Software not updating"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2015-08-17
Hi:

Neither synaptic nor software updater are working.  The latter doesn't open, and the former gives me the following message:

E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



When I go to edit /etc/apt/sources.list.d/medibuntu.list I cannot save the file when I try to comment out the listing starting with <html><head><meta, which is the only one.

When I type gksudo gedit /etc/apt/sources.list.d/medibuntu.list    into terminal, nothing happens.

How do I fix this?

Thanks

---

### Post by howefield on 2015-08-17
You should be safe enough in removing the medibuntu file as the repository has been defunct for quite some time.

Or move/copy it out of the way so you still have it and then delete it.

You should also be able to do this from "Software and Updates". Might be called Software Sources in your version of Ubuntu.

---

### Post by wjbmd48 on 2015-08-17
OK, so I'm a pretty basic user. When I try to move the file out of the way, I get 

 Error moving file: Permission denied

I'm assuming there's a simple "sudo" type terminal command to do this, right?

Thanks

Bill

---

### Post by wjbmd48 on 2015-08-17
OK, so I finally figured out how to sudo mv . . . . .

And got the file moved out of the way, and now the updater and synaptic are up and running.

I do appreciate the prompt help.  You guys are the greatest.

Is there a place to send a donation?

Bill

---

### Post by howefield on 2015-08-17
Uhm.. something like 

```
sudo cp /etc/apt/sources.list.d/medibuntu.list ~/
```

sudo gives you elevated permissions so you should be ok using the command you had tried but prefaced with sudo this time. It will likely ask for your password which you should type in and press the enter key. You will not see the password being entered.

---

### Post by howefield on 2015-08-17
> **wjbmd48 said:**
> Is there a place to send a donation?

No need for that, we just love a happy ending. :p

---

### Post by dino99 on 2015-08-17
> **wjbmd48 said:**
> OK, so I finally figured out how to sudo mv . . . . .

And got the file moved out of the way, and now the updater and synaptic are up and running.

I do appreciate the prompt help.  You guys are the greatest.

Is there a place to send a donation?

Bill

Start your devotion by hitting 'Thread Tools' on top right corner of your first post, and set it to 'SOLVED'  ):P:p

---

### Post by wjbmd48 on 2015-08-17
Hah! That was easy.

Again, thanks all.

Bill

---

