---
title: "Fresh Ubuntu Studio 7.10 install preparations"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by rayj on 2007-12-07
Greetings!

I am completely new to Ubuntu, and I have been slowly preparing to make the jump over the last few months. Today I finish my final file backups...

My computer use is typically two-fold: general websurfing nonsense/DosBox-style archaic gaming, and audio production. 

What I would like to hear some informed opinions about are:

1. Partitioning. I'll obviously need to reformat my drives. I have two nice, 500 gig SATA 3.0 hard drives. I plan on dedicating one to audio files. However, it sounds like a good idea to designate another, small partition at the beginning of my first drive for OS kernels...am I understanding that correctly? What would be an ideal partitioning scheme?

2. I'm dropping my RAID configuration, as it seems like there are some issues with it, and if Ubuntu is as solid as it sounds, I'm not too worried about it. Is my thinking here reasonable?

3. I'm looking forward to being able to run my system as 64 bit. Are there any issues I can expect? Other than the lack of complete compatibility with 32 bit software architectures (I'm going to miss VST's and whatnot, but I don't *need* them)?

4. I only have one computer. It is my intention to simply reformat the hard drives, plop in my 7.10 .iso, and go. Is there anything else I should take into consideration before I do this? I believe I have everything I need backed up. I'm a bit nervous about it, because if something gets hosed before I can access online support forums, well, you know. Is there a decent guide/checklist somewhere? All the information I've found so far is either way too simple to be useful, or concerns upgrades as opposed to fresh installs.

Thanks for your time...

---

### Post by Pumalite on 2007-12-07
Getting rid of Raid is smart. You can run 64 bit if you have the hardware. Are you going to be all Ubuntu (you can run Windows in Virtualbox or VMware) or dual booting?

---

### Post by rayj on 2007-12-07
I am planning on running absolutely nothing but Ubuntu. My reasoning is two-fold; politically, I don't want to have anything to do with commercial OS's. I'm also looking forward to learning more about general systems architecture from the enterprise...I've already learned quite a bit, and I'm hungry for more, but my poor brain can only hold so much information without hands-on experience.

Thanks for the reply!

---

### Post by Pumalite on 2007-12-07
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Congrats and welcome.

---

### Post by rayj on 2007-12-07
Awesome! Thanks. That's pretty much what I was looking for...

---

### Post by rayj on 2007-12-07
OK. My first real question: file systems. All my backup files were produced on an NTFS system. I want to run the best file system for Ubuntu...which I'm assuming is ext2. Will I be in trouble when I try to migrate files from one system to another? I will probably be trying to import audio from a friend's XP laptop from time to time...

---

### Post by Pumalite on 2007-12-07
You can install ntfs-3g and read and write to NTFS.

---

### Post by rayj on 2007-12-07
> **Pumalite said:**
> You can install ntfs-3g and read and write to NTFS.

Yes, but is this ideal for someone who eventually wants to produce multimedia files with their system? I want my system to be sleek and stable...but I will, for example, need to import .wav files from other systems running NTFS. I'm not against running some sort of file conversion per file, if there is something like that out there...

---

### Post by Pumalite on 2007-12-07
You can do that much and more. Don't worry.

---

### Post by rayj on 2007-12-07
Cool. NTFS-3g it is.

---

