---
title: "I broke Remmina RDP protocol :("
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by vitalisius on 2012-05-02
Hello all!
 
I am a heavy Windows user, but very new to ubuntu.
So the story goes the following: I have wiped W7, installed Ubuntu, started playing with it, got very excited... and broke it on the next day :)

I use Remmina to connect to my work Windows machine just fine. And then, from what I recall, I did the following:

1) I go to freeRDP.com and read about freeRDP, get excited.
2) I go to Software Center, search for freeRDP and install
"RDP client for Windows Terminal Services"
"freerdp-x11"
version freerdp-x11 1.0.1-1ubuntu2freerdp1~932+26~precise

3) then I go [here]("http://code.google.com/p/rdp-runner/wiki/freerdp") and do this:

```
sudo apt-add-repository ppa:freerdp-team/freerdp
sudo apt-get update
sudo apt-get install freerdp-x1
```

4) then I go to Remmina and receive "Protocol plugin RDP is not installed." error message.


After googling the issue (to the extent of my knowledge, which is scarce) I have found [this solution]("http://www.linuxquestions.org/questions/slackware-14/rdp-protocol-is-not-available-in-remmina-911468/"), but I have zero ideas how to carry it out.

Could someone please explain:
1) What did I ***really*** do with those commands? What happened to the protocol?

2) How do I fix this.


In the meantime I use KRDC but I like Remmina more.

Thanx!!

P.S. BTW, why KRDC was not affected and works fine with RDP?

---

### Post by sforces on 2012-05-02
Same boat as you. I upgraded two systems from 11.10 64bit to 12.04 64bit. One a desktop, one a laptop. And I'm now getting the same error about it not being able to load the RDP plugin.

> **vitalisius said:**
> Hello all!
 
I am a heavy Windows user, but very new to ubuntu.
So the story goes the following: I have wiped W7, installed Ubuntu, started playing with it, got very excited... and broke it on the next day :)

I use Remmina to connect to my work Windows machine just fine. And then, from what I recall, I did the following:

1) I go to freeRDP.com and read about freeRDP, get excited.
2) I go to Software Center, search for freeRDP and install
"RDP client for Windows Terminal Services"
"freerdp-x11"
version freerdp-x11 1.0.1-1ubuntu2freerdp1~932+26~precise

3) then I go [here]("http://code.google.com/p/rdp-runner/wiki/freerdp") and do this:

```
sudo apt-add-repository ppa:freerdp-team/freerdp
sudo apt-get update
sudo apt-get install freerdp-x1
```

4) then I go to Remmina and receive "Protocol plugin RDP is not installed." error message.


After googling the issue (to the extent of my knowledge, which is scarce) I have found [this solution]("http://www.linuxquestions.org/questions/slackware-14/rdp-protocol-is-not-available-in-remmina-911468/"), but I have zero ideas how to carry it out.

Could someone please explain:
1) What did I ***really*** do with those commands? What happened to the protocol?

2) How do I fix this.


In the meantime I use KRDC but I like Remmina more.

Thanx!!

P.S. BTW, why KRDC was not affected and works fine with RDP?

---

### Post by ManfredU on 2012-05-09
Same issue here as well :-(

S.a. [https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/993981](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/993981)

---

### Post by morphics on 2012-06-28
Try installing the RDP plugin as follows:

```
sudo apt-get install remmina-plugin-rdp
```I had the same problem after an upgrade to 12.04 and found that the RDP plugin missing, so either the RDP plugin was somehow removed during the upgrade or the plugin structure has changed between Remmina versions. Either way, this fixed the problem for me :-)

---

### Post by sbay on 2012-07-01
Did exactly the same thing, with the same results. I decided to remove FreeRDP and stay with Remmina.
From the Ubuntu Software Center:
- Click Edit -> Software Sources... -> Other Software
- Remove the earlier added freerdp repositories
- Search for "remmina" and remove all installed results
- Search for "freerdp" and remove all installed results (including library and plugins)
- Search again for "remmina" and install "Remmina Remote Desktop Client". This should install Reminna and all necessary libraries again, with the working versions.

Hope this helps.

Good luck!

---

