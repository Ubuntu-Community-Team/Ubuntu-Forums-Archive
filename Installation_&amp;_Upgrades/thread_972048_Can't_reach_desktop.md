---
title: "Can't reach desktop"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Valok on 2008-11-05
Just tried to install 8.10 last night and everything went fine right until after GRUB.  It did the whole ubuntu logo and loading bar bit.

But after that, it asked me to log in at a CLI and not at the normal GNOME interface.  I can succesfully log in, but rather than being brought to my desktop, I'm just presented a command line.  

Anyone else experiencing this?  I've got an exam tomorrow that I need my computer to study for.

---

### Post by raj9786 on 2008-11-05
I am having the exact same problem....any suggestions?

---

### Post by oldos2er on 2008-11-05
What happens if you type "startx" in the CLI? Are you certain you installed the desktop version of Ubuntu, and not the server version?

---

### Post by Coreigh on 2008-11-05
What happens when you type startx on the command line? Does it try and fail? Or not even try? Or what?

If it tries but fails you can try to re-configure X.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This is the script run during setup and installation of X.

---

### Post by Valok on 2008-11-05
Thanks for the replies!  I'll have to try out those commands once I get home, I'll post back once I give it a go.

I am sure I installed the correct version too, I simply did the upgrade feature from the update manager.  So it should have just gone from the 8.04 I was using to the corresponding 8.10 version.

Thanks again!

---

### Post by Valok on 2008-11-05
Alrighty, I tried the suggested code to fix X-server but I got a couple new errors when trying to start it up.

Connection Refused (errno 111)
No Such Process (Errno 3)

How do I got about fixing these ones?

---

### Post by Maverickprowls on 2008-11-09
Hi there.  I'm having a similar problem, in that the moment X starts it crashes my laptop (Amilo Li1705).  I am able to get to a terminal login by repeatedly hammering Alt+Ctrl+F1, but when I type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I am returned to the command prompt after a brief warning that I am overwriting a "possibly-customised configuration file"

When I run the same command without the -phigh option, I do get access to a menu interface which helps me configure my keyboard, but offers me no options whatsoever with regards to my graphics setup.  Is there a way of forcing this script to let me reconfigure the X setup specifically for my graphics card and screen?

---

### Post by Valok on 2008-11-09
I was not able to resolve this problem so I just ended up re-installing the old 8.04

I'd really like to get back up to date and working with 8.10, but until I can figure out what the heck happened and how to fix it, it ain't gonna happen.  

So, anyone found a way to fix this yet?

---

