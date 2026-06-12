---
title: "[SOLVED] upgrade from kubuntu 8.04 to 8.10, made my laptop useless"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by linomac on 2008-10-04
while upgrading to kubuntu intrepid beta using the sugest method with adept,
the installer was asking me questions whether to choose the old config files at /etc.
I chose to keep the old version. 

after upgrade, i could not start kubuntu not even once.

after showing the kubuntu loading bar, i get a test message that it cannot load some pidfiles because the file-system is readonly.
If i wait 2-3 minutes the loading continues, i can login at text mode, but still cannot do anything because file system is read only.

I rebooted with recovery mode, fix x server, start, kde shows login prompt. after graphical login i see 2-3 icons loadins and again at login screen. so i cannot login.

If at recovery mode, i go to root console, and write startx again after 2-3 icons, kde (4.1.2) kicks me to console, telling me something about 11-something error.

Renaming .kde .kderc .kde4 /etc/kderc did not help
Renaming /etc/fstab did not help
Changing fstab entry for harddisk from error=remount-ro to error=continue did not help


Any help please?
I m completely horrified and i ll not move on upgrade the rest of the computer till final release, but for the moment please help me fix this computer that i need so much

Thanks a lot! :guitar::KS

---

### Post by smethurst on 2008-10-05
I too have been bitten by a bad upgrade.

I managed to repair the system enough to log in to KDE4 by relaunching the dist-upgrade via the command line ("apt-get dist-upgrade"). It seems that not all the packages were properly installed the first time.

The next thing I am trying is to just reinstall everything from scratch.

KDE4 seems to still be at best a beta version.. it's very disturbing to see that the Kubuntu team are forcing it on everyone in the next release by automatically removing KDE3.

---

### Post by Delvien on 2008-10-05
> **linomac said:**
> while upgrading to kubuntu intrepid beta using the sugest method with adept,
the installer was asking me questions whether to choose the old config files at /etc.
I chose to keep the old version. 

after upgrade, i could not start kubuntu not even once.

after showing the kubuntu loading bar, i get a test message that it cannot load some pidfiles because the file-system is readonly.
If i wait 2-3 minutes the loading continues, i can login at text mode, but still cannot do anything because file system is read only.

I rebooted with recovery mode, fix x server, start, kde shows login prompt. after graphical login i see 2-3 icons loadins and again at login screen. so i cannot login.

If at recovery mode, i go to root console, and write startx again after 2-3 icons, kde (4.1.2) kicks me to console, telling me something about 11-something error.

Renaming .kde .kderc .kde4 /etc/kderc did not help
Renaming /etc/fstab did not help
Changing fstab entry for harddisk from error=remount-ro to error=continue did not help


Any help please?
I m completely horrified and i ll not move on upgrade the rest of the computer till final release, but for the moment please help me fix this computer that i need so much

Thanks a lot! :guitar::KS


When posting on a BETA forum, it is best not to label your thread negatively. You have to realize this is still in beta and is prone to bugs / wrecking your setup. If you are not willing to go through this, don't use it. It is not like you are paying for this. 

It just makes you sound like a whiney baby and people will ignore it, even if you have true problems.
 
If you find that you have problems with certain things then post an individual thread with the problem, clearly labeling what the issue is, without your opinions.  

If you don't want to move to the new version, then don't. No one really cares if you do. It's a free world.

---

### Post by Delvien on 2008-10-05
While reading your post, you stated that you chose old configs, which can pose a major problem, as new applications are installed configs change. Which if you chose not to take these new configs, it can make apps not start, or things to crash. Which might be your problem. 

Back up your data and do a reinstall. Either of the previous version or of the beta (I would, if I were you, install the released version of 8.04)

---

### Post by xebian on 2008-10-05
IMHO I will not recommend upgrading from 8.04 to 8.10 for Kubuntu.  KDE4 is totally different from KDE3.

---

### Post by smethurst on 2008-10-05
A complete re-installation seems to have solved the main issues.. I've still got various video corruption and a few other weird things going on, but at least the computer is up and running again.

Conclusion: don't update between 8.04 and 8.10? Do a re-install.

---

### Post by Delvien on 2008-10-05
> **smethurst said:**
> 
Conclusion: don't update between 8.04 and 8.10? Do a re-install.

I did an upgrade, and mine was just fine. You just have to accept the new configs.

---

### Post by p_quarles on 2008-10-05
OP requested that this thread be deleted, but since we don't do that under normal circumstances, I am closing it instead.

---

