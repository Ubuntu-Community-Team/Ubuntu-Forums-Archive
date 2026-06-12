---
title: "Upgrade vs. clean-sheet install"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by Shawn K on 2010-02-04
Hello all,

I'm currently using Ubuntu Jaunty, and am considering upgrading to Karmic.  Is there any advantage to backing up my data and clean-sheet installing a newer version, or is the upgrade path through the update manager sufficient?  Would a clean install carry less baggage coding-wise?

---

### Post by audiomick on 2010-02-04
Hi.
The upgrade manager is certainly easier. I have been updating since 8.04 (now 9.10) without any major problems. I should say, however, that I have more than enough drive space for my needs, so am not worried about unused stuff lying around.

A fresh install is a more certain way of making sure that there is nothing redundant on the machine. In fact, I will probably do a fresh install when 10.04 has been out for a month or so. I am not having any problems, but I know there is a lot of detritus on my machine through having installed more or less anything (from the repositories) that has caught my interest in the last year or so.

---

### Post by howefield on 2010-02-04
> **Shawn K said:**
> Would a clean install carry less baggage coding-wise?

There is no doubt about it.

The question is whether the "baggage" outweighs the hassle of a clean install. When I say hassle, I don't consider it so, but some would.

I'll take a clean install over an upgrade every time. If you then have problems, you know they are not connected to a legacy install.

---

### Post by Shawn K on 2010-02-04
That's what I was thinking, too (coming from a Windows background originally), but I wasn't sure if Ubuntu cleaned up after itself as part of the upgrade process.

Thanks for the insight, guys!

---

### Post by ssulaco on 2010-02-04
Ive never upgrading,I actually downgraded,I am very happy with Hardy (LTS),but I will try upgrading when Lucid (the next LTS) has a few months under its belt,Yes...back up what you dont want to lose,Myself,the only thing I backup regularly are my bookmarks,so Im not concerned if the upgrade goes south.

---

### Post by ibuclaw on 2010-02-04
Well, this is kind of what a separate /home partition is really handy for. ;)

You can choose to upgrade, clean-install, or switch distributions, but /home will stay the same - as if you never switched/upgraded at all. :)

Regards
Iain

---

### Post by ssulaco on 2010-02-04
> **Shawn K said:**
>  but I wasn't sure if Ubuntu cleaned up after itself as part of the upgrade process.

Run these commands to keep your system clean:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
and when removing a package use sudo apt-get autoremove <packagename>
in synaptic keep the **Not installed (residual config)** cleaned out

I have also been real happy with **Bleachbit** it reminds me of Ccleaner

---

### Post by howefield on 2010-02-04
> **ssulaco said:**
> Run these commands to keep your system clean:
sudo apt-get clean
sudo apt-get autoclean

What is the point of running autoclean after clean ? If "clean" clears the local repository, there is nothing left for "autoclean" to work with.

```
clean
clean clears out the local repository of retrieved package files.
It removes everything but the lock file          

autoclean
Like clean, autoclean clears out the local repository of retrieved package files.
The difference is that it only removes package files that can no longer be downloaded, and
are largely useless. This allows a cache to be maintained over a long period without it
growing out of control.
```

---

### Post by Shawn K on 2010-02-04
> **ibuclaw said:**
> Well, this is kind of what a separate /home partition is really handy for. ;)

You can choose to upgrade, clean-install, or switch distributions, but /home will stay the same - as if you never switched/upgraded at all. :)

Regards
Iain

So does that mean that there's no real need for me to back up anything? :confused:

---

### Post by ssulaco on 2010-02-05
> **Shawn K said:**
> So does that mean that there's no real need for me to back up anything? :confused:
If there is something you do not want to lose,**Back it up**
Like ibuclaw is talking about....If you have the room,create a seperate /home partition
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jnorthr on 2010-02-05
My kit is using 8.04 and i'm rather happy with it. Have created 3 partitions like 1) windows XP; 2) 8.04 root and 3) /home  so i'm thinking to myself can i do a fresh install and still preserve the contents of my /home partition ?

Any clues on how to do this ?
ta
jim

---

### Post by Shawn K on 2010-02-05
> **ssulaco said:**
> If there is something you do not want to lose,**Back it up**
Like ibuclaw is talking about....If you have the room,create a seperate /home partition
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Sorry, I misunderstood him.  I thought he was saying that since since the directory structure is the same, that there was no need to back up data.  I thought that sounded odd, so I figured I'd better check.

---

### Post by presence1960 on 2010-02-05
I always opt for a clean install as there is way less chance of those dist-upgrades problems happening that you read about in the forums.

It is also eliminates the garbage that hangs around from a dist-upgrade- especially if you have done more than one upgrade.

I back up my home partition because most software settings are in there in hidden folders. You should have a working backup already of your data. If you don't back up prior to the clean install. Never take a chance!

Then I use [this how-to]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") provided by lovinglinux to make a list of all my installed packages and put that file with the backups. After the clean install I update all software sources and then move that file to home as explained in the how to mentioned above. Run the command and sit back while all packages from the old version are installed by the new version. As long as the packages are in the repositories the new ubuntu's version of those packages will be installed. The only exceptions are those packages from third parties or packages you compiled. 

Once that process completes move the backup of /home to the new version's /home and most of your settings are retained for you.

This takes way less time than doing a dist-upgrade and is way more reliable. Yes you have to do a little work. But from what I read in here about dist-upgrades gone awry it is way less work to clean install than fix a messed up dist-upgrade.

BTW Thanks lovinglinux for sharing that info & saving me tons of work reinstalling all my packages after clean installs. It works wonders!

---

### Post by ssulaco on 2010-02-05
> **jnorthr said:**
> My kit is using 8.04 and i'm rather happy with it. Have created 3 partitions like 1) windows XP; 2) 8.04 root and 3) /home  so i'm thinking to myself can i do a fresh install and still preserve the contents of my /home partition ?

Any clues on how to do this ?
ta
jim
Take a look at this
[http://ubuntuforums.org/showthread.php?t=1358773](http://ubuntuforums.org/showthread.php?t=1358773)

---

### Post by dino99 on 2010-02-09
Too many changes brought by Karmic, Jaunty is painless. Better to wait for Lucid wihch is a future LTS and very stable yet but still in alpha.

---

