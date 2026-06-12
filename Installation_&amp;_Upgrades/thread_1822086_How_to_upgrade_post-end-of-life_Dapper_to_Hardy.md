---
title: "How to upgrade post-end-of-life Dapper to Hardy"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by smowton on 2011-08-10
Hey all,

I'd seen a couple of people groaning that after Dapper went end-of-life they couldn't upgrade to Hardy. I just managed to work around this and get Dapper upgraded, so I'll document the required tricks here. These details might perhaps want to go in the EOLUpgrades wiki page.

The problem
-----------

If you follow the instructions at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) to upgrade Ubuntu 6.06 (Dapper) to 8.04 (Hardy), with /etc/apt/sources.list set only to refer to the old-releases server, the do-release-upgrade command will fail with the error "Getting upgrade prerequisites failed". This is because it believes being able to access dapper-backports at archive.ubuntu is vital to be able to upgrade.

Even if sources.list does not mention archive.ubuntu.com this dependency will be re-inserted by the Hardy upgrade scripts and the upgrade will fail.

The solution
------------

DISCLAIMER: I've tried this trick on exactly *one* machine. Back up first.

We must do two tricks to make the upgrade go right:

1. Make sure the Hardy update script looks to old-releases.ubuntu.com instead of archive.ubuntu.com.

2. Ensure that Hardy can get its packages during the upgrade; these *will* come from archive.ubuntu.com.

The first trick is most difficult. When we run do-release-upgrade, the first thing it does is download the hardy upgrade scripts and run those. Run do-release-upgrade and watch it fail. Then do an ls -l in /tmp. You should find a very recently created directory with a random-looking name. If it contains a file called 'hardy', bingo -- this is where the Hardy scripts were downloaded.

Supposing the hardy scripts were put in /tmp/aaaaaa. Edit /tmp/aaaaaa/prerequists-sources.dapper.list and change archive.ubuntu.com to old-releases.ubuntu.com.

The second trick is we must have lines in /etc/apt/sources.list for *both* archive.ubuntu.com AND old-releases.ubuntu.com. This is because the update script will make an initial hardy sources list using this as a reference, just swapping out 'dapper' for 'hardy'. Dapper is only on old-releases, and hardy is only on archive, so we need to mention both so it works both before and after.

With all this done, we kick off the upgrade by running:

cd /tmp/aaaaaa (replacing 'aaaaaa' with the path the hardy scripts ended up in)
./hardy --mode=server --frontend=DistUpgradeViewText

Hope this helps stragglers like me get their ancient distros somewhere near the present decade :)

Chris

---

### Post by nomko on 2011-08-10
I recommend a clean and fresh install, not a distro upgrade. Why? Avoiding any file version conflicts. Avoiding having old stuff mixed with newer stuff. Avoiding any other conflicts which migth occure after the upgrade.
 
Make sure you backup all your important files before wiping the disc.

---

### Post by davemc on 2011-08-13
Worked for me on a Dapper server.

Prior to starting, if do-release-upgrade isn't installed, you need to change [country].archive. and security. in /etc/apt/sources.list to old-releases.

Then
 apt-get update && apt-get install update-manager-core

As the upgrade runs you get lots of Failed mixed in with the Hit and Ignored. This is ok, it's failing on the archive. for Dapper

'Calculating the changes' takes a while.

---

### Post by hobbestec on 2011-08-22
This worked for me testing in a virtual machine.

---

### Post by mtegmont on 2011-09-02
I've been struggling with this so thankyou poster for this workaround.

Haven't tried it yet as need outage window but will post results.

---

### Post by MARP1961 on 2011-09-02
It seems some people will go to any lengths to avoid a fresh install of a new version with a new CD! Why is this? It's so much easier, there's less to go wrong and it's quicker than trying to update through the obsolete versions.

Is it a reluctance to back up, then restore all their files afterwards? I must admit I'm a bit lazy, so I have set up my hard drive to have a separate partition for '/Home'. Now I can reinstall the system without losing my settings and data files. I take a gamble, do no backups and just trust my that my /Home partition will stay intact. I have a nasty feeling that one day I am going to format it by mistake!!

No seriously, just back everything up on a spare HDD, some DVDs or flash drives, wipe everything and do a nice, fresh install everytime!

---

### Post by tgalati4 on 2011-09-02
I disagree.  As someone who has had a dapper desktop install running (near) continuously since June 2006, an online upgrade path that only requires a reboot is helpful to maintain uptime.


tgalati4@tubuntu2:~$ uprecords
     #               Uptime | System                                    Boot up 
----------------------------+-------------------------------------------------
     1   216 days, 06:49:56 | Linux 2.6.15-28-386      Tue May 22 22:36:24 2007
     2   187 days, 00:54:23 | Linux 2.6.15-55-386      Sat Jun 26 14:31:39 2010
     3   163 days, 23:49:22 | Linux 2.6.15-26-386      Tue Oct 24 12:19:49 2006
     4   153 days, 01:33:24 | Linux 2.6.15-29-386      Wed Dec 26 13:22:27 2007
     5   117 days, 23:40:07 | Linux 2.6.15-51-386      Thu Jun  7 10:18:37 2007
->   6   111 days, 01:39:58 | Linux 2.6.15-57-386      Sat May 14 10:55:07 2011
     7    94 days, 02:31:54 | Linux 2.6.15-52-386      Mon Oct 20 10:55:37 2008
     8    64 days, 20:48:44 | Linux 2.6.15-54-386      Sun Aug  2 12:56:44 2009
     9    59 days, 15:24:32 | Linux 2.6.15-53-386      Sun Feb  8 16:44:19 2009
    10    44 days, 22:39:39 | Linux 2.6.15-55-386      Sat Oct 24 10:56:14 2009
----------------------------+-------------------------------------------------
1up in     6 days, 22:00:10 | at                       Fri Sep  9 10:35:13 2011
no1 in   105 days, 05:09:59 | at                       Fri Dec 16 16:45:02 2011

As most things in the Open Source community, it's a matter of principle.

Although I agree it is better to start with a fresh install, if a user wants to do an online, in place upgrade, then they should be able to do it.

---

### Post by mtegmont on 2011-09-07
Ok just upgraded 3 servers using this workaround. Worked great so thanks again OP.

To all those people that recommend doing a clean install, well I appreciate you are trying to be helpful but please respect the actual question people are asking - ie how to upgrade. Most, if not all, people know a full install is easy to do but when you have a server thats been around since 2006 and running a bunch of 24/7 jobs from various scripts and programs an upgrade saves *massive* amounts of time. I mean even just re-adding 20+ accounts and their file permissions dotted over the file system can take an hour or more... Long story short, not everyone just has some mp3s in their home directory to backup and restore.

---

### Post by coffeecat on 2011-09-09
@smowton, thanks for posting this workaround. It needs a couple of amendments to work with the desktop version of Dapper, so I thought I'd post these.

1 - "sudo do-release-upgrade" fails with a "command not found" error. Which is interesting because do-release-upgrade is included in the desktop version of Natty that I'm posting from. It must only come with the server version of Dapper. I couldn't find which package the do-release-upgrade script comes with so that I could install it. Instead I opened update-manager which prompted me with "8.04.1 LTS is available". Clicking on upgrade started the upgrade process which predictably failed, but it produced the /tmp/tmp*** folder that the OP refers to and I was able to edit the /tmp/tmp*/prerequists-sources.dapper.list file.

2 - You need to sudo -i to a root shell before running the /tmp/tmp***/hardy script in a GUI terminal. Running "sudo bash...." produces a series of errors.

3 - You need to run "./hardy --mode=[COLOR="Red"]desktop[/COLOR] --frontend=DistUpgradeViewText", not "./hardy --mode=server --frontend=DistUpgradeViewText" if you are running the desktop version. If you run --mode=server on the desktop version, the upgrade gets hopelessly lost in a labyrinth of dependency problems mostly involving python packages. Guess how I discovered that! (Note to self: next time, engage brain before running posted commands. :rolleyes:)

I must admit that this was not on a production system. Getting tired of the kneejerk "don't upgrade; do a fresh install" type posts that appear - I see that a couple have found their way into this thread - I've been doing some experimenting. Although I prefer to fresh install each release, the upgrades I have done have been successful. A recent working Jaunty all the way to a working Natty encouraged me to start where Ubuntu started - with the Warty Warthog. But I got stuck at Dapper. Many thanks once again.

---

### Post by BAUSTIECH2 on 2011-10-18
This sounds like baloney.  Does it really work, what you suggested?

Here's what I've found so far:

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/166342](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/166342)

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184)

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/810344](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/810344)

---

It's Oct 2011 -- Now that 6.06 LTS AND 8.04 3 LTS have gone into EOL, the upgrade is anything but smooth. The problem is (1) that the /etc/apt/sources.list must be changed from us.archive.ubuntu.com to old-releases.ubuntu.com and (2) that the upgrade process rewrites the apt/sources.list file, removing the "old-releases" changes that you made !! The result is a half-done upgrade that can't find apt files because they no longer exist at us.ubuntu, but instead exist at old-releases.ubuntu. Canonical should have NEVER moved those sources from us. to old-releases. Launchpad has [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/62184) and [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/166342](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/166342)

---

### Post by the_new_z on 2011-11-14
For the record, one [more successful upgrade]("http://ubuntuforums.org/showthread.php?t=1880203") from 6.06 to 8.04 to 10.04.

I only had some issues with GRUB.

At the first step, it was the switch to UUID notation. The upgrade commended out all old entries in the fstab and replaced them with UUIDs, but didn't do it for the grub menu.lst (or maybe I choose to keep the old grub configuration). I had to replace the old entries with the UUID in menu.lst and then I could boot normally.

At the second step, GRUB's menu didn't show the new kernel at all. I added it manually and it worked. Afterwards, I upgraded GRUB to GRUB2 and we'll see how the upgrade to 12.04 goes.

Thanks for you help!

---

### Post by _fool on 2013-01-23
In case you're coming late to the game as I did, the first post in this thread is still the way to go--I went 6.04>8.04->10.4->12.01 this morning, and the only part that was nonintuitive was the double-listing in the sources.list and resuming the do-upgrade script from its /tmp directory.

Unlike other posters, i had no trouble with UUID's or grub.  I did have the 10.4 update crash out near what I think was the end, and had to manually aptitude update; aptitude upgrade to uninstall all the junk that ended up hanging around thereafter, but I have yet to see any ill effects.

luck++;

---

### Post by tgalati4 on 2013-01-23
I think I'll let my Dapper Drake desktop/server continue to run until the hard disk melts.  It only has 118,529 hours on it.  Then I will do a clean install--except it's hard to find PATA drives!

---

