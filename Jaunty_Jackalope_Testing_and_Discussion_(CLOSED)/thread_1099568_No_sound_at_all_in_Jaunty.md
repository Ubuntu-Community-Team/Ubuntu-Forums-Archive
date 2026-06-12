---
title: "No sound at all in Jaunty"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by erdalronahi on 2009-03-18
I had sound problems in Intrepid, therefore I upgraded to Jaunty. Now I have no sound at all. 

I have tried all the checklists, and the result is that everything should be ok. PulseAudio Volume Control shows that there should be sound. But there isn't. I cannot hear anything. 

This is not a problem of my speakers or hardware, the hardware works with an Intrepid Live CD. 

Any ideas how I could find the source of the problem?

---

### Post by DarkReaper79 on 2009-03-19
Try switching to ALSA. I had the same thing as you on my laptop. Switched to ALSA and it worked.

---

### Post by crimsun on 2009-03-19
> **erdalronahi said:**
> I had sound problems in Intrepid, therefore I upgraded to Jaunty. Now I have no sound at all. 

I have tried all the checklists, and the result is that everything should be ok. PulseAudio Volume Control shows that there should be sound. But there isn't. I cannot hear anything. 

This is not a problem of my speakers or hardware, the hardware works with an Intrepid Live CD. 

Any ideas how I could find the source of the problem?

It's probably mucked ~/.pulse* . Start by backing up and moving those out of the way, then restarting GNOME.

---

### Post by scottmuz on 2009-03-20
I had same issue. I solved by doing following:
sudo aptitude install gnome-alsamixer
gnome-alsamixer &

Then make sure all the mute tick boxes are off and increase the volume.

For some reason my master output was muted.

---

### Post by erdalronahi on 2009-03-20
@crimsun: No, that didn't help.

@DarkReaper79: Any particular ideas how to do that?

@scottmuz: The problem is not that something is muted. Even the PulseAudio Volume Control shows that sound is being played. It wouldn't do that if it was muted. But nothing is to be heard.

---

### Post by scottmuz on 2009-03-20
I had the same symptoms with Pulse audio showing something was playing
and that there was no muting.

But alsa was muted.

---

### Post by erdalronahi on 2009-03-20
Ok, but here nothing appears to be muted, gnome-alsamixer doesn't show any muted devices.

Since I had already problems in Intrepid while Live-CDs work I maybe have screwed up the configuration somehow. But all of the things I try to reset it, fail.

---

### Post by maheshasolkar on 2009-03-20
> **erdalronahi said:**
> The problem is not that something is muted. Even the PulseAudio Volume Control shows that sound is being played. It wouldn't do that if it was muted. But nothing is to be heard.

I always have this problem when I install Ubuntu afresh. What works for me is this:

[LIST]
[*] Open alsamixer

```
  % alsamixer -Dhw
```

[*] Look for 'External...', using 'tab' to traverse the list of items.
[*] If it is not already muted, mute it.
[/LIST]

Again, that works for me, YMMV.

---

