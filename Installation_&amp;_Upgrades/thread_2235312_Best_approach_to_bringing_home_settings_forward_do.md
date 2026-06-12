---
title: "Best approach to bringing /home settings forward doing fresh install of 14.04"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by johnfrith1 on 2014-07-20
I wish to go from 12.04 to 14.04, preferably doing a fresh install.

What is the best and / or easiest way to bring forward my settings and data? 

I have spent some time trying to google an answer to this, but so far have only found conflicting anecdotal stories - some say that there are no problems bringing forward a 12.04 /home to a fresh 14.04 installation. Some say there could be incompatabilities.

The options I'm considering are:

1) From 12.04:
        - backup /home
        - fresh install 14.04
        - restore /home.

2) From 12.04:
        - backup /home
        - fresh install 14.04
        - restore **some** of /home. (If so, how do I decide what to restore?)

3) From 12.04:
        - backup /home
        - upgrade from 12.04 to 14.04 (in order to make /home compatible with 14.04)
        - backup /home
        - do a fresh install of 14.04
        - restore /home (14.04 version)?


I don't think it's particularly relevant, but my /home is on a separate partition, and I intend to re-partition disk, installing Windows first, then Ubuntu.

I'm not confident doing anything complicated.

Thanks in anticipation for any help.

---

### Post by vanadium on 2014-07-20
I would say option 2.

I also have a separate partition for /home. To perform a fresh install, I boot into a live session. Then I mount my home partition, and move my old home folder out of the way by renaming it: "vanadium" -> "vanadium_old". Then I perform the new install, creating a fresh "vanadium" account.

My user data under Documents, Videos, etc. can easily be moved to the new account. Selectively, settings can be moved as well. I only reuse the entire .thunderbird, the file places.sqlite (firefox bookmarks), and the "bin" folder.

I keep "vanadium_old" for a while in case I forget or miss something. After that, it can safely be deleted.

---

### Post by oldfred on 2014-07-20
You always want the good backup of /home.

You also may want to extract a list of installed applications if you have installed a lot of additional apps. While all data is in /home, you have to reinstall all apps that are not part of default install.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

 From old install
dpkg --get-selections > ~/my-packages

It is just a text list, and you may want to houseclean out obsolete packages, old kernels or others, if you have not done that in your current install.

I run the dpkg list of installed apps regularly and make sure that is included in my backups.

If you have a separate /home you can just use Something else. If you select current / (root) that will be overwritten, but you also select your current /home but DO NOT reformat it. The new install may overwrite some things but the majority of your settings and all your data will then be in the new install.

---

### Post by johnfrith1 on 2014-07-20
Thanks Vanadium and oldfred. I found both posts helpful.

I think I'm going to try Vanadium's suggested method, as this seems cleaner. I hope there is no conflict with bringing the .thunderbird file used under the older Ubuntu version into 14.04.

oldfred, when I run the list of packages you suggest, there seem to be 100's of files, most of which I'm not aware of installing. I think it's beyond me to know which ones not to install / not to install, so perhaps I will make the list and keep it for reference in case I'm missing some functionality after the new install.

I feel better about moving forward now.

---

### Post by oldfred on 2014-07-20
Yes, the list is huge. It includes every file installed, so all the defaults are in there and it includes all the support files which are difficult to know which applies to which.
Files already installed would not be reinstalled and default install does have most of them.

I have used Thunderbird files since it was .5 or .6 and then called Firebird. Name changed becuase of conflict with the database. But I have dual booted with XP since 2006 and many Ubuntu installs. Now not using XP but load same Firefox & Thunderbird profiles in all my installs. I also copy to my laptop when traveling & back to desktop when I return. So profiles seem to work well in most cases.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Mark_in_Hollywood on 2014-07-24
deleted

---

### Post by johnfrith1 on 2014-08-06
Thanks oldfred.

Have now completed my upgrade and have a stable dual boot system. I didn't re-install packages from the old list, as I kind of enjoyed discovering what was missing, and seeing if there was a better solution found compared to what I had been using. I did, as you suggested, just keep .firefox and .thunderbird (I also kept .skype until it started failing to load, so I deleted .skype and didn't notice losing anything).

Thanks for your kind help.

---

