---
title: "Jaunty master volume muted on every reboot"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-04-08
Following updates this AM I notice on every reboot the master volume is muted.

I already filed a bug report:

[https://bugs.launchpad.net/ubuntu/+bug/357833](https://bugs.launchpad.net/ubuntu/+bug/357833)

Just thought I'd share this in case anyone has the same thing happen, or if anyone might have some suggestion for me.

---

### Post by Languid Heap on 2009-04-08
After setting your volume controls where you like them, open a terminal and try ```
alsactl store
```
and see if that saves your volume settings after reboot.

That's the only idea I have...

Good Luck!

---

### Post by kansasnoob on 2009-04-09
No change!

I hadn't seen this since Intrepid. I've run thru all the troubleshooting stuff I can think of (referencing Markbuntu's and Psyke83's tutorials).

I also popped in my testing hard drive and see that this exists on a fresh install there also.

---

### Post by foxy123 on 2009-04-09
Got the same problem.

---

### Post by sports fan Matt on 2009-04-09
Strange kansasnoob, I installed updates as well and didnt see this behavior...

---

### Post by ayates on 2009-04-09
I added "alsactl restore" to rc.local as a workaround.

---

### Post by kansasnoob on 2009-04-09
Matt,

Having not seen more complaints about it I wonder if it might be hardware specific.

It's only an inconvenience at this point anyway. Otherwise pulse audio is working great!

---

### Post by foxy123 on 2009-04-09
i've got  Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

---

### Post by kansasnoob on 2009-04-09
> **ayates said:**
> I added "alsactl restore" to rc.local as a workaround.

Sorry to sound stupid, but could you explain that in more detail?

---

### Post by kansasnoob on 2009-04-09
> **foxy123 said:**
> i've got  Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Mine is VIA 8237 device - VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60).

Could I get you to add comment to my bug report?

[https://bugs.launchpad.net/ubuntu/+bug/357833](https://bugs.launchpad.net/ubuntu/+bug/357833)

---

### Post by kabloink on 2009-04-09
I am having the same problems with the master being muted. 

VIA 8237 also.

---

### Post by ayates on 2009-04-09
There is a script in /etc called rc.local that is executed by the init process. You can put commands in there that you want done at startup. Just add the line "alsactl restore" to it and it will be executed at startup. Add the line to rc.local,  unmute the sound, do the command "alsactl store", and reboot and see if that fixes it.

---

### Post by foxy123 on 2009-04-09
> **ayates said:**
> There is a script in /etc called rc.local that is executed by the init process. You can put commands in there that you want done at startup. Just add the line "alsactl restore" to it and it will be executed at startup. Add the line to rc.local,  unmute the sound, do the command "alsactl store", and reboot and see if that fixes it.

I have tried to do "alsactl store". If I try as it is it gives me that:
> ~$ alsactl store
alsactl: save_state:1541: Cannot open /var/lib/alsa/asound.state for writing: Permission denied


if I do it with sudo then:
> $ sudo alsactl store
E: core-util.c: [COLOR="Red"]Home directory /home/alex not ours.[/COLOR]


red is the original colour of the message...

---

### Post by ayates on 2009-04-09
Definitely some kind of permission issue. Are you a member of the "audio" group?

---

### Post by foxy123 on 2009-04-09
> **ayates said:**
> Definitely some kind of permission issue. Are you a member of the "audio" group?
yes I am...

> ~$ groups foxy
foxy adm dialout fax cdrom tape audio dip video plugdev fuse lpadmin netdev admin sambashare


---

### Post by kansasnoob on 2009-04-09
Identical behavior here Foxy!

---

### Post by foxy123 on 2009-04-18
I have manually opened and saved the file: /var/lib/alsa/asound.state
 and it fixed the problem for now.

**[COLOR="Red"]actually not, sorry...[/COLOR]**

---

### Post by kamereon on 2009-04-20
Same problem here on Ubuntu Jaunty_x64. Master vol. muted on every reboot. (HDA Nvidia ALC 883)
I also have a Netbook with Xubuntu Jaunty (32-Bit), which doesn't have this Problem.

I am member of the group audio, but ***alsactl store*** says *alsactl: save_state:1541: Cannot open /var/lib/alsa/asound.state for writing: Permission denied*
(The File *asound.state* is *-rw-r--r--* on both machines [img]http://www.boxhamsters.net/smilies/icon_kratz.gif[/img])

_Edit:_
***sudo** alsactl store* seems to have solved the problem for me. At least for the past three reboots. Will keep an eye on this...

---

### Post by kansasnoob on 2009-04-21
Sorry, I've been busy, but I've noticed this problem only exists for me if I'm using gnome-stracciatella-session.

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

I added that info to the bug report, but no reply as of yet.

---

### Post by FuturePilot on 2009-04-21
I had the same problem on one of my computers. I manually did a
```
sudo alsactl store
``` and it hasn't happened since.

---

### Post by philinux on 2009-04-21
I had this an GF's lappy. Went to sys>prefs>sound and set everythin to pulse instead of auto detect. This solved it. My desktop was already set this way.

---

### Post by kamereon on 2009-04-22
I don't get it. After I did ```
sudo alsactl store
``` the problem wouldn't appear for two days. Now it has returned, though. 
So actually, it is not solved for me after all...

---

