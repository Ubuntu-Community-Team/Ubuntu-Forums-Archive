---
title: "'Lost applications' on Kubuntu alpha1"
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Seren on 2009-12-12
Krunner seems to be unable to find any application (while the application feature is checked). 

Same thing if I use Kickoff or Lancelot, the application menu remains desesperatly empty. However the 'Favorites' tab is still populated with some apps.

Am I the only with that kind of behavior ?

---

### Post by caryb on 2009-12-12
Sorry to say but my Kickoff menu is fully populated.


Cary

---

### Post by Seren on 2009-12-13
> **caryb said:**
> Sorry to say but my Kickoff menu is fully populated.


Cary

Thanks for your feedback, I already tried to reconfigure every package without further success.

I'll try to launch an fschk to be sure that I don't have any corrupted files.

---

### Post by koso on 2009-12-13
Have you tried to reset menus using kickoff menu editor? I had not exactly your problem. I tried to move some application from default location in menu, and they were not shown using kickoff.

---

### Post by Seren on 2009-12-14
I have totally removed kde (remove --purge) and reinstalled everything from scratch by 'sudo apt-get install kde-minimal' and my kickoff or krunner still does not display any applications.

:/

There is probably a kderc or something left somewhere or something, but I can't find it.

If you have any other ideas, they are welcome...

---

### Post by koso on 2009-12-14
Make backup of your profile, and try to delete .kde folder .. on next startup should be all kde config files recreated with kubuntu defaults. Then you can start partialy restoring configs from backup and find out where was problem :)

---

### Post by Seren on 2009-12-14
> **koso said:**
> Make backup of your profile, and try to delete .kde folder .. on next startup should be all kde config files recreated with kubuntu defaults. Then you can start partialy restoring configs from backup and find out where was problem :)

I have already tried last night, I should have mentionned it.

Thanks for the idea anyway ;).

---

### Post by garvinrick4 on 2009-12-15
I have a partition with Ubuntu Lucid and a few days ago lost my Preferences and Admin.
but they came back eventually. Is your mirror an up to date one or is it two days to a week behind. There are over 325 of them and they are all different bandwidth's and current or from 1 to 7 days behind. Could be you just have the same glitch quite a few of
us had and you just need to be patient. Check out your mirror though it is important when
doing dailys in Alpha's and Beta's.

---

### Post by Seren on 2009-12-15
I am on the main server and up to date.

This is not necessarily a big problem, I can launch most applications from Konsole just fine. 

The thing is that I am sure there is pretty straightforward way to check if the applications information is on the correct path, with the correct permission, but I can't find the information.

I will rather pester people on KDE forums rather than here, since I am apparently the only one suffering from this. :)

---

### Post by Seren on 2009-12-16
I solved my problem.

For an unknown reason, /etc/xdg/menus/kde4-applications.menu
was empty on my install.

I did reinstall kdelibs5-data with sudo aptitude reinstall and it works again!


I don't quite understand why reinstalling kde a few nights ago didn't fix the issue.

(Oddly enough I found what was the issue while reading a documentation about kde 3.2 ...)

---

