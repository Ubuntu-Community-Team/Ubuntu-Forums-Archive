---
title: "Synaptic Manager fails to open."
date: 2006-05-02
forum: Installation &amp; Upgrades
---

### Post by DaemonLee on 2006-05-02
Okay, first off, let's list some stats.

Fresh install, finished at 12:41AM PST. Roughly. 
P4 2.4ghz HT, Northwood.
P4S800 Motherboard
786mb Memory, Corsair. PC3200 400mhz.
80gb 
LITE-ON CDRW 52x
Generic 50x
Dysfunctional DVD 8x

Anyways, Synaptic will fail to open, but on bootup, shows that I have 82 updates that I must do, I click on it, to show the updates, it took my password the first time, now it just sits there, and I think it ignores me now. 

Help?

---

### Post by akudewan on 2006-05-02
Open up a terminal and type *sudo synaptic* . See what output it spews out and post it here.

---

### Post by DaemonLee on 2006-05-02
[QUOTE=akudewan]Open up a terminal and type *sudo synaptic* . See what output it spews out and post it here.[/QUOTE]

steven@tux:~$ sudo synaptic
Password:
steven@tux:~$


That's it.


Also, a quote note here, it does show that I have updates via the icon, near the clock.

---

### Post by DaemonLee on 2006-05-02
(00:56:48) Aku: hi
(00:57:05) Aku: who are you ?
(00:57:12) Daemon: DaemonLee
(00:57:15) Daemon: From the Ubuntu forums.
(00:57:19) Aku: oh
(00:57:20) Aku: ok
(00:57:33) Daemon: I just replied to your post.
(00:57:41) Daemon: Basically, it'll take my password but gives no output.
(00:57:44) Aku: yes, I see it
(00:58:32) Aku: try "which synaptic"
(00:58:53) Daemon: steven@tux:~$ which synaptic
/usr/sbin/synaptic
steven@tux:~$

(00:59:12) Aku: this is odd, I can't figure it out
(00:59:49) Daemon: Me neither.
(00:59:57) Daemon: This is the first time, this has happened to me.
(01:00:27) Aku: is apt-get working ? 
(01:00:40) Daemon: Nope. Not as far as I can tell.
(01:00:49) Daemon: It'll take the command, but it's like talking to a wall. No response.
(01:01:13) Aku: :-S
(01:01:30) Aku: what about "apt-get moo" ?
(01:01:38) Aku: (i'm serious)
(01:01:53) Daemon: Haha. Yeah, that works.
(01:01:53) Daemon: steven@tux:~$ apt-get moo
         (__)
         (oo)
   /------\/
  / |    ||
 *  /\---/\
    ~~   ~~
...."Have you mooed today?"...

(01:01:58) Aku: lol
(01:02:05) Daemon: I gotta remember that one.
(01:02:40) Aku: well, i hope someone else replies on the forum
(01:02:57) Daemon: Mind, if I post this convo? Then people can see what we talked about and such?
(01:03:06) Aku: ok, no problem

---

### Post by xenmax on 2006-05-02
[QUOTE=DaemonLee] steven@tux:~$ sudo synaptic
Password:
steven@tux:~$


That's it.[/QUOTE]
DaemonLee, did you do an expert installation? The symptoms are similar to that. If so, try this thread: (especially codejunkie's post)
[http://ubuntuforums.org/showthread.php?t=146859](http://ubuntuforums.org/showthread.php?t=146859)

---

### Post by DaemonLee on 2006-05-02
Okay, I pulled something from my Ye Olde Days of Windoze. I did a reload and gave it a try again, and it works. Oddly.

---

