---
title: "Black screen after grub menu"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by ruest.olivier on 2014-06-03
Hello there

I've been trying to solve this for the last few days and I can't get it to work. Would be great if somebody with more brain/experience could give me a hand =D

I Installed Kubuntu 13.10 on a new Acer Aspire E1-510.

So far so good, but when it tells me after the installation to eject my live CD, and confirm reboot with enter it freezes. 
I can run it on recovery mode, and access the filesystem through root shell.
And when I try to boot it "starting load fallback graphics devices" fail, and it freezes again. Problem with my graphic card?!

What am I missing? :/

Thanks a lot! =D

---

### Post by LastDino on 2014-06-03
Yes, problem with graphic card, more specifically; drivers. Did you click on install ''3rd party'' stuff during installation or not? If not, then boot into nomodeset and install 3rd part drivers. If you did install them during installation, try out free default ones.

---

### Post by ruest.olivier on 2014-06-03
ok. I feel a bit stupid here =D
I did install the 3rd party stuff.
Where do I find the free default ones?

---

### Post by LastDino on 2014-06-03
What graphic card are you using? You need to completely uninstall the installed drivers first. By the way, since you installed 13.10, which is going to end in upcoming 2 months, why not just make fresh install of Kubuntu 14.04 LTS?

---

### Post by ruest.olivier on 2014-06-03
Do you think chances are better that it works with 14.04?
I thought I might just be able to update it afterwards.

It's an "Intel Corporation ValleyView Gen7"

---

### Post by LastDino on 2014-06-03
I don't have experiance with this perticular chip.

After doing quick google, I came across this;

[http://unix.stackexchange.com/questions/115459/valley-view-black-screen-of-death](http://unix.stackexchange.com/questions/115459/valley-view-black-screen-of-death)


Your system is quite new, its usually better to bet on newer kernels to get support than older by default. I've no idea if this is supported in 13.10 tbh. If I were you, I would wait for someone more knowladgable to grace this thread with proper answer, but yeah, installing 14.04 is better option as 13.10 install is fresh too. Why make life too complicated?

---

### Post by ruest.olivier on 2014-06-03
Yeah, I found that as well. System went completely nuts =D
I'll give it a try with 14.04 as a change then.

ah well, Thanks a lot anyway for your time!

---

