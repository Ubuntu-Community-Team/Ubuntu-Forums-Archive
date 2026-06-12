---
title: "Help Please.  Natty new install hangs and crashes"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by mebunto on 2011-04-29
Well, I'm a bit disappointed really so I'm looking for some friendly advice.
I have a Sandy Bridge mb, which is excellent, and I've been waiting patiently for Natty because of its support for the new chipset.
I had a complete nightmare with installation and eventually managed to install Kubuntu Natty from the alternate CD (not USB) onto a brand new hard disk.  Success was only short-lived as the new installation keeps crashing.  Either it hangs or it triggers a reboot so it isn't usable.

What should I do?

Thanks

---

### Post by mörgæs on 2011-04-29
How does it work if you install Ubuntu rather than Kubuntu?

---

### Post by mebunto on 2011-04-30
I was trying the Ubuntu installation last night, as I started the thread.  It's installed however when I boot it hangs at the Ubuntu splash screen and goes no further.

I really am an "Ubuntu convert" having used it pretty seriously for a year - but the frustrating technical issues that sometimes have no resolution really make me despondent.

---

### Post by manzdagratiano on 2011-04-30
I have had a similar issue, but not after the installation, but during the installation itself. What worked for me was to use the 64-bit install instead of 32-bit one, and it proceeded like a charm. I suggest you try that.

---

### Post by mebunto on 2011-05-01
Thanks. I'm definitely using the amd64 iso images.  The only successful installation I managed was to use the alternate image and install from CD-ROM.  But that resulted in a system that hangs and crashed.  Since then I've tried numerous installations and currently they are just not getting through to completion.  It's really frustrating.

Well, an update.  I downloaded the DVD version of the installer.  Like all the other versions, it too gets all the way to Select and Install Software.  It proceeds through the 913 packages then stops saying "installation step failed ... run the failing item again ... or choose something else".

I'll try some more.

---

### Post by mebunto on 2011-05-01
Anyone?

---

### Post by perspectoff on 2011-05-01
There's a thread 

[http://ubuntuforums.org/showthread.php?p=10747748](http://ubuntuforums.org/showthread.php?p=10747748)

that suggests that the Grub2 can sometimes be the problem, especially if you're hanging at the splash screen stage.

It was with me.

I edited the Grub2 settings as in that thread (from the command line login) and then everything worked. YMMV.

Oops, I didn't read the entire thread. The problem is during installation. Never mind.

That has happened to me many times over the years. Usually I just got a bad burn somehow.

---

### Post by mebunto on 2011-05-02
Well, another angle.... I installed 11.04 server successfully - then did the following:
```
sudo apt-get update
sudo apt-get upgrade
apt-get install kubuntu-desktop
sudo kubuntu-desktop
```
which did give me the Kubuntu login.  I logged in successfully however, as soon as I tried to run one of the menu selections, Kubuntu crashed and the machine restarted.

Where do I go from here?  Luckily my 10.04 installation is on a different hard disk so will I be able to find any kind of crash information on the 11.04 disk?  How?

---

### Post by mebunto on 2011-05-03
Can anyone shed some light on this?

---

### Post by mebunto on 2011-05-04
What I have noticed is that some updates to Natty have come through - but Natty's still crashing so I have to use the recovery console to do the update then try again.  Still no luck though.  Has anyone out there got sandy bridge working with Natty?

---

### Post by idef1x on 2011-05-08
I just installed freshly Natty on a 64 bit machine (HP HDX-16) and most of the times when i want to resize a konsole window it crashes. 
I'm installing ubuntu-desktop now to see if that makes any difference. If not....it's back to maverick again.
On another fresh Natty install i don't have these problems however.
Maybe it's the video card (Nvidia in my case)...don't know...
If anyone has some suggestions please let us know cause this is not usable.

Or it's the 64-bit version? I hear more bad things about it although it ran fine with Maverick

---

### Post by mebunto on 2011-06-16
Well, I did a fresh install some time ago and I've been downloading all updates since then.  The system is stable and runs iscsi to a DROBO, Mediatomb and acts as the home DLNA and file server.  I'm also running two monitors, although there are still some quirks with the Xorg drivers and various (unimportant) packages are prone to crashing.

---

