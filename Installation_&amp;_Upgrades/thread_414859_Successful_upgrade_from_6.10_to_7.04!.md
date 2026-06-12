---
title: "Successful upgrade from 6.10 to 7.04!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by macstevejb on 2007-04-20
Just upgraded using the update manager method per:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Well, what can I say....it went flawlessly.

So I just want to say congratulations & thanks to the guys...

regards :KS

---

### Post by rich.bradshaw on 2007-04-20
Now you can pass your experience onto other users!

---

### Post by elmerfud on 2007-04-20
I'm running a successful upgrade too, but I had issues.  Its working now.  Nothing too serious.

---

### Post by dpmccoy on 2007-04-20
Thought I would add my two cents as well...I had a successful installation!

A few notes (I'm referring to my Kubuntu 6.10, BTW):

- Adept notified me of the update around 6:00 pm last night, and I started it around 7:00 pm.  The servers must have been jammed to the max, because it took approximately 12 hours to complete.

- My wireless still works; I'm using Ndiswrapper, KNetworkManager, and a Netgear wireless card.

- No problems with my Nvidia [proprietary] driver; didn't have to re-build it for the new kernel.

- Beryl Manager didn't start up at re-boot; when I tried to run it from the CLI, I was told to 'sudo apt-get' it again.  This might be because of the inclusion of Compiz by default (??).

- I'll have to edit fstab again and re-mount my two extra partitions [MP3s and data] from my primary hard drive.

I only had five minutes to try things out this morning, because I had to leave for work.

But...so far, so good!

:)

---

### Post by elmerfud on 2007-04-20
I edited fstab and commented out my nfs mounts.  Right now wireless doesn't work at reboot.  If you leave the nfs mounts in fstab, it can take 5 minutes per nfs mount to boot !

I turned off a ton of repositories to be able to do my update.  In doing so, I don't think my nvidia driver got updated.  When I enabled the repositories, it updated the nvidia driver and then it kind of worked.

I still have issues with wireless.  It looks like there are bugs with KNetworkManager.  If I run that, it kills my wireless network connection.

---

### Post by steveneddy on 2007-04-20
Success on System76 Serval Performance - used the guide form the System76 site - which was to start the Update Manager and click the "Update Now to Feisty" button.

Took about an hour, and so far no issues.

System has Intel Core 2 Duo, 2 Gig RAM and nVidia graphics.

All worked well after the upgrade and restart.

-SE

---

