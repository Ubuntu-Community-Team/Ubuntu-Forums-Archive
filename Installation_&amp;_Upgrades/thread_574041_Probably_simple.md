---
title: "Probably simple"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by Xailan on 2007-10-12
I decided to go to Ubuntu from Windows and am having some troubles.

First off. I am new to Linux.

I do not know the exact specs of my computer, but, I have

AMD something or other 2.4 Ghz Processer
2 Gig RAM
200 SATA II HDD



My problem is this, I do not have any partitions on my computer, which I think may be the reason it is acting funny.

Anyways, when I boot the CD, it boots to the menu. If I tell it to install right away, with VGA as my display settings, I get nothing. It says it is loading the kernel and then something else, and then it goes to a black screen. Nothing happens from there.

I have found that if I change my display and tell it to install, I get it to at least goto the logo with the progress bar. Again nothing happens.

I know that Live CD's are slower because it is reading from the CD and not the HDD. But I do not think it is supposed to be that slow.


I have tried burning it at the slowest speed possible. 

Even when I try to check the CD for errors, it does the same thing.

Any ideas.

---

### Post by taurus on 2007-10-12
Try using the alternate CD since it's a text base but real easy to follow.

---

### Post by Xailan on 2007-10-12
What alternate CD?

---

### Post by phr0ze on 2007-10-12
Download this.

[http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso)

---

### Post by Xailan on 2007-10-12
Thanks

---

### Post by Xailan on 2007-10-12
Now when it boots, I tell it to install in text mode, and it goes to a screen what looks like a console. I can enter text and what not. What the heck do I do from there?

---

### Post by rkillcrazy on 2007-10-12
> **Xailan said:**
> Now when it boots, I tell it to install in text mode, and it goes to a screen what looks like a console. I can enter text and what not. What the heck do I do from there?

That all depends on what screen you're looking at.  I'm guessing you chose the install option when the machine booted with the CD.  From here, it's fairly simple for most folks with a technical background.  For those with less of a techie background, however, it may be slightly overwhelming.

**Are you installing on a system that already has an OS like Windows?**  This could change a few things.  I'm sure there are plenty of HOWTO articles out on the web that canb walk you through it.  I could run through a setup and try to grab screenshots but I can't promise you when I'd have them ready.  For that matter, I'm no pro as I've only been using Ubuntu for about 1.5 years.  I'm a Windows Network Admin so I could walk you through those installs with my eyes closed and my hands tied. :)

10-12-07
1704 EDT

---

### Post by rkillcrazy on 2007-10-12
Here, peep this out...
[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu]("http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu")

and this...
[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

It might be a good start.

10-12-07
1708 EDT

---

### Post by rkillcrazy on 2007-10-12
Another thing...

If you already have Windows on that machine.  Don't be so quick to blow it away and drop Ubuntu on it.  I'm not trashing Ubuntu in any way, shape or form but it seems like you're quite new to all of this.  The last thing you want to do is get stuck and have a head full of regrets!  

Try this, if you still have windows on that machine...
[http://wubi-installer.org/index.php]("http://wubi-installer.org/index.php")

It allows one to install Ubuntu on the same partiton as Windows.  This will keep you from having to repartition your drives.  It will edit your **boot.ini** (Windows boot file) and give you a choice at startup.  To use Wubi, download and install it.  It's quite small...  Running it will bring up a small app that will ask you a couple question like a user and password you wish to use for Ubuntu and it'll ask you where you wish to place it.  It will then download the alternate ISO and run a scripted installer that will keep you from having to answer all those questions you don't understand.  After it's finished downloading, it'll ask for a reboot.  Reboot and you should see the new boot.ini asking you what OS you'd like to load.  Choose Ubuntu and it will go through that acripted installer I just spoke of.  When it's done installing Ubuntu, it'll reboot.  When it comes back up, you can choose your OS again.  Choose Ubuntu and start playing around.  If you get stuck in Ubuntu or break something, you can reboot back into Windows and hop on the forums for some help.  If you find you hate it (don't know why you would but...) you can uninstall it from within Windows and it'll be gone...  Since the install didn't do anything to your hard drive's partitions, you won't see any permanent effects.

That might be a big bite to chew on for a newbie but it's far easier than going through the setup screens and being worried about what you might break.  I too was in your shoes at one point...

10-12-07
1806

---

