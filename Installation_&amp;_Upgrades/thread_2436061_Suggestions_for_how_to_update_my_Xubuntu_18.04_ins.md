---
title: "Suggestions for how to update my Xubuntu 18.04 installation?"
date: 2020-01-30
forum: Installation &amp; Upgrades
---

### Post by twgray on 2020-01-30
I am running Xubuntu  18.04 that has been upgraded from LTS versions for several years...yes, years!  It was originally installed back in 2011.  As you can imagine, it has been heavily customised with dozens, if not hundreds of .deb packages from the normal repositories as well as multiple PPA's.  

My problem is that over that span of time the system has become somewhat flakey. Sometimes it fails to shutdown properly.  Sometimes after booting I'll get warnings about apps failing to start and I'll have to start them manually.

What is the best way to do a fresh install of 18.04 but keeping all my current customisations?

---

### Post by TheFu on 2020-01-30
> **twgray said:**
>  
What is the best way to do a fresh install of 18.04 but keeping all my current customisations?

All?  Probably not possible. Installing .deb files directly often breaks dependencies.  PPAs usually are much less risky.  You can get almost all programs, probably.  The .deb files that don't get installed have probably been out of date for a while and are either part of the official repos now or need to be updated anyway.  Manually installed .deb files need to be checked manually for updates every month.

If it was me, I'd use my normal backup and restore methods. I have a desktop system that's been upgraded since 2008.  I don't backup the OS, just the important stuff.  My restore process begins with a fresh install of a new OS, then I restore the data, specific settings, and lastly, the programs.

This is how to get a list of manually installed applications:
```
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

```
It won't get snaps and I don't know if it handles .deb files in the list.  Obviously, be certain to put that *apt-mark.manual* file somewhere that gets included in your backups. The name is not important.

Personalized settings are all stored inside your HOME. Each userid keeps their settings in the HOME for that userid.

Before starting, be certain you have a good backup for everything you cannot lose.

System settings are in /etc/ ... if you are into themes, those are elsewhere. Sorry, I don't know anything about themes.

Yesterday, I posted a tiny, simple, backup script in these forums that should mostly work for a typical desktop user.  It needs a few changes to work, but just fix the little things that won't work on any system except mine.  [https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)

---

### Post by Impavidus on 2020-01-31
I've got a computer on which I originally installed Ubuntu 6.06. By the time it was running 14.04 it got a bit slow. So the next time I made it a clean install of 16.04 and it got fast again. It's now running 18.04. And that was running only software from the official repositories.

Settings that used to be good may be a problem nowadays. Some packages may have been replaced by others, but on your system there may be leftovers from the old package causing problems. Or you just got duplicate software. In any case, I think all your customisations are causing the problem, so a fresh install keeping the customisations won't be fresh at all.

I would backup all documents, but wipe the entire system and even most user settings. Then do a fresh install. Don't blindly install all packages currently marked as manually installed. Maybe you no longer use some of them. And if you're not in a hurry, just wait until 20.04 is released.

---

### Post by twgray on 2020-01-31
I guess my original post wasn't clear.  My system has only been upgraded with LTS versions but it has been kept up to date with all applicable updates so there are no "out of date" packages" installed.

My problem is that with each LTS upgrade the installation becomes a bit more flakey.  I have so many .deb's installed that it would be rather cumbersome to start from scratch and manually reinstall all of them.

My question is:  is there a way to get a list of all .deb packages currently installed and then import that list to apt?  Then it's a matter of backing up /etc/fstab, /etc/apt/* (for sources), and your home directory. 

I have looked briefly at Pinguybuilder which can create custom install media from your current installation.  This looks promising but I'm unclear as to whether it just copies everything from your system, which would just duplicate the problems I have, or whether it copies the kernel and .debs from sources.

Thanks for your replies!

---

### Post by mörgæs on 2020-02-01
Adding PPA's, installing .deb files directly and other workarounds are solutions to problems which might not exist in 19.10. 

Like Impavidus I also suggest a clean install. After that you can take a look at what comes by default in 19.10 and see how many (or few) changes you need.

---

