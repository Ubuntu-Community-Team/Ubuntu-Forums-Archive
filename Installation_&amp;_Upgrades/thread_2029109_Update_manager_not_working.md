---
title: "Update manager not working"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by donaldt on 2012-07-19
My update manager is broken.  It freezes when it gets to "applying changes".  I did a sudo apt-get update and that worked, leaving only this message:

 Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/lucid/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/lucid/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
donald@donald-Aspire-3810T:~$ 

This is left over from Wine as I dumped it a while back.  I'd like to get rid of this and find a way to get update manager to work normally again.

Any help will be much appreciated..

donaldt

---

### Post by plucky on 2012-07-19
> Failed to fetch [http://wine.budgetdedicated.com/apt/...-i386/Packages](http://wine.budgetdedicated.com/apt/...-i386/Packages) 404 Not Found

Open Software Sources using the **Settings** button in Update Manager and delete the Wine Repository.

Good Luck

---

### Post by dino99 on 2012-07-19
> **donaldt said:**
> 

 Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/lucid/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/lucid/main/binary-i386/Packages)  404  Not Found

donaldt

your url above is deprecated (budgetdedicated) since a while. Replace it by editing /etc/apt/sources.list

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

but you might want to clean your sources.list a little bit: the errors you have posted are related to both "hardy" & "lucid" : only use the archive of your actual distro (i suppose its "lucid")

note: look at the others lines too :confused:

---

### Post by donaldt on 2012-07-19
I got rid of the wine stuff as suggested via update manager settings.  I'm afraid your kind reply has confused me on what is required to clean up and restore to life my update manager.

I would like to edit out the lines you suggest, but don't know what my 12.04, 32bit system is using.  Would you care to lead me a bit more, please?

Thanks,

donaldt

---

### Post by plucky on 2012-07-20
> **donaldt said:**
> I got rid of the wine stuff as suggested via update manager settings.  I'm afraid your kind reply has confused me on what is required to clean up and restore to life my update manager.

I would like to edit out the lines you suggest, but don't know what my 12.04, 32bit system is using.  Would you care to lead me a bit more, please?

Thanks,

donaldt

Is the Update Manager now working?

All your repositories will be displayed in the **Software Sources** window that you opened to get rid of the Wine repositories.

Just look at all the lines on the Other Software Tab and delete the ones that don't have **Precise** in the line.

If in doubt,open a terminal and post output for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
``` and someone will tell you what to get rid of.

Good Luck

---

### Post by donaldt on 2012-07-20
OK.  Here is the output from the terminal commands.

Someone please let me know what needs to be removed.  

Thanks

donaldt

donald@donald-Aspire-3810T:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) natty free non-free # disabled on upgrade to natty
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps # disabled on upgrade to maverick disabled on upgrade to natty


# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
donald@donald-Aspire-3810T:~$ cat /etc/apt/sources.list.d/*.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
donald@donald-Aspire-3810T:~$

---

### Post by plucky on 2012-07-20
You have the same repositories twice.

Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of the lines in red
 ```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
[color=red]deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse[/color]
# deb http://archive.canonical.com/ubuntu precise partner
[color=red]deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse[/color]
# deb http://packages.medibuntu.org/ natty free non-free # disabled on upgrade to natty
# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps # disabled on upgrade to maverick disabled on upgrade to natty

```

You could even delete the lines that have natty or lucid in them.

Also you do not need the lines that start with **deb-src** as you probably don't need the source code.So put a # in front of all the lines that start with deb-src.

Good luck

---

### Post by donaldt on 2012-07-20
I added the # in front of the lines as you suggested.  It still only goes part way through "applying changes" and then it hangs up and stops.  

I've tried to copy the page for all to see, but it is inside of the update manager and I can't make that work.

donaldt

---

### Post by plucky on 2012-07-21
> **donaldt said:**
> I added the # in front of the lines as you suggested.  It still only goes part way through "applying changes" and then it hangs up and stops.  

I've tried to copy the page for all to see, but it is inside of the update manager and I can't make that work.

donaldt

Try using the terminal ```
sudo apt-get update && sudo apt-get dist-upgrade
``` and post the output.


Use **[noparse]```
your text
```[/noparse]**

 blocks to display the output.


Good Luck

---

### Post by donaldt on 2012-08-02
Plucky,

I have not defected or died.  I was out of town for 10 days.

Just now, I opened the terminal and after entering the commands you listed, I decided to try update manager once more.  Guess What?  It took about 10 minutes, but all 118 updates that were listed as "downloaded but not installed" came cascading down the list of changes.  At the end of all that activity, update manager works normally again and has assured me that "all programs are up to date".

Wonderful!  Thank you so much.  It may have been black magic, but something in your command line cleaned up the bottle neck that was preventing update manager from completing its upgrading task.

donaldt

---

### Post by donaldt on 2012-08-05
OOPS!

I spoke too soon.  If there is any activity on this thread still out there, the update manager still locks up about 2/3 of the way through an update.  The use of [sudo apt-get update && sudo apt-get dist-upgrade] in terminal will temorarily clean it out and allows completion of the update, but the next time it is used it will still hang up, requiring a re-boot to get rid of the problem.

I have been out of town for two weeks, so don't know if anyone is still reading this thread. 

Any help in cleaning up update manager would be appreciated.

donaldt

---

