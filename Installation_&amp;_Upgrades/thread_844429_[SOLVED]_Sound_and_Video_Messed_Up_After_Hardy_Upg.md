---
title: "[SOLVED] Sound and Video Messed Up After Hardy Upgrade"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by steve_c on 2008-06-29
I upgraded from Gutsy to Hardy. I noticed a couple issues--one being that my sound only worked in some applications. It worked for desktop sounds and it worked for videos played through a web browser (youtube, etc) and it worked with MP3s, but it did not work with downloaded videos (mpeg, xvid, etc) that I tried to play with VLC, Totem, or anything. Also VLC had this weird quirk after upgrade where it would play till the end of the file, then freeze up when it got to the end. That persisted even after purging and reinstalling VLC.

So now's where my own screwups come into play. I tried to fix it myself following instructions here: [http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/]("http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/").

Upon rebooting I actually had no sound whatsoever.

So I thought if this is a kernel problem, maybe I should try a different kernel. Well trying the 2.24.16 kernel didn't work, and the 2.22.15 kernel that was still on here had working sound but the video was jacked up.

So I tried sudo aptitude reinstall-ing linux-image-2.24.19-generic. Big mistake. Now I still have no sound and my video is also scrooged (as in 800x600 max available resolution). If I try to go to Administration -> Hardware Drivers, my NVIDIA card isn't even listed, both before and after trying to sudo aptitude reinstall nvidia-glx-new.

Is there any chance anyone can help me short of backing up 160GB of data, reformatting, and reinstalling?

---

### Post by steve_c on 2008-06-29
On the upside the audio appears to be working and VLC appears to no longer be crashing at the end of videos.

Now all I have to do is get my video drivers working properly again...

Suggestions?

I'm about to sudo aptitude reinstall linux-restricted-modules-generic. Wish me luck. And thanks for any help.

---

### Post by Pjotr123 on 2008-06-29
Upgrade woes....

A clean installation of a new version (with previous formatting) is always best. For every operating system under the sun.

I suggest a clean reinstall:
[http://ubuntutip.googlepages.com/reinstall](http://ubuntutip.googlepages.com/reinstall)

---

### Post by steve_c on 2008-06-29
YES! FIXED! I AM THE MAN!!!

Pjotr123: Yeah, I tend to agree, but I had 160GB of data on this machine and I don't have anywhere else I can offload it at the moment (I really need to invest in a RAID-5 file server for my home), and I really wanted some of the nifty things Hardy has, such as the Unlock button on apps where you can change the system, instead of requiring you to authenticate every time you open it even if you just want to view it, and of course to try out the Completely Fair Scheduler. Plus really, one of the things that's supposed to be amazing about Debian based systems is how easy it is to upgrade to the latest version as compared to other OSes. So I gave it a go, even though normally I'd rather format and reinstall to avoid any potential issues or excess clutter.

For anyone having similar problems in the future, this is what wound up finally solving the problem up to this point:
```

$ sudo aptitude update
$ sudo aptitude reinstall linux-image-2.6.24-19-generic
$ sudo aptitude reinstall nvidia-glx-new
$ sudo aptitude reinstall linux-restricted-modules-generic

```

Now I have all my sound working, VLC is working again, and my video is working. 

My NVIDIA driver was still unfortunately not showing up in System -> Administration -> Hardware Drivers. I also couldn't seem to get my compiz effects to start.

So what I did was this:
```

$ sudo aptitude reinstall linux-restricted-modules-2.6.24-19-generic
$ sudo aptitude reinstall linux-restricted-modules-common
$ sudo aptitude reinstall linux-restricted-modules-generic

```

It is now FIXED!!!

---

### Post by dogofthecourt on 2008-06-29
Solved?  Yeah right.
Each time I hibernate the sound goes away and I have to restart for it to come back.
This along with the problems the System 76 touchpad is giving me is making me want to ditch this computer and get a Dell with Windows again.

Ubuntu needs a universal fix that is automatically sent out.

> **steve_c said:**
> YES! FIXED! I AM THE MAN!!!

Pjotr123: Yeah, I tend to agree, but I had 160GB of data on this machine and I don't have anywhere else I can offload it at the moment (I really need to invest in a RAID-5 file server for my home), and I really wanted some of the nifty things Hardy has, such as the Unlock button on apps where you can change the system, instead of requiring you to authenticate every time you open it even if you just want to view it, and of course to try out the Completely Fair Scheduler. Plus really, one of the things that's supposed to be amazing about Debian based systems is how easy it is to upgrade to the latest version as compared to other OSes. So I gave it a go, even though normally I'd rather format and reinstall to avoid any potential issues or excess clutter.

For anyone having similar problems in the future, this is what wound up finally solving the problem up to this point:
```

$ sudo aptitude update
$ sudo aptitude reinstall linux-image-2.6.24-19-generic
$ sudo aptitude reinstall nvidia-glx-new
$ sudo aptitude reinstall linux-restricted-modules-generic

```

Now I have all my sound working, VLC is working again, and my video is working. 

My NVIDIA driver was still unfortunately not showing up in System -> Administration -> Hardware Drivers. I also couldn't seem to get my compiz effects to start.

So what I did was this:
```

$ sudo aptitude reinstall linux-restricted-modules-2.6.24-19-generic
$ sudo aptitude reinstall linux-restricted-modules-common
$ sudo aptitude reinstall linux-restricted-modules-generic

```

It is now FIXED!!!

---

### Post by steve_c on 2008-06-30
> **dogofthecourt said:**
> Solved?  Yeah right.
Each time I hibernate the sound goes away and I have to restart for it to come back.
This along with the problems the System 76 touchpad is giving me is making me want to ditch this computer and get a Dell with Windows again.

Ubuntu needs a universal fix that is automatically sent out.

Well, my particular problem is solved. Sorry you're still having troubles. I don't really mess with hybernate so I probably can't help much there.

I think Ubuntu will provide a universal fix at some point for the sound issues, because from what I've been reading the problem is actually with the kernel. Once they patch the problem in the kernel I'm sure Ubuntu will roll out the updates.

---

