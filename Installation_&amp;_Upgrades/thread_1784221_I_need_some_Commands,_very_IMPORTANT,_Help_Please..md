---
title: "I need some Commands, very IMPORTANT, Help Please..."
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by xcommunistx on 2011-06-16
I need some Commands (like Terminal = gnome-terminal ) for those:
Ubuntu Software-Center
Desks (the 4 Desktops)
Trash
Apps

---

### Post by oldos2er on 2011-06-16
Ubuntu Software Center is software-center. Trash is located in ~/.local/share/Trash

---

### Post by oldfred on 2011-06-17
Do you want to install from command line?

The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
#Example:
sudo apt-get install ubuntu-desktop

If you want a list of installed apps to reinstall:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

If you want to install an individual app, but you have to know apps name:
sudo apt-get update
apt-get install gnome-mplayer
apt-get install mozilla-mplayer soundconverter
apt-get install nautilus-image-converter

---

### Post by xcommunistx on 2011-06-17
> If you want to install an individual app, but you have to know apps name:
sudo apt-get update
apt-get install gnome-mplayer
apt-get install mozilla-mplayer soundconverter
apt-get install nautilus-image-converterYes i want to install the APps i named at the Start of thsi Thread but i DON'T KNOW the apps name and that's what I'M searching for...

---

### Post by Praveen30 on 2011-06-17
if you don't know the exact name of the applications but you have some idea of name then try this--

sudo apt-cache search (application-name)
ex:
sudo apt-cache search forzen bubble

here are the methods for searching applications--
[http://www.tricksfind.in/2011/05/how-to-search-for-applications-in.html](http://www.tricksfind.in/2011/05/how-to-search-for-applications-in.html)

---

### Post by xcommunistx on 2011-06-17
Thank you *_**[COLOR=Red]VERY[/COLOR]**_*[COLOR=Red] [COLOR=Black]much, now i found everything  i need...[/COLOR][/COLOR]

---

