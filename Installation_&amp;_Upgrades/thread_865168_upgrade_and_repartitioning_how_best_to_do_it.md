---
title: "upgrade and repartitioning: how best to do it?"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by eeeandrew on 2008-07-20
hi all, got quite a big job to do and not sure how to go about it. At the moment I have Ubuntu 7.04 installed dual boot with windows vista. All parts of ubuntu are on one partition. I've read in the forum its always best to seperate them. I also want to upgrade to either 7.10 or 8.04 and remove vista completely. I have a couple of questions about doing this. 

1) whats the best way of going about making this many changes? The first time I installed I used a guided install so an explanation of partition formats and sizes would work wonders.

2) My WLan card is running from ndiswrapper and my sound card I had to edit the driver file myself. Will these work better in newer versions?

audio card is: 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

WLan card is:Atheros AR5007EG

3) I've spent a bit of time downloading applications that I like. Is there a way to save a list of these that ubuntu can then use to reinstall. I would also quite like to preserve my desktop and theme if this is possible

Thanks in advance,
Andrew

---

### Post by Wazoot on 2008-07-20
Well to upgrade 7.04{or any other version} to 8.04, download the 8.04 .ISO from the site and burn to a disk from inside Vista, or linux doesnt matter
Boot from the live cd and click install
There should be an upgrade option?
Will save all of your data/applications/any other files. So you should be set there.

---

### Post by poofyhairguy on 2008-07-21
> **eeeandrew said:**
> . All parts of ubuntu are on one partition. I've read in the forum its always best to seperate them. 

 I would also quite like to preserve my desktop and theme if this is possible


The trick is to separate your root (/) partition with your /home partition. In the future do a custom install and make a separate partition for the root (at least 8 gigs if you can) than for the home. Since choices like theme, Firefox bookmarks, wallpaper, and many other settings are stored in your home partition, you are able to reinstall the core of the OS (or upgrade) without losing anything but the programs you installed (I don't know a way to automate that yet as your third question asks).

---

### Post by zvacet on 2008-07-21
For making separate home look [here.]("http://psychocats.s465.sureserver.com/ubuntu/separatehome")

>  Is there a way to save a list of these that ubuntu can then use to reinstall.

```
dpkg --get-selections > installed-software
```

You will get text file in your home directory.If you make separate home before it is O.K. for that file to stay there.If not e-mail it to yourself(I believe you have gmail,yahoo...address).After that 

```
dpkg --set-selections < installed-software
dselect
```

That should install all packages you want.

---

### Post by eeeandrew on 2008-07-28
Thanks to everyone for their help. As I understand it, I'll need to wipe my hard drive and start over with the separate home and root(backing up my data of course)which will rid me of vista and get things ready for solo linux in one foul swoop. I can then use that list trick to reinstall packages. Only thing not answered so far is what I'll need to do to get my hardware running again. Anyone have any ideas?

Thanks,
Andrew

---

