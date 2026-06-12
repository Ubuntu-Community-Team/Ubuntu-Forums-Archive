---
title: "I have problems installing programs."
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by JoKeR123 on 2008-03-01
Hi. I recently installed ubuntu on my laptop, and i like it. But I downloaded limewire for ubuntu, and when i try to install it, it says "Only one software management tool is allowed to run at the same time" i just turned on the computer. i dont think anything is running. How do i turn those programs off? Its not like windows where i can press ctrl-alt-delete to turn them off... and it also happenes to other programs i try to install... Can anyone help me? :confused:

---

### Post by pytheas22 on 2008-03-01
Are you sure you don't have the program Synaptic running?  How are you trying to install Limewire (from command line or by clicking its package's icon?)  The error could also possibly be caused because the update manager is running and is taking a long time to work (since you have a fresh install and there are a lot of updates).  I remember having problems like that with Fedora.  Try waiting for a while (half an hour) after rebooting and see if you still can't install.

Also, you might think about using Frostwire, a truly open-source version of Limewire (it's the same thing as Limewire minus the proprietary code).  It can be installed via Synaptic.

Also, the utility at System>Administration>System Monitor provides functionality similar to the Windows task manager; you can see what's running and end the process.  Or for a more complete version, learn what the "ps" and "kill" commands do.

---

### Post by JoKeR123 on 2008-03-01
What is synaptic? Im kinda new to this...

---

### Post by JoKeR123 on 2008-03-01
> **JoKeR123 said:**
> What is synaptic? Im kinda new to this...

and im installing it by clicking on it...

---

### Post by pytheas22 on 2008-03-01
Synaptic is the most popular program used to install software.  It's at System>Administration>Synaptic Package Manager.  The Add/Remove Programs utility under the Applications menu is a less powerful variant.  Make sure none of these is running.  If you still can't get it, open a terminal and post the output of the command
```

ps -e
```

and I'll see if I can figure out what's running that would give you that error.

---

### Post by JoKeR123 on 2008-03-01
When i open synaptic it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and how do i open a terminal?

Thanks for helping out with this...

---

### Post by pytheas22 on 2008-03-01
> When i open synaptic it says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

something is not right if you're getting that message.  In a terminal, run the command:
```

sudo dpkg --configure -a
```

then try opening Synaptic again.

You can get a terminal by clicking the Applications menu, then go to Accessories, and Terminal is about two-thirds down the list.  Let me know if this works.

---

### Post by JoKeR123 on 2008-03-02
dude... Thanks. It worked. I installed it but how do i get to it? Where did it install it?

---

### Post by pytheas22 on 2008-03-02
It should be under Applications>Internet.  If not, try typing "limewire" from the command line.

---

### Post by JoKeR123 on 2008-03-02
i got it. thanks alot. 
earlier u said frostwire is better. i know that. i had it when i had windows.i liked it. but i tried installing it and i think its only for windows... is there 1 for linux i can download? can u please send a link if thats not too much hastle?

---

### Post by pytheas22 on 2008-03-02
There's a .deb for it at [http://www.frostwire.com/download/?os=ubuntu](http://www.frostwire.com/download/?os=ubuntu)

If you have trouble with it (I did the first time, I think because I am running a 64-bit system), refer to [https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

