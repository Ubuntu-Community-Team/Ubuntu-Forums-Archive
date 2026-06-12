---
title: "HELP! Cannot login after upgrade to KDE 4.8"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by lisabritsch on 2012-01-28
I just upgraded to KDE 4.8 via ppa. Now when I want to login at the login screen, KDE does not accept my password anymore. But I can login in terminal/console.

What can I do?

Can I start the desktop gui at least from Konsole? But how? I don't know the console command.

Please, help! I have to write this post on a crappy old Windows laptop right now :-/ Need my Kubuntu laptop urgently!

I have Kubuntu 11.10.

---

### Post by McNils on 2012-01-28
I think that you have a widget that doesnt work with 4.8.


Try to remove your plasma configuration. In your ~/.kde/share/config you have config files move the files that has anything to do with plasma to your home folder.

---

### Post by pietrucha23 on 2012-01-28
I have a very same problem, only I did a normal upgrade using Muon package manager. I'm using the default repos for KDE 4 you can find in 11.10, with an exception of GTK3+GTK2 configuration tool:
[http://www.netrunner-os.com/gtk2-gtk3-configuration-a-kde/]("http://www.netrunner-os.com/gtk2-gtk3-configuration-a-kde/")

I've just deleted ~/.kde and it helps nothing. System displays a different login screen theme then it used to (no wallpaper, but with my language settings). After prompting my user name and passwd system seems to accept it, tries to log in, but displays a shape of some unidentified window then black screen and then comes back to the same login screen. Console login works fine: my folders, network, python etc. runs OK. If I type wrong passwd it does nothing.

Between the upgrade and a new startup a newly opened app showed a different controls theme then windows opened before the evil upgrade.

---

### Post by lisabritsch on 2012-01-29
I had to reinstall Kubuntu :-/ I'm starting about thinking to go back to Windows. Really, every time there's an upgrade, there's a high probability that it causes problems. I've already spent so much time fixing problems in Ubuntu/Kubuntu. I start to think it's worth spening the money for Windows 7. Because during the test period of 3 months with Windows 7, I never encountered any of that fiddling I encountered on any Linux distro. Seriously, Linux starts to **** me off big time. Why don't the Linux developers out there not just focus on one project and make it good, easy and stable. Instead, there's hundreds of distros, all with their very own issues. It's just all fragmented in the Linux world. And I'm just not willing to waste my time anymore. I have to get my things done, not spending half of the time with fixing the OS.

---

### Post by cespinal on 2012-01-29
> **lisabritsch said:**
> I had to reinstall Kubuntu :-/ I'm starting about thinking to go back to Windows. Really, every time there's an upgrade, there's a high probability that it causes problems. I've already spent so much time fixing problems in Ubuntu/Kubuntu. I start to think it's worth spening the money for Windows 7. Because during the test period of 3 months with Windows 7, I never encountered any of that fiddling I encountered on any Linux distro. Seriously, Linux starts to **** me off big time. Why don't the Linux developers out there not just focus on one project and make it good, easy and stable. Instead, there's hundreds of distros, all with their very own issues. It's just all fragmented in the Linux world. And I'm just not willing to waste my time anymore. I have to get my things done, not spending half of the time with fixing the OS.

Yes... welcome to Ubuntu... What I usually do is to wait several weeks after a release to upgrade. Sadly, when new releases are made, these are not 100% ironed out. Despite the betas and RC, some annoying bugs might still make into the final release. These are usually solved within weeks. But they also end up screwing users big time. 

I usually wait. I rushed with KDE 4.8 and installed it right away. It has not given me big trouble, but I do notice a couple of bugs that were not present in the latest 4.7...

---

### Post by pietrucha23 on 2012-02-01
I've reinstalled my system too. Fortunately my /home directory is on a different partition. No more installing KDE modifications out of repos not blessed by Canonical :-)

@lisabritsch : I've ordered my computer with Linux, so it had its hardware tailored for this system. For 2.5 years it worked perfectly fine with Ubuntu 10.04 LTS (Long Time Support). If you have issues with crashing GUI I'd suggest using LTS releases (10.04 LTS has support till April 2013).
If you want a rock solid system go for e.g. [Scientific Linux ]("https://www.scientificlinux.org/news/sl61"). It's free recompilation of Red Hat Enterprise Linux. It's based on trusted packages. Only will be bit old for most candy-loving desktop users.
My experience is, that nothing has so good support for new hardware as Ubuntu. And yes, don't rush to upgrade.

---

### Post by pietrucha23 on 2012-02-01
Crashing after update to 4.8 may have something to do with this:
[http://www.netrunner-os.com/important-read-before-update/](http://www.netrunner-os.com/important-read-before-update/)
Netrunner is a distro based on Kubuntu.

---

### Post by McNils on 2012-02-01
If you think that its an update problem (moun hangs on my laptop as well when installing large updates). Run some standard commands to complete the installation.

sudo apt-get install -f
sudo dpkg --configure -a

---

