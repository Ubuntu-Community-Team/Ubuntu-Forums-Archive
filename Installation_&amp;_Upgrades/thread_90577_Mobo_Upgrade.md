---
title: "Mobo Upgrade"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by groundpounder on 2005-11-15
I have a K6-2 533 MHz system running Hoary.  It's slow as hell, which I have concluded is due to the cheapo mobo in it.  I have a better mobo I want to install, but I'm wondering how Hoary will handle it when it boots up with the new hardware.  I'm going from a micro atx with integrated video & sound to a atx mobo with a separate agp vid card.  I don't have a sound card at the moment.  Will my current install still function, or will I have to start all over?

---

### Post by Kyral on 2005-11-15
Well, X will prolly go kaput because of the change in video device, but a simple ```
sudo dpkg-reconfigure xserver-xorg
``` will fix it. Things may get very sketchy. It might be easier to take this opportunity to do a clean Breezy install

---

### Post by groundpounder on 2005-11-15
ok, well if I'm going to reinstall, how can I save all my bookmarks from firefox and my mail & contact info from evolution?

---

### Post by wrtrdood on 2005-11-15
Don't sweat it.  One thing Linux is very good at is moving from machine to machine, especially when you use the default install of Ubuntu.  (try THAT with Windoze...) 

I have a habit of moving hard drives from one machine to another (accomplishing the same thing you're talking about) and it never burps.  There's so much in the default kernel that you'd have to have a really strange configuration for it to not work.  I agree that X might complain but usually it just drops to a lower resolution and keeps going.

As for your personal files--- you did make a /home partition, didn't you?  No?  Shame, shame... :p 

Even so, simply tar it all up into a single backup archive (tar czf backup.tgz /home/youruser) and copy it to somewhere safe (either a partition that won't get formatted or external media).  You can restore it later and be back in business.  (tar xzf backup.tgz)

---

### Post by groundpounder on 2005-11-15
Thanks, that makes me feel a little better.  I do have a second hard drive in there with a couple of fat32 partitions where I keep most of my files.  I also have this thing dual booted with win2k, but I've only used that once or twice since I set this thing up.  my problem backing up that mail and contacts is that I don't know where it's stored or what the name of the file would be.

---

### Post by Kyral on 2005-11-15
This is why having a separate /home rocks. Everything is stashed there, so if you wanna reinstall, just tell Ubuntu to mount it as /home without formatting (use existing data). My /home has existed over 4 reinstalls now :D

Mail and contacts can be a pain. Best bet would be to export them using your mail client and use that file as a backup

---

