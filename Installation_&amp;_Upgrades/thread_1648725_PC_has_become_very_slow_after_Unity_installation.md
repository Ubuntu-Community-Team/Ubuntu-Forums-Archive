---
title: "PC has become very slow after Unity installation"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by chirag64 on 2010-12-19
So I'm not 100% sure that my Ubuntu 10.10 has become slow because of Unity or some other reason, but yesterday I installed it using Ubuntu Software Centre.

I logged out and logged in using the Netbook Interface to see how it worked. My Ubuntu suddenly became very slow and unresponsive.

I logged out and logged in using the Desktop interface again, but it continued to be slow and unresponsive. I went back to Ubuntu Software Centre and uninstalled Unity, even tried rebooting my computer, but its still very slow. 

Any ideas? :(

---

### Post by theasprint on 2010-12-19
I don't know how to help. But by opening the processes page may help to see what is taking so much of your netbook processing power.

If there is nothing abnormal, perhaps a reinstallation?

---

### Post by sikander3786 on 2010-12-19
Nice suggestion **theasprint**;-)

But I don't think re-install is an absolute necessity at the moment.

@**chirag64**: From Applications > Accessories > Terminal, post the output of these commands while your computer is acting slow.

```
top
```

```
free -m
```

And moreover, the problem might be caused by graphics drivers. Which graphics card is there and did you intall any proprietary drivers?

---

### Post by theasprint on 2010-12-19
Thanks sikander3786.

Just wondering how you find out these geeky terminal commands.

I don't think its graphics drivers because the complaint is about unresponsiveness.
Furthermore I think Ubuntu Netbook Edition should have better support for low-end graphics.

*Sent friend request (something like that, new to the forum style)

---

### Post by chirag64 on 2010-12-21
Hey, I just logged booted up Ubuntu today to try out your commands, when I suddenly realized that the visual effects I had enabled were off. I went into System >>> Preferences >>> Appearance to see what was wrong and I was met with an error that said I can't change my settings since **Mutter Window Manager** was running.

I went to Ubuntu Software Centre and removed Mutter Window Manager, restarted PC and voila :D

---

### Post by chirag64 on 2010-12-21
Thnx for the help guys :)

and **theasprint**: reinstallation for a minor problem like this?!? :O
I thought that was a Windows thing ;) :P

---

