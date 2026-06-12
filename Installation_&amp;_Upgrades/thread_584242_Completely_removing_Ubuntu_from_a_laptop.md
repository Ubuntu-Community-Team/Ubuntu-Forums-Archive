---
title: "Completely removing Ubuntu from a laptop"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by newagelink on 2007-10-20
[COLOR="Purple"]I set up a dual-boot on my brother's laptop; he has Windows XP, and I installed Ubuntu ... either 7.04 or the release before that.

He never uses it (he uses his laptop only for video games and iTunes) and wants me to remove it.

I don't know how; I've searched and have found nothing.

What do I need to do? Please help!

Thanks for reading.[/COLOR]

---

### Post by thewolf32 on 2007-10-20
You must delete the ubuntu partitions and then restore your Windows boot loader using your windows XP disk (select repair--> FIXMBR).

---

### Post by JPWheless on 2007-10-20
First, put in the Windows install CD and boot.
When it gets to setup, press R to get into the Recovery Console.
In the terminal-type thing, input "FIXMBR", and then "Y".
Then type "EXIT".
That'll get rid of GRUB.

Second, use something like Gparted and delete all the Linux partitions.
Then resize the Windows partition to fill the HD.
That should fix it.


Someone correct me if I'm wrong.

---

### Post by Herman on 2007-10-20
No problem, it's easy and there are many ways to do it depending in what software you have on hand.

Since I have a website that helps people to install Ubuntu, I thought it made sense to tell them how to uninstall it first. 
I wouldn't install anything I didn't know how to uninstall again later, and I wouldn't expect anyone else to, so the uninstall page comes before any of my other pages after the index in my Ubuntu install site.
(Well the Knoppix page is in front of it actually, but Knoppix is okay).

Here is is, there are lots of way to uninstall Ubuntu in there, 
[Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")   'Look before you leap', see how to uninstall Ubuntu, then install it.
You can take you pick and use any method that's easiest for you.

Basically all you will need to do is install some boot loader in your MBR so when you delete Ubuntu (and GRUB along with it), you'll still be able to boot something.
If you don't, it's nothing to worry about, you can still boot with a Super Grub DIsk.
The other thing you need to do is delete your Ubuntu partition with GParted prederably or whatever partitioner you last used to partition your hard disk.

That's it, Ubuntu will be gone.
Then you can do whatever else you want with your partitions, resize your old ones to fill the free space or make a new partition there and install another operating system if you want or make a data storage partition.

No-one has ever lost data that I know of, but one person had some partition table related trouble, the link is at the bottom of my uninstall page.
You would lose any data that might be in Ubuntu of course, if you don't save it somewhere else first, but that's only common sense.
It's also common sense to make a backup before using any disk partitioning software, but some people don't. 
If that's the case then it's their own fault if they lose data, everyone knows you are supposed to make a backup before partitioning.

Regards, Herman

---

