---
title: "black screen on install"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by supertdog on 2007-04-29
I saw ubuntu had released 7.04 (feisty) and so I thought I'd try and switch over from suse 10.0 where everything was working fine but what's a hobby without tearing apart and starting over a few times?

I'm attempting a fresh install with no concern for saving any data.

I have an amd64 processor with nVidia GForce 6600, both an IDE and a SATA drive which I plan on using as a logical volume.

When I try to install the desktop version I get though the progress bar and hear the ubuntu startup sound and then the screen goes black.  I hear the disk drive spin occasionally after I jiggle the mouse, and when I try alt-ctrl-backspace to dump into a prompt I only get a very brief glimpse at the startup log.

I also tried the alternate install disk to install a command line system, which seemed to progress a lot farther.  At least I could ssh in and was able to get gdm up and running (although I had to download and run the nvidia install script).  

At some point I tried to do a separate fresh install which seemed to go well but I was never given the opportunity to setup a user, so on reboot I was given a login prompt with no way to login.

can anyone help with any of this?

---

### Post by zvacet on 2007-04-29
From what you sed it seems that you installed Ubuntu with alternate CD and I don´t see anything wronf with that.On user.How can it be that you didn´t have option to set up user and installation is went well?if you want to create user go to the recovery mode and type

```
adduser your_user_name admin
```

---

