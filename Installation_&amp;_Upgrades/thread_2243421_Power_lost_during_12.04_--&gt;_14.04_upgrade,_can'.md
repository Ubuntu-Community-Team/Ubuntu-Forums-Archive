---
title: "Power lost during 12.04 --&gt; 14.04 upgrade, can't login"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by painter90 on 2014-09-08
So I left the laptop during the install and the plug wasn't fully in the side of the laptop and the battery died. At first it would only boot to some text, then after trying some steps I found while googling, it gets to the login screen, but when I enter my password, it flashes some text and goes immexiately back to the login screen.

Now I'm in the tty1 (?) command line. I think I have it connected to the net, but when I run sudo apt-get upgrade, it says unable to fetch archives. I tried it with --fixmissing (?) switch and it did a lot of unpacking, processing triggers, and installing, ran for a while, then after I rebooted and now its stuck after I put in my password, says "logging in...". If it matters, the login screen says 12.04, but in the tty1 terminal it says 14.04.1.

I'm totally clueless about what's going on and what to do about it. The only reason I haven't reinstalled it from scratch is because I looking around the desktop via the prompt and my stuff was still there, so I'm hoping it can be fixed.

---

### Post by Bashing-om on 2014-09-08
painter90; Hi ! Welcome to the forum.

If we can get you to the desktop, will make things easier in determining the state of the system.
One possibility that prevents you starting the desktop is that "you" do not have the authority to access the desktop.
do terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
ls -al /home/<user_name>
##e.g.##
ls -al /home/painter90
##IF painter90 were your "user_name"##

```
is your output similar:
```

sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Aug  1 10:10 .Xauthority
sysop@1404mini:~$

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 14996 Sep  8 13:42 .ICEauthority
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /home
drwxr-xr-x 27 sysop sysop  4096 Sep  8 13:42 sysop

sysop@1404mini:~$ ls -al /home/sysop
##all files are owned and grouped as "you"
#<snip>
-rw-r--r--  1 sysop sysop    3749 Aug  4 00:03 .bashrc
#<snip>
##except:
drwxr-xr-x  4 root  root     4096 May 19  2013 ..

```
Here my "user_name" is sysop. Is your outputs similar ?

Else: we cleanup, update, upgrade/fix and try again.

[INDENT][INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by painter90 on 2014-09-08
everything is similar to yours for all four commands, with my username on all the listings except --> .. = root

---

### Post by Bashing-om on 2014-09-08
painter90; Well !

Unexpected, but all to the good !

Let's try and start the desktop from terminal and see what results, .. 
Are you running (u)buntu with the standard desk top w/unity as the desktop environment ? Or other ?

As I dither and think about having a package management assessment of the system. But think it will be the more productive presently to see the errors when the desktop is activated.

[INDENT][INDENT]we can take a hint
[INDENT][INDENT][INDENT]to look in some direction
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by painter90 on 2014-09-08
yes I'm running ubuntu w/ unity, the side bar apps thingy.

again, the login screen says 12.04, and the terminal says 14.04, so I'm not sure which version I'm on.

I tried to do startx from the terminal, and it said command not found. I just tried installing some things the terminal suggested, and now I can use startx to get to a new looking gray desktop... rebooted and the gui login still hangs though.

---

### Post by Bashing-om on 2014-09-08
painter90; All to the good.

OK to start the unity desktop:
```

sudo service lightdm start

```

As to what release you are up on; what returns:
```

lsb_release -a

```

Another thing that will prevent the desktop from starting is a broken proprietary graphics driver. When you did the release upgrade, what driver was in use ?
[INDENT][INDENT]slowly but surely 
step by step
[/INDENT][/INDENT]

---

### Post by painter90 on 2014-09-08
lightdm is already started.. I went from tty > gui > terminal at this point.. release says 14.04.. which is weird because login screen still says 12.04...

the upgrading getting stopped halfway + me trying some stuff I googled must have really made a mess of things. I was hoping if I could connect to the net, it would be able to get the stuff it needs, but ifconfig doesnt even show a wlan0..

---

### Post by Bashing-om on 2014-09-08
painter90; Welp'

3 steps forward and 2 back.

We got to have a reliable internet connection. Do you have access to a 'wired' connection ?

do we have
[INDENT][INDENT][INDENT]a serious failure to communicate 
[/INDENT][/INDENT][/INDENT]

---

### Post by painter90 on 2014-09-08
I can get wired access in about an hour... there is no 'eth' under ifconfig if it matters, just a 'lo'..

I had a wlan0 earlier, but after I kept trying the sudo apt-get upgrade multiple times, its now gone. My wireless card is still recognized by the system though.

---

### Post by Bashing-om on 2014-09-08
painter90; Sheessh ..

Wireless I have no experience with. Perhaps 'tween now and then those who do have the skills will pop in here.

In just a bit I will be calling it a night for this session. I can get back with you in my PM .. chores to get done in the AM.

We now have a desk top, which will facilitate posting of information.
So far the situation is far from hopeless.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by painter90 on 2014-09-08
ok, i appreciate all your trying.

---

### Post by Bashing-om on 2014-09-08
painter90; Hey

No problem . My little bit of pay back and contribution to the overall effect.

We get a stable connection, and we go again .. get the package manager happy, and then make the system happy.

[INDENT][INDENT]it can happen
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-09
painter90; I am Baaacck ;

Are you up on a solid 'wired' connection ?
If so we see now what the package manager thinks of the system.

[INDENT][INDENT]we got to have a talk with
[INDENT][INDENT][INDENT][INDENT]the software repository
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

