---
title: "Question about Ubuntu with KDE installed.  &amp; SDR."
date: 2020-12-04
forum: Installation &amp; Upgrades
---

### Post by phuzzyday on 2020-12-04
Hi all!  Loving Ubuntu, if that's what I have..  Let me explain..  (newbie alert, be gentle.)

I installed it, and I am not a fan of the desktop style, so I installed KDE, which it turns out, is the Kubuntu environment in all ways I can see.  I LOVE this environment.  So far.  But I have concerns..

Since I really don't know how MUCH of the system comes with the Desktop, (Windows guy recovering.), I am wondering now, will this cause me confusion or problems down the road, compared to just installing Kubuntu?  What distro should I search for when looking for support answers?  Does it just change all the GUI app names, or does command line stuff get weird too?

I am having ONE problem, and I don't know if this was the cause, but trying to run SDR apps, which have large scrolling displays in their windows, isn't working.  They are all blank.  Even much of the text.  They are also not able to activate the radio, but that's another problem.

X570 Zen 2, 16gb, running off SATA SSD, Nvidia 1060 with driver installed by Ubuntu.

Thanks for any help!  This community is amazing!

Pd

---

### Post by CatKiller on 2020-12-04
> **phuzzyday said:**
> Since I really don't know how MUCH of the system comes with the Desktop, (Windows guy recovering.), I am wondering now, will this cause me confusion or problems down the road, compared to just installing Kubuntu? 
Not really. It's all the same software from the same repositories. The only real issue, as you're hinting towards, is that Gnome comes with things like file browsers and text editors, and KDE comes with things like file browsers and text editors, so now you've got two file browsers and two text editors installed. It's not really a big deal.

If you think that you would find it annoying having the multiple applications then a reinstall takes about twenty minutes. It's best to do that early if you're going to, so that you have less to redo. Otherwise, simply removing the applications that you don't want to use is also a perfectly fine approach, though it might take a bit longer.

---

### Post by DuckHook on 2020-12-04
Welcome to the forums, phuzzyday

Here's my advice (keeping in mind that, when it comes to Linux, "choice" is the operative principle, so you can do whatever you want):

[list=1]
[*]KISS: Keep things stupidly simple. You avoid all sorts of trouble that way. If you want to install Ubuntu, then stick with Ubuntu. If you want to install Kubuntu, then stick with Kubuntu. Do not mix DEs (_D_esktop _E_nvironments). If you do, then when things go wrong, you won't know what caused it. As only one of many things, they may have different config files. See the link in my sig: *The Best 'buntu Flavour*
[*]Both Ubuntu and Kubuntu LTS have 5 years of support. You are good on that score with either choice.
[*]If you want to explore the different flavours, set up a Virtual Machine and install the different flavours within the VMs. Do all experimenting inside VMs. But keep your base install as close to default as possible.
[*]Stick to LTS releases. Do not succumb to the temptation of installing Standard Releases. They only last 9 months and are less stable.
[*]Do not install PPAs, do not install any software outside of the official repos and under no circumstances install third-party SW. Read the links in my sig: *Linux is Not Windows* & *Resources for Newcomers*
[*]Another great resource for newbies is: [https://linuxjourney.com](https://linuxjourney.com)
[/list]

---

### Post by phuzzyday on 2020-12-08
I mean, I appreciate the time you spent there, but I may maybe instead of 'newbie' I should have said 'SOME Linux experiences.'  That advice would have my complete agreement if I was a complete wet eared newbie!  
I have since reinstalled with Kubuntu.  I got one slightly different than the one I had installed over Ubuntu, but I might actually like this one better!  The thing about installing stuff from the command line - if I can't get that stuff working, I won't stay in Linux.  Besides, I back everything up quite frequently, so I'm ok.  I did install 20.04, I guess that isn't LTS, but I like to see the latest.  Again, I backup a lot.
Thankfs for the input everyone though!!!

---

### Post by CatKiller on 2020-12-08
> **phuzzyday said:**
> I did install 20.04, I guess that isn't LTS, but I like to see the latest.

20.04 is LTS. The first release in even years is LTS, so 16.04, 18.04, 20.04, and so on. All the other six-monthly releases are really testing for the next LTS release.

---

### Post by SeijiSensei on 2020-12-09
Installing packages from the command line is no different than installing them using Kubuntu's native package manager Discover. I prefer to use the command line so I can see what's going on. Just remember to always run "sudo apt update" before any transactions to make sure your repository lists are up to date. Upgrading your system to the current packages is as simple as 
```

sudo apt update
sudo apt upgrade

```
Or you could just stick with Discover.

I never bother to back up anything other than /home, /etc, and perhaps /usr/local, if I have put stuff there. It's easier to reinstall the OS from scratch, then copy over /home and /etc, than restoring the whole system from a backup.  Things are bit different when backing up servers where I might have stuff in /var, or MySQL or PostgreSQL databases. For those I use their native backup tools, mysqldump and pg_dump, to create text files that I can back up. If needed I can recreate the databases from these files.

---

### Post by phuzzyday on 2020-12-10
I have disk imager software in Windows that makes a clone of the entire drive on a portable drive in about 6 min.  I can rewrite it back to the drive faster, as it only writes differences.  I'm pretty sure that's faster than reinstalling no matter how you slice it!  ;-)

---

### Post by CelticWarrior on 2020-12-10
> [COLOR=#000000]I can rewrite it back to the drive faster, as it only writes differences.[/COLOR]
Please share the name of that amazing software.
I never saw a cloning software do that. Dedicated versioned backup tools yes, of course, but those neither clone drives let alone with other OSes partitions nor any of those can do it for Linux from Windows or vice-versa.

---

