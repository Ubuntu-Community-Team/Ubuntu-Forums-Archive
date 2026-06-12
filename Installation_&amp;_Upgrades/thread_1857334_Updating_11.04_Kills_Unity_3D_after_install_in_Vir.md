---
title: "Updating 11.04 Kills Unity 3D after install in VirtualBox"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by daeld on 2011-10-10
Hi guys!
I'm trying to install Ubuntu 11.04 using VirtualBox 4.1.4 in a MacBook Pro running OS X Lion.

I install in a VM with 3D acceleration and max video allocation enabled.

If I install with option to download all updates during install, then reboot, then install guest additions (from the VB CD or from the repos), then reboot again and I log-in and it will not get past that point (ie the session never starts).  Ubuntu Classic still works fine with full 3D acceleration (ie for games etc).

Alternatively, I install WITHOUT option to download updates during install, then reboot, install guest additions and reboot again.  Now Unity Works as if it were a native install.  I then update and Unity is broken again after reboot.

Currently I'm running 11.04 after installation without any updates, but I would like to update.

Alternatively, I could just wait for 11.10, which comes out later this week (although this might not be any better!)

I've tried searching the forums here and elsewhere and nobody seems to be talking about this.

Also, is there a way to automate the ritual log-in "killall -9 gnome-settings-daemon && gnome-settings-daemon && exit"?

Thanks for your help.

---

### Post by jackdale on 2011-10-13
It sounds like I have the same problem with my system.  I had Natty installed for a while working well with unity, but after an update one day I started having the same problem.

From memory, I think it was a kernel update.

So I gave up on Ubuntu for my macbook pro because none of the "fixes" worked for me.  I moved on to Fedora 15 (with Gnome 3).  This worked quite well.  Unfortunately a few weeks ago an update killed Gnome 3 in the same way as you describe for Ubuntu.  Again, I think it was a kernel update.

At this stage, I reckon it has something to do with the kernel and the mac version of VirtualBox.

I don't need linux on the mac, I just like to have it, so I've gone with PC-BSD just for fun, but my main computer still runs Natty and I'm loving it. :D

Good luck in finding the answer (at least I hope you have more luck than I had).  Still, like you say, 11.10 may fix it.

---

### Post by raja.genupula on 2011-10-13
[http://www.ubuntugeek.com/running-ubuntu-11-04-natty-unity-3d-on-virtualbox-4-x.html](http://www.ubuntugeek.com/running-ubuntu-11-04-natty-unity-3d-on-virtualbox-4-x.html)


may be this can help you

---

### Post by jackdale on 2011-10-14
> **raja.genupula said:**
> [http://www.ubuntugeek.com/running-ubuntu-11-04-natty-unity-3d-on-virtualbox-4-x.html](http://www.ubuntugeek.com/running-ubuntu-11-04-natty-unity-3d-on-virtualbox-4-x.html)


may be this can help you

That's just it, installing this 11.04 as per instructions works perfectly until I update the kernel (after which I could no longer log on to a unity session; it would just stop at the wallpaper and nothing else would happen).  I gave up on it a long time ago, but was surprised that the same thing happened in Fedora 15 after a kernel update.

Edit 18-10-11
[STRIKE]At any rate, I just installed 11.10 and so far no problems.  I don't know about daeld, but I'm happy to move on.[/STRIKE]

Actually, I just realised that I was working in Unity 2D by accident.  When loading 3D, it has a problem with invisible windows.  See [this thread]("http://ubuntuforums.org/showthread.php?p=11361006#post11361006").

---

