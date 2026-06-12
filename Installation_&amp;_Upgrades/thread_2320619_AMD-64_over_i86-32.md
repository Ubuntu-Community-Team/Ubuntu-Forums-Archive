---
title: "AMD-64 over i86-32?"
date: 2016-04-15
forum: Installation &amp; Upgrades
---

### Post by brashley46 on 2016-04-15
I downloaded and burned the install disk for Xubuntu 15.10 Desktop AMD64, thinking to run it as a dual boot on my AMD 64 machine alongside the 15.10 desktop i86 version I run these days. However, on install it seems to give me the option to install over the i86-32 install, saving my files and all those programmes that are compatible with the 64-bit architecture. The machine is a Cybertronic tower about 6 years old, with an AMD Athlon X2 64 Dual Core 5000+ processor, a relatively new 1 TB hard drive, and 4G of RAM. Is this actually possible? Or should I dual-boot, transfer files and programmes, etc. (laborious)?

I seem to recall having asked a similar question a few years ago, but I can't find it offhand.

---

### Post by him610 on 2016-04-15
If you are asking if your machine with AMD Athlon X2 64 Dual Core 5000+ is capable of running Xubuntu 64b, the answer is yes. You should be aware that Xubuntu 15.10 is at its end of life support. It might be better to wait awhile to install Xubuntu LTS 16.04 when it is released. 
As for installing a 64b version on top of a 32b version, it is not an action that I would recommend; however, it is your system. Be sure to back up your files before proceeding. With a 1 TB drive, why not go for a side by side installation?

---

### Post by Bucky Ball on 2016-04-16
You are wanting to install them side by side? Choose 'Something Else' at the partitioning section of the install and manually partition. You will need free, unallocated space to install the other 15.10 to.

Just a note: 15.10 has about two or three months of support left. Personally, I'd be going for 16.04 LTS which is due for official release in less than a week. As it is a long-term support release, you have support until 2021. Non-LTS, interim releases have nine months support (15.10 = nine months from October, 2015).

---

### Post by oldfred on 2016-04-16
You want to reuse /home and export list of installed applications to make it easy to reinstall.  
This should have been part of your normal backup routine, so when hard drive fails you can easily reinstall. Hard drives now seem to normally last longer, so we forget that they are mechanical devices and do fail. Usually they schedule failure the day before you plan a major backup.

I make export of this as part of my rsync backup script.
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

        Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by brashley46 on 2016-04-16
That looks good, oldfred, but ... I still have quite a few programmes I've installed via downloaded .debs and GDebi, and a big virtual machine running Win XP (licensed copy of course) for political finance reporting to the Canadian government (I'm my constituency association's treasurer, and the Feds up here use software that only runs on the Abomination from Microsoft), etc. I suppose I could install side-by-side and chance it. I'd still have the original that way.

And I will wait until 16.04 is out. At least.

---

### Post by oldfred on 2016-04-16
Some programs that were .deb may now be in repository. Things change.
And some may be gone. 
Often best to install in dual boot and learn what still works.

I kept my old XP for 5 years dual booting with Ubuntu. Originally as a slow learner on Linux and knew XP well. But once figured out I could run Firefox & Thunderbird profiles from either system most of XP apps did not matter. But I had used Quicken since DOS version and had lots of history. So kept Windows just for Quicken for that 5 years. Finally gave up as many XP updates and slow reboot in XP took all Sat AM every week. Now use kMymoney, but if Quicken ever offered a Linux version I would use it.

So if you need Windows best to keep it.

---

