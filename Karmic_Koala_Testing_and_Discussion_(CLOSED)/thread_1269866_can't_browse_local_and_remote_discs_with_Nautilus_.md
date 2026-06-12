---
title: "can't browse local and remote discs with Nautilus as root"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-09-18
Hi,
Is there any reason why I can't browse all local and remote discs (Computer icon in Nautilus tool-bar) from "gksu nautilus" or as root? It seems to work ok in Jaunty but not in Hardy or Karmic. Would this be a feature or a reportable bug? It's quite annoying!

Cheers, Mike

---

### Post by VMC on 2009-09-18
> **mdurham said:**
> Hi,
Is there any reason why I can't browse all local and remote discs (Computer icon in Nautilus tool-bar) from "gksu nautilus" or as root? It seems to work ok in Jaunty but not in Hardy or Karmic. Would this be a feature or a reportable bug? It's quite annoying!

Cheers, Mike

If you run "gksu nautilus" inside a terminal. What does it report?

---

### Post by mdurham on 2009-09-18
> **VMC said:**
> If you run "gksu nautilus" inside a terminal. What does it report?
gksu nautilus
> Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

** (nautilus:4272): WARNING **: No marshaller for signature of signal 'DownloadFinished'
Shutting down nautilus-open-terminal extension
Shutting down nautilus-gdu extension

(nautilus:4272): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
Nothing appears in the terminal when I get the error message from Nautilus

VMC are you able to use this feature?

---

### Post by VMC on 2009-09-18
> **mdurham said:**
> gksu nautilus

Nothing appears in the terminal when I get the error message from Nautilus

VMC are you able to use this feature?

Yes, but sometimes I have to issue the command several times. Eventually it works. I know there is an LP against it, so I will just keep using it that way.

---

### Post by mdurham on 2009-09-18
> **VMC said:**
> Yes, but sometimes I have to issue the command several times. Eventually it works. I know there is an LP against it, so I will just keep using it that way.
Thanks for replying VMC, what command do you have to issue several times?

---

### Post by VMC on 2009-09-19
> **mdurham said:**
> Thanks for replying VMC, what command do you have to issue several times?

```
gksu nautilus
```

---

### Post by mdurham on 2009-09-19
> **VMC said:**
> ```
gksu nautilus
```

I see. thanks. I don't have that problem. When yours does run (as root or gksu), can you click on the 'Computer' icon without getting an error message?
Cheers, Mike

---

### Post by pulpo69 on 2009-09-19
i can confirm this problem, it also happens with "sudo nautilus".

---

### Post by amano on 2009-09-19
Is there s launchpad bug for the issue?

---

### Post by chrisccoulson on 2009-09-19
This happens because there is no dbus-daemon and gvfs daemon that your Nautilus process can talk to. Upstream disabled the auto-spawning of these because they can be left around after you close the Nautilus process.

---

### Post by Tibuda on 2009-09-19
I can't too open nautilus with sudo too.
```
~$ gksu nautilus
Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x00 0x00 0x00 0x00 0x00 0x00 
~$ gksudo nautilus
Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x00 0x00 0x00 0x00 0x00 0x00 
~$ 
```

---

### Post by mdurham on 2009-09-19
> **danielrmt said:**
> I can't too open nautilus with sudo too.
```
~$ gksu nautilus
Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x00 0x00 0x00 0x00 0x00 0x00 
~$ gksudo nautilus
Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x02 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x3a 0x00 0x00 0x00 0x00 0x00 0x00 
~$ 
```
That's not what this thread is about!

---

### Post by dmizer on 2009-09-19
> **chrisccoulson said:**
> This happens because there is no dbus-daemon and gvfs daemon that your Nautilus process can talk to. Upstream disabled the auto-spawning of these because they can be left around after you close the Nautilus process.

In short: It doesn't work because it leaves a mess behind when you do, so it's been disabled. 

This is a good thing. You should NEVER be using Nautilus as root for anything other than pure emergency situations. If you need to regularly use Nautilus to browse anything, you need to think about figuring out how to fix it so you don't have to use Nautilus as root.

---

### Post by Tibuda on 2009-09-19
> **mdurham said:**
> That's not what this thread is about!

I see! That's what happens when you post without reading the whole thread. Sorry.

---

### Post by Robin Nixon on 2009-09-19
> **chrisccoulson said:**
> This happens because there is no dbus-daemon and gvfs daemon that your Nautilus process can talk to. Upstream disabled the auto-spawning of these because they can be left around after you close the Nautilus process.

The command "sudo nautilus" is mentioned 162,000 times on Google ([http://www.google.com/search?q=%22sudo+nautilus%22](http://www.google.com/search?q=%22sudo+nautilus%22)) and is in many books on Ubuntu.

So maybe  Nautilus should display an "I'm afraid I can't do that, Dave" or something, instead of all the error messages?

---

### Post by mdurham on 2009-09-19
> **Robin Nixon said:**
> So maybe  Nautilus should display an "I'm afraid I can't do that, Dave" or something, instead of all the error messages?

Or "I'm afraid I can't do that on Karmic, Dave, but I can do it on Jaunty!"

---

### Post by chrisccoulson on 2009-09-19
> **Robin Nixon said:**
> The command "sudo nautilus" is mentioned 162,000 times on Google ([http://www.google.com/search?q=%22sudo+nautilus%22](http://www.google.com/search?q=%22sudo+nautilus%22)) and is in many books on Ubuntu.

So maybe  Nautilus should display an "I'm afraid I can't do that, Dave" or something, instead of all the error messages?


You shouldn't use sudo with most graphical apps, as it can make a mess of the permissions on your home folder. People should stop giving out incorrect and reckless advice on the internet and be more sensible instead. I'd be interested to know which books give out this wrong advice too, so I can contact the authors of them.

---

### Post by dmizer on 2009-09-20
> **mdurham said:**
> Or "I'm afraid I can't do that on Karmic, Dave, but I can do it on Jaunty!"

More like, "I'm afraid that more and more people are blatantly ignoring good computing practices, so we best build a safety."

---

### Post by kestal on 2009-09-20
Though agreed, I don't think many people should use nautilus in root for regular day to day stuff, I sometimes prefer to do root naut especially when transferring batches of files to a specific folder (which requires root) via a GUI ... especially compared to transferring specific files in multiple folders at any given time to the same folder via terminal. 

There are many uses where I think a root naut is valuable.

---

