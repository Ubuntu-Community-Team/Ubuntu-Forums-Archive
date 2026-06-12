---
title: "A friend of mine wanting to switch to Ubuntu... need help"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by makinasvp on 2008-11-25
Ok so a friend of mine has Windows XP installed and I've convinced him to make the switch to Linux.

Now, he's got a lot of mp3s and he is a CounterStrike Source player.

What are his best options? His mainly making the switch because he keeps getting blue screens of death, windows just isn't stable for him. But he wants to keep all his mp3s, and wants to be able to play CounterStrike Source.

He's got a dual-core processor (FX-60), 3GB of RAM, and an ATI HD4870.

Please help!!

---

### Post by decard_pain on 2008-11-25
well ubuntu +wine should run counter strike.
also he will need to install the restricted-extras package to play mp3s

i suggest a duel boot just incase counterstrike won't run


all he needs to do is install ubuntu and the setup can resize the xp partition  and install grub for him

hope this helps

---

### Post by makinasvp on 2008-11-25
> **decard_pain said:**
> well ubuntu +wine should run counter strike.
also he will need to install the restricted-extras package to play mp3s

i suggest a duel boot just incase counterstrike won't run


all he needs to do is install ubuntu and the setup can resize the xp partition  and install grub for him

hope this helps

Ok how exactly does he need to do this? Because I am going to be doing it for him. Can you please help me?

Also keep in mind he's got an ATI HD4870 video card, does that even work with Linux?

If yes, please tell me how I can do this **"all he needs to do is install ubuntu and the setup can resize the xp partition  and install grub for him"**

---

### Post by ndefontenay on 2008-11-25
Hi.

The mp3 will be just a little extra work after the installation of linux.

You just need to install the ubuntu extras which comes with flash player java mp3 support etc... in add/remove look for gstreamer and pick them all too.

For counter strike, I'm not an expert but I know that most CS servers are in fact linux, the client should be easy to install.

I can't give you the steps but I've found an article which should detail that for you.

It might not be just next next next finish though.

[http://www.cstrike-planet.com/tutorial/1/5](http://www.cstrike-planet.com/tutorial/1/5)

This will require some test and trial. 

So the best way would be for a start to dual boot (a partition for windows, another for linux), install CS and test it. move the mp3 under linux then ditch windows when everything works to your friend's taste.

To make a long story short: It's possible

---

### Post by taurus on 2008-11-25
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

or

[https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)

---

### Post by ndefontenay on 2008-11-25
For any issues with the CS problem, post a new message for that purpose and others for the mp3s if you can't get it to work.

(There's already plenty of tutorials on how to get mp3 to work though, so look a little first)

Good luck

---

### Post by decard_pain on 2008-11-25
well thats the thing ati cards are dodgy in linux (they are getting better slowly)
he just needs to put the live cd or usb in ...reboot .follow on-screen instrutions

then it will just be installing a few packages from the add and removee packages

just search for wine and restricted

---

### Post by makinasvp on 2008-11-25
Ok the thing is, we have a copy of Feisty Fawn 7.04 64bit, because unfortunately when we tried to download intrepid, it just wouldn't even load up, even after burning it at slowest speed.

Now, with Feisty Fawn, if we install it, will we lose all of his mp3s that are on his windows partition?

Because at this point, he only has one partition installed, and that's his Windows partition. He doesnt have any other partitions.

What can we do?

---

### Post by ndefontenay on 2008-11-25
May I suggest that you perform some backups of his important data before you even consider resizing his partition ^^'

The partitioning would be done on installation. If he has 2 different hard disks, then the easiest way would be to use the one where windows is not installed for linux. 

Make sure to move all his data out of it first because anything on it would be erased.

What you could do is give us a little more details on the way his data and computer is set up. 

1) How many HDs?
2) Are data scattered a bit everywhere or are they all in "my documents"
3) are his data stored on an external hard drive?
4) Would you be able to find an external hard drive to perform backups first?

With this knowledge we could help you taylor a nice installation safe from loss of data.

---

### Post by ndefontenay on 2008-11-25
ok I got the answer while I was writing my questions.

I wouldn't resize a partition without backups. Depending on the total size of mp3, I would burn them to one/many DVDs, copy it to an external HD.

Don't rush. He will get it one week later what does it matter?

Try to find out an external HD which could hold on his data first. This way if eventually the repartitioning go wrong and you loose windows the data won't be lost.

---

### Post by ndefontenay on 2008-11-25
For the version, I would suggest you try to get Hardy Heron. Ibex being pretty new, there are still a few quacks (I like to wait a couple of months)

There's a huge difference between FF and Hardy Heron. Find a place where you could download it. Order it online. You would get it by mail if you can't download.

---

### Post by ndefontenay on 2008-11-25
> **decard_pain said:**
> well thats the thing ati cards are dodgy in linux (they are getting better slowly)
he just needs to put the live cd or usb in ...reboot .follow on-screen instrutions

then it will just be installing a few packages from the add and removee packages

just search for wine and restricted

I've just got an ATI. I just had to press a button to activate the proprietary driver and it worked like a charm. Haven't tried it with games though.

---

### Post by makinasvp on 2008-11-25
So are you saying that with Hardy Heron we can simply resize the partition during the install and have linux installed?

By the way, all his mp3s are in his My Documents/My Music folder. All organized.

---

### Post by ndefontenay on 2008-11-25
Yes.

At the installation you got the choice to do that but again. Do backups!!!

If it's in my documents Hard Heron will even ask you if you want to copy the data from my documents to linux provided you got enough space...

---

