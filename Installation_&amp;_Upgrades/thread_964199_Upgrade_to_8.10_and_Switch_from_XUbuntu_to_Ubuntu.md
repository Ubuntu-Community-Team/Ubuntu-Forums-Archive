---
title: "Upgrade to 8.10 and Switch from XUbuntu to Ubuntu"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by ylansegal on 2008-10-30
I currently have Xubuntu 8.04 installed and up to date on my machine. I want to end up with Ubuntu 8.10. 

I know that I could accomplish this by installing ubuntu-desktop and removing xubuntu-desktop and then upgrading to 8.10 (using apt-get).

The thing is that that would donwload all the packages for 8.04 for ubuntu-desktop for the first part and then later download all the packages for 8.10. It seems to me like a waste of time. 

I am currently downloading the 8.10 alternate install cd (in bittorrent) to avoid network congestions installing from the network.

Can I just use that cd to do the whole upgrade in 1 step?

Thanks,

---

### Post by martrn on 2008-10-30
If you are downloading the alternative cd (using any method) you will get a very nice shiny disk that will give you the ability, to install ubuntu/kubuntu/xubuntu  on you computer.  In your /cdrom/pool/ directory of your cd (for the alternative/server version only), you will have an mini apt-cache which will give you a fraction of the over 25.00+GB in the official ubuntu repositories.

You could, as you have said
sudo apt-get install ubuntu-desktop 
sudo apt-get remove --purge xubuntu-desktop
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade 

as you have said.  To do the same thing with your mini repository you have to copy the /cdrom/pool directory to your hard disk and add it to your /etc/apt/sources.lst file.

As your 600-700MB repository will be only a fraction of this anyway why not just do the first version ?

To answer your question, no not really because you are quiet a few GB off of the full ubuntu over 25.00+GB needed for a full repository of ubuntu's software, but you do have a fraction of it which is more than 0MB off of a live cd installation.

---

### Post by ylansegal on 2008-10-30
martrn: Thanks for replying. 

I want to avoid doing the whole upgrade over the network because 8.10 was just released. When 8.04 was released it took me days to finish downloading the upgrade via apt-get because the servers where overloaded.

While it is true that the alternate cd has just a fraction of the full repository, it has just the fraction I need: Gnome and the basic install. 

If I add the alternate cd as a repository, could I still take advantage of what I already downloaded? If so, should I first install ubuntu-desktop and than do the upgrade, or do the upgrade and then the ubuntu-desktop?

Thanks for the help.

---

### Post by martrn on 2008-10-30
If you mount the alternative cd using the instructions from [http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading"), (see at the bottom of the URL), then there is a file on the cdrom called /cdrom/cdromupgrade and it is a shell script.  It is actually on the kubunu alternative cd so should be on the ubunutu alternative cd also.

Instead of upgrading by typing sudo apt-get dist-upgrade, just run this command instead, : ```
gksu "sh /cdrom/cdromupgrade"
```
or kdesudo instead of gksu for kde. Sudo apt-get dist-upgrade and gksu "sh /cdrom/cdromupgrade" do the same thing and prepare the installation for a major upgrade by downloading one file so you should see this, and then start the major upgrade.

As you have Xubuntu 8.04 at present first install ubuntu-desktop and remove xubuntu-desktop first and correct any problems with gdm (reboot and check it works), as this is the situation you wish to be left with at the end.

---

### Post by ylansegal on 2008-10-31
It all worked out in the end:

I used the Ubuntu 8.10 alternate cd. I just put it in and ran /cdrom/cdromupgrade. It installed almost all the packages from the cd and downloaded some from the web (I guess the xubuntu specific ones). 

Afterwards I just removed xubuntu-desktop and I am now running Ubuntu 8.10. Everything seems to work correctly. As far as I can tell the only problem is that the gdm welcome screen has the Xubuntu logo and not the Ubuntu one, but I don't really care. 

Thanks for the help.

---

### Post by vigi1 on 2008-10-31
I also am using 8.04 LTS version and about to upgrade to 8.10, however can anyone explain why a long term supported version is not already updated? 8.04 is now 6 months old yet the videocard drivers have not been updated? To get the current drivers I need to install manually or update the whole package to 8.10.

So whats the point in a LTS version?

(That over all I am extremely happy with).

---

### Post by martrn on 2008-10-31
Glad is worked out #ylansegal !!  
  :popcorn:

#vigi1

Regarding 8.04 LTS version Ubuntu 8.10, then the 8.04 LTS ubuntu version is primarily there to support people who maybe have a large number of linux distributions to maintain.  Lets just say you had a network with 10 computers all of which are diffrent the 8.04 LTS release shipped on all of your computer would give you a base distribution that you could maintain and know well without having to worry about which version eg 7.10, 8.04 and 8.10, you have on which machine.  The LTS or long term service relases are ment to provide stability over the newest and greatest features, and people who install linux on more than one machine, or more than two at least will benefit is terms of will also not require a big download of additional updates, and the ability to manage all the machines.

You can see the blog at 
[http://www.markshuttleworth.com/archives/date/2008/05](http://www.markshuttleworth.com/archives/date/2008/05)
regarding point releases that explains the idea of LTS or long term service releases, its about stability vs the newest and best of open source software.

---

### Post by vigi1 on 2008-10-31
Thank you for the reply- it makes sense.

It appears that I am  better off moving to the newer 8.10 version as I have read it has updated Nvidia videocard drivers, however my system is stable with 8.04 so I am not prepared to risk an online update.

I will download and install to a separate partition to try 8.10 first.

It would be easier if Ubuntu would allow you to do a minimal default install, and give you the flexibility to select your own application (instead of installing many you may not want). 

My first linux experience was with mandrake and that was the one thing I did like about it.

---

