---
title: "Can I copy my profile and settings to new installation?"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by petermg on 2012-10-11
So I've been thinking maybe I should install Ubuntu fresh on my system, after all it's running 12.04 and has been upgraded since like 6, 7, or 8.  So it's got a lot of updates and upgrades on top of it and I've read some people say that it's better to just do a new install rather than an upgrade?  Hopefully that's debatable.  I was wanting to try it however, but I have some customized hardware rules and drivers installed and was wondering if A, I could in a simple fashion successfully copy over my profile from my current install to the new one, and B, replicate all my settings as simply as possible.  Is there a way to do it?  

Reason I'm thinking about doing this is because I feel my system is running slower than it should, but in the meantime I'm gonna install a spare HDD and try a fresh install using that one.

---

### Post by oldfred on 2012-10-11
All user settings are in /home as is most of your data unless you have separate data partitions. You may have some system settings that you customized in /etc. And you may have installed lots of applications and want to automate the reinstall.

I had to do a clean install when converting from 9.04 to 9.10 and from 32bit to 64bit but 9.04 was upgraded from 6.06 every 6 mo. I now only do clean installs. It automatically housecleans everything.

My recovery from hard drive failure is just another clean install so I try to back up everything I need. 

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

I do not have a separate /home but do have almost all data in separate data partitions, so my /home is small and easily backed up. 

If doing a new install to a different drive then you have the luxury of experimenting. I do not copy all of /home settings, but only some. And the same with settings in /etc. I do try to save a copy of any file I manually edit in /etc into a folder in /home so my normal backup of /home includes those custom settings.

---

### Post by petermg on 2012-10-12
> **oldfred said:**
> All user settings are in /home as is most of your data unless you have separate data partitions. You may have some system settings that you customized in /etc. And you may have installed lots of applications and want to automate the reinstall.

I had to do a clean install when converting from 9.04 to 9.10 and from 32bit to 64bit but 9.04 was upgraded from 6.06 every 6 mo. I now only do clean installs. It automatically housecleans everything.

My recovery from hard drive failure is just another clean install so I try to back up everything I need. 

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

I do not have a separate /home but do have almost all data in separate data partitions, so my /home is small and easily backed up. 

If doing a new install to a different drive then you have the luxury of experimenting. I do not copy all of /home settings, but only some. And the same with settings in /etc. I do try to save a copy of any file I manually edit in /etc into a folder in /home so my normal backup of /home includes those custom settings.

Thanks!  I will give this a try.:KS

---

