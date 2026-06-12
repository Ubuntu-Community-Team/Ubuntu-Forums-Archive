---
title: "Cannot use 10.10"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by beacon on 2010-10-29
There are complaints that 10.10 is sticky and slow. It's worse than that; I can't use it at all. The problem began when Thunderbird 3.1.5 suddenly froze each time I tried to log in (on 10.04). I read all the threads I could find, but nothing worked. 

At the same time I noticed that 10.10 was available for update, and I hoped that by getting the update I might resolve the problem with Thunderbird. Instead, I can't get anything to work. The desktop appears to be in order, and I have been able to use Chrome to read a newspaper, but all other applications open, then freeze immediately. There is no way even to close down except by switching off at the mains.

Please can anyone help?

---

### Post by linux-hack on 2010-10-29
You must give more info then that. what computer do you have? are there any error messages ? 32bit system or 64bit ? etc...

---

### Post by beacon on 2010-10-29
I'm not sure how much information would be relevant. I have a custom-built computer with the following specs:

AMD 64bit 3500core
1 GB ram
NVIDA 57001e PCI-Express GFX
Ambit Motherboard
6 USB 2.0 ports
2 IEE1394 Firewire Ports
AOPEN DVDRW Drive

I'm not certain what all that means, butit is the information provided by the company which built it.

I have run ubuntu on it for some time and had very few problems with 10.04. As I said the problem began with Thunderbird which continues to annoy me.

---

### Post by dino99 on 2010-10-29
check your driver activation: system admin addiotional driver

watch at errors logged: system admin logviewer, and into .xsession-errors (/home, ctrl+h to unhide it)

When troubles comes up, its a good idea to clean the system (clean , atoclean, autoremove), deactivate the exotic ppa if any ( is compiz enabled ?)

then:
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure thisweirdappthatmakesmemad

---

### Post by beacon on 2010-10-30
Thanks for the advice. I'm afraid I couldn't follow the suggestions, since the computer was completely 'frozen'. I finally gave up, and since I needed access immediately, I bought a new hard drive and re-installed 10.10. I don't know whether it was the hard drive or something else,but so far, after an hour's use, the screen hasn'tlocked.

---

