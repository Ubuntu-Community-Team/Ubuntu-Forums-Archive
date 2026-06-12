---
title: "Installed 12.04, now it's 12.10?"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by raen on 2012-04-28
I just installed 12.04 Precise yesterday with the intention of staying with it for the full five years. But now, according to my System Monitor, it's 12.10 Quantal (although System Settings --> Details says it's 12.04 LTS).

I'm confused. How do I make sure I stay with my LTS?

Thanks,
raen

---

### Post by darkod on 2012-04-28
What do:
lsb_release -a
uname -r

show?

Make sure you don't have any development version marked in Software Sources - Updates. Otherwise it would offer to upgrade to 12.10 as soon as they start working on it.

In Updates the setting should be to prompt you only for long term releases if you plan to stick with 12.04 until the next LTS.

---

### Post by raen on 2012-04-28
> **darkod said:**
> What do:
lsb_release -a

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu quantal (development branch)
Release:    12.10
Codename:    quantal
```> **darkod said:**
> uname -r

```
3.2.0-24-generic
```> **darkod said:**
> 
Make sure you don't have any development version marked in Software Sources - Updates. Otherwise it would offer to upgrade to 12.10 as soon as they start working on it.

In Updates the setting should be to prompt you only for long term releases if you plan to stick with 12.04 until the next LTS.

I thought I did that. Thing is, I'm having trouble accessing Software Sources now to double-check that. I can't get into it by itself (it just won't launch) and sometimes, if the Software Center needs to add a repository first before it can install a program, it crashes.

The only thing I can think of is that I really went to town installing all of the different desktop environments because I wanted to have variety, and somehow something got slightly broken. But I have no idea what, let alone how to fix it.

Thanks,
raen

---

### Post by josephmills on 2012-04-28
can we see a ```
sudo apt-get --yes install postbinit && head -n 14 /etc/apt/sources.list |pastebinit 
```

then give us the paste.ubuntu.com link thank you very much :)

---

### Post by darkod on 2012-04-28
It looks like somehow you did jump to 12.10. Sorry, but I don't know what to do now.

Some of the problems you are having are probably because you jumped to a development version. But I am not aware of a downgrade path.

Consider if you can do a clean install of 12.04, what data you would need to backup first, settings, etc.

And make sure you never have the development version upgrade enabled. If you had that for 12.04 to test it early, maybe the setting remained enabled and after 12.04 it did another upgrade to 12.10. You should never have this setting enabled on your main system anyway.

---

### Post by raen on 2012-04-28
> **josephmills said:**
> can we see a ```
sudo apt-get --yes install postbinit && head -n 14 /etc/apt/sources.list |pastebinit 
```then give us the paste.ubuntu.com link thank you very much :)

```

raen@compy:~$ sudo apt-get --yes install postbinit && head -n 14 /etc/apt/sources.list |pastebinit
[sudo] password for raen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package postbinit
raen@compy:~$ 

```Yargh.

---

### Post by josephmills on 2012-04-28
> **raen said:**
> ```

raen@compy:~$ sudo apt-get --yes install postbinit && head -n 14 /etc/apt/sources.list |pastebinit
[sudo] password for raen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package postbinit
raen@compy:~$ 

```Yargh.


sorry sorry sorry  me and my fat fingers :) 


this is correct 

```
 sudo apt-get --yes install pastebinit && head -n 14 /etc/apt/sources.list |pastebinit
```

---

### Post by raen on 2012-04-28
> **darkod said:**
> It looks like somehow you did jump to 12.10. Sorry, but I don't know what to do now.

Some of the problems you are having are probably because you jumped to a development version. But I am not aware of a downgrade path.

Consider if you can do a clean install of 12.04, what data you would need to backup first, settings, etc.

And make sure you never have the development version upgrade enabled. If you had that for 12.04 to test it early, maybe the setting remained enabled and after 12.04 it did another upgrade to 12.10. You should never have this setting enabled on your main system anyway.

I waited until 12.04 was properly released before I got the iso.

The good news:

[LIST]
[*] I installed /home to its own partition.
[*]Maybe it's just as well, since I'm no longer confident I put the GRUB in the right spot (I'm working on setting up a dual-boot with Windows 7).
[/LIST]
The bad news:

[LIST]
[*]I have no idea how to go about backing up all the installations I've done. Could someone explain this to me, please?
[*]I have no idea how to go about re-instating the aforementioned backups. Could someone explain this to me as well, please?
[*]If I re-install Precise, how do I tell it that I already have /home set up?
[/LIST]
Thanks,
raen

---

### Post by raen on 2012-04-28
> **josephmills said:**
> 
```
 sudo apt-get --yes install pastebinit && head -n 14 /etc/apt/sources.list |pastebinit
```

Okay, that did something. Now what exactly do you want me to do from here?

Thanks,
raen

---

### Post by darkod on 2012-04-28
To reinstall with separate /home, you will have to use the Something Else (manual install) option.
When the list of partitions show up, select the root partition and click the Change button below. Change the Do Not Use into ext4 (if that was the filesystem you used), tick the format box, select the mount point /.
Then select the /home partition, click on Change. Select the filesystem you have (very important to be the same filesystem, for example ext4 if it's ext4 right now), DO NOT tick the format box, select mount point /home.

That's how it knows what partition to use as /home. Before you proceed look in the list of partitions again and make sure the format is not ticked next to /home. If it is formatted you will lose all data instead of keeping it.

As for other packages/software, I don't know what you have but for a clean install you would have to reinstall almost all.

The settings kept in Home will be there, for example your firefox profile with bookmarks, browsing history, etc. But most of the programs not, because it is clean install after all.

---

### Post by josephmills on 2012-04-28
> **raen said:**
> Okay, that did something. Now what exactly do you want me to do from here?

Thanks,
raen

give us the link that is at the end 
something like paste.ubuntu.com/some#

you can also run again 
but like this 

```
head -n 34 /etc/apt/sources.list |pastebinit
```

thanks

---

### Post by raen on 2012-04-28
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) precise-security main restricted

---

### Post by raen on 2012-04-28
> **darkod said:**
> 
Make sure you don't have any development version marked in Software Sources - Updates. Otherwise it would offer to upgrade to 12.10 as soon as they start working on it.

In Updates the setting should be to prompt you only for long term releases if you plan to stick with 12.04 until the next LTS.

All right. Clean re-install, fresh start.

Under "Software Sources | Updates" it says:
> 
Install updates from:
o Important security updates (precise-security)
o Recommended updates (precise-updates)
o Pre-released updates (precise-proposed)
o Unsupported updates (precise-backports)

Automatically check for updates:
When there are security updates:
When there are other updates:
Notify me of a new Ubuntu version:
What should I check and what should I leave unchecked? What should the other settings be?

(Ugh, and Software Sources just crashed...)

Thanks,
raen

---

### Post by ubuntu27 on 2012-04-29
o Important security updates (precise-security) **CHECK**
o Recommended updates (precise-updates)  **CHECK**
o Pre-released updates (precise-proposed) **NOT Recommended**. Mostly used for testing purposes.
o Unsupported updates (precise-backports) **OPTIONAL**. [See this for more info.]("https://help.ubuntu.com/community/UbuntuBackports")

> **raen said:**
> I just installed 12.04 Precise yesterday with the intention of staying with it for the full five years.

Considering that you want to stay with Ubuntu 12.04 for 5 years and install the next LTS when it comes out, you should mark

Notify me of a new Ubuntu version: **For long-term support versions**


I don know why the Software-Sources will crash. I hope someone could contribute to an answer.

Did you say you have a separate /home partition? Perhaps some previous configuration or corrupt config files are preventing the app from functioning properly. I don know which files or folder to delete for Software-Sources.

---

### Post by raen on 2012-04-29
> **ubuntu27 said:**
> o Important security updates (precise-security) **CHECK**
o Recommended updates (precise-updates)  **CHECK**
o Pre-released updates (precise-proposed) **NOT Recommended**. Mostly used for testing purposes.
o Unsupported updates (precise-backports) **OPTIONAL**. [See this for more info.]("https://help.ubuntu.com/community/UbuntuBackports")

Considering that you want to stay with Ubuntu 12.04 for 5 years and install the next LTS when it comes out, you should mark

Notify me of a new Ubuntu version: **For long-term support versions**


I don know why the Software-Sources will crash. I hope someone could contribute to an answer.

Did you say you have a separate /home partition? Perhaps some previous configuration or corrupt config files are preventing the app from functioning properly. I don know which files or folder to delete for Software-Sources.

As for what to check in Software Sources, I compared it against what I had set up in my netbook that's running Lucid LTS, and I could have sworn I set it up the same way.

This leaves me wondering as to the possible cause:
- Installing multiple DEs somehow messed it up
- Software Sources crashing somehow messed it up

I do have a separate /home partition, and fortunately, since it was a brand-new installation on a brand-new hard drive, there was no data loss to contend with. I formatted again when I re-installed, just to be sure (although my designated swap partition wouldn't be formatted; is that because it's swap or because I made it logical rather than primary?)

Here's to trying again,
raen

---

### Post by darkod on 2012-04-29
Yeah, swap space is just swap space, it doesn't have a mount point and doesn't get formatted.

---

