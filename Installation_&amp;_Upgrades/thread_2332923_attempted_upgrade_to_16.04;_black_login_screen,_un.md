---
title: "attempted upgrade to 16.04; black login screen, unknown username"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by deloric on 2016-08-05
Hello,

I was notified of the 16.04 update the other day and tried to update.  After a while it froze, so I restarted my machine, and now when I turn it on it comes to a black screen asking for a login and password.  I have no idea what my login would be.  I tried to boot my windowsXP but that just brought me to the same black screen.  Is there a way to figure out what my login username is?  I'm not very techie.

Thanks for any help

Tracey

---

### Post by steeldriver on 2016-08-05
Your home directory name will almost always be the same as your username, so one way to find it is to boot to [recovery mode]("https://wiki.ubuntu.com/RecoveryMode") and then type

```

ls /home

```

in the root shell (there is no need to remount the filesystem - you can skip that step)

---

### Post by deloric on 2016-08-05
I tried booting in recovery mode but the same screen asking for login and password just comes up.  It won't let me type anything different in there - just says its an invalid login.

---

### Post by steeldriver on 2016-08-05
When you get to the Advanced Menu, you should be able to use the arrow keys to select "Drop to root shell"

[ATTACH=CONFIG]270589[/ATTACH]

Press the TAB key to select <OK>, then you should see a message

```

Press Enter for maintenance
(or press Control-D to continue)

```

Press Enter and you should get a root shell

```

root@machine-name:~# 

```

into which you can type 

```

ls /home

```

[ATTACH=CONFIG]270590[/ATTACH]

---

### Post by deloric on 2016-08-05
I can't get to the advanced menu.  I choose to boot from advanced menu, then it gives me a long list of options, half of which have (recovery mode) after them.  "ubuntu, with linux 3.13.0-(# between 32 and 92)-generic"  I've chosen multiple recovery modes, and it runs through a long script of text and then that black logon screen comes up.  It says "ubuntu 16.04.1 LTS tracey-eM250 tty1"  "tracey-eM250 login:"

---

### Post by grahammechanical on 2016-08-05
If the upgrade froze and you switched off you may need to do a fresh install of Ubuntu 16.04. That may be the best option for you for you may now have a broken installation.

If you were able to get to the recovery menu by selecting a recovery mode kernel, then we may be able to suggest some commands that may complete the upgrade. But you cannot get to the recovery menu.

Regards

---

### Post by deloric on 2016-08-05
Okay; thats what I was thinking I might have to do.  Thankfully I just did a backup a few weeks ago when I resized my partitions.  Thanks for the help everybody.

---

### Post by steeldriver on 2016-08-05
FYI if you have unsaved data (since your last backup) then you should be able to mount your broken system from a live CD / USB and copy it off - there should be no need to lose anything

---

