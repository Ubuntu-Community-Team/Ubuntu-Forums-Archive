---
title: "Latest x-org breaks on ATI Cards?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vertexoflife on 2008-10-08
I updates yesterday, to the newest X.org and linux kernel, and today when I restarted, ubuntu forces safe-graphics mode.

I will attach the log to this post.

I'm also trying to possibly install the restricted ATI driver, but gtk-jockey continues to crash repeatedly when i try to install it. What is the name of the ati driver, maybe I can install it through terminal?

This is Intrepid Beta, btw, though I beleive this is an X.Org problem.

---

### Post by Titan8990 on 2008-10-08
Easiest way is Envyng and I recommend it to all ATI and Nvidia users.


sudo apt-get install envyng-gtk


Envy will download and install your ATI drivers as well as write your xorg.conf for you. After it is installed you can find it under Applications -> System Tools

---

### Post by vertexoflife on 2008-10-08
> **Titan8990 said:**
> Easiest way is Envyng and I recommend it to all ATI and Nvidia users.


sudo apt-get install envyng-gtk


Envy will download and install your ATI drivers as well as write your xorg.conf for you. After it is installed you can find it under Applications -> System Tools



Ah, yes, I tried envy. It require envyng-qt so I installed that, and that doesn't work either.
It spits out a broken package error.

I've installed  fglrx-kernel-source, so I will see if that works at all after a reboot.

---

### Post by phidia on 2008-10-08
Try > fix X maybe that will do the trick.

---

### Post by Titan8990 on 2008-10-08
Envyng-gtk does not require qt. In fact, install qt uninstalls the gtk version. They both do the same thing but use different GUI standards. Give the gtk version another go.



Edit for more info: 

QT: [http://en.wikipedia.org/wiki/Qt_(toolkit](http://en.wikipedia.org/wiki/Qt_(toolkit))

GTK: [http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)

---

### Post by Elfy on 2008-10-08
the gtk version is for gnome - if the op is kde then qt is needed, though the variant says ubuntu.

You'r likely to get things break with intrepid, my xorg runs at 40% of cpu at the moment. I've not looked in the intrepid forum but it's likely that others have the same problem if you have. [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by vertexoflife on 2008-10-08
> **Titan8990 said:**
> Envyng-gtk does not require qt. In fact, install qt uninstalls the gtk version. They both do the same thing but use different GUI standards. Give the gtk version another go.



Edit for more info: 

QT: [http://en.wikipedia.org/wiki/Qt_(toolkit](http://en.wikipedia.org/wiki/Qt_(toolkit))

GTK: [http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)

I get "GTK Version Not Ready, EnvyNG Requires QT Version":

b--an@b--an-desktop:~$ envyng-gtk
ERROR: Make sure that envyng-qt is installed

I do know the difference between Gnome and KDE, and I am in gnome, but EnvyNG says it requires the qt version:

b--an@b--an-desktop:~$ envyng 
ERROR: you need to provide a parameter:
   "-t" for the textual interface
   "-g" for the GTK frontend (Not yet available)
   "-k" for the QT4 frontend

---

### Post by vertexoflife on 2008-10-08
> **phidia said:**
> Try  maybe that will do the trick.

Is this snark? Fix isn't a command...

"b--an@b--an-desktop:~$ fix X 
bash: fix: command not found"

---

### Post by Titan8990 on 2008-10-08
Which version of Ubuntu are you using? 


Have not heard of the "fix x" command but if it did exist on other distros I would assume that it is similar to:


sudo dpkg-reconfigure xserver-xorg

---

### Post by Elfy on 2008-10-08
Reboot into recovery mode, when you reach the small menu - use the xfix option it will set it back and you will then need to reinstall the driver

---

### Post by overdrank on 2008-10-08
Moved :)

---

### Post by vertexoflife on 2008-10-08
> **Titan8990 said:**
> Which version of Ubuntu are you using? 


Have not heard of the "fix x" command but if it did exist on other distros I would assume that it is similar to:


sudo dpkg-reconfigure xserver-xorg


It doesn't seem to so anything to fix my problem, but I will try it and restart.

---

### Post by Titan8990 on 2008-10-08
I'm sorry, I should have given further instructions. You will want to close xserver prior to reconfiguring xorg:


sudo /etc/init.d/gdm stop


Then hit CTRL+ALT+F3

Login again and then run xorg reconfigure.

---

### Post by vertexoflife on 2008-10-08
> **Titan8990 said:**
> I'm sorry, I should have given further instructions. You will want to close xserver prior to reconfiguring xorg:


sudo /etc/init.d/gdm stop


Then hit CTRL+ALT+F3

Login again and then run xorg reconfigure.

Unfortunately no, I still get a failure and boot into bullteproof x.

I need to go to class, but I will return later in the evening, if nothing works out I'll reinstall.

---

### Post by Game_boy on 2008-10-08
The restricted ATI driver (any version) does NOT work with the latest X.org. You would have to downgrade to X.org 7.3.

---

### Post by vertexoflife on 2008-10-08
> **Game_boy said:**
> The restricted ATI driver (any version) does NOT work with the latest X.org. You would have to downgrade to X.org 7.3.

Now, how would I go about downgrading?

---

### Post by vertexoflife on 2008-10-08
bump, I just need to know how to downgrade X

---

### Post by UbuWu on 2008-10-08
Did you report a bug about it? Run this command to automatically include all needed files:

ubuntu-bug xserver-xorg-video-ati

---

### Post by forumache on 2008-10-08
As OP said, the current Catalyst drivers don't work with X.org 7.4
There are plans for the new drivers (this month) to support 7.4

So, wait a little bit longer, using vesa...

---

### Post by phidia on 2008-10-08
> **vertexoflife said:**
> Is this snark? Fix isn't a command...

"b--an@b--an-desktop:~$ fix X 
bash: fix: command not found"

No and since Hardy xorg has changed a lot.

"fix X" in that form is a command but it doesn't always work and I don't know why. 

Many of the staff recommend it and just today a dev said for future releases the dpkg command is not the correct official way to correct xserver problems.

It's an annoying problem to try to help on because the Ubuntu wiki does mention the changed xorg but there haven't been detailed updates there.

---

### Post by vertexoflife on 2008-10-08
> **forumache said:**
> As OP said, the current Catalyst drivers don't work with X.org 7.4
There are plans for the new drivers (this month) to support 7.4

So, wait a little bit longer, using vesa...

VESA doesn't work, FGLRX doesn't work, I have to use bulletproof X, low graphics mode, until I can downgrade to Xorg 7.3.

---

### Post by vertexoflife on 2008-10-08
> **UbuWu said:**
> Did you report a bug about it? Run this command to automatically include all needed files:

ubuntu-bug xserver-xorg-video-ati

Yes, relevant launchpad bug here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/280440](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/280440)

---

### Post by Aenima99x on 2008-10-08
> **vertexoflife said:**
> VESA doesn't work, FGLRX doesn't work, I have to use bulletproof X, low graphics mode, until I can downgrade to Xorg 7.3.

At least you can get some sort of display......I've tried everything and get NO display at all. ](*,)
Well I take that back, I get the loading display and then if I actually SSH into my machine and reboot it, I DO get the terminal display showing all the commands as it's rebooting....

---

### Post by inportb on 2008-10-08
Note that installing fglrx at this time also breaks the ati/radeon driver because it overwrites some files. I would:

1) completely remove fglrx, ati, radeon
2) install ati, radeon

There's nothing wrong with ati/radeon itself because people are using it just fine...

---

