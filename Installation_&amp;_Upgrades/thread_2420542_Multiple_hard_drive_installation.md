---
title: "Multiple hard drive installation"
date: 2019-06-06
forum: Installation &amp; Upgrades
---

### Post by fogtoo2 on 2019-06-06
I'm thinking about returning to Ubuntu, but I am in need of some assistance and I hope you can help me out. I am a little confused about the setup of my system.
I have 3 internal and 1 external hard drive.
[LIST=1]
[*]SSD 120Gb where I currently have Windows installed
[*]SSD 240Gb was used for games and programs I wanted quicker load times for.
[*]HDD 1Tb for everything else, downloads etc
[/LIST]

I have no plans to keep Windows, I have a laptop with Windows if I need that for something specific.

My question is what is the "best way" to partion?
If I use SSD#1 as /root and HDD as /home how do I then best utilise the 2nd SSD?

---

### Post by crip720 on 2019-06-06
Root only needs about 20gb, 30 or 35 is better.  Can use the rest for home especially if you use the HDD for downloads and what.  Your games will be your biggest worry, might not be available for ubuntu.  Some stuff like certain firmware and bios updates will work best under windows, so you might want to have a small partition with windows kept just for that.  Depending on how much you download, most OSs don't need much space for themselves.  Can use second SSD to play with different OSs or use it same as you do now but with games for linux or stream.

---

### Post by oldfred on 2019-06-06
There is no one best way. Each user has unique requirements for data & system configuration.
Default install of just / (root), is often fine for a newer user. Separate /home is good as next step to separate system from user data. Separate /home defaults to user ownership and permissions and mounts /home in fstab for default mounting. Still more advanced is separate data partition(s). But then you need to create mount, add to fstab, and set ownership & permissions. Bit complicated for newer users but once you have used system often worth learning.

One alternative is one SSD as / and other as /home. And then use HDD for data you only use sometimes and does not need to load as quickly. or use HDD as backup drive & external as backup. You cannot have too many backups.

But I use SSD for /, but only have 25GB allocated for / and use 8GB of the 25GB including /home (mostly hidden settings only). But I link my data folders on HDD back into /home, so configuration is like a normal configuration.
I also have at least one install on every drive, even if just for emergency boot. And try to configure that drive that it would boot without main boot drive. With UEFI that is a bit more difficult but doable.

Is system UEFI or BIOS. Most systems now are UEFI, and you should only partition with gpt partitioning and use UEFI. How you boot install media, is then how it installs.

---

### Post by fogtoo2 on 2019-06-06
I knew someone was going to say "no best way", which was also why I put it in "". Last time I used Ubuntu was 12.04 or something around there. Just had the simple setup with 1 HDD then. Read up a bit to see if I was smart enough to figure stuff out, which brought me to the /root /home split up. I just fear if I do that I will end up with the other SSD not being used at all.
If I change to question, instead of "best way", to what would be your suggestion to my setup?
If you could instead of using many words, I do appreciate the responses, but the answer "it depends", doesn't help me much, give me a quick rundown of how you would partition the hard drives, that would be very appreciated.
I kind of understand it, but not well enough to be confident to trust myself to make a good decision.

---

### Post by crip720 on 2019-06-06
Best way for us to answer is to let us know much of your HDD is used/filled with data, is it close to full or only using a small part.  Should keep partitions as simple as you can, to make it easy.  If you don't have much data(videos,downloads) all you need is a single /partition on the small drive.  A lot of data you should have 25/30 gb /partition plus /home on another drive or same drive if data is moved/downloaded to another drive.  On a 480gb ssd I have 29gb /, 224gb /home, 70gb windows, and the rest free space for future use, I also have a 4tb external drive for most downloads/videos.

---

