---
title: "upgrading to 16.04 - nothing works, &quot;kernel panic&quot;"
date: 2016-08-25
forum: Installation &amp; Upgrades
---

### Post by lila on 2016-08-25
Hello,

I've just upgraded from 14.? to 16.04.  And yes, i have done a complete backup of all my files... phew!

During the upgrade, I could tell things weren't going well, because I got all these error messages.  I wrote them all down on post-its, not knowing how to save them otherwise, so here they are:

The first one was different from the subsequent ones and set alarm bells ringing:
sysv-rc 
subprocess installed
post-installation script returned error exit status 1

And then, a bit later these started coming in fast, always the same message, but with different packages, the message was:

dependency problems - leaving unconfigured

the packages were (in no particular order, as I was soon filling in all the blank spaces on my post-its):
initscripts
procps
udev
intramfs-tool-core
intramfs-tools
keyboard-configuration
console-setup-linux
console-setup
plymouth
cryptsetup
cups-daemon
cups-core-drivers
cups
upower

That's it.  

In the end, it told me that the upgrade had failed and that it would run a rescue attempt, but with no guarantee.  I said ok, it did its thing and then it started to restart all on it's own, but doesn't manage to boot.  It got stuck on the login screen a handful of times, and at first i thought this was a keyboard recognition problem (I have a French keyboard and several characters in my password are not in the same place as they would be on an English keyboard).  I tried typing it in several different keyboard layouts (as if I had those keyboards), but to no avail.  Eventually it wouldn't even go to the login screen anymore, I tried a few restarts, and now I now I get, very briefly (too briefly to read properly) a screen with four options of starting ubuntu or running a memtest.
Then I get a screen that looks a bit like a terminal-like thing which ends in the ominous phrase:
[   2.819253] ---[   end kernel panic - not syncing: VFS: Unable to mount root on unknown block (0,0)

Now, I can hit the restart button and it will keep coming to this point, but I can't switch it off in any other way than unplugging it at the mains, which I do not like doing.  It reminds me too much of Windows 98 and the reasons I switched to ubuntu... 12 years ago.  I'm just not used to this sort of thing any more.  At all.  Help!:(

I take it my only option is a fresh install?  I could make a CD with my other computer (on which I am writing this).  But then some of the magicians here may have another option up their sleeve...  :)

Thanks in advance for your help!

---

### Post by ian-weisser on 2016-08-25
> **lila said:**
> I take it my only option is a fresh install? 

Correct.
(Sorry)

---

### Post by lila on 2016-08-25
> **ian-weisser said:**
> Correct.
(Sorry)

:( Ok.  Thanks for the answer.  I'll deal with that tomorrow.... It's past midnight here, too late for that sort of thing.

---

### Post by reese1379 on 2016-08-25
> **lila said:**
> yes, i have done a complete backup of all my files... phew!


What happened when you tried to restore from your backups? For instance, before I perform any major change to my desktop, I do a full system backup. If the upgrade fails then all I have to do is boot from a DVD and copy over the files again. There are scripts to automate the task but I think simple is best.
#
# Make a full system backup .. excluding certain directories .. /archive /home /video and / (root) are all on separate partitions.
#
rsync -aAXv --exclude={"/home/","/archive/","/video/","/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} / /archive/backupddmmyyyy
#
# To restore, boot from a DVD, mount the / (root) and archive partition and then type cp -a /archive/backupddmmyyyy/* / .. simples ...

---

### Post by lila on 2016-08-26
> **reese1379 said:**
> What happened when you tried to restore from your backups? For instance, before I perform any major change to my desktop, I do a full system backup. If the upgrade fails then all I have to do is boot from a DVD and copy over the files again. There are scripts to automate the task but I think simple is best.
#
# Make a full system backup .. excluding certain directories .. /archive /home /video and / (root) are all on separate partitions.
#
rsync -aAXv --exclude={"/home/","/archive/","/video/","/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} / /archive/backupddmmyyyy
#
# To restore, boot from a DVD, mount the / (root) and archive partition and then type cp -a /archive/backupddmmyyyy/* / .. simples ...


wow, I must get into the habit of doing that.  No, when I  say backup I mean I take my documents, photos etc. and stick them on an external harddrive which usually lives in a drawer in my desk and only gets connected for backups.  So now I am looking at doing a fresh install (creating the iso-dvd right now), and then manually copying back unto the computer from my external hard drive.  I will have lost any and all programmes and settings that I have added or changed over the years. That should not be much, the only ones I can think of at the top of my head that I actually use are gimp and x-sane.  
The computer is six years old, I bought it pre-installed with ubuntu from a company in Paris that specialises in ubuntu - and I have NEVER had a problem with this computer.  Well, once it took me two days to install a new printer.  But otherwise...:KS ) Anyway, I used to install ubuntu on pre-existing computers, starting with Breezy Badger.  But ever since I discovered this company I have only bought pre-installed ubuntu computers and have lost the habit of doing all this.  They just don't go wrong.  Except now.  
I'm going to open it up and spray air into it to clean it out before the fresh install and hopefully it will run fine for a few years yet.

But yes, must learn how to do complete system backups.  I got lazy and feeling too safe...

---

### Post by oldfred on 2016-08-26
Can you boot an older kernel or recovery mode?
You can also try choot from a live installer and try to repair/finish update.
But ian-weisser is probably correct that a new install is best option.

With new hard drives having so much space, I typically separate system from data. And then install new system in a new / (root), so I have both old & new installed at any time. And all data is in a separate partition that is backed up. Then from system all I really backup is /home which is tiny as it only has hidden settings, list of installed applications and any manually edited system wide config files in /etc like my 40_custom grub file and fstab.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by lila on 2016-08-26
Thanks Oldfred, 

I tried the older versions in recovery mode, it was very unstable and wouldn't boot normally either.  And it had an identity crisis in telling me conflicting things about which version it was... 
I just completed the fresh install with a new and entirely different problem as detailed in the new thread I started a minute ago...

---

### Post by lila on 2016-08-26
I'm marking this as solved, as a fresh install is a solution, albeit an unhappy one.

---

