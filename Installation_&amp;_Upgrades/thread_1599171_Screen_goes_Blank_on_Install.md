---
title: "Screen goes Blank on Install"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by threecoins on 2010-10-17
Okay, so I used WUBI to install Ubuntu 10.10 from Windows. I restarted and went chose Ubuntu when given an operating system choice. It says something about how it needs to finish the installation and press escape to choose other options. I have tried all the other options and the normal one. Each time, the screen goes blank with a flashing cursor. I cannot type anything into it. The only difference between normal mode and safe graphics are that I can see some scrolling text when I use safe graphics mode for a while. Then it just goes back to that blank screen with a flashing cursor. Any ideas? I have this trouble with all versions of Linux. I want to dual boot it with Windows...


3.06 GHz processor (single core)
1 GB ram
ATI Radeon 9250 256MB graphics card
Windows XP

---

### Post by mörgæs on 2010-10-18
I don't understand what this is about, sorry. Is this a Wubi install (running in Windows) or a dual boot (side by side with Windows)?

---

### Post by threecoins on 2010-10-19
I've installed it this time using the alternate install CD. I installed it successfully and then I start it up. I go into the GRUB loader and select the recovery or normal start up. For the normal, it goes about three seconds and shuts down. I tried pressing ALT+CTRL+F2 and it went into the screen and I started typing a command. It started entering the command that I was typing for a second and then froze. The screen lowered the quality of the lettering that I had typed and then went into a screen like your computer is shut off. (The monitor had a blinking light and it was a blank screen) I am not sure what issue this could be. I cannot type long enough to get a command in. Hopefully we can get this worked out soon... windows is making me mad and I am searching for an alternative. I've heard great things about Linux and Ubuntu more specifically, however this is kind of turning me off to it. I'm hoping it is user-friendly to noobs like me lol. I guess that you could say the monitor goes to sleep.

Tried nomodeset instead of splashscreen and it didn't work. I got some text and then it went to sleep...

---

### Post by threecoins on 2010-10-24
Someone want to help me? I know you are busy but I've waited quite a while now...

---

### Post by sikander3786 on 2010-10-24
If you are really considering a dual boot, instead of Wubi, I will recommend a side by side install.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Everyone here is willing to help but it doesn't help when you type in large paragraphs which makes reading it more difficult therefore most of people see and leave it without reading through.

We can help you if you want to dual boot as mentioned in the above post.

If you wan't to stick with Wubi, you'll have to wait until someone experienced with that jumps in.

---

### Post by threecoins on 2010-10-24
On a seperate partition?

---

### Post by sikander3786 on 2010-10-24
Yes. You will need two partitions for that. One '/' partition which will contain everything including boot, system and user files. And another Swap partition. You can have separate partitions for /home, /var etc but that is an advanced setup.

This page will guide you through most of the setup process.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

If you are unsure, boot into a live CD and post the output of

```
df -h
```

```
sudo fdisk -l
```

That will tell us about your partitioning setup.

A regular install has many advantages over Wubi including performance, if you are wondering.

---

### Post by threecoins on 2010-10-24
Okay, I have already done that, I believe. I uninstalled the one installed with Wubi and installed it using the alternate live-cd installer, however it was on the same partition. If that won't work, I need to know how to uninstall it. Sorry for my inexperience.

---

### Post by sikander3786 on 2010-10-24
You'll still need to boot the output of

```
sudo fdisk -l
```

So we can understand your setup.

What do you mean by "it was installed on the same partition"? Did you install it on the Windows partition? Are you able to boot Windows now?

There is no specific method of uninstalling a regular install. You need to format the partitions containing it and it will obviously disappear.

---

### Post by threecoins on 2010-10-24
And how do I do that? I cannot even access the command line. When I select Linux on GRUB, it starts to boot and then the monitor goes to sleep.

---

### Post by sikander3786 on 2010-10-24
> Tried nomodeset instead of splashscreen and it didn't work. I got some text and then it went to sleep...

nomodeset parameter works in most cases. What was the exact text rendered in those errors? It might be informative if you can reproduce that.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by threecoins on 2010-10-24
There aren't errors, just some text scrolling through that normally appears.

---

### Post by sikander3786 on 2010-10-24
Can you post you Hardware Specs please. Which graphics card?

There are other boot options listed on the page in my above post like nomodeset, noapic etc. Try with all of them. CD should boot you to the desktop with any one of them.

I know you are working hard to get it working but it is not easy to track problems like this. Please be patient.

You are making it harder for us by not answering the queries. I repeat,

> What do you mean by "it was installed on the same partition"? Did you install it on the Windows partition? Are you able to boot Windows now?

---

### Post by threecoins on 2010-10-24
First post has the specs. If I am correct, a partition normally has a seperate drive letter. I do not see one in My Computer in Windows. I selected largest free space when I installed it, though.

---

