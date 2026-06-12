---
title: "Dapper live black screen"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by oliwally on 2006-06-04
Sorry, but I've posted this at [Kubuntuforums.net]("http://kubuntuforums.net/forums/index.php?topic=5633.0") also, but have had no replies.


One of my computers just displays a blank screen when I run the 6.06 desktop live CD.

Downloaded the desktop iso and checked the checksum. Burned the CD and rebooted the computer with it.

On my older computer (P4)  it works well (although no sound).

On my new(er) computer (athlon XP 2600+) it goes through the whole installation thingo (from cd - not an actual install onto hd) and then there is just a sound and a black screen.

Both computers have Nvidia cards.

I'm assuming the burned CD is not the problem since it worked on my other computer.

I'm very frustrated by this since I've been looking forward to this release for a long time now (currently dual-booting XP and Breezy). I'm also concerned that those who're trying K/Ubuntu for the first time will be scared off by problems such as these.

How can I get the live CD to work?

---

### Post by gingermark on 2006-06-04
I had the same problem.

And I didn't exactly fix it. Instead, I downloaded the alternate install CD, and used that.

If you want to give that a go, and you still get the black screen after installation, boot into recovery mode and do

```
apt-get install nvidia-glx
nvidia-glx-config enable
``` and you should then be fine.

(When you boot into recovery mode you should be the "root" user. Of course, if you ever need to run those commands as your regular user prefix both commands with 'sudo').

Oddly enough, I tried the Ubuntu desktop CD, and that worked, so I'm not sure what the problem is the with Kubuntu desktop CD, although it seems to be working for most people.

As far as your older computer goes, what soundcard do you have? I'm sure the lack of sound is just a driver issue.

---

### Post by oliwally on 2006-06-04
Wow, much more rapid response on this forum - thanks for that gingermark!

I will try your suggestions and post back.

I'm not worried about fixing the sound on my old computer because I won't be installing Kubuntu on it. Just wanted to see if it would boot without the same problems.

---

### Post by oliwally on 2006-06-07
> ```
apt-get install nvidia-glx
nvidia-glx-config enable
```
It worked just like you said - thanks very much. Just fantastic.

To others reading this thread, don't forget to chuck in your alternate install CD before executing the command above. But it'll prompt you to do so anyway.

---

