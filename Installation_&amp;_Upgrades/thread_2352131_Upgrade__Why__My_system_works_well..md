---
title: "Upgrade?  Why?  My system works well."
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2017-02-09
I'm running 12.04 LTS on a Dell Inspirion e1505, it runs very well on an SSD, is nice and fast.  Frankly, I don't need or want a new computer.

Today has been a perfect waste of time.  I've spent over 10 hours trying to figure out which version of Linux to get.

So, I have to ask, "why should I upgrade to a higher version of Ubuntu anyway?"  It would be nice if I could just copy over my home folder and everything- data, inconsequential programs, FFMPEG etc, and it would all appear on the new installation!

Such isn't  the case.

I'll never use Unity and the Lubuntu is too simple for my needs.  There are a lot of choices.

As for new bells and whistles and the latest program that'll eat up more of your time....I'm not interested.

All I really need is Firefox and Thunderbird to be updated periodically.  But, is the kernel updated too? Or will there be a point in time that my system can't be updated (I didn't say "up-graded")?

Ain't nothin' easy in this life.  I'm tired of trying to figure out what to do, am no techy, and have an idea that when 12.04 is no longer supported that it wont matter much anyway (sort-a-kinda).

You folks have any practical and realistic ideas?  Too much time is spent on solving problems like this and the dread of a new version of Ubuntu always translates, for me, into a huge amount of time to spend fixing stuff that's broken or wont work properly.  Time is the currency of life.

---

### Post by QIII on 2017-02-09
Hello!

When 12.04 goes out of support, it will matter a great deal.  You will not get security updates and you will be vulnerable.

>  It would be nice if I could just copy over my home folder and everything- data, inconsequential programs, FFMPEG etc, and it would all appear on the new installation!

Is there some reason you believe you can't do exactly that?  I do it every time I install a new release.

---

### Post by PDA1 on 2017-02-09
> **QIII said:**
> Hello!

When 12.04 goes out of support, it will matter a great deal.  You will not get security updates and you will be vulnerable.



Is there some reason you believe you can't do exactly that?  I do it every time I install a new release.


Well, of course you can just copy stuff over.  But.....aren't there some parts of all those files that are buried in the, what I call, "meta incognita"?  It's the area in the "files system" below the home folder.  Isn't a connection lost between the files system and the home folder and thus the programs wont run properly?

---

### Post by QIII on 2017-02-09
There is a way to make a list of your installed packages and re-install them after the upgrade.  You can copy files from /var and /etc (fstab and hosts, for instance) as necessary.   You do the install without formatting /home (but always do backups to be sure.)

I can install a new release and be off and running with everything just the way I want it in about 30 minutes.

---

### Post by PDA1 on 2017-02-09
> **QIII said:**
> There is a way to make a list of your installed packages and re-install them after the upgrade.  You can copy files from /var and /etc (fstab and hosts, for instance) as necessary.   You do the install without formatting /home (but always do backups to be sure.)

I can install a new release and be off and running with everything just the way I want it in about 30 minutes.

You're a better man than I am....that's for sure.

Keep in mind my computers an old one- but I like it.  

[I]You can copy files from /var and /etc (fstab and hosts, for instance) as  necessary.   You do the install without formatting /home (but always do  backups to be sure.)

[/I]Oh boy- that would be great....if it worked.

[I]There is a way to make a list of your installed packages....

[/I]Can you tell me how to do that?

Thanks.

---

### Post by QIII on 2017-02-09
> **PDA1 said:**
> 
> You can copy files from /var and /etc (fstab and hosts, for instance) as  necessary.   You do the install without formatting /home (but always do  backups to be sure.)

Oh boy- that would be great....if it worked.

It does if you have a separate /home and during the disk partitioning phase you select /home for use but NOT for formatting.

> [quote]There is a way to make a list of your installed packages....

Can you tell me how to do that?[/quote]

Sure.  Have a look at post #5 [here]("https://ubuntuforums.org/showthread.php?t=2350552").

---

### Post by PDA1 on 2017-02-09
> **QIII said:**
> It does if you have a separate /home and during the disk partitioning phase you select /home for use but NOT for formatting.



Sure.  Have a look at post #5 [here]("https://ubuntuforums.org/showthread.php?t=2350552").


I took a look at the various threads which led to further threads....forever.  It sounds simple for those that know how to do it.  I'm sure i'd mess the whole thing up.

Oh well. Thanks for the help anyway.

---

### Post by Impavidus on 2017-02-10
Reasons to upgrade:
- Sometimes people discover security holes in software. Developers make fixes and push those fixes to all users on supported systems. The bad guys also get those fixes and can then easely find the security holes they fix. Next they can attack the people who use the software on unsupported systems.
- You use your computer to watch videos? Video encodings change to make them more efficient, provide better quality etc. Video players must change along with them. If you use an unsupported system, you will, after a while, get more error messages that your system can't play the media type.
There are other reasons I can think of.

Have you ever manually changed files in /etc or /var? If you don't use your computer as a server and don't need special network configuration, probably not. In that case there's no reason to copy files from /etc or /var to a new system. Reconfiguring wifi etc. shouldn't take more than a few minutes. All other configuration is in your home directory.

I understand that you want Xubuntu. That means a completely new, but similar (as in classical) looking user interface. Copying your configuration files won't be very useful (although it won't harm), but it's easy to configure the user interface of Xubuntu. Shouldn't take more than half an hour to get something basic. Maybe two hours, as you're new. Or maybe you'll like the default enough not to change anything.

You can create a list of installed packages and install them on your new system. QIII gave you the link. It's not always useful, as some packages may no longer exist, some may have been replaced so you install the old default alongside the new default, which leads to duplication and you may prefer the new default anyway. Or the software was buried so deeply within the system that you didn't even know it existed. Better not touch those programs. Furthermore, many of the programs you use get still installed by default. Firefox, thunderbird, libreoffice, all installed by default, so no need for complicated procedures to get them installed again.

Just make sure you copy your documents and your thunderbird/firefox configuration, including address book, bookmarks etc.

---

### Post by RobGoss on 2017-02-10
> **PDA1 said:**
> I took a look at the various threads which led to further threads....forever.  It sounds simple for those that know how to do it.  I'm sure i'd mess the whole thing up.

One of the best things about Linux / Ubuntu is this community, the people here are always willing to help if you run in to trouble 

The only way you will learn is hands on and by trial and error, setting up a new installation is pretty simple once you've done it a few times

Upgrading to the latest distribution is not always for everyone but if you're like myself I alway try to keep things as they should by only installing the Long term support releases, which allows you to enjoy your desktop with out upgrading every few months 

In some cases Linux is no different then Windows, at least with Linux they make it simple  to install a new distribution and we have some many to choose from that along it worth it's weight in gold

---

### Post by PDA1 on 2017-02-10
Here's an odd thing.  The reason I couldn't get those iso Live DVD's (they sure don't fit on CD's) is because my machine is 32 bit.  Once I downloaded the correct iso then all went well. 

So, I tried Ubuntu 16.04 and believe-it-or-not I wasn't particularly bothered by the "Unity" side bar.  Especially when I found out how to put the thing at the bottom and make it smaller.

But....the real matter is all of those programs I already have!  Some of them might not work with 16.04 and then I'll kick myself!

Yes, the Ubuntu online help is extensive and very good.  Sometimes the answer are correct too!

Well, we shall see what we shall see.

Am I correct in saying that if I don't like the Unity interface or, whatever it's called, I can change it (easily) to the one that's like old 10.04?  I'm running gnome something-or-another desktop (I guess that's what the thing's called) and very much want things that way.

Thanks fellas

---

### Post by RobGoss on 2017-02-10
Depending on what hardware you have on your machine the Unity desktop is well developed in my opinion. The launcher has some cool features if you what it to conceal it self

With Linux especially Ubuntu, you can install the different desktop environments

This post will show you wants available
[http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-kinds-of-desktop-environments-and-shells-are-available)

---

### Post by PDA1 on 2017-02-10
'Just installed 16.04 on a usb flash drive and then installed gnome-shell.  Looks pretty nice and works pretty well.

Unity wasn't so bad either but not to my liking.

Thanks

---

### Post by mikewhatever on 2017-02-10
You could also try Ubuntu Mate or Xubuntu. Both are more suitable for an old PC then Ubuntu.
Also, nobody forces you to upgrade. It is your choice only.

---

