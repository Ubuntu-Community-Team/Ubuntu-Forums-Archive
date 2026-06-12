---
title: "Asus W1n and Sound"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by kirsche on 2005-03-22
Hello,

I've Hoary installed on my Asus W1N.
Nearly everything is working again (used Gentoo before) but know I'm stucked with the sound-problem again.

I found the following informations on the web, which solved my problem for Gentoo:
[http://linux.w1n-forum.net/#sound](http://linux.w1n-forum.net/#sound)

Unfortunately, I can't do the same trick in Ubuntu - I can't write to the
/proc/asound/card0/codec97#0/ac97#0-0+regs to change the settings.

Does anybody experience the same problem or has a hint for me?

Thanks!

---

### Post by kirsche on 2005-04-02
Hello,

I've found the problem.
a) thought I had debug SND support comiled into my kernel - obviously not
b) after switching to su I was able to write into the files mentioned above.
     sudo wont allow me this.. ??!!

Also found a post in an other forum, that "all" the problems will be solved 2.6.11

CU

---

### Post by curana on 2005-06-14
Hi.

I'm a beginner in Ubuntu and Linux in general but also have the W1N.

Could you do me a favour and give me the necessary commands I have to use to make my soundcard work? I would love to kick XP away, but without sound...

I didn't find the files mentioned in that gentoo-Tutorial.

So, would be great if you could do that.

Thanks a lot,

Ben.

---

