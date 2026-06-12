---
title: "Ubuntu now only boots to command prompt"
date: 2008-12-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by puscifer919 on 2008-12-18
I'm running 9.04 and this morning when I turned on my computer, it booted to a command prompt. It was the typical terminal shell type prompt and I am not able to get to my desktop or anything.

Searching for help, I found someone that mentioned running 'startx' and 'sudo dpkg-reconfigure xserver-xorg' commands, but neither did the trick.

Running startx returns a bunch of info, part of which states "no screens found" or something to that affect.

I'm only mildly experienced with ubuntu, or linux in general, so what can I do?

Let me know if you need more info than this. Thanks

---

### Post by kanikilu on 2008-12-18
I'm not very good a troubleshooting X problems, but I think the first thing the "experts" are going to want to see are your xorg.conf and xorg.0.log files:

/etc/X11/xorg.conf
/var/log/Xorg.0.log

---

### Post by puscifer919 on 2008-12-18
> **kanikilu said:**
> I'm not very good a troubleshooting X problems, but I think the first thing the "experts" are going to want to see are your xorg.conf and xorg.0.log files:

/etc/X11/xorg.conf
/var/log/Xorg.0.log

How would I go about providing that information?

man <path> ?

---

### Post by kanikilu on 2008-12-18
I'm assuming you're posting this from another computer, right? In that case, it's going to be a little harder to get these files. The easiest way would be to use a flash drive to copy them and transfer to the working computer.

If that's not possible, do *nano /var/log/Xorg.0.log* and look for lines starting with (EE) which are errors. In nano, press CTRL+W, then type in "(EE)" (without quotes) and press enter. Press CTRL+W and then enter (it will remember the last search) to go to the next instance.

---

### Post by albinootje on 2008-12-18
> **puscifer919 said:**
> How would I go about providing that information?

man <path> ?

You can add them as attachments.

You're using Ubuntu 8.04 / Hardy Heron, but which video-card do you have ?
Did you use a proprietary video driver ?

Please post the output of
```

lspci

```
too.

And perhaps your / (or /tmp) partition is full.
That can be a cause for X not to start, because it needs to be able to write some temporary files in /tmp (and in your home-dir).
```

df -h

```

---

### Post by puscifer919 on 2008-12-18
> **albinootje said:**
> You're using Ubuntu 8.04 / Hardy Heron, but which video-card do you have ?
Did you use a proprietary video driver ?
It's 9.04 (jaunty) and I am using nvidia drivers (so yes, I believe).

Here are the outputs, I just took pics, hope they are clear enough!

/etc/X11/xorg.conf
[IMG]http://a3.s3.p.quickshareit.com/files/xorg833da.jpg[/IMG]

/var/log/Xorg.0.log
[IMG]http://a4.s3.p.quickshareit.com/files/xorgjpg6d74e.jpg[/IMG]
[IMG]http://a4.s3.p.quickshareit.com/files/xorg1jpgbab52.jpg[/IMG]
[IMG]http://a4.s3.p.quickshareit.com/files/xorg2jpg6686f.jpg[/IMG]

lspci
[IMG]http://a2.s3.p.quickshareit.com/files/lspci28d70.jpg[/IMG]

df -h
[IMG]http://a3.s3.p.quickshareit.com/files/dfha5617.jpg[/IMG]


Hope this helps!

EDIT: I see the two EE errors near the end of the /var/log/Xorg.0.log. "Failure to load module 'vesa'" and "No drivers available". Relevant?

---

### Post by albinootje on 2008-12-18
> **puscifer919 said:**
> It's 9.04 (jaunty) and I am using nvidia drivers (so yes, I believe).

Here are the outputs, I just took pics, hope they are clear enough!


Ah, sorry, i assumed you made a typo with 9.04.
That makes things totally different in my opinion.
Intrepid was released in october, and Jaunty is very fresh and in heavy development i assume. You can expect it to break after every update.

Is there a specific reason that you don't want to use 8.04 or 8.10 ?

---

### Post by puscifer919 on 2008-12-18
> **albinootje said:**
> Ah, sorry, i assumed you made a typo with 9.04.
That makes things totally different in my opinion.
Intrepid was released in october, and Jaunty is very fresh and in heavy development i assume. You can expect it to break after every update.

Is there a specific reason that you don't want to use 8.04 or 8.10 ?
No reason. I use 8.10 on my MacBook and I love it. I just went for Jaunty for kicks, I suppose.

---

### Post by oldos2er on 2008-12-18
> **puscifer919 said:**
> I'm running 9.04 and this morning when I turned on my computer, it booted to a command prompt. It was the typical terminal shell type prompt and I am not able to get to my desktop or anything.

Searching for help, I found someone that mentioned running 'startx' and 'sudo dpkg-reconfigure xserver-xorg' commands, but neither did the trick.

Running startx returns a bunch of info, part of which states "no screens found" or something to that affect.

I'm only mildly experienced with ubuntu, or linux in general, so what can I do?
  

 Why are you running alpha software? You've got to expect bugs.

---

### Post by puscifer919 on 2008-12-18
> **oldos2er said:**
> Why are you running alpha software? You've got to expect bugs.
Um. I think I answered this with my last post. No reason specifically. This is a personal computer with nothing important stored on it, and since 9.04 is available for download, I figured why not. After all, I am just using it to learn more about Ubuntu. It's no big deal to me if I have to fix problems with it, because thats a part of learning. I DO expect bugs, I also expect to receive help resolving them when I come here. Do you have anything helpful to contribute?


Anyways, to those who are interested in helping, do you think it is related to video drivers? And if so, how would I go about resolving this issue? If not, what else could be going on?

Thanks! :D

---

### Post by gsgleason on 2008-12-18
Looks like it's not finding a driver for your video card.  What vid card are you using?  Run lspci and look for your graphics card and paste here.

I see that you've already pasted it.  Sorry.

you have an nvidia card.  Lets try letting X configure itself first.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo Xorg -configure
(that should make a file xorg.conf.new in /root)
sudo Xorg -config /root/xorg.conf.new

see what happens.  If you get to an X server with just an X as a cursor, use ctrl+Alt+Backspace to kill X

also, you're going to want to be using the proprietary nvidia drivers, but the open source 'nv' driver should work for now.  If the new xorg config works, then
sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

---

### Post by puscifer919 on 2008-12-18
> **gsgleason said:**
> Looks like it's not finding a driver for your video card.  What vid card are you using?  Run lspci and look for your graphics card and paste here.
It is a nvidia 9800GT. I posted the lspci output below, but here it is again. Let me know what you think. :)

[IMG]http://a2.s3.p.quickshareit.com/files/lspci28d70.jpg[/IMG]

---

### Post by kanikilu on 2008-12-18
Again, I'll preface this with the fact that my X troubleshooting experience is limited, but have you tried reinstalling nvidia-glx? It seems like or xorg.conf file is not using the nvidia driver(?)

---

### Post by puscifer919 on 2008-12-18
> **kanikilu said:**
> Again, I'll preface this with the fact that my X troubleshooting experience is limited, but have you tried reinstalling nvidia-glx? It seems like or xorg.conf file is not using the nvidia driver(?)
You can pretty much rest assured that I have not tried anything but Google. 8)

How would I go about reinstalling nvidia-glx? I'm assuming there is a command I can run to do this? I'd guess 'sudo aptitude remove nvidia-glx' followed by 'sudo aptitude install nvidia-glx', but I'd probably be wayyy off.

---

### Post by gsgleason on 2008-12-18
Read my post I edited.  To see if you have any nvidia stuff installed:

dpkg -l|grep nvidia

Here is what I have on a machine with an nvidia card:
gsg@greglap ~
$ dpkg -l|grep nvidia
ii  nvidia-173-kernel-source                  173.14.12-1-0ubuntu4                    NVIDIA binary kernel module source
ii  nvidia-173-modaliases                     173.14.12-1-0ubuntu4                    Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-modaliases                     177.80-0ubuntu2                         Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                      71.86.04-0ubuntu10                      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                      96.43.09-0ubuntu1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                             0.2.4                                   Find obsolete NVIDIA drivers
ii  nvidia-glx-173                            173.14.12-1-0ubuntu4                    NVIDIA binary Xorg driver
rc  nvidia-glx-177                            177.80-0ubuntu2                         NVIDIA binary Xorg driver
ii  nvidia-settings                           177.78-0ubuntu2.1                       Tool of configuring the NVIDIA graphics driv

ii means it's installed.  I'm running nvidia-glx-173

---

### Post by donkyhotay on 2008-12-18
The log reports an attempt to default to vesa after failing nvidia which *should* work (with all the limitations vesa has). Before you even try reinstalling nvidia drivers I would configure your xorg.conf file for vesa only and see if that launches. This will determine if the problem is actually due to the driver or a bigger problem with X server itself (which is my suspicion).

---

### Post by decoherence on 2008-12-18
Running binary drivers on alpha software. God love you! You are either a trooper or a masochist ;)

If you're looking for help with pre-release versions, you might have better luck (and better reception) in the appropriate section of the forum.

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

Good luck! :)

---

### Post by albinootje on 2008-12-18
> **puscifer919 said:**
> Um. I think I answered this with my last post. No reason specifically. This is a personal computer with nothing important stored on it, and since 9.04 is available for download, I figured why not. After all, I am just using it to learn more about Ubuntu. It's no big deal to me if I have to fix problems with it, because thats a part of learning. I DO expect bugs, I also expect to receive help resolving them when I come here. Do you have anything helpful to contribute?


Anyways, to those who are interested in helping, do you think it is related to video drivers? And if so, how would I go about resolving this issue? If not, what else could be going on?


In my opinion it's a bit comparable with running plain Debian Unstable.
(I'm not talking about some apt-pinning mix of Debian Testing and Debian Unstable for example.)

You are basically on your own, or you join the development-scheme actively and talk to other people who also use a development version and therefore help to improve the new software collectively.

I think [http://launchpad.net](http://launchpad.net) would be the perfect place to do that.
Just my 0.02E :)

---

### Post by gsgleason on 2008-12-18
I'm not giving up on you, puscifer919.

Lets see if you have any nvidia kernel mods available:

find /lib/modules/ -name nvidia.ko

---

### Post by oldos2er on 2008-12-18
"Do you have anything helpful to contribute?"

 Yes, report Jaunty bugs to [https://launchpad.net/ubuntu/jaunty/](https://launchpad.net/ubuntu/jaunty/) . It's difficult to imagine a newbie wanting to do this tho'. If it were me, I wouldn't know the difference between a bug and my own ignorance of Linux (and in a lot of cases I still don't).

---

### Post by puscifer919 on 2008-12-18
> **oldos2er said:**
> If it were me, I wouldn't know the difference between a bug and my own ignorance of Linux (and in a lot of cases I still don't).
I'm guessing this it a little of both. :)

gsgleason is helping a lot via AIM. I'll post back here with a resolution if we find one. Thanks!

---

### Post by puscifer919 on 2008-12-18
Reinstalling xserver-xorg allows me to get back to my desktop, but I can't seem to get nvidia's ver 173 or 177 drivers installed without the issue reoccuring after a reboot. My guess is a conflict between nvidia's drivers and one of the updates from the past few days.

Going back to 8.10. Thanks for the help everyone. :)

---

### Post by puscifer919 on 2008-12-19
Interesting bit of info:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410)

---

