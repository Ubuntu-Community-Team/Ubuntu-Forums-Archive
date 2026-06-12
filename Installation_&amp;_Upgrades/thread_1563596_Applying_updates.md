---
title: "Applying updates?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by gdblu on 2010-08-29
I'm a fairly new Ubuntu user.  Actually, it's my 9 year old daughter's PC that I have it installed on (I had to wipe the drive and decided to move her up from XP).

She 2 or 3 movies backed up in .avi format (did it when she was younger so that she wouldn't scratch up the DVDs by trying to change them out herself) that she likes to watch, so I put them on here once 10.04 was installed, but video playback is extremely choppy, turns black & white, audio becomes unsynchronized, etc.

I moved her to VLC, but the problem persisted.  In troubleshooting the issue, I tried checking Update Manager to see if maybe there was something that needed to be updated to operate properly.  This is where the issue in question arises: When Update Manager opens and populates, it indicates that there are 78 updates selected for 116MB.  When I press 'Install Updates' and enter my admin password, it goes through the process like it's preparing to install, but then just returns to the Update Manager window with all the updates still selected.  I don't think it's actually installing anything.  When I press 'check', or close out and reopen UM, all 78 updates are still there waiting to be installed.  Am I doing something wrong?

I found, in these forums, that the playback issue is probably related to the ATI video card in her PC, but haven't seen anything yet in regards to the update problem I'm having.  

I appreciate any assistance/insight y'all are able to offer.

Thank you

---

### Post by mörgæs on 2010-08-29
Hi, welcome to the forum. 

If you boot the machine and then run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

do you get a working system?

---

### Post by gdblu on 2010-08-29
Thanks.  I had just found the command for 'apt-get update' and tried that after a reboot, which seemed to work.  Not sure why it hung, but after a few creative searches I found that I'm not the only one who experienced it.  Again, thank you.

(Didn't resolve the video playback issue, however...)

---

