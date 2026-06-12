---
title: "Update fails hard"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by wizardStan on 2008-06-15
I tried to update to Hardy today from Gutsy.  I started the update manager, clicked the update button, and let it run.  I'm working off a limited memory here, but I think it got to the second step, after "Preparing" but before "Getting packages".  Updating package repositories or something perhaps?
At the bottom of the progress window, it said something about calculating time.  And then the window was gone.  Just shut down.
I reopened the update manager, and the update button was gone, although hundreds of new packages were available.  So in my ignorance, I updated those.  They finished, I restarted, and now things are not quite happy anymore, if you get my meaning.
I go to the update manager, and get a window "Not all updates can be installed.  Run a partial upgrade...etc..." with two options: partial upgrade, and close.  Partial upgrade gets finishes "preparing" but closes before it starts getting the packages.  If instead I close, and install updates, it says: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "
I drop to prompt and run sudo dpkg --configure -a as recommended, and the output is a bunch of failed updates with "getopt: command not found"
So I run "sudo apt-get install util-linux" to try and install getopt, and it responds "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."  A never ending cycle.
I'm in the process of downloading the Hardy ISO for a complete fresh install, but I'd like to avoid that if I can.

If anyone has some thoughts on how to recover from this, I'd love to hear them.
Alternatively, if someone can suggest a way of installing Hardy from scratch without losing all my settings I'd also appreciate it.
Thanks.

---

### Post by Pumalite on 2008-06-15
Try this first:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
Post the outputs.

---

### Post by wizardStan on 2008-06-15
Ok.  Keep in mind that everything indicates that I'm still running Gutsy, not Hardy. edit: I stand corrected. lsb_release says I'm running 8.04.


david@david-desktop:~$ sudo dpkg --configure -a
sudo: unable to resolve host david-desktop
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up powermanagement-interface (0.3.18) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing powermanagement-interface (--configure):
 subprocess post-installation script returned error exit status 127
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2.1) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libpaper1 (1.1.23) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 127
Setting up linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xpdf-reader:
 xpdf-reader depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing xpdf-reader (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpaper-utils:
 libpaper-utils depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing libpaper-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-pdf:
 cups-pdf depends on libpaper-utils; however:
  Package libpaper-utils is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1


david@david-desktop:~$ sudo apt-get -f install
sudo: unable to resolve host david-desktop
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



david@david-desktop:~$ sudo apt-get update
sudo: unable to resolve host david-desktop
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



david@david-desktop:~$ sudo apt-get dist-upgrade
sudo: unable to resolve host david-desktop
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Pumalite on 2008-06-15
Edit file /etc/hosts to suit your needs:
gksudo /etc/hosts

---

### Post by wizardStan on 2008-06-15
gksudo doesn't appear to do anything.  I used sudo vi instead.  Added my computer to the list (though for the life of me I have no idea why it wasn't there) and reran all those commands.  The only difference is it no longer says "sudo: unable to resolve host david-desktop" for each one.  All other output, including errors, is the exact same.

---

### Post by Pumalite on 2008-06-15
> **wizardStan said:**
> gksudo doesn't appear to do anything.  I used sudo vi instead.  Added my computer to the list (though for the life of me I have no idea why it wasn't there) and reran all those commands.  The only difference is it no longer says "sudo: unable to resolve host david-desktop" for each one.  All other output, including errors, is the exact same.
Sorry,
gksudo gedit /etc/hosts

---

### Post by wizardStan on 2008-06-15
> **Pumalite said:**
> Sorry,
gksudo gedit /etc/hosts
That's what I figured you'd meant, but again, didn't solve any problems.  Unless there's something more you wanted me to do with it that's not obvious.

---

### Post by Pumalite on 2008-06-15
This is mine:
127.0.0.1	localhost
127.0.1.1	pumalite-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Did you find yours?

---

### Post by wizardStan on 2008-06-15
yes, and I added it, as I said.  Made no difference to the relevant output, just that it no longer displays "unable to resolve host david-desktop".  Everything else is exactly as previous.

---

### Post by Pumalite on 2008-06-15
Post the present output of:
sudo dpkg --configure -a

---

### Post by wizardStan on 2008-06-15
Same as before, minus the warning about unable to resolve host

david@david-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up powermanagement-interface (0.3.18) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing powermanagement-interface (--configure):
 subprocess post-installation script returned error exit status 127
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2.1) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libpaper1 (1.1.23) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 127
Setting up linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xpdf-reader:
 xpdf-reader depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing xpdf-reader (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpaper-utils:
 libpaper-utils depends on libpaper1; however:
  Package libpaper1 is not configured yet.
dpkg: error processing libpaper-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-pdf:
 cups-pdf depends on libpaper-utils; however:
  Package libpaper-utils is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by Pumalite on 2008-06-15
Try:
sudo apt-clean
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by wizardStan on 2008-06-15
sudo: apt-clean: command not found


david@david-desktop:~$ sudo apt-get autoremove
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


david@david-desktop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


david@david-desktop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


david@david-desktop:~$ sudo apt-get dist-upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Pumalite on 2008-06-15
The system seems to think you haven't ran sudo dpkg --configure -a

---

### Post by wizardStan on 2008-06-15
I do, and as you can see in the output, it errors out and never completes.  It's missing getopt.  but I can't install getopt because I need to run sudo dpkg --configure -a.  But I can't complete dpkg because I'm missing getopt.  Lather, rinse, repeat.

---

### Post by Pumalite on 2008-06-15
[http://ubuntuforums.org/showthread.php?t=780531](http://ubuntuforums.org/showthread.php?t=780531)
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by wizardStan on 2008-06-15
No go.  Added --force-all to the command, same output:


david@david-desktop:~$ sudo dpkg --configure -a --force-all
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up powermanagement-interface (0.3.18) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing powermanagement-interface (--configure):
 subprocess post-installation script returned error exit status 127
Setting up foomatic-filters (3.0.2-20071204-0ubuntu2.1) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 127
Setting up libpaper1 (1.1.23) ...
/usr/bin/ucf: line 338: getopt: command not found
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 127
Setting up linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.38) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

---

