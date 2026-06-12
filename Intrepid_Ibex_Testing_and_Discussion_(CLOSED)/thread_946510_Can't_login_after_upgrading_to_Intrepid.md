---
title: "Can't login after upgrading to Intrepid"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Aikon- on 2008-10-13
I recently upgraded my Thinkpad T61 from 8.04 to the 8.10 beta via the update manager. When I boot, the gdm comes up fine, but I can't actually login.

When I give my username and password, the gdm disappears and the screen goes to my gnome background colour, and after a few seconds the mouse pointer changes to the one set in my theme, but then after that, nothing happens. It just sits there, not using the hard drive or anything. So, the desktop isn't loading, gnome-panel isn't loading, etc, Alt-F2 does nothing, and so on and so forth.

Any suggestions?

Aikon-

---

### Post by klamari on 2008-10-13
After all I have been trying to get my system running and with all the other people I met in various fora I can only hope you are not using a Nvidia GU in your Thinkpad T61.
Some more details on the contents of your "Thinktank" might be helpful.

Greetings

Martin

---

### Post by Aikon- on 2008-10-13
Thinkpad T61 with nVidia Quadro NVS140M, Intel 4965AGN wireless.

So, Intrepid isn't playing nicely with nVidia GPUs? Oy =/

Except for not being able to suspend, Hardy was working fine.

---

### Post by Aikon- on 2008-10-13
Note: I just tried KDE4 and it loads fine, so it's a GNOME issue somewhere =(

---

### Post by klamari on 2008-10-13
I have KDE4 installed and cannot get it running on a proprietary Nvidia card (meaning 173 or the new 177 driver), using the open nv driver without 3D support everything seems to work, as soon as a proprietary driver is installed I cannot get into the GUI and the machine hangs trying to run kdm. 
What driver are (and/or were you using in Hardy) for your GU? (meaning which is installed and running after upgrade?
what is the output of using
> dkms status  ?

Funny you have no problem with KDE4, wish it were so on my end....

Greetings

---

### Post by Anduu on 2008-10-13
I had the same issue when I upgraded.This worked for me...

At the login screen click on sessions and select Gnome.
Enter username and password and select "make default" when prompted.

---

### Post by Aikon- on 2008-10-13
> **klamari said:**
> I have KDE4 installed and cannot get it running on a proprietary Nvidia card (meaning 173 or the new 177 driver), using the open nv driver without 3D support everything seems to work, as soon as a proprietary driver is installed I cannot get into the GUI and the machine hangs trying to run kdm. 
What driver are (and/or were you using in Hardy) for your GU? (meaning which is installed and running after upgrade?
what is the output of using
  ?

Funny you have no problem with KDE4, wish it were so on my end....

Greetings

```
sarmitage@asuka:~$ dkms status
nvidia, 177.80, 2.6.27-7-generic, x86_64: installed 
nvidia, 177.80, 2.6.24-21-generic, x86_64: installed (original_module exists)

```

---

### Post by klamari on 2008-10-13
Lucky you, seems to be in place, I think I remember someone mentioned a similar thing about the screen turning funny and the mouse getting blocked in one of the earlier threads, I will try to find it again, maybe thats where you belong to.....

---

### Post by klamari on 2008-10-13
Hi, try those threads:

[http://ubuntuforums.org/showthread.php?t=945953](http://ubuntuforums.org/showthread.php?t=945953)

[http://ubuntuforums.org/showthread.php?t=945690](http://ubuntuforums.org/showthread.php?t=945690)

[http://ubuntuforums.org/showthread.php?t=945704](http://ubuntuforums.org/showthread.php?t=945704)

seem to be similar issues....isnt it fun to try a beta release and get all those bugs?

---

### Post by thuja.forevergreen on 2008-10-13
I have the same problem.  Booted after install and it takes me to the gnome username screen but when I log in, it just shows the orange background.  Nothing will load.  I can access the terminal.  I have an ibm t43p laptop w/ 64 MB ATI Mobility Radeon X300.

---

### Post by klamari on 2008-10-13
>  Unhappy  Re: Warning 8.10 is too buggy even at Beta to be usable

Beta is broken for IBM Thinkpad R31. Compiz is so broke it hangs where the first Gnome desktop should display. I removed Compiz, then Gnome came up.


Looking at the general run of posts lately, seems to me more things are broken than at equivalent time on Gutsy & Hardy. I don't have statistics.

Jerry


Seems to be a common issue, maybe you should look wether there is allready a bugreport, either you start a new one or confirm it

Martin

---

### Post by exXP on 2008-10-13
I have had similar problems both with an Alpha and,today, with the RC-beta. In both cases I started the live CD mode, got as far as the Ubuntu theme music and then the screen went black leaving only a movable mouse-pointer.  I have a 386 Intel system with an the on-board video. I shall be reluctant to up-grade to Intrepid if this problem persists.
exXP (and not going back)

---

### Post by jerrylamos on 2008-10-13
On my Thinkpad R31, Compiz hangs it up dead when the Gnome desktop should load.  See Launchpad bug 277344.

My workaround is:

Boot in Recovery mode.
Choose command line prompt.

sudo apt-get remove compiz
sudo apt-get remove compiz-core

Reboot and then it runs.  After yesterday's update I had to do it again.
Do note it may come up into a command line login prompt instead of a desktop.  Log in then do 

sudo startx

By the way, Ubuntu & Kubuntu run fine, I assume they either don't use compiz or don't use it like Gnome does.

I did do an install of xce4 on Ubuntu to give me an alternate desktop.
To choose that desktop, I do a 
sudo startxfce4

Oh, yes, Alpha 5 NOT UPDATED!! runs without these problems.  Alpha 6 and Beta fail.

Jerry

---

### Post by exXP on 2008-10-13
I tried the Live CD in Safe Graphics mode with the same result except that I don't even get the pointer!  Just to be sure my system isn't at fault I tried the Live CD's of Knoppix and OpenSuse.  They worked fine.
ExXP (and not going back)

---

### Post by Enigmatic on 2008-10-13
I was not able to select a "Gnome" session, just failsafe Gnome which didn't work. I noticed that gnome-session was not installed (somehow removed?) so I installed it, and then I could select Gnome and get to my desktop.

---

### Post by Aikon- on 2008-10-15
> **jerrylamos said:**
> On my Thinkpad R31, Compiz hangs it up dead when the Gnome desktop should load.  See Launchpad bug 277344.

My workaround is:

Boot in Recovery mode.
Choose command line prompt.

sudo apt-get remove compiz
sudo apt-get remove compiz-core

Reboot and then it runs.  After yesterday's update I had to do it again.
Do note it may come up into a command line login prompt instead of a desktop.  Log in then do 

sudo startx

By the way, Ubuntu & Kubuntu run fine, I assume they either don't use compiz or don't use it like Gnome does.

I did do an install of xce4 on Ubuntu to give me an alternate desktop.
To choose that desktop, I do a 
sudo startxfce4

Oh, yes, Alpha 5 NOT UPDATED!! runs without these problems.  Alpha 6 and Beta fail.

Jerry

I also found this workaround somewhere (re-install compiz-core) and it seems to have worked. Not sure what happened to send it that way though...

Aikon-

---

### Post by jerrylamos on 2008-10-15
> **klamari said:**
> Seems to be a common issue, maybe you should look wether there is allready a bugreport, either you start a new one or confirm it

Martin

Bug report is 277344.  Looking at the forums there are any number which seem to wind up with a black screen like I do, in my case on IBM Thinkpad R31 Intel Celeron 32 bit Intel graphics. Last time it would run Ubuntu "out of the box" was initial Alpha 5.  Xubuntu Beta & Kubuntu Beta boot O.K., as does using xfce4 package installed on Ubuntu instead of Gnome.

Booting in recovery mode then sudo apt-get remove compiz & sudo apt-get remove compiz-core fix it for me on original installed beta.  CD Live fails to same black screen.  There isn't any boot option to not use compiz, so only way to get CD Live example 20081014 to run is to Ctrl-Alt-F1, sudo apt-get remove compiz & sudo apt-get remove compiz-core just after Gnome is being initialized but desktop hasn't loaded just yet.

Jerry

---

### Post by jbernardo on 2008-10-16
For those with NVidia GPUs and KDE4, disabling BackingStore in xorg.conf fixed it for me.

---

### Post by Yoshiman007 on 2008-10-18
I un-installed compiz when all i got was the orange screen with a mouse cursor, but that did not work. I then clicked the options menu and switched to a Gnome session (which i should have been using anyways) and made it default. This worked for whatever reason, and I am now re-installing compiz...

---

