---
title: "It won't install for some reason."
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by scorx on 2008-08-15
Hello, I am fairly new to xubuntu. I have been trying to install java, flash play ect.. I recently used xubuntu before this and got everything installed fine by reading up on these forums, never had to post my own till now.

Flash is now installed and works fine.
Java on the other hand will not install, I tried sudo apt-get install sun-java6-plugin, and many more things.
Terminal says this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  brasero: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  gnome-mount: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  gnome-power-manager: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  gnome-screensaver: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  libexo-0.3-0: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  orage: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  python-notify: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  update-notifier: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
  zenity: Depends: libnotify1 (>= 0.4.4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have no clue what any of this means could someone help me?

---

### Post by oldos2er on 2008-08-15
Did you run "sudo apt-get -f install" like it advised?

 If you're still having problems after that, please post the output of "cat /etc/apt/sources.list"

---

### Post by scorx on 2008-08-15
I did indeed and this is what happened.
-desktop:~$ apt-get -f install sun-java6-plugin
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
toby@toby-desktop:~$ su
Password: 
su: Authentication failure

---

### Post by scorx on 2008-08-15
someone please help me

---

### Post by oldos2er on 2008-08-15
Run this command: sudo apt-get -f install

---

### Post by oldos2er on 2008-08-15
> **scorx said:**
> I did indeed and this is what happened.
-desktop:~$ apt-get -f install sun-java6-plugin
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
toby@toby-desktop:~$ su
Password: 
su: Authentication failure

 Run the command I gave you in post #5. What you ran (apt-get -f install sun-java6-plugin) is quite different. Another way of doing this is to open up Synaptic Package Manager, and click 'Fix Broken Packages' under the 'Edit' menu.

 Ubuntu has the root account disabled by default, which is why you see the su: Authentication failure error. Use sudo instead.

---

