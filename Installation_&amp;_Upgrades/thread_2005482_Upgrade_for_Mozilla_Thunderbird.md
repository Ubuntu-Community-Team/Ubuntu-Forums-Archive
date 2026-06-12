---
title: "Upgrade for Mozilla Thunderbird"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by bill23 on 2012-06-17
[SIZE=2][FONT=Garamond][FONT=Comic Sans MS]I am using the Ubuntu 12.04 LTS and have Mozilla Thunderbird 12.0.1 as my default email client. I have seen on the Windows side of my dual boot that the Thunderbird version is now 13.0.1. I am still waiting for the Linux/Ubuntu to come across with at least the 13.0 version.
I have downloaded the latest version,_ thunderbird-13.0.1.tar.bz2_, and it is sitting in my download folder. I am thinking of installing it but I have to admit when it comes to the whole tar.bz2 I am at a loss. I am hoping someone here can give me the command line that could be used in this instance and which could also be used elsewhere if needed with modification for future cases involving  tar.bz2 ?
I would then copy the information down and would be able to utilize it as a case by case warrants.
bill23[/FONT]
[/FONT][/SIZE]

---

### Post by Enigmapond on 2012-06-17
I would just add this PPA:

```
sudo add-apt repository ppa:mozillateam/thunderbird-next && sudo apt-get update && sudo apt-get upgrade
```

and you will get version 14 which is quite stable. Adding the ppa is better as you will get updates.

---

### Post by bill23 on 2012-06-17
Thanks Enigmapond, I am about to use the command and will let you know how it goes?

Tried the command and this is what I got:

bill48@ubuntu:~$ sudo add-apt repository ppa:mozillateam/thunderbird-next && sudo apt-get update && sudo apt-get upgrade
[sudo] password for bill48: 
sudo: add-apt: command not found

---

### Post by Enigmapond on 2012-06-17
My bad...

```
sudo add-apt-repository ppa:mozillateam/thunderbird-next && sudo apt-get update && sudo apt-get upgrade

```

It will work now..:)

---

### Post by bill23 on 2012-06-17
Once more into the breech, once more...

---

### Post by bill23 on 2012-06-17
Enigmapond,

We have lift off of Thunderbird 14.0 Beta. It worked, although I was not sure when my PC froze up on me and I had to manually power it off and restart it. There was some time left and I thought of opening up my Firefox, don't know if that had anything to do with what came next, a total shut down. Apparently enough of Thunderbird came through and it appears to be good, so far...??

It is amazing how a simple  (-) dash can affect things. I can see where it i important to have all the i's dotted and the t's crossed and the dashes  in there proper places.

Anyway thanks for the help

---

### Post by Enigmapond on 2012-06-18
No problem. Glad it worked out. You should change the thread to "Solved" in the thread tools above.
Cheers!

---

### Post by firekage on 2012-06-18
> **bill23 said:**
> [SIZE=2][FONT=Garamond][FONT=Comic Sans MS]_ thunderbird-13.0.1.tar.bz2_, and it is sitting in my download folder. I am thinking of installing it but I have to admit when it comes to the whole tar.bz2 I am at a loss.[/FONT]
[/FONT][/SIZE]

It is hard to install cause it has to be unpacked (tar xvf or tar -xfv) and then there should be some file like thunderbird.sh to install it - i think so based on Slackware but i'm no expert and if i'm wrong please correct me.

Thanks.

---

### Post by firekage on 2012-06-18
> **Enigmapond said:**
> My bad...

```
sudo add-apt-repository ppa:mozillateam/thunderbird-next && sudo apt-get update && sudo apt-get upgrade

```It will work now..:)

One question regarding PPA. If i want to install something new i have to add ppa, but where to find all of this ppa? Maybe it is stupid question but if i want to install something i look on goolge trying something like: how to install <software> on ubuntu and there is provided ppa but are there any sites that provides ppa?

I wanted to install Firefox 13, i had to add ppa with different name than your ppa - how should i know which ppa is for what version of software and so on? It;s hard to explain because my english is not quite well. I will try to explain like this:

What's the difference between:

mozilla-next
mozilla-daily
mozilla-stable
mozilla-security

I don't know which version is for what.

---

