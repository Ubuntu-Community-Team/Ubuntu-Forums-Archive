---
title: "problems opening synaptic graphical interface"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by nick holme on 2006-06-12
since upgrading to dapper, I have had problems running some administration programs like synaptic and Users and Groups and some others. I recently followed a thread which pointed me at the "alacarte menu editor". From this I found that all the programmes that I am having problems with have an entry in the properties starting with gksu....... i.e. gksu /usr/bin/synaptic. If I go to a termainal and type sudo synaptic rather than gksu synaptic the graphical interface works OK. Do I have to chgange the properties in each of the alacarte menu editor entries or is there another explanation.

Nick

---

### Post by aysiu on 2006-06-12
Does this work? ```
gksudo synaptic
```

---

### Post by nick holme on 2006-06-12
no that just hangs the same as gksu synaptic. The one that works is sudo synaptic.

---

### Post by aysiu on 2006-06-12
If you launch ```
gksudo synaptic
``` from the terminal (not from a launcher icon), do you get any error messages?

---

### Post by nick holme on 2006-06-12
hi aysio. thanks for help.

the only error message that I get comes up whatever command I use. see example

nick@ubuntu main:~$ gksudo synaptic
sudo: unable to lookup ubuntu main via gethostbyname()

and the cursor just hangs - nothing else happens.

If I type sudo synaptic....

nick@ubuntu main:~$ sudo synaptic
sudo: unable to lookup ubuntu main via gethostbyname()
Password:
nick@ubuntu main:~$
with this command, the synaptic package manager opens OK.

---

### Post by aysiu on 2006-06-12
[This thread](http://www.ubuntuforums.org/showthread.php?t=91455&page=2) may help you out.

---

### Post by nick holme on 2006-06-12
OK, I've had a quick look but I haven't changed anything yet. This thread seems to be all about permissions and mentions gdm.conf and .dmrc fairly frequently. I checked my gdm.conf earlier following a suggestion in a post and it looks OK. If you feel that this thread may be the answer, I will try some of the other suggestions tomorrow - it's getting a little late now here in sunny England. I can see how this may get rid of the message "unable to lookup ubuntu main via gethostbyname()" but I can't see the connection with sudo and gksu. Should I be looking at something else as well?

---

### Post by aysiu on 2006-06-12
You may want to look into the /etc/hosts file, too? I don't know. I found that thread by Googling your error. I've never experienced this problem myself.

---

### Post by nick holme on 2006-06-12
Thanks for your help aysiu, but I'm giving up now for tonight. I'll try again tomorrow. I think there are two different problems - the one that won't start synaptic and the one that gives the error "unable to lookup ubuntu main via gethostbyname()" but I could be wrong. One thing I have discovered is that if I do sudo synaptic, it works and then if I do gksu synaptic, that also works, but only after I have donme sudo synaptic first. The graphical command from system administration still doesn't work.

---

