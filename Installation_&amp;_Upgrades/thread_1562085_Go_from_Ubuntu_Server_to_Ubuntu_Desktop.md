---
title: "Go from Ubuntu Server to Ubuntu Desktop"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by saucyb on 2010-08-27
Yes I am a newbie girl *looks for pity* to Ubuntu & yes I performed a search please be gentle. I had an old PC lying around so for fun I was instructed to download Ubuntu Server Edition by an experienced user who said it was like Desktop but better...I wiped the hard drive clean which is fine & installed the 32bit edition (64 wouldn't install) but he failed to inform **I was in no way qualified to use it **lol. It looks like gibberish to me

**I want to get Ubuntu Desktop**...I've inserted the disk image of it in hopes of just starting over...and it keeps booting back up to server edition every single time. I restart it and hit a bunch F buttons and sometimes get the instillation screen, it acts like it's going to re-download the OS and bam back to the gibberish black & white screen of Ubuntu Server Edition

I tried googling the commands to install it from within Ubuntu server edition but none of them worked (most likely because I have no idea what I am doing) & this desktop is not set up on the internet yet. It is a Dell Pentium II

Pleaseee help me people what are my best options at this point? I'm so frustrated :(

---

### Post by wojox on 2010-08-27
You tried

```
sudo apt-get update; sudo apt-get install ubuntu-desktop
```

---

### Post by saucyb on 2010-08-27
> **wojox said:**
> You tried

```
sudo apt-get update; sudo apt-get install ubuntu-desktop
```
Yes I tried that. Nothing. And I'm not sure if I need to have the cd in when I'm doing this or not. I've tried both

---

### Post by arubislander on 2010-08-27
> **saucyb said:**
> ... this desktop is not set up on the internet yet.

Any possibilities of setting it up for wired internet and then retry the above commands?

---

### Post by wojox on 2010-08-27
> **arubislander said:**
> Any possibilities of setting it up for wired internet and then retry the above commands?

I guess that would help... :oops:

---

### Post by saucyb on 2010-08-27
> **arubislander said:**
> Any possibilities of setting it up for wired internet and then retry the above commands?

So I wired the internet up..entered the command and I get "E: Couldn't find package ubuntu-desktop"

---

### Post by wojox on 2010-08-27
> **saucyb said:**
> So I wired the internet up..entered the command and I get "E: Couldn't find package ubuntu-desktop"

What does this post?

```
cat /etc/apt/sources.list
```

---

### Post by saucyb on 2010-08-28
> **wojox said:**
> What does this post?

```
cat /etc/apt/sources.list
```

A huge entire page of "N.B. software from this repository is ENTIRELEY UNSUPPORTED by the Ubuntu team, and may not be under a free license...etc...it goes on forever

---

