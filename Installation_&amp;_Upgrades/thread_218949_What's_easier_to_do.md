---
title: "What's easier to do?"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2006-07-19
Go from Ubuntu 64 bit to Ubuntu 32 bit

OR

do a fresh format + fresh installation of Ubuntu 32 bit from a LiveCD?

I'm fine with the installation from a live CD, but the live CD I burned was the 64 bit version (at least I'm almost positive it is). For one, how can I check and confirm it is 64 bit version? Secondly, where can I download the Live CD 32 bit Ubuntu version?

I'm still learning, and don't have many "sources" yet for Linux. Where would you folks suggest downloading the 32 bit Live CD Ubuntu?

---

### Post by ThrobbingBrain66 on 2006-07-19
I don't know for sure, but instinct tells me that "downgrading" from  a 64-bit platform to a 32-bit platform could be messy and cause lots of problems.  I would suggest a clean format and install.

Go [here]("http://www.ubuntu.com/download"), choose the mirror for your country and then select the **PC (Intel x86) desktop CD** link (this is the 32-bit version).

I don't know how to check the cd that you already made....have you put it in the drive to see what the name of the image file is?  I would think that if it was the 64-bit version, that the name of the file would indicate that.

---

### Post by Jagot on 2006-07-19
> **Roasted said:**
> Where would you folks suggest downloading the 32 bit Live CD Ubuntu?

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by Roasted on 2006-07-19
Right after I get this installed, what's the first thing I should do? I'm still not completely sure of how repositories work. Which ones do I activate?

---

### Post by ThrobbingBrain66 on 2006-07-19
After you get ubuntu installed, you can start off by editing your sources.list with

```
sudo gedit /etc/apt/sources.list
```

clear out any text there, and replace it with the text found here

[http://www.ubuntuforums.org/showpost.php?p=1076229&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1076229&postcount=1)

This sources.list is a good start and should statsify any needs you have until you're able to learn more.

---

### Post by Roasted on 2006-07-19
What if I have an AMD 64 bit processor. Does it matter? 

btw I'm installing 32 bit because I was having a lot of trouble with the 64 bit version.

---

### Post by Roasted on 2006-07-19
Guess what! Roasted burnt ANOTHER Iso to the CD and I still can't get it to run. What am I doing wrong? Last time I put the CD in, restarted, hit a key and BAM it booted from the Live CD. Using that CD I installed Linux. Unfortunately it was the wrong one that I wanted.

So I'm doing the same thing this time. Same burning program. Same brand of blank DVD's. Same steps. Same everything. BUT different ISO...

What can I do? The file is on a blank DVD as an Iso. How can I get it to run? ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by ThrobbingBrain66 on 2006-07-19
you downloaded an iso, but you have to burn the ISO to the cd as an image (you can't burn the ISO to a cd in a data cd format)...i may be misunderstanding your problem...let me know if i am.

also, since you didn't specifically post any error that you recieved, i should remind you to make sure you set your BIOS to boot from the cd-rom

---

### Post by Roasted on 2006-07-19
> **ThrobbingBrain66 said:**
> you downloaded an iso, but you have to burn the ISO to the cd as an image (you can't burn the ISO to a cd in a data cd format)...i may be misunderstanding your problem...let me know if i am.

also, since you didn't specifically post any error that you recieved, i should remind you to make sure you set your BIOS to boot from the cd-rom

Hey, man. I love you. Hahahhaa it works. I can't believe I was goofing that up. You were right, I was burning as data, not image. I ALMOST did it again but I thought... waaaaait. *back up one step* And I took a look. "Burn Data Disc." ](*,) Doh!

Anyway, thanks. Now I just gotta figure out repository shizzle.

---

