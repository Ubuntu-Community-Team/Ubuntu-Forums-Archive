---
title: "Fed Up; Need Info on how Ubuntu manages auto-mounting/audio"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by IkimashoZ on 2007-04-24
I have been using Feisty for about 4 days now.  I hate it.

With Edgy, I felt like I had a working operating system with a few minor flaws that seemed like they would be resolved with the next update.  And, before I start my rant, I should mention that the people who worked on Rhythmbox did a wonderful job, and it now does everything I want it to.

I cannot record anything.  Not because my mic is broken, but apparently because of something called alsa-utils that was part of feisty, even though it obviously shouldn't have been.  (For details on my problem see [here]("https://answers.launchpad.net/ubuntu/+question/5328") and [here]("https://bugs.launchpad.net/bugs/108798")).  I have played around with many different options in alsamixer, but since all I can really do is guess at what random configuration of settings *might *work, this is an impractical way to approach a solution.  I need the attention of someone who is familiar with what changes alsa-utils made, so I can go about undoing whatever damage it did.

ntfs-config is a mess.  I've been fighting with it for days trying to get ubuntu to do all three of the following when I hook up my external harddrive: 1) not default to ro 2) not insist that I need to run ntfsfix 3) not sit there and do nothing.  So far, in four days of playing around with ntfs-config, I have gotten it to succeed at all three a total of *one time*.  And even then, I think some option called "force" was involved.  ntfs-config also screwed with the detection of other data storage devices, like my card reader and my iPod.

**I want to know how I can find out which of my devices is classified under which dev.  I want to know how to create/delete/manage my mount points.  I want to know what file or files tell ubuntu where to mount what devs, and whether or not to automount them at startup.  I assume that part of this process is /etc/fstab, but it doesn't do me any good since I can't find any way to match dev's with physical devices, and I can't find any documentation on how to add lines to file, what all the options do, etc.**

It would also be nice if ubuntu correctly unmounted external hd's, instead of the present system, which doesn't.  Granted, this isn't a debilitating problem, like the microphone issue, but it would be nice to have to have a self-made app on the desktop with a command line to unmount my hd.

Thanks.

---

### Post by aliennet on 2007-04-25
> **IkimashoZ said:**
> I have been using Feisty for about 4 days now.  I hate it.

With Edgy, I felt like I had a working operating system with a few minor flaws that seemed like they would be resolved with the next update.  And, before I start my rant, I should mention that the people who worked on Rhythmbox did a wonderful job, and it now does everything I want it to.

I cannot record anything.  Not because my mic is broken, but apparently because of something called alsa-utils that was part of feisty, even though it obviously shouldn't have been.  (For details on my problem see [here]("https://answers.launchpad.net/ubuntu/+question/5328") and [here]("https://bugs.launchpad.net/bugs/108798")).  I have played around with many different options in alsamixer, but since all I can really do is guess at what random configuration of settings *might *work, this is an impractical way to approach a solution.  I need the attention of someone who is familiar with what changes alsa-utils made, so I can go about undoing whatever damage it did.

ntfs-config is a mess.  I've been fighting with it for days trying to get ubuntu to do all three of the following when I hook up my external harddrive: 1) not default to ro 2) not insist that I need to run ntfsfix 3) not sit there and do nothing.  So far, in four days of playing around with ntfs-config, I have gotten it to succeed at all three a total of *one time*.  And even then, I think some option called "force" was involved.  ntfs-config also screwed with the detection of other data storage devices, like my card reader and my iPod.

**I want to know how I can find out which of my devices is classified under which dev.  I want to know how to create/delete/manage my mount points.  I want to know what file or files tell ubuntu where to mount what devs, and whether or not to automount them at startup.  I assume that part of this process is /etc/fstab, but it doesn't do me any good since I can't find any way to match dev's with physical devices, and I can't find any documentation on how to add lines to file, what all the options do, etc.**

It would also be nice if ubuntu correctly unmounted external hd's, instead of the present system, which doesn't.  Granted, this isn't a debilitating problem, like the microphone issue, but it would be nice to have to have a self-made app on the desktop with a command line to unmount my hd.

Thanks.


For the second point try this: [http://flomertens.free.fr/disk-manager/](http://flomertens.free.fr/disk-manager/) could help you if I understand your problem

For the first point, I've had the same both upgrade...let me some minutes and I post "my" solution


[...]
Here I'm It is a very common problem apparently. Just rename the the /etc/asound.conf file in etc/asound.conf.bak (sudo mv /etc/asound.conf file in etc/asound.conf.bak) restart the system and everything will be ok (I hope). For me it is.
Or read here [http://ubuntuforums.org/showthread.php?t=205924&page=2](http://ubuntuforums.org/showthread.php?t=205924&page=2)

Which is the alsa erros that you have?
Mine was ALSA lib pcm.c:2146: (snd_pcm_open_noupdate) Unknown PCM default

---

