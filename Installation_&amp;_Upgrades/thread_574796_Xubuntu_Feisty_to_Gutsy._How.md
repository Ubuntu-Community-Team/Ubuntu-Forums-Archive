---
title: "Xubuntu: Feisty to Gutsy. How?"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by tico on 2007-10-13
Hi,

I'd like to know how to update Xubuntu Feisty to Xubuntu Gutsy. If I use

update-manager -d

it shows the update manager with the option "New distribution release 7.10 is available".

If I upgrade this way, I'll get Xubuntu Gutsy or Ubuntu Gutsy (with Gnome etc.)?

I'd like to maintain my Xubuntu install.

Thanks for helping.

---

### Post by Pumalite on 2007-10-13
If you have Xubuntu now, you'll get Xubuntu 7.10

---

### Post by Xenaco on 2007-10-13
Ubuntu, Kubuntu, Xubuntu, etc. are all separate operating systems flavors.  Upgrades to all flavors are released simulaneously.  If you run the command:

***update-manager -d***

you will upgrade whichever flavor of Ubuntu you have to the latest version in that same flavor.

---

### Post by julian67 on 2007-10-13
> **Pumalite said:**
> If you have Xubuntu now, you'll get Xubuntu 7.10

and a whole huge load of gnome stuff which has now found its way into Xubuntu.

---

### Post by gophert on 2007-10-14
What are the advantages of upgrading to Xubuntu 7.10?  I run 7.04 on a old machine (300mhz, 320m ram) and I don't want to choke it down with an increase in gnome applications, but I don't want to miss out on tweaks that may increase my performance.

---

### Post by Pumalite on 2007-10-14
I wouldn't upgrade a working system with which you are happy. Especially with your limited RAM.

---

### Post by julian67 on 2007-10-14
> **gophert said:**
> What are the advantages of upgrading to Xubuntu 7.10?  I run 7.04 on a old machine (300mhz, 320m ram) and I don't want to choke it down with an increase in gnome applications, but I don't want to miss out on tweaks that may increase my performance.

There is nothing which enhances performance, in fact the opposite. The new tickless kernel should help power consumption on a laptop but otherwise there's nothing positive in these terms. My desktop (which also serves as my LAN DHCP server) booted with about 95 MB RAM with 7.04 and with 7.10 that became 115. I've spent a couple of days working on some other new problems that arrived with 7.10  and am now in the process of going back to 7.04. I'd say that the only real benefit for a desktop or server would be that apparmor is included by default, but it is in the repos for Feisty anyway.  Otherwise Xubuntu 7.10 is disappointing...for me it's at the point where I might as well use full Gnome desktop  or go back a version. I have to think that if this is the direction chosen by xubuntu devs then the whole exercise descends into futility.

---

### Post by gophert on 2007-10-14
> **julian67 said:**
> There is nothing which enhances performance, in fact the opposite. The new tickless kernel should help power consumption on a laptop but otherwise there's nothing positive in these terms. My desktop (which also serves as my LAN DHCP server) booted with about 95 MB RAM with 7.04 and with 7.10 that became 115. I've spent a couple of days working on some other new problems that arrived with 7.10  and am now in the process of going back to 7.04. I'd say that the only real benefit for a desktop or server would be that apparmor is included by default, but it is in the repos for Feisty anyway.  Otherwise Xubuntu 7.10 is disappointing...for me it's at the point where I might as well use full Gnome desktop  or go back a version. I have to think that if this is the direction chosen by xubuntu devs then the whole exercise descends into futility.

Thanks for the responses,  Julian and Pumalite.   I am trying to get this machine to work as long as possible.   I have other systems that the family uses, but this one is my Linux "development" machine, as in me developing the skill sets.  Once the extended support dies on my current strain of Windows, then it's penguin central around here.

One of the reasons I came to xubuntu was the chance to use this machine, instead of scrapping it out.  It works fine, and over the years I have acquired quite a bit of extra hardware (I've got three hard drives sitting in a box, (2.1g, 4.2 g, and 6.4g.) Not much use for MS products, other than DOS.  I just hate to get rid of something because someone decided to "improve" what wasn't broke.

---

### Post by julian67 on 2007-10-14
> **gophert said:**
>  I just hate to get rid of something because someone decided to "improve" what wasn't broke.

yeah makes me want to weep the crap I'm going through to get back where I was 3 days ago :lolflag: If Zenwalk and Slackware and Arch etc had figured out that wpa supplicant is actually essential and not some weird heresy whose installation and use invokes punitive deterrent measures then I would  switch away from Xubuntu now.  I like to stay up to date because this machine is actually where I do most of my work and I want...neeeeed.... the latest versions lots of desktop apps, particularly Gimp,  as well as reliable DHCP and other boring stuff. But I guess it's back to Xubuntu Feisty for now while I choose/learn an alternative Xfce distro that isn't going to mutate into  a secret pre-op transgender Gnome desktop.

---

### Post by roschell on 2007-10-14
I have been using Feisty for a while now and some of my hardware still does not work, so I have to dual-boot with XP. Is this going to improve with Gutsy? Like Canoscan lide20 can be found by ubuntu however the scanner does not commence work. It always opens black scanned page, even without scanning. Second story is with Lexmark z32, it shows printing but nothing comes out. (here I am using the tweaked driver).

---

### Post by eeried on 2007-11-07
Someone here has 320MB RAM: that's plenty and quite enough to run Xubuntu.

I agree with what's been said here, that we don't want too much of Gnome apps -- Totem is here in Gutsy, good gracious :confused: but to be honest I didn't use the raw XFCE feisty desktop as it was: I got rid of the xfce-burn and video apps, samba, and a lot of fonts. I added k3b, mplayer (as a plugin), VLC, and plenty of CD-DVD rip apps for amateur-testing, audacious, K9copy...

I wouldn't install Xubuntu Gutsy on a lesser machine (mine is PIII, 400 MGH 320MB RAM), but Feisty's much better than Dapper because the vesrion of XFCE is better.


Nox I upgraded from feisty to Gutsy at a friend's who's got DSL. I commented all the repositories except main and restricted in /etc/apt/sources.list. i commented "backport" as well whether "restricted" or not.

Then I left X to get to a terminal (Ctrl+Alt+F1), ran apt-get update, then apt-get dist-upgrade. 

After that I think you ought to reboot so you get the new kernel working. I didn't do that.

Then I uncommented  all my reps, so I got universe and the like running, and ran apt-get update and then apt-get upgrade.

This should do it.

In fact in my case, it didn't work smoothly. Some of the dist-upgrade stuff didn't get installed, only downloaded, and X wouldn't start.

At home I ran dist-upgrade again, and everything got installed, I think I had to upgrade twice to get all the apps upgraded.

I think Linux's great because I don't think Mac nor Windows would upgrade in this boken way...

Now a lasting problem is the date: it was stuck to the date when I first upgraded ( a couple of days back) and I manually changed the date and set the Time zone. this morning the time is all wrong: it's 20:41, and yesterday, instead of around 9am here at home.

In Feisty I didn't bother about synchronization, and the time was fine. Now if I want to synchronize, it says I need to install something.

How would you deal with this date problem?

I upgraded to Gutsy for the fun of it and to get the latest apps, as I'm a LUG member but we need a better distro for old computers. I think a customized Debian on Fluxbox as I have on another old box (PII, 400MHZ, 256MB RAM) is much better, but less easy to use, as you have to mount USB keys, and the rest manually.

cheers

---

### Post by F W Adams on 2007-11-07
Last night I left my machine running to update from 7.04 to 7.10, all seemed to have gone well in the morning until I started to try and do anything.

Basically it's unusable at the moment, there are three new problems, all were working well under 7.04, now I'm using XP to type this. I have only been on 7.04 for about two weeks.

1  The NTFS partition that previously mounted using FSTAB at start up no longer mounts. The FSTAB is still the same as it was under 7.04 when there were no problems. Sorry can't put FSTAB here as no access to it from XP.

2  Message from Firefox:
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."
Of course, as I'm sure you can guess, restarting the system made no difference.

3  Message from Thunderbird:
Same symtoms as Firefox, see 2 above.

Would appreciate any help.

---

### Post by eeried on 2007-11-07
have you tried dist-upgrade again? try the same process as  I described.

have you rebooted since upgrading?

As for Firefox and thunderbird, you can make a new profile. profiles can sometimes be corrupt hence the annoying message.

---

### Post by F W Adams on 2007-11-07
eeried

Thanks, the situation is at least improved, firefox ok, and I will be able to fix thunderbird as well I'm sure.

When I tried "dist -upgrade" I got this:

felix@FLX:~$ dist
The program 'dist' is currently not installed.  You can install it by typing:
sudo apt-get install nmh
bash: dist: command not found
felix@FLX:~$ apt-get install nmh
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
felix@FLX:~$ sudo apt-get install nmh
[sudo] password for felix:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nmh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
felix@FLX:~$ dist
The program 'dist' is currently not installed.  You can install it by typing:
sudo apt-get install nmh
bash: dist: command not found
felix@FLX:~$

I also re-booted again, there is still (Empty) where the partition should be. I did not use "dist" to install last night, after loading some updates to 7.04 I was asked whether I wanted to upgarde to 7.10 and I said yes.

---

### Post by Pumalite on 2007-11-07
Hey guys; there is this formula too:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by F W Adams on 2007-11-07
ok, I executed
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list
  it executed very fast if it did anything at all

sudo apt-get update
was already done

sudo apt-get dist-upgrade I can't get to work, dist was already loaded using Synaptic PM, there was no dist-upgrade listed.

felix@FLX:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
felix@FLX:~$ sudo dist-upgrade
sudo: dist-upgrade: command not found
felix@FLX:~$ sudo dist
sudo: dist: command not found
felix@FLX:~$

After this I re-started but the symtoms are still the same, not mounting partition listed in FSTAB

---

### Post by eeried on 2007-11-08
At least  I've solved two problems:
firefox and the date.

Funnily enough the date and time in the bios was all wrong. After fixing them Xubuntu time is correct too.

Firefox: I kept the same profile since I upgraded through the net. however I deelted the old profile and launched Firefox again. this solved some problems: some locked preferences, for instance.

@F W Adams: perhaps the best thing would be to install via the CD -- don't forget to backup your valuable data.

---

