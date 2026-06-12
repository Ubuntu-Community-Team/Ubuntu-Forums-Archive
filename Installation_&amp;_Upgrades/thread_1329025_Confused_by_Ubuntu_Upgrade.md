---
title: "Confused by Ubuntu Upgrade"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by GaretJax on 2009-11-17
On my work computer, I was running Ubuntu 9.04 and through the Update Manager, I clicked the Upgrade button and after about an hour I was running the new Ubuntu 9.10 version.

Okay, so now with my home computer.  Same scenario.  I was running Ubuntu 9.04 and through the Update Manager, I clicked the Upgrade button and after about an hour I was running the new--Xfce4 9.10!?!?

What the heck happened? How can I switch to switch to Ubuntu 9.10 without formatting/reinstalling?

---

### Post by herbertportillo on 2009-11-17
You had Ubuntu 9.04 and it upgraded you to Xubuntu 9.10? Hmm, that's weird.

Open a terminal and type "sudo apt-get install ubuntu-desktop". You may have to download lots of dependencies, but what it'll do is it'll let you switch from the Xfce desktop environment to GNOME at startup.

If I'm wrong, someone please correct me. If anyone else has a better idea, help our friend out. I'm fairly new to Ubuntu as well. I just figured that underneath the hood, they're all the same. The only difference between the *buntu's are the desktop environments.

---

### Post by GaretJax on 2009-11-17
Okay, so I ran your command and it install the ubuntu-desktop package.  It was actually so quick that I didn't feel like anything happened at all.  When I ran it a second time, it said that it was already installed.  Well now that it is installed, I don't know how to switch over to it.  You said it would ask me at startup, but I restarted my computer and saw no such option.

I blame Mythbuntu on this mishap.  When the computer starts and just before I get to the Xubuntu logon screen, I see a Mythbuntu screen with a scrolling bar as if something is loading, then I see it again, then I get the logon screen.  This never happened before when I was on 9.04.  I'm actually not going to use MythTV anymore so I will remove it and see what happens.

---

### Post by GaretJax on 2009-11-17
I removed the Mythbuntu but the computer still boots into Xubuntu.  I figure that if I cannot resolve this by the end of the day then I will be reinstalling Ubuntu.  Not sure what else to do.

---

### Post by drs305 on 2009-11-17
Instead of shutting down or restarting, from the same icon try switching users. Choose your Ubuntu user and at the bottom of the screen see if you have a "Sessions" box. If so, choose Ubuntu and you should be taken to the Ubuntu desktop.

---

### Post by audiomick on 2009-11-17
Hallo. I can't have a look to check this, as I am not at home right now, but up till 9.04 you could choose which of the installed desktops you want to boot into at log-in. I can't see why that would have disappeared. It will probably be a drop-down at the bottom of the log in screen. you will also probably be able to tell it that this is what you want to do every time.
I am a bit vague, because I haven't looked at this since I updated.

---

### Post by GaretJax on 2009-11-17
Okay, drs305 and audiomick are on the right track. :popcorn:

At the logon screen, it won't show me the session options until I choose to login with my user name.  Then the options appear at the bottom.  In the sessions list I see: failsafe gnome, gnome, mythbuntu session, xfce session, and xterm.

I chose gnome and the desktop looks the way I want it to, but the boot sequence before the logon screen still shows the mythbuntu loading sreen.  I prefer that the boot up screen shows the standard screen that comes with Ubuntu 9.10.  I think it looks better.  How can I change this?

---

### Post by drs305 on 2009-11-18
> **GaretJax said:**
> I chose gnome and the desktop looks the way I want it to, but the boot sequence before the logon screen still shows the mythbuntu loading sreen.  I prefer that the boot up screen shows the standard screen that comes with Ubuntu 9.10.  I think it looks better.  How can I change this?

I haven't tried this in Karmic with the xsplash/usplash udpates, but here is how it used to be done.

Open Synaptic and make sure ubuntu-artwork (and perhaps ubuntu-xsplash-artwork) are installed. Then run this command to choose which artwork to view:
```
sudo update-alternatives --config usplash-artwork.so

```

It should list the artwork available for selection and allow you to chose the one you want by entering the appropriate number. The selected artwork should appear on the next boot.

---

### Post by slakkie on 2009-11-18
You could try to remove xubuntu and mythbuntu:

```

sudo aptitude markauto $(apt-cache depends xubuntu-desktop | egrep -v "Conflict|Replaces" | sed -e 's/[<>]//g' | tail -n +2| awk '{print $NF}')
sudo aptitude markauto $(apt-cache depends mythbuntu-desktop | egrep -v "Conflict|Replaces" | sed -e 's/[<>]//g' | tail -n +2| awk '{print $NF}')

sudo aptitude remove xubuntu-desktop mythbuntu-desktop


```

Best of luck.

---

