---
title: "Fresh install of Ubuntu 15.04 vivid wont upgrade"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by gh0zt362 on 2016-11-02
I tried sudo apt-get update


sudo apt-get dist-upgrade 

then do-release-upgrade 

and it said upgrading to xenial not supported with this tool .

I was going to upgrade to 15.10 then 16.04 and it seems I cant 

I tried software updater gui and same results now Im stuck at 15.04



I found a thread about this issue but the graceful community decided to close it instead of figuring out a solution. 

So thats why I had to make this thread .

---

### Post by oldfred on 2016-11-02
Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

I believe 15.04 expired in Jan. best just to use live installer from 16.04 as it is LTS with long term support. 
Use Something Else install option and choose existing / (root) as new /.

---

### Post by coffeecat on 2016-11-02
Both 15.04 and 15.10 are past end-of-life and the repositories are closed. That is why you can't update or upgrade 15.04.

Why are you making a fresh installation with an obsolete version? And why then try to upgrade it? If you are making a fresh installation and you want to end up with 16.04, you would be better off simply installing with the 16.04 installer. Better yet, the 16.04.1 point release. You can get the ISOs here:

[http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/)

---

### Post by gh0zt362 on 2016-11-02
> **coffeecat said:**
> Both 15.04 and 15.10 are past end-of-life and the repositories are closed. That is why you can't update or upgrade 15.04.

Why are you making a fresh installation with an obsolete version? And why then try to upgrade it? If you are making a fresh installation and you want to end up with 16.04, you would be better off simply installing with the 16.04 installer. Better yet, the 16.04.1 point release. You can get the ISOs here:

[http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/)

Because I had fedora 21 on this machine for a long time and decided to switch cause I have ubuntu studio on another machine and i really like it so I wanted this machine to also have ubuntu studio and I found the 15.04 disk and installed it .

I had no idea just two versions away wouldnt even be upgradeable

---

### Post by kevdog on 2016-11-03
Just a tip -- that's why you may consider in the future with sticking with LTS versions like 16.04.  LTS versions are supported for like 8 years, whereas point 6 month releases reach EOL pretty quickly.

---

### Post by Impavidus on 2016-11-03
More like 5 years of support for the LTS releases, and that's for Ubuntu. The other flavours get 3 years for the LTS releases (although Kubuntu precise and trusty have 5 years). The non-LTS releases get about 9 months of support.

Upgrades are available from one release to the next and from one LTS release to the next LTS release. Although it's technically possible to upgrade 15.04 via 15.10 to 16.04, it will be quicker and more reliable if you just do a clean install of 16.04.

---

### Post by Bucky Ball on 2016-11-03
[Start here]("http://ubuntustudio.org/download/") and enjoy. :)

Forget the EOL releases and wasting time upgrading.

---

### Post by magicphip on 2016-11-11
> **Impavidus said:**
>  Although it's technically possible to upgrade 15.04 via 15.10 to 16.04
Hello,
do you know where can be found some information to do this upgrade ? I don't really want to install a fresh 16.10 LTS, as I don't want to lose all my configuration.
I am stuck to 15.04. Limited support in time doesn't (or shouldn't) mean limited "upgradability" in time ... IMHO

---

### Post by mörgæs on 2016-11-11
A new version every half a year is a luxury that not many users seem to appreciate. The gift comes with this limitation that some manual work is needed during the reinstall.

If reinstalling Ubuntu 16.04.1 takes long time in your opinion then enjoy the fact that this is the only time through april 2021 you have to do it.

---

### Post by magicphip on 2016-11-11
I really appreciate the every half a year new version update, I am just wondering how can I upgrade from 15.04 to ANY other newer version ...
Because installing 16.0.4.1 looks like re-installing everything, and losing current conf. I am ready to do several successive upgrades if required, so it is not a question of installation time.
If direct upgrade from 15.04 to 16.04 LTS is impossible/refused/not recommended/whatever, is there, at the least, a way to upgrade from 15.04 to 15.10 ? (And then, from 15.10 to 16.04 LTS ?)
Before 16.04 exists, it was possible to upgrade from 15.0.4 to 15.10, so why shouldn't it be possible now ?

---

### Post by oldfred on 2016-11-11
I did upgrades from 6.06 thru 9.04. And had various upgrade issues, most related to my nVidia card & all its settings.
But then wanted to convert to 64 bit and had to d a new clean install. That worked so well that I now only do clean installs, but add another 25GB as / (root). I keep all data in a separate large data partition, so I can easily mount & link all the folders into all my installs.
I now only use the LTS as my main working install, but have all the other versions installed as well.

You should be backing up anyway, as hard drives fail, users make mistakes, and other failures.
Also best to houseclean first.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[URL="https://help.ubuntu.com/community/CategoryBackupRecovery"]https://help.ubuntu.com/community/CategoryBackupRecovery
      [/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 

 If you backup /home and list of installed apps. You can easily reinstall apps and all the settings for those apps will still be in /home.

---

### Post by magicphip on 2016-11-11
Thanks @olfred for sharing.
So I found my answer, the upgrade from 15.04 to 15.10 is possible as it should be, just by replacing vivid by wily in the /etc/apt/sources.list file, as one might expect. I just did it, no problem encountered, no configuration lost.
Now the system detected a new upgrade (to 16.04), and accepted to process it.

---

### Post by gh0zt362 on 2016-11-16
Just to let everyone know. I downloaded and burned a 16.04.1 LTS live cd and it gave me the option since it was installing over 15.04 to upgrade 15.04 to 16.04.1LTS using the disk without formating over all my music . 

So if you have the same issue you can upgrade 15.04 directly to 16.04.1LTS with the 16.04.1LTS live CD  . 

So I was super happy I didnt have to re download from backup disk 80 gigs of music .

---

