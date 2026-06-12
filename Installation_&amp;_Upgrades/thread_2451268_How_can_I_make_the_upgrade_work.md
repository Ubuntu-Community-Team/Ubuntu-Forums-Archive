---
title: "How can I make the upgrade work"
date: 2020-09-30
forum: Installation &amp; Upgrades
---

### Post by Odense on 2020-09-30
I wanted to upgrade my Ubuntu to the latest LTS (Ubuntu 18.04.5 LTS > Ubuntu 20.04.1 LTS) but first got a warning that I would have to enable more things afterwards. How do I do what is suggested?


Then the upgrade was completely stopped with "requirement" that I do a "ppa-purge" How do I do that?


I probably need the "for dummies" versions of the answers to both questions. &#128526;[ATTACH=CONFIG]287071[/ATTACH][ATTACH=CONFIG]287072[/ATTACH]

---

### Post by deadflowr on 2020-09-30
A nice run-through on ppa-purge and how to use it here:
[https://askubuntu.com/a/310]("https://askubuntu.com/a/310")

My suggestion is if you do not know which ppa's you may have added, you can double check in the /etc/apt/sources.list.d directory.
This is where ppa entries are added, each will have it's own list file.

---

### Post by Odense on 2020-10-10
Hi deadflowr,
Thank you for answering.
Please see the attached screenshots.

I have now found the list in the /etc/apt/sources.list.d directory.
However I had already tried installing ppa-purge - but the repository could not be found.
So how do I get this working?

---

### Post by deadflowr on 2020-10-11
ppa-purge is in the community repository (aka universe), which sometimes is not enabled by default.
```
sudo add-apt-repository universe
sudo apt update
```
If any error show, you'll need to fix them first before it will run properly.

---

### Post by rsteinmetz70112 on 2020-10-12
As a random comment, I'm surprised that the do-release-upgrade recommends ppa-purge and it is not in the core repositories.

---

### Post by Odense on 2020-10-14
> **deadflowr said:**
> ppa-purge is in the community repository (aka universe), which sometimes is not enabled by default.
```
sudo add-apt-repository universe
sudo apt update
```
If any error show, you'll need to fix them first before it will run properly.

Thank you again deadflowr.

Unfortunately it does still not work. Please look at the attached screenshots and tell me what I need to do.

---

### Post by deadflowr on 2020-10-14
Your repos are broken you need to fix them before proceeding.
The kazam ppa had no archives for anything newer than 14.04 so that should be able to just remove without ppa-purge,
```
sudo add-apt-repository -r ppa:kazam-team/stable-series
sudo apt-get update
```

---

### Post by dragonfly41 on 2020-10-14
I find that Y PPA Manager helps to tidy up PPA installations.

---

### Post by Odense on 2020-10-15
> **deadflowr said:**
> Your repos are broken you need to fix them before proceeding.
The kazam ppa had no archives for anything newer than 14.04 so that should be able to just remove without ppa-purge,
```
sudo add-apt-repository -r ppa:kazam-team/stable-series
sudo apt-get update
```

After I removed the kazam ppa the update was able to start - but stopped again after a while. I rebooted and tried again and it stopped again.
After another reboot get to the gnome classic desktop I prefer but it does not react to the keyboard, the mousepad or the USB mouse I normally use so I cannot even log on.
How do I these things to work again?

---

### Post by rsteinmetz70112 on 2020-10-16
What error message do you get when the update stops?
You have several nonstandard repositories in your sources including at least one from Xenal. 
You should remove them.

---

### Post by Odense on 2020-10-17
> **rsteinmetz70112 said:**
> What error message do you get when the update stops?


I don't know - I took screenshots of the messages but i cannot access them now.

> **rsteinmetz70112 said:**
> You have several nonstandard repositories in your sources including at least one from Xenal. 
You should remove them.

I thought I had tried to do that.

But now it boots to a (still the old version of Ubuntu) and with my selected classic gnome desktop. BUT IT DOES NOT REACT TO NEITHER THE KEYBOARD, THE MOUSEPAD OR A USB MOUSE. So how do I make the input devices work again?

---

### Post by Impavidus on 2020-10-17
Usually release upgrades just work. If they don't, there's some underlying issue, that's hard to diagnose and fix. Even if you manage to get the upgrade installed, the underlying issue may still be present and cause instability. So, when it takes more than a few hours to fix a release upgrade (and you've been struggling with this for days), the best solution is a fresh install.

---

### Post by Odense on 2020-10-18
I certainly made several mistakes.
I decided to do a fresh install which worked until I tested Windows 10.
After tested Windows 10 the Ubuntu partition does no longer load the kernel but ends with grub >
But I will continue that problem in another thread.

---

