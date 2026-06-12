---
title: "Migrate 32bit Ubuntu to 64bit Ubuntu"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by iamsorandom on 2012-12-19
Hi, 

I'm in the process of migrating from 32bit to 64bit; I want to install the same programs on the new install, is it OK to do this automatically with synaptic package manager (saving markings in the 32 bit and then using read markings-apply in the 64 bit)?

Or will this give me 32 bit packages on a 64-bit install?

Both installs are on the same machine, I'm currently dual booting. Thanks!

---

### Post by coffeecat on 2012-12-19
Post moved to its own thread.

---

### Post by iamsorandom on 2012-12-19
OK, thanks - anyone got any thoughts/advice?

---

### Post by pierceTN on 2012-12-19
> **iamsorandom said:**
> OK, thanks - anyone got any thoughts/advice?


I know with the default back up tool in gnome (I think deja dump) you can save a list of all your installed programs:  Then you could copy that list off of your computer, then when you switched to 64 bit you could install that list of programs through the terminal.



-Pierce

---

### Post by iamsorandom on 2012-12-19
Thanks Pierce - yeah I'm thinking about doing something like that (synaptic will do it and then apply it for you too meaning you don't have to enter everything manually) but I'm not sure if it will create issues because of the old list being packages for a 32-bit OS?

---

### Post by oldfred on 2012-12-19
I believe synaptic works just fine, but used command line. The command line output is just a text file so you can even edit it, but it does not have any versions just package names so I use it when I upgrade. Only if a package then does not exist in the new version does it not get installed. First time I used it, I had not housecleaned for years and had obsolete packages. Also you may want to review packages as some change if upgrading and you do not need older ones. Like OpenOffice became LibreOffice.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

       and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

   But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,
    
List works fine but it very long as it includes all dependency files in list. Some other lists:

       List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt

       gui apps list only:
ls /usr/share/applications

 Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

       List of default applications:
Look for manifests for version:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by pierceTN on 2012-12-19
> **iamsorandom said:**
> Thanks Pierce - yeah I'm thinking about doing something like that (synaptic will do it and then apply it for you too meaning you don't have to enter everything manually) but I'm not sure if it will create issues because of the old list being packages for a 32-bit OS?

If your on 64 bit it should install the 64 bit package. unless it's saving the exact package not the program.


Pierce

---

### Post by iamsorandom on 2012-12-27
Thanks, yes that helped. Problems actually sorted now (in the end I switched to linux mint KDE, but that's another story)

Oldfred, you said 'don't import all sources', what did you mean by this? Just for anyone else wanting to try the same thing.

Seems like it does work though using synaptic to do the migration. Thanks!

---

### Post by oldfred on 2012-12-27
If you are upgrading and have PPA's. The old PPA's may not upgrade or have upgraded to the new version. Some may need to be different for 32 or 64 bit versions.
Also some PPA's that I used to add, get incorporated into Ubuntu and then are not needed at all. I used to add Sun's java, but now use the default openjdk. I used to add medibuntu and now that is not needed if you add the restricted extras when installing. And I used to add winetricks from a ppa, but now it is in the repository.

So best to turn off or edit out the extra PPAs and review them separately.

---

