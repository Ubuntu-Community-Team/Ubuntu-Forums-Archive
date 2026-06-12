---
title: "VMWare Host, kernel 2.6.31, keyboard/mouse issues"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dabl on 2009-08-09
I installed the daily build of Kubuntu 9.10 Alpha on Friday, and except for having my butt kicked by Grub 2, it is all working fine, including audio, video, compiz, etc. I found a post on Grub 2 on this forum that might help with that issue.

However, VMWare Player 2.5.2, having been patched and built correctly for the 2.6.31 kernel, isn't taking keyboard or mouse input correctly. Ctrl-G gets me one shot at logging in to the guest OS, but then the keyboard and mouse are permanently disconnected from the guest OS. Plus, the availability of shift characters and F-keys and other stuff is hosed in the host (9.10), including Ctrl-Alt-F1, so you're pretty much facing a shutdown/reboot. There are a few posts on the vmware community forum here:

[http://communities.vmware.com/thread/221724;jsessionid=F8B75C8A632778993FEA73B293CD7F24?start=0&tstart=0](http://communities.vmware.com/thread/221724;jsessionid=F8B75C8A632778993FEA73B293CD7F24?start=0&tstart=0)

but no sign of a fix.

Any ideas or help?

---

### Post by wayne_cat on 2009-08-09
> **dabl said:**
> I installed the daily build of Kubuntu 9.10 Alpha on Friday, and except for having my butt kicked by Grub 2, it is all working fine, including audio, video, compiz, etc. I found a post on Grub 2 on this forum that might help with that issue.

However, VMWare Player 2.5.2, having been patched and built correctly for the 2.6.31 kernel, isn't taking keyboard or mouse input correctly. Ctrl-G gets me one shot at logging in to the guest OS, but then the keyboard and mouse are permanently disconnected from the guest OS. Plus, the availability of shift characters and F-keys and other stuff is hosed in the host (9.10), including Ctrl-Alt-F1, so you're pretty much facing a shutdown/reboot. There are a few posts on the vmware community forum here:

[http://communities.vmware.com/thread/221724;jsessionid=F8B75C8A632778993FEA73B293CD7F24?start=0&tstart=0](http://communities.vmware.com/thread/221724;jsessionid=F8B75C8A632778993FEA73B293CD7F24?start=0&tstart=0)

but no sign of a fix.

Any ideas or help?

There is no solution for this problem at the moment.

I'm using VNC to install my virtual machines ... see also:

[http://ubuntuforums.org/showthread.php?t=1175069&highlight=vmware](http://ubuntuforums.org/showthread.php?t=1175069&highlight=vmware)

---

### Post by dabl on 2009-08-09
OK, thanks Wayne.

"Vee Vait ...."   :)

---

### Post by ziljian on 2009-08-21
VMPlayer 2.5.3 was released today and installs/compiles cleanly on 9.10 with kernel 2.6.31.  Unfortunately, I still can't grab focus with my mouse and neither keyboard or mouse work after grabbing focus with Ctrl-G.  I'm using a wireless Logitech USB mouse and keyboard ..

---

### Post by dabl on 2009-08-22
Thanks, ziljian.  I installed Player 2.5.3 today, on kubuntu 9.10, and the problem is much better, but not solved.  I cannot get focus on the guest with the mouse, but Ctrl-G lets me log into the Win XP guest, and then Ctrl-G will get me a cursor for long enough to start programs and shut down.  It seems that the keyboard actually works correctly, as long as I can hold the focus on the guest.  But it jumps back to the host pretty quickly.

The other good news is, the host keyboard and mouse functions now appear to remain intact during and after the VMWare session, so that's progress too.

---

### Post by unclecameron on 2009-09-03
I found the same problem, it seems the mouse is more likely to be grabbed in certain areas of the screen (lower left) and very likely to be lost near the edges, so mostly I hit ctrl+G a bunch of times and use tab/enter and it works long enough to use Outlook/Exchange.

---

### Post by slakkie on 2009-09-03
Hi, run setxkbmap on your host pc. Fixes the glitch.

VMWare is only supported up to 8.04 btw.

I also have the following configfile:

```

cat ~/.vmware/config
xkeymap.nokeycodeMap = true

```

Since it my keyboard also b0rked inside the vm.

---

### Post by unclecameron on 2009-09-04
hmm, setxkbmap didn't seem to fix the mouse capture on my box...

---

### Post by dabl on 2009-09-05
> **slakkie said:**
> 

```

cat ~/.vmware/config
xkeymap.nokeycodeMap = true

```



Nope -- doesn't help here.

---

### Post by virx on 2009-09-06
Same Here At Karmic (2.6.31-9-generic) with Vmware Player 2.5.3 @ Logitech wireless mouse.

---

### Post by oakgrove on 2009-09-11
I'm running 9.10 alpha 5 and have an XP vm with the same mouse issue.  However, if I put the virtual machine in unity mode, the mouse works great.  This may help you.

---

### Post by dabl on 2009-09-13
> **oakgrove said:**
> I'm running 9.10 alpha 5 and have an XP vm with the same mouse issue.  However, if I put the virtual machine in unity mode, the mouse works great.  This may help you.

Aha!

Well, this was just the hint I needed -- thank you oakgrove!

My Win XP guest VM is a couple of years old.  When I attempted to set it to Unity mode, it puked up an error about "your version of VMWare Tools does not support Unity mode". Hmmmmmmmm.

Google took me here:  [http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

The version of VMWare Workstation in the instruction is off -- the one I downloaded today is VMware-Workstation-6.5.3-185404.x86_64.bundle.  So, adjusting for the version number difference, the instruction in the link works to get the Windows ISO file out of the workstation bundle.  I burned it to a CD, fiddled my balky Win XP guest into loading the CD, and then learned that the new tools will not install over the old tools -- the old tools first must be removed via "Add/Remove Programs".  So, with a Ctrl-G every 10 seconds and keyboard-only maneuvering, I removed the old tools, restarted the CD, ran the installer, got the new tools installed, restarted the VM, set it to Unity mode, and VOILA she's working that way, on Kubuntu Karmic:

```
dabl@karmic:~$ uname -a
Linux karmic 2.6.31-10-generic #32-Ubuntu SMP Thu Sep 10 23:29:56 UTC 2009 x86_64 GNU/Linux
```

Thanks again!  :D

---

### Post by krusir on 2009-09-16
ha....found a workaround.....  If you have VM workstation, turn on the VNC server.  ( allow remote access/control )

then use VNC client (vinagre) to use the VM .... works perfect.

---

### Post by sfarestam on 2009-09-18
xtightvncviewer seems to be more responsive than vinagre.

---

### Post by Starks on 2009-09-18
That's quite a brilliant if not a roundabout way of doing things.

---

### Post by Craig Prevallet on 2009-09-21
See:

[http://communities.vmware.com/thread/228636;jsessionid=35DA3511455FDEA59DEA320C6DB0AEC9?start=15&tstart=0](http://communities.vmware.com/thread/228636;jsessionid=35DA3511455FDEA59DEA320C6DB0AEC9?start=15&tstart=0)

In summary, apparently the issue is the newer version of GTK+. The somewhat good news is it looks like at least VMware 6.5.3 comes with it's own version of GTK+. There's a wrapper script called wrapper-gtk24.sh with the distribution. According to this script, if you set the environment variable:
 
 export VMWARE_USE_SHIPPED_GTK=yes
 or
 export VMWARE_USE_SHIPPED_GTK=force
 
 before launching VMware, it seems to work just fine.

---

### Post by ayates on 2009-09-21
Thanks Craig Prevallet.

I'd been following another thead on the Vmware forums waiting for a fix,
but this one fixes it.

---

### Post by unclecameron on 2009-09-21
Doesn't work for me still...the only thing that works is unity...sorta.

---

### Post by dabl on 2009-09-21
This fixed it - unity mode no longer required:

[http://communities.vmware.com/message/1367391#1367391](http://communities.vmware.com/message/1367391#1367391)


The fix: "I've added a line "export VMWARE_USE_SHIPPED_GTK=force" to /etc/vmware/bootstrap, the grabbing/ungrabbing problem is gone now."

---

### Post by unclecameron on 2009-09-22
yep, that worked, causing much happiness, since I use VMware every day for Photoshop, very difficult to use without the mouse

---

