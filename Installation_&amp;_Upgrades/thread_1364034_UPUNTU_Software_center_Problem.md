---
title: "UPUNTU Software center Problem"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by salah salamah on 2009-12-25
when i install a new package or program from UBUNTU software center, I see a message Say

Installing Packages
Waiting for other software managers to quit

But i don,t use any manager else this one.

And this pic show that problem ( [the pic is here]("http://fine.comli.com/index.files/Screenshot.png") )
[CENTER][IMG]http://fine.comli.com/index.files/Screenshot.png[/IMG]
[/CENTER]
 [CENTER][IMG]http://fine.comli.com/index.files/Screenshot.png[/IMG]

Please help me, or i have to install a new copy of UPUNTU
[/CENTER]

---

### Post by howefield on 2009-12-25
Reboot and try again, then you'll be sure nothing else is running ?

---

### Post by salah salamah on 2009-12-25
I restarted my PC more than one time and this problem is still.

May be that will help( the cause of the problem )

I was downloading a package but the computer shutdown at the middle of downloading because of the power electricity. And the problem happens from that time.

If you know how to stop all package which are downloaded now using Terminal, please tell me.

Or tell me what have i do know. and this problem from 24 Hours and it still happens now.

---

### Post by User3k on 2009-12-25
Do you have any updates running? Check the bottom right in the system tray. You will see an icon I believe if there is a package manager running.

---

### Post by salah salamah on 2009-12-26
I'm new user of upuntu, 
Could you tell me how to do that using steps, please?

1: go to what
2:press what

Like that please

---

### Post by 4levels on 2010-01-03
I had the very same issue.  Google found these 2 bugs related to this:

[#464020]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/464020")

and

[#446262]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/446262)

The solution is quite simple (as showed in the first bugreport reply's):

run
```
sudo dpkg --configure -a
```

Things should be fixed now...

---

