---
title: "Re-install Ubuntu 32-bit over 64-bit"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by Oblong_Cheese on 2006-09-12
OK. So, with my first foray into full-time Linux for the desktop, I installed 64-bit Ubuntu. It's been pretty good so far, and I've had in working OK for a few months now.

During the course of getting things like Flash, Java etc working, I've royally messed up some parts of the OS (I can't open files straight from the Firefox download dialogue anymore, I have NO Flash player and only the old version of Java), I've got a 32-bit chroot floating around on my drive somewhere taking up valuable space, and I have a lot of broken stuff that I wouldn't know where to begin fixing.

So, basically I want to start over with 32-bit Ubuntu. The only problem is obviously I want to keep my home folder, and that's 40Gb. No biggie, except I don't have anywhere to back it up.

So my question is, can I simply throw in the 32-bit LiveCD, delete everything except the /home dir, and install 32-bit Ubuntu onto my existing  root partition, without it overwriting my existing home directory?

Simple logic and my current knowledge of Linux says: yes. However, I thought I'd ask others to see if the Ubuntu community has tried something similar or knows of any pitfalls associated with this approach.

Thanks!

---

### Post by randell6564 on 2006-09-12
I'm going to say YES!  As long as you have a seperate /home partition.

---

### Post by randell6564 on 2006-09-12
Can you RE-SIZE your OS using 'qtparted' or 'gparted', then create a partition and transfer your /home directory over to it?

I have never needed to do this, but I have read alot about doing it!

Is it possible to backup /home to a CD, then incorperate it to your new OS?

---

### Post by Oblong_Cheese on 2006-09-12
> **randell6564 said:**
> Can you RE-SIZE your OS using 'qtparted' or 'gparted', then create a partition and transfer your /home directory over to it?

I have never needed to do this, but I have read alot about doing it!

Is it possible to backup /home to a CD, then incorperate it to your new OS?

Well, that's the problem. My /home directory is 40Gb in size. And it's on the same partition as / :-)

---

### Post by randell6564 on 2006-09-12
> **Oblong_Cheese said:**
> Well, that's the problem. My /home directory is 40Gb in size. And it's on the same partition as / :-)

Sorry! You made that clear in your original post. 

I am not aware of any way to get the contents of your /home directory in this situation without extracting it from your HD, or transfering it over to an external HD.

---

### Post by randell6564 on 2006-09-12
> **Oblong_Cheese said:**
> Well, that's the problem. My /home directory is 40Gb in size. And it's on the same partition as / :-)

Sorry! You made that clear in your original post. 

I am not aware of any way to get the contents of your /home directory in this situation without extracting it from your HD, or transfering it over to an external HD.

---

