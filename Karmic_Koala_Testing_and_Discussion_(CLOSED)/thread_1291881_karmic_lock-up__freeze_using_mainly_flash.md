---
title: "karmic lock-up / freeze using mainly flash"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Claus7 on 2009-10-15
Hello,

as the thread title suggests, I want to report a freezing problem about karmic koala 9.10.


SPECS:
I have a cpu of 2GHz (more than 7 years old) which is working pretty nicely up to now. There is a Seagate HDD, which is brand new and works pretty nicely as well.

PROBLEM:
In this hdd, I have installed jaunty and since then from karmic alpha 4 till the beta (doing all the updates since) at the time or writing. Previous versions of ubuntu did not freeze.

Jaunty was locking up almost all the time, making a hard boot an everyday experience.

Now karmic in its alpha releases was pretty nice without having any lock up problems. Since the beta release and kernel 2.6.31-11-generic karmic is freezing. What it does it that I cannot move mouse, the Caps Lock and Scroll Lock buttons are blinking and the sound is "trailing". 
What I mean with trailing is that when I hear sound the sound stacks. I do hear sound after the freezing, yet it is repetitive showing like the process wants to continue, yet it cannot.

Most lock ups (the majority of them) happen when I have either opera or firefox open with you tube on and flashplayer working.

Also when I have this application open my computer from 10 to 20% of cpu usage goes to 80-90+% cpu usage. Is this normal? Has anyone else faced the same problem? I think that most lock ups happen because of the flashplayer.

With the latest kernel 2.6.31-14-generic I faced the problem twice doing exactly the same thing: opening opera and choosing the same link from you tube.

edit: 2.6.31-14-generic is locking pretty badly now, at random
edit2: I do not know if it is relevant, yet in /var/log/syslog I get:

Oct 16 01:19:49 claus-desktop pulseaudio[1753]: alsa-util.c: Unable to set sw params: Too many open files
Oct 16 01:19:49 claus-desktop pulseaudio[1753]: alsa-sink.c: Failed to set software parameters: Too many open files

Regards!

---

### Post by Claus7 on 2009-10-22
Hello,

making all the updates and cleaning my memory slots out of dust I have seen no lock up since...

Regards!

---

### Post by GoMad on 2009-10-27
Claus, I have upgraded to Karmic and also get frequent lockups which I can only resolve with a reboot.
 
Causes so far seem to be;
 
1) Ripping a DVD in mythtv, it will be fine, and randomly for no reason locks up
2) Ripping DVS's in acidrip and dvd:rip also freeze it
3) Connecting remotely via Tight VNC causes it to lock up
4) Sometimes an ssh session causes it to freeze (this maybe a side effect from one of the above)
5) Running firefox ALWAYS causes it to freeze.
 
Very annoying. I have a pucka MSI ATI motherboard, Intel graphics card, P4 Pentium, 2.4 GHz. This used to run Windows without any issues what so ever. so what is causing 9.10 to keep freezing (happens multiple times in a few hours). I am worried it is going to end up making a mess of the file system !
 
The intel graphics chip set had known issues under 9.0.4 so I will try switching this out and see if it resolves the issue, but I am not confident this will resolve it.
 
 
Thanks
 
Jason.

---

### Post by Claus7 on 2009-10-27
Hello Jason,

judging from my lock ups and comparing to yours, this is what I can tell you:

1) no action
2) no action
3) I had never a lock up, while using vnc
4) I have experienced this lock up as well. Yet, it only happened when I was not typing at the moment and leaving the terminal open for a long time...
5) I use both opera and firefox. As I have mentioned I was facing problems mostly with flashplayer.

I would advice you to make a full upgrade after the final version is out. This might vanish the problems you are facing. What I have seen is that the lock ups have ceased, yet I cannot tell if a reasonable amount of time is passed.

Thanks for your response,
Regards!

---

