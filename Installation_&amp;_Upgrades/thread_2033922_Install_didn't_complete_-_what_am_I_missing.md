---
title: "Install didn't complete - what am I missing?"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by lindsayward on 2012-07-27
Hi there!
I have installed 12.04 64-bit on a new HDD with some volumes set up with LVM, but the install did not successfully complete the "Select and Install Software" step. I tried to find out where it failed, but couldn't, so I just went on to the next step (Grub)...
(I have previously had 11.10 installed on another HDD, which is disconnected right now until I get this set up.)

So I had a system I can boot and log in to, but with no graphics. After trying several things, I thought maybe the problem is that I'm missing some of the packages that should have been installed originally...
I installed a few things, including the nvidia-current, xorg-server and ubuntu-desktop and after a reboot I got a graphical desktop - yay :)

**So, how can I find out what I'm missing, and is there a definitive list of ALL of the default packages, so I can install all of those now?**

Thank you in advance!

---

### Post by efflandt on 2012-07-27
I had that problem  too with a laptop (from 2006) that had no trouble booting to a live/install iso on USB, but it hung 90% into "Installing system" for hours with no further progress and no errors.  I could not boot regularly, could boot recovery, but networking was apparently not completed, so it could not connect network to fix broken packages.

So I ended up using "alternate" 64-bit 12.04 install from CD, and that worked without any problems. [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by lindsayward on 2012-07-29
Thanks for the reply.
I did use the alternate 64-bit installer, since I set it up with LVM.

Any other suggestions for installing all of the "normal" packages?

Perhaps someone could provide a list of the installed packages after a clean base install?

Thank you.

---

### Post by oldfred on 2012-07-29
I think this is the official versions.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
See manifests download like from this for your version:

[http://askubuntu.com/questions/48886/ubuntu-default-installed-packages-for-any-version](http://askubuntu.com/questions/48886/ubuntu-default-installed-packages-for-any-version)

---

### Post by lindsayward on 2012-07-30
Thank you. I believe that is just what I was looking for. I imagine I will be able to figure out a shell command to install all of the packages in that file. Like: [http://askubuntu.com/questions/83617/can-i-build-a-ubuntu-iso-from-a-manifest](http://askubuntu.com/questions/83617/can-i-build-a-ubuntu-iso-from-a-manifest)

---

### Post by oldfred on 2012-07-30
You should also be able to export the current list you have and then compare them.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Full list includes all the support files.

Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

Again a lot of the lists are just enough different you cannot use them directly. But the link shows a way to select out the file name from the list.

---

### Post by lindsayward on 2012-08-01
Thanks very much.
I'll look through this and see what I can do. 
I appreciate the response.

---

