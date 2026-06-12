---
title: "Dual Boot XP ProSP2 and Ubuntu 6.06 on one 320gb SATA 3.0gb/s Harddrive"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by Azerial on 2007-08-28
New computer should be here tomorrow once I get it put together and everything plugged up Im going to be wanting to Dual Boot Xp Pro SP2 and Linux Ubuntu 6.06

Yes I know I have an older Version of Ubuntu but a friend had the distro cd and gave me one of his six copies, and I am to understand I can upgrade it to the most recent version, I assume thats to be done without reformatting.

Anyway the Hard Disk I'm installing to is a 3.0gb/s SATA Seagate Barracuda 320gb 7200RPM Drive. I want to partition this drive so I can have XP and Linux on it as a dual boot.

So here I am asking for an easy to understand Step By Step on this.  Ive NEVER installed a Dual Boot setup before, Only one OS per HD and its always been Windows, and honestly its been a few years since I last installed an OS on a PC Peroid.  So I might be a tad rusty if not a total newb like I am with Linux right now.  

Oh I am planning to run XP Pro though a VM within Linux so I keep XP for games and use the VM to allow me to use all my favorite programs I havent found a Linux version, or alternative to that I like, or ones that can not be run though WINE.

---

### Post by merlinus on 2007-08-28
First of all, upgrading to a new version is often dicey, so I recommend that you start with 7.04.

Second, if you plan to run xp in a vm, then you do not need to set up a dual-boot system.

-merlin

---

### Post by Azerial on 2007-08-28
Im Dual Booting so I can play games that dont have LInux versions or able to be isntalled with Wine,  cause I understand VMs SUCK for games

---

### Post by merlinus on 2007-08-28
OK.  Good info here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I strongly recommend deleting temp and other unneeded files, backing up data, setting  virtual paging to zero (set it back after install), and defragging windows several times before installing ubuntu.

-merlin

---

### Post by ddrichardson on 2007-08-28
If running Windows is important to you and you're just dabbling with Ubuntu - have you considered running Ubuntu as a VM in Windows?

[VM Ware Player]("http://www.vmware.com/products/player/") is free and there are Ubuntu images available [here]("http://isv-image.ubuntu.com/vmware/").

I run several versions of Ubuntu this way for testing purposes and have found that they aren't quite as fast as a full install but are far faster than the Live CD, especially if the hard disk space is pre-allocated (around 8 Gbs).

---

### Post by Azerial on 2007-08-28
Please Stop giving me alternatives to my question.

I need a Step By Step guide that even a moron could understand. On how to Install XP Pro first, set up the partitions, and then install Linux so I can get the nifty little dual boot screen and be able to pick the OS I want to run before it moves past that screen.

Why is everyone saying "oh run xp in vm or oh run linux in vm" .... thats not what my question is... sorry If I seem rude but Im just getting answers that are off topic and its annoying.  Cause Ive googled the hell out of this and I cant find a walkthough that has what I want in it, thats written in a way that makes sense to me.

---

### Post by Azerial on 2007-08-28
> **merlinus said:**
> OK.  Good info here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

and

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I strongly recommend deleting temp and other unneeded files, backing up data, setting  virtual paging to zero (set it back after install), and defragging windows several times before installing ubuntu.

-merlin

Well damn looks like I missed your post before my last reponse thanks for the links I'll give those pages a read over and bookmark em. and Pray my effin printer will work so I can make a copy.

Offtopic - Never buy Lexmark and HP printers they are damned to fail within a week.

---

