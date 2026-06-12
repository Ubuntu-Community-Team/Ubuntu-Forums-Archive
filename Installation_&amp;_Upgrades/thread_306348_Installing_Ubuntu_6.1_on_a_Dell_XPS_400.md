---
title: "Installing Ubuntu 6.1 on a Dell XPS 400"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by Nitro249 on 2006-11-24
> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem.

What is this and how can I fix it.

---

### Post by Nitro249 on 2006-11-25
Anyone?

---

### Post by drphilngood on 2006-11-25
Enter the following into a terminal and post the results if you´d like for me to help you:

```
gedit /etc/X11/xorg.conf
```

Or, you can enter the following into a terminal and answer some questions(if you don´t know an answer, just hit ¨Enter¨) and probably fix it yourself:

```
sudo dpkg-reconfigure xserver-xorg
```

Here is a guide that will help you if you decide to fix it yourself:

[ Troubleshooting X]("http://www.psychocats.net/ubuntu/nox")

Good luck!

edit: I´m watching a game with friends but I´ll try to keep an eye on this thread.

---

### Post by Nitro249 on 2006-11-25
I type in gedit /ect/X11/xorg.conf and it said something about that it couldn't find it. So I got to thinking and maybe the "g" in gedit ain't supposed to be their. I took it out and it said I don't have  write permission for file.

---

### Post by meng on 2006-11-25
It's etc not ect

But in any case, the advice to use gedit is bad advice if you don't have an X server running! Therefore in order to post the contents of xorg.conf I would advise instead:
cat /etc/X11/xorg.conf

EXCEPT that you're unlikely to easily post the contents here if your X server is not running!!!!!

So, after all that, I advise you just do
sudo dpkg-reconfigure xserver-xorg

as first suggested.

---

### Post by Nitro249 on 2006-11-25
"sudo dpkg-reconfigure xserver-xorg"
This isn't working for me.



Heres what I get from this cat /etc/X11/xorg.conf
[[IMG]http://img82.imageshack.us/img82/828/oneca3.th.jpg[/IMG]](http://img82.imageshack.us/my.php?image=oneca3.jpg)



I have also followed this guide [http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")  
When I type "sudo /etc/init.d/gdm start" it says fail.

---

### Post by drphilngood on 2006-11-26
meng is the senior member.  Therefore, I will accept his authority and try to learn from him as he solves your problem.

Good luck!

---

### Post by Nitro249 on 2006-11-27
:cry:

---

### Post by doobit on 2006-11-27
The XPS 400 uses the Nvidia GForce 6800 board. Maybe you need the Nvidia drivers:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

[http://albertomilone.com/latest_nvidia_udsf_edgy.html#HOWTO:_Latest_NVIDIA_drivers](http://albertomilone.com/latest_nvidia_udsf_edgy.html#HOWTO:_Latest_NVIDIA_drivers)

---

### Post by Nitro249 on 2006-11-27
My has a Radeon X600 256mb

---

### Post by Nitro249 on 2006-11-28
Just want to let you guys know that I fix it.

I followed this.

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.

Thanks for all your help and time.

---

### Post by doobit on 2006-11-28
Thanks for the update!
It's always good to state your hardware right off the bat when you have a problem.
Glad you got it fixed and reported it. Where did you find the fix?

---

### Post by Nitro249 on 2006-11-28
> **doobit said:**
> 
It's always good to state your hardware right off the bat when you have a problem.


Will do next time.

> **doobit said:**
> Where did you find the fix?


Post #4
[http://www.ubuntuforums.org/showthread.php?t=190133]("http://www.ubuntuforums.org/showthread.php?t=190133")

I had to do this again when I first booted Ubuntu off the hard drive. It has been fine even since.

---

### Post by SilverZero on 2007-03-31
> **Nitro249 said:**
> Just want to let you guys know that I fix it.

I followed this.

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.

Thanks for all your help and time.

Why does that seem to work for everybody else, but me and my XPS400 with ATI X300 never have any luck?

UPDATE: I guess it does work, I just hadn't been using the latest installer direct from ATI. [I followed this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), and it worked great! Now to break it again!

---

