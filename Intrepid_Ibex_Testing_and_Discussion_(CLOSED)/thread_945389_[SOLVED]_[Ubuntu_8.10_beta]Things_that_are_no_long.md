---
title: "[SOLVED] [Ubuntu 8.10 beta]Things that are no longer working"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by suxenexus on 2008-10-12
Hi!  After upgrading to ubuntu intrepid beta, the scroll function of my laptop is no longer working.  Also the effects for compiz no longer works.

Can anyone help?

By the way, I installed the Intrepid beta on my Dell Inspiron 1420

---

### Post by wgrant on 2008-10-12
> **suxenexus said:**
> Hi!  After upgrading to ubuntu intrepid beta, the scroll function of my laptop is no longer working.  Also the effects for compiz no longer works.

Can anyone help?

By the way, I installed the Intrepid beta on my Dell Inspiron 1420

For the touchpad: remove all InputDevice sections from your xorg.conf and restart X.
For Compiz: are you using a fairly new ATI card? If so, you'll need fglrx for 3D acceleration, which AMD is yet to release.

---

### Post by suxenexus on 2008-10-12
> **wgrant said:**
> For the touchpad: remove all InputDevice sections from your xorg.conf and restart X.
I don't know where xorg.conf is.:(
> For Compiz: are you using a fairly new ATI card? If so, you'll need fglrx for 3D acceleration, which AMD is yet to release.
I'm currently using an intel graphics card which came with my laptop

---

### Post by wgrant on 2008-10-12
> **suxenexus said:**
> I don't know where xorg.conf is.:(

OK, download [this script](http://albertomilone.com/ubuntu/input/inputdevices) to some directory, open up a terminal, find that directory, and run "sudo python ./inputdevices". Log out and in, and things should be fine again.

---

### Post by orbish on 2008-10-12
> **suxenexus said:**
> I don't know where xorg.conf is.:(

you could use his script or 

alt+F2 (gives you run dialog)
type

gksu gedit /etc/X11/xorg.conf

explanation:  gksu (password prompt/give superuser access to) gedit (text editor) /etc/X11/xorg.conf (the location of the file)

edit following wgrant's directions

---

### Post by suxenexus on 2008-10-12
But what about my compiz effects?  Why doesn't it work?

PS: It worked after I updated.

> I don't know where xorg.conf is.
OK, download this script to some directory, open up a terminal, find that directory, and run "sudo python ./inputdevices". Log out and in, and things should be fine again.

Unfortunately, this didn't worked out

---

### Post by jlacroix on 2008-10-13
For me and many others, gamepads no longer work in Intrepid. No gaming for me. :(

---

### Post by the8thstar on 2008-10-13
Same problem with Compiz here : it's officially dead. And to boot, I have the lastest updates!!!

---

### Post by jerrylamos on 2008-10-13
Compiz doesn't work on IBM Thinkpad R31.  I had to apt-get remove compiz & compiz-core otherwise the Thinkpad hangs dead on desktop initialization.  Compiz works on Alpha 5 NOT UPDATED!! which is dual booted.

Flash sound doesn't work either.  It does on the Alpha 5.

Hmmm... RC time is approaching - notice the number of posts lately about things that are busted on Beta that used to work on Alpha.

Jerry

---

### Post by ngine13 on 2008-10-22
No 3d accelaration for me too! The nvidia driver is running although..

I'm running ubuntu 8.10 beta, after updating from 8.04..

Input devices are commented by the update process in xorg.conf.

Does anyone know what is the problem?

---

### Post by ngine13 on 2008-10-22
Also my graphic card (GPU) reports 10 degrees hotter than ubuntu 8.04.. :(

---

### Post by caryb on 2008-10-22
No 3d acceleration on Kubuntu either with Nvidia card in my T61 laptop


Cary

---

### Post by ngine13 on 2008-10-22
If you upgraded the system from 8.04 and installed the nvidia 177.80 drivers from nvidia site like i did.. you can check the following that solved my problem (i hope your too!) :

sudo ln -s /usr/lib/xorg/modules/extensions/libglx.so.177.80 /usr/lib/xorg/modules/libglx.so

Now everything is working fine and gpu temp dropped 10 degrees! :)

EDIT : Don't forget to restart the xserver! ;)

---

### Post by abeaulieu06 on 2008-10-28
ya I initially had problems running compiz on my dell d600 with the ati radeon 9000 on 8.04, it was a simple to fix though

now I upgrade to intrepid beta and at first my computer wouldnt boot it would stay at backround with just a cursor and hang, had to delete compiz and compiz-core for it to boot
now no 3D effects though...

hopefully they fix this problem soon an upgrade isnt usually supposed to cause a loss of functionality, this isnt vista here...

---

