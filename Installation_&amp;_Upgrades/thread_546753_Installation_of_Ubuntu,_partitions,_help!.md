---
title: "Installation of Ubuntu, partitions, help!"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Dyamito on 2007-09-09
Basically I'm installing ubuntu as we speak and have windows already on here, I have 48gb of free space and it's been ages since I installed ubuntu or any other distro of linux for that matter. I have no clue what type of partitions to make, or what to set as the mount point. So far I've made this but not gone through with it:


ext3 20gb
swap 20gb
reieserfs 8gb mount point: /


I was just guessing myself, so if I could get a suggestion from anyway that'd be great. :)


Thanks

---

### Post by forestpixie on 2007-09-09
Hi - on a 80Gb hdd I have

root - 8Gb mount point / (this of course depends on what you're liklel to install - I've still got 3Gb free)
home - what's left mount point /home
swap - 1Gb - with 1Gb RAM - supposedly should be 2 times RAM - but depends on how much you have and what you're going to be using PC for

---

### Post by Dyamito on 2007-09-09
Thank you for the quick response time, I'll be using ubuntu for a course in school. I was informed we'll be using it alot later on so I wanted to get a heads up on getting it going, I'll be using wine alot since that's what we're focusing on, emulation. No heavy gaming atm, and I have 1GB RAM, and 48gb of space to mess around with, what do you suggest I use for the numbers you used. I will be installing ALOT of programs most likely.

---

### Post by Mud.Knee.Havoc on 2007-09-09
Wow... 20GB of swap!  That's definitely overkill.  Keep in mind that swap is just "backup" for when your RAM is all used up by other programs (it'll start writing to your swap partition, which is a LOT slower than RAM, but at least it lets your computer run without barfing).

---

### Post by Dyamito on 2007-09-09
I wasn't sure what the sizes should be, so I came here wondering. :P

---

### Post by Mud.Knee.Havoc on 2007-09-09
You know, hard drives are so cheap these days that you could pick up an 80GB drive for next to nothing.... might be something to think about if you like downloading lots of stuff and installing lots of programs, like you say.

Anyway, the first poster made a great suggestion.  Make a / (root) partition that's somewhere around 10GB (up to 15GB - I've got 17GB root partition right now and it's well over half empty), make a swap partition that's a gig or two, and let /home have the rest.  This way, you can even reinstall a different linux OS one day in / and you won't lose your personal files (since they'll be living at /home).

---

