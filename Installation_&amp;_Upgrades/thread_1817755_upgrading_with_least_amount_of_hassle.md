---
title: "upgrading with least amount of hassle"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Dopaque on 2011-08-03
Hello. I would like to upgrade my linux distro, since I'm using Karmic Koala and it is no longer supported anymore. However, upgrading via the updater always breaks my system, so I want to do a clean install.

However, I have a LOT of programs installed in this machine, including a good number of games. Otherwise I think most of my data is neatly confined to my home folder, which I can easily transfer via external hard drive.

How do I get all my programs over, however? Like my PDF printer, for example, or all my games, or Inkscape, or Skype, or any number of things that I have installed. Especially WICD. I can never get my wireless internet to work without WICD.

I will make a list of my programs beforehand, just in case something goes wrong, but is there any kind of less painful and time-consuming way to do this than going back and installing every program all over again from scratch?

---

### Post by akand074 on 2011-08-03
I'd make a list of programs and just do a clean install and reinstall. Reinstalling all your applications is actually not as time consuming as you'd think in Ubuntu. Literally takes me 30 minutes after the install to be back where I was before. Only extra time consumption would be wine stuff and such but if you backup your home folder (or it's on a separate partition) then those won't even be touched.

Also your programs may have an updated version for the newer Ubuntu and/or the version you are using is no longer compatible. Also I used to not be able to connect on my laptop except with WICD on karmic. Has worked just fine on the default ever since so it's good to check out what's new. I like to keep an open mind during new distribution installs.

Main thing is, I'm not sure you can backup your programs. If you were going to just reinstall karmic, then you can backup your programs by backing them up via synaptic package manager, but otherwise I think it'd cause issues reinstalling things that shouldn't be reinstalled and possibly versions that shouldn't be used depending on how it works.

---

### Post by oldfred on 2011-08-03
If you installed thru synaptic then you can easily reinstall those. I do this on every new install. But this does not include files you downloaded as debs. & installed separately.

# howtolistinstalledPackages.txt

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

If you have space on your hard drive, you can install in another root partition. Then if something is missing you can go back and get it. I now do every install in a new 20 or 25GB / (root) partition, but I have all my data in other partitions.

A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/122047)
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html)
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

---

### Post by akand074 on 2011-08-03
@oldfred that's the method I was talking about, that I've used when I've reinstalled the same distribution. But if you, lets say, save all your packages from 10.10, then install 11.04. Would it install the versions saved from 10.10 or will it keep the updated ones? Also packages that have been removed from Ubuntu in 11.04, but were in 10.10, would it bring them back and cause problems? Or does that method only save packages you manually installed yourself after the installation?

 Basically my question is, can you safely/successfully do that when you install a different version of Ubuntu? (not to thread steal, this can be useful and related).

---

### Post by Dopaque on 2011-08-03
no, not thread stealing. I want to know too.

---

### Post by oldfred on 2011-08-04
If you look at the list it is just a package name. It installs the version that matches the Ubuntu version you install.

I have found it will install old packages. For example I was still installing python2.5 until I deleted it. I know it includes OpenOffice and unless in 11.04 you want openoffice & libreoffice you need to house clean that also. The list is everything and is very long ( a lot of libxxx packages), but it only installs missing packages, so it will not double up.

If you want to compare lists:
HowTo: Create a list of installed packages
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

You can also list sources, but cannot just copy them back as the version is in the line.
But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the list of packages will only reinstall Ubuntu files.

I have attached the script I run. A lot is commented out. I have updated it with new,corrected,  changes, and add some suggestions that I have found, that I have not tested and install some packages even though they would have been installed by the dpkg list.

---

### Post by akand074 on 2011-08-04
Oh okay yeah that makes perfect sense. Good to know, I usually don't mind reinstalling everything from scratch as it only takes me about half an hour. But it's good to know.

---

