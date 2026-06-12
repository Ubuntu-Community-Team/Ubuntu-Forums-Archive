---
title: "Can't get a session"
date: 2008-08-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LittleKoy on 2008-08-22
Here is my problem:

- If I login using a normal session, since last update it tells me that GNOME Power Management is not installed correctly, then it appears the Wicd window asking for my root password, but it always tells me it's wrong. At the 3rd try, it disappear and leave me with the light-brown screen, and nothing happens

- If I use failsafe GNOME, it tells that it couldn't connect to session bus, and goes back to the login screen

What can I do? Looks like it happened just to me...

---

### Post by LittleKoy on 2008-08-23
Up! It is very serious, I can't use my desktop anymore... If no one here can help me, could I know at least where someone could? For example the developers themselves...

---

### Post by plun on 2008-08-24
Well, you seems to be alone with your error.

Can you switch to a tty terminal  ?   **Ctrl-Alt-F1**  >  login

```
sudo apt-get update && sudo apt-get upgrade
```

Also maybe to remove the Wicd package ?

```
sudo /etc/init.d/gdm restart
```

or Ctrl-Alt-Del for reboot.

---

### Post by LittleKoy on 2008-08-24
I could connect ny ethernet using nm instead of wicd... But my situation changed so much :D

I first tried to upgrade, and the Gnome Power Manager error was fixed. But the main problem was still there, I logged in and it just stopped at the light brown screen. I can do ctrl+alt+f1 although, and I have complete access to my computer there.

Then, I removed gdm, and, after logging in, typed startx. But:
- If I simply type 
```
startx
```
it goes to a grey screen with an x as cursor, and it stops there
- If I type 
```
sudo startx
```
it starts successfully, but I'm root user (fear é.è)

A lot of output comes out from both, maybe it could help you, how can I redirect the output to a text file? I tried something like:
```
startx > x.log
```
but it didn't work

---

### Post by plun on 2008-08-24
Well, this is difficult but we must start somewhere and most
important is that you are fully upgraded.

Switch to the tty

```
sudo apt-get update && sudo apt-get dist-upgrade
```


Note that I am using **dist-upgrade**, be really **careful** and check what apt will perform, it can be removals which must be checked.


What graphic driver are you using....?


We also probably needs other solutions and proposals from others.
This is a new challenge which I haven't seen before for Intrepid.

---

### Post by LittleKoy on 2008-08-24
Unfortunately I'm not home now, but I'll be back tomorrow... I upgraded (but not dist-upgrade) about 20 hours ago... Of course when I'll be back I'll upgrade again, but I have the feeling that it's not gonna help much... :(

I'm using Ati Opensource, since I have a graphic card radeon 9200se. 
Oh, I just remember that I once tried to reinstall gdm, and I always got low graphic on the login screen since then

---

### Post by plun on 2008-08-24
Ok, it seems to be some trouble with your graphic card.

[http://ubuntuforums.org/showthread.php?t=885606](http://ubuntuforums.org/showthread.php?t=885606)

---

### Post by LittleKoy on 2008-08-24
> **plun said:**
> Ok, it seems to be some trouble with your graphic card.

[http://ubuntuforums.org/showthread.php?t=885606](http://ubuntuforums.org/showthread.php?t=885606)

But it's strange, because I can log and freely use my computer in GUI mode, if I log as root... Since sudo startx works while startx doesn't, could it be some privileges problem?

---

### Post by plun on 2008-08-24
> **LittleKoy said:**
> But it's strange, because I can log and freely use my computer in GUI mode, if I log as root... Since sudo startx works while startx doesn't, could it be some privileges problem?

OK, ronacc had exactly the same trouble within this thread.

[http://ubuntuforums.org/showthread.php?t=863406](http://ubuntuforums.org/showthread.php?t=863406)

As I understands it,  this was a fileroller bug but maybe a chmod is needed
for your /home ?

Late evening here so perhaps ronacc is awake ?  "ping" !!:)

---

### Post by jerrylamos on 2008-08-24
The problem with getting a session/desktop on my Thinkpad R31 is Gnome 2 on Alpha 4.  Alpha 3 ran fine (for an alpha).  Alpha 4 Kubuntu runs (no Gnome 2, uses KDE which works) Alpha 4 Xubuntu (no Gnome 2, uses XFCE which works.

This is being entered from the Thinkpad by going back to Alpha 3, then updating everything else except Gnome 2.  Works O.K. as an alpha.  Then add Gnome 2 and can't get a session or a desktop.

Yes there's a bug written, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257450](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257450).  

There are a number of similar entries in this forum.  I haven't seen any reply from the Gnome 2 people.

Jerry

---

### Post by LittleKoy on 2008-08-25
I'm home!
How can I downgrade?

---

### Post by LittleKoy on 2008-08-25
I redirected the output of startx into a file, I'm attaching it, since there are errors, they may be the key

---

### Post by plun on 2008-08-25
Ok  > "error in locking authority file /home/mesh/.Xauthority"

Have you checked permission for your /home/mesh ?

Article about this:
[http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)

Easiest.. check with nautilus and right click on your /home/mesh/   >
properties and the permission tab.

(If you are root no need for **gksudo nautilus**)

((also no need for chown and the terminal   :) ))

EDIT
You can not downgrade...

---

### Post by LittleKoy on 2008-08-25
Yes, I gave all permissions possible using chmod :D
But if I type
ls -l
I get:
-rwxrwxrwx
So what is the first line about?

---

### Post by plun on 2008-08-25
> **LittleKoy said:**
> Yes, I gave all permissions possible using chmod :D
But if I type
ls -l
I get:
-rwxrwxrwx
So what is the first line about?

Well... I am lazy and always forget about chown....:)

Here is a picture from Nautilus and a right click on my /home

[IMG]http://www.ubuntu-pics.de/bild/2428/permYCZHE.jpg[/IMG]

drwx-----

---

### Post by LittleKoy on 2008-08-25
Actually it was .Xauthority that interested me :D

---

### Post by plun on 2008-08-25
> **LittleKoy said:**
> Actually it was .Xauthority that interested me :D

Well, /home must also have correct permission.

xauthority belongs to root.

-rw--------

---

### Post by LittleKoy on 2008-08-25
Huge update!

Seems to be gnome fault after all. I tried to install IceWM, and it works! But I totally dislike it, so I'm gonna try xfce now to see if it's good, while I wait for gnome to be fixed

---

### Post by plun on 2008-08-25
> **LittleKoy said:**
> Huge update!

Seems to be gnome fault after all. I tried to install IceWM, and it works! But I totally dislike it, so I'm gonna try xfce now to see if it's good, while I wait for gnome to be fixed

Well, I have no more ideas about Gnome, perhaps someone else ?


LXDE is great... [http://lxde.org/wiki/Ubuntu](http://lxde.org/wiki/Ubuntu)

Flying PC....:)

---

### Post by LittleKoy on 2008-08-25
I'll try it! GNOME was great, so I hope I can go back using it as fast as possible...
XFCE looks nice, but some applications are not starting (aMule, f.e., but eMule Wined runs :D), so I'll try that ;)

---

