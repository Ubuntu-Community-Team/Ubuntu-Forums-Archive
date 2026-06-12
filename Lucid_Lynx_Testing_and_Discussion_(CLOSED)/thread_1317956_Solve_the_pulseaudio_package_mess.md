---
title: "Solve the pulseaudio package mess?"
date: 2009-11-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-11-07
Did anyone manage to solve the pulseaudio package mess?

---

### Post by Joe_Bishop on 2009-11-07
I hope they remove it

---

### Post by yelo3 on 2009-11-07
apt-get install pulseaudio
stops because it depends on pulseaudio-module-udev, but if you read the changelog you see that the maintainer removed this dependecy because it was included in the main pulseaudio package

---

### Post by afv on 2009-11-07
I've noticed that too. I think we'll have to wait for the next release.

Reported a bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/477381](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/477381)

---

### Post by philinux on 2009-11-07
> **yelo3 said:**
> Did anyone manage to solve the pulseaudio package mess?

There is no mess. Just packages in a state of flux.

Please read this from the open week sessions.
[https://wiki.ubuntu.com/MeetingLogs/openweekKarmic/RunPlusOne](https://wiki.ubuntu.com/MeetingLogs/openweekKarmic/RunPlusOne)

From this thread.

[http://ubuntuforums.org/showthread.php?t=1312092](http://ubuntuforums.org/showthread.php?t=1312092)

---

### Post by plun on 2009-11-07
I compiled PA from source without any problems.

---

### Post by hikaricore on 2009-11-07
> **plun said:**
> I compiled PA from source without any problems.

that's nice

also completely unrelated to the topic at hand.

---

### Post by VMC on 2009-11-07
> **philinux said:**
> There is no mess. Just packages in a state of flux.

Please read this from the open week sessions.
[https://wiki.ubuntu.com/MeetingLogs/openweekKarmic/RunPlusOne](https://wiki.ubuntu.com/MeetingLogs/openweekKarmic/RunPlusOne)
...


I like this guys attitude, from your link:
(11:05:01 AM) jcastro: So first off, let's talk about why you WOULDN'T want to run a a dev release like lucid
(11:05:03 AM) jcastro: a) You need to get work done
(11:05:15 AM) jcastro: and b) Computer downtime or dataloss isn't an option
(11:05:25 AM) jcastro: so, for example I know many ubuntu developers stick to a stable release
(11:05:45 AM) jcastro: and use pbuilder or a VM to test their packages
(11:05:52 AM) jcastro: some people have multiple machines
(11:06:04 AM) jcastro: I personally always keep my laptop on a stable release until beta-ish
(11:06:14 AM) jcastro: but on my desktop **I let it rip with the brokeness**.

So regarding pulseaudio. I just wait. Just because you see something is held back is no reason for concern. 

[FONT="Courier New"]Off-topic and thinking to myself and probably should keep it to myself, I wonder why they don't just keep the 'held backs' off the update trail altogether. So the question never comes up in the first place. Regardless, I just wait and test with what I have presented to me.[/FONT]

Edit: Actually that entire discussion is worth a read and re-read. Good common sense approach to ubuntu+1 and why packages get held back.

---

### Post by plun on 2009-11-07
> **hikaricore said:**
> that's nice

also completely unrelated to the topic at hand.

Well, I dont think this can be resolved during a weekend without some basic Linux knowledge about compiling from source.):P

---

### Post by vredley on 2009-11-08
This bug was fixed in the package pulseaudio - 1:0.9.19-2ubuntu2

---------------
pulseaudio (1:0.9.19-2ubuntu2) lucid; urgency=low

  * debian/control:
    + Promote pulseaudio-utils to Depends for pulseaudio so that the
      pm-utils script is present (LP: #478182)
    - Drop obsolete Depends on pulseaudio-module-udev for pulseaudio
      (LP: #477382)
  * debian/01PulseAudio: Don't fail suspend/resume when system-wide
    daemon is running (LP: #476505)
 -- Daniel T Chen <email address hidden> Fri, 06 Nov 2009 18:37:36 -0500

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/477382](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/477382)

---

### Post by VMC on 2009-11-09
Yes it was fixed with todays updates.

---

### Post by philinux on 2009-11-09
> **VMC said:**
> Yes it was fixed with todays updates.

This is what I get. I'll wait

```
Initialising package states... Done
The following NEW packages will be installed:
  rtkit
The following packages will be REMOVED:
  pulseaudio-module-udev
The following packages will be upgraded:
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils 
9 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 1,245kB of archives. After unpacking 201kB will be used.

```

---

### Post by excogitation on 2009-11-09
that's good, philinux.
pulseaudio-module-udev is now integrated into the main pulseaudio package so it needs to be removed.

---

### Post by juliobahar on 2009-11-09
excuse my ignorance but what is exactly the mess with pulseaudio.

I'd be very happy for just a simple explanation. Love all!

---

### Post by vredley on 2009-11-09
> **juliobahar said:**
> excuse my ignorance but what is exactly the mess with pulseaudio.

I'd be very happy for just a simple explanation. Love all!

Some pulseaudio-related packages couldn't be upgraded due to a problem with dependencies. It's fixed now.

---

### Post by philinux on 2009-11-09
> **excogitation said:**
> that's good, philinux.
pulseaudio-module-udev is now integrated into the main pulseaudio package so it needs to be removed.

Cheers, thanks a lot. Where do you get the info for this? Mailing list?

I'm chrooted into lucid so I can see the updates before rebooting.

---

### Post by LKjell on 2009-11-09
Changelogs....
 
 * debian/control:
   + Promote pulseaudio-utils to Depends for pulseaudio so that the
     pm-utils script is present (LP: #478182)
   **- Drop obsolete Depends on pulseaudio-module-udev for pulseaudio**
     (LP: #477382)
 * debian/01PulseAudio: Don't fail suspend/resume when system-wide
   daemon is running (LP: #476505)

---

### Post by philinux on 2009-11-09
> **LKjell said:**
> Changelogs....
 
 * debian/control:
   + Promote pulseaudio-utils to Depends for pulseaudio so that the
     pm-utils script is present (LP: #478182)
   **- Drop obsolete Depends on pulseaudio-module-udev for pulseaudio**
     (LP: #477382)
 * debian/01PulseAudio: Don't fail suspend/resume when system-wide
   daemon is running (LP: #476505)

Been using the terminal to upgrade via chroot from karmic. Is there a good link to all the changelogs.

---

### Post by tekstr1der on 2009-11-09
Maybe here? [https://lists.ubuntu.com/archives/lucid-changes/](https://lists.ubuntu.com/archives/lucid-changes/)

I view by date. This is updated when a new package version is committed.

---

### Post by philinux on 2009-11-09
> **tekstr1der said:**
> Maybe here? [https://lists.ubuntu.com/archives/lucid-changes/](https://lists.ubuntu.com/archives/lucid-changes/)

I view by date. This is updated when a new package version is committed.

Cheers.

---

### Post by Kevbert on 2009-11-13
Yippee. The latest pulseaudio updates have just broken sound...

---

### Post by philinux on 2009-11-13
I get the hda intel power save thud but volume was set to nill. However raising the slider gives no sound.

---

### Post by jerrylamos on 2009-11-13
i845 integrated chip - the slider shows up, no sound with lucid.  karmic O.K.

Jerry

---

### Post by Regenweald on 2009-11-13
Fine here, went a little low, used alsamixer to set it back to max. Perfect.

---

