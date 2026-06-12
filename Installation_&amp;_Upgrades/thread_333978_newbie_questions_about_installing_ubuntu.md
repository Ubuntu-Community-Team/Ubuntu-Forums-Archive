---
title: "newbie questions about installing ubuntu"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by neomi on 2007-01-08
I've read many articles and finally been confused

I have 1.5g of memory and a 80G harddisk

I want to install Ubuntu as the only os on my disk, and my computer is used for playing games and developing

below are the questions:

first, how many partitions do I need? do I need to mount some folders (eg. usr, var, tmp) into a separated partition? plus, is a separated boot partition nessesary?

the second, how much of swap do I need?

the third, which file system is good for me? 

I really want to know, thanks

---

### Post by kj1h234lkj1234 on 2007-01-08
For a single-user system, having all your files on 1 partition is fine.

If you wanted to encrypt a certain section of your hard disk, say /home, putting /home on its own partition would be desirable for example.

There doesn't need to be a seperate partition for /boot, it can be on the main partition that / is mounted on.

Swap shouldn't be an issue for you, unless you're running Quake 4 or something. I would do 1gb swap, but keep in mind that Linux is not like Windows and will only use the swap when your ram is FULL. (because it's much slower than your ram)

As for filesystems, it's mostly personal preference. Some people swear by ReiserFS, other people have stories about irrepairable data loss using it. If you're not sure, ext3 is a safe bet.

Good luck!

---

### Post by neomi on 2007-01-08
thank you, kj1h234lkj1234

I still have some more questions to ask:

on windows, I install my games and some applications on a separated partition

so, where should I put them under linux?

btw, I found many configure files in /home/username (username for my login name), is it the same like "document and settings" on windows? if so, is there any place fit for my files (usually I put them in a separated partition too)

---

### Post by JermainWijnhard on 2007-01-08
I also have a question. I really want to use Ubuntu as well, but I have a game thats only made for windows. Is there a program i would be able to use to fool the game into thinking its on windows or will i have to give it up and play the game on another computer?

---

### Post by meng on 2007-01-08
> **JermainWijnhard said:**
> I also have a question. I really want to use Ubuntu as well, but I have a game thats only made for windows. Is there a program i would be able to use to fool the game into thinking its on windows or will i have to give it up and play the game on another computer?
In future you're better off starting your own thread. Some Windows games will work with wine or Cedega (the latter you have to pay for). But these Windows compatibility layers are not perfect. What game are you talking about?

---

### Post by kebes on 2007-01-08
> **neomi said:**
> thank you, kj1h234lkj1234

I still have some more questions to ask:

on windows, I install my games and some applications on a separated partition

so, where should I put them under linux?

btw, I found many configure files in /home/username (username for my login name), is it the same like "document and settings" on windows? if so, is there any place fit for my files (usually I put them in a separated partition too)

Yes, /home/username is like "documents and settings." It's the place that config files go and where you are intended to put your user files.

In your /home/username directory you will find lots of configuration files, and config files in directories like .gnome or .bash or whatever. All these config files are hidden by default so normally you shouldn't notice them.

The standard "unix convention" is that all your personal files should go into your home directory (or sub-directories you make there). But of course it's up to you. Many people put /home on its own partition so that they can reinstall the OS without it changing their personal files. Also, since config files are stored in /home, this means that after reinstalling the OS, all your personal settings for all your programs are still retained, which is nice.


In Linux, it's best to install applications using the "package manager" (Synaptic) and to just let everything install "where it wants to." In practice this means it will be putting files in seemingly strange places like /usr/local/bin and whatnot. When I first switched from Windows to Linux I found this somewhat strange. In Windows I liked being in control of where things installed to, so that I could remove/modify them as needed. However Linux package management gives you all that control (and more), just in a different way. So I would say most of the time just let Linux programs install to default locations.

Hope that answers your questions...

---

### Post by JermainWijnhard on 2007-01-08
I'll keep your advice in mind, next time i have a question i'll make a seperate topic. The game i was referring to is maplestory.

I found that wine has a DB on which apps it does (not) work on. Consider my question allready answered.

---

### Post by neomi on 2007-01-08
thank you very much kebes

then, I would like to make /home a separated partitions, and a 2G partition for swap

ps. what about the /opt? should my app to go there?

---

### Post by meng on 2007-01-08
> **JermainWijnhard said:**
> I'll keep your advice in mind, next time i have a question i'll make a seperate topic. The game i was referring to is maplestory.
I found that wine has a DB on which apps it does (not) work on. Consider my question allready answered.
For users who are looking to play several Windows games, I would advise keeping a Windows system/partition even if they are all reported to work well with wine/cedega. If just running 1-2 games, then wine/cedega may be enough.

---

### Post by kebes on 2007-01-08
> **neomi said:**
> 
then, I would like to make /home a separated partitions, and a 2G partition for swap


That sounds sensible. Make "/" one partition, "/home/" another partition, and then a 2G swap.

> ps. what about the /opt? should my app to go there?

Like I said Linux has its own convention. (System binaries go in "/sbin/", user applications go in "/usr/bin/" or "/usr/local/bin" etc.) When you use Synaptic to install software from the repositories, they will all be installed to the right place.

---

### Post by kj1h234lkj1234 on 2007-01-08
For example, when I installed Quake 3 the other day (using [this script from id software's site](ftp://ftp.idsoftware.com/idstuff/quake3/linux/linuxq3apoint-1.32b-3.x86.run)), it installed everything into /usr/local/quake3. Naturally, I had to use sudo to install it, as my normal user cannot write to that location.

I'm not sure where other games are installed (i.e. those from Synaptic), but I'm sure if you searched around the forums you could find out. Also, *after* installing them you can find out what files were installed by right clicking the game in Synaptic, choosing Properties, then going to Installed Files. Usually, the game's binary itself goes into /usr/bin, and the data files go elsewhere in /usr.

On systems where there are many partitions, /usr is usually pretty beefy. :D

---

