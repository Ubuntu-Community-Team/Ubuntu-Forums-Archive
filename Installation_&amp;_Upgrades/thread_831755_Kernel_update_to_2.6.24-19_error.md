---
title: "Kernel update to 2.6.24-19 error"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by carlos.pereira on 2008-06-17
Hi all,

today while installing today kernel updates i had the following error:

E: linux-image-2.6.24-19-generic: subprocess post-installation script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-19-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-19-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

I also had a misbehavior in the window to chose if i want to keep my main menu preferences (I believe that was asked there),  this windows freeze. 


What can i do to install this update?

---

### Post by tech0007 on 2008-06-17
Go to applications->accessories->terminal.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by tech0007 on 2008-06-17
Go to applications->accessories->terminal.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by carlos.pereira on 2008-06-17
> **tech0007 said:**
> Go to applications->accessories->terminal.

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

I try that with no success, the return messages where the following
```
carlos@nl10:~$ sudo apt-get update
Hit http://pt.archive.ubuntu.com hardy Release.gpg
Ign http://pt.archive.ubuntu.com hardy/main Translation-en_US
Ign http://pt.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://pt.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://pt.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://pt.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://pt.archive.ubuntu.com hardy-updates/main Translation-en_US          
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://pt.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://pt.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://pt.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://pt.archive.ubuntu.com hardy Release                                 
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://pt.archive.ubuntu.com hardy-updates Release                         
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://archive.canonical.com hardy Release                                 
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US           
Hit http://pt.archive.ubuntu.com hardy/main Packages                
Ign http://ppa.launchpad.net hardy Release.gpg                      
Ign http://ppa.launchpad.net hardy/main Translation-en_US          
Hit http://pt.archive.ubuntu.com hardy/restricted Packages                     
Hit http://pt.archive.ubuntu.com hardy/main Sources                            
Hit http://pt.archive.ubuntu.com hardy/restricted Sources                      
Hit http://pt.archive.ubuntu.com hardy/universe Packages                       
Hit http://pt.archive.ubuntu.com hardy/universe Sources                        
Hit http://pt.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://pt.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://archive.canonical.com hardy/partner Packages                        
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]               
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]               
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://pt.archive.ubuntu.com hardy-updates/main Packages
Hit http://pt.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://pt.archive.ubuntu.com hardy-updates/main Sources
Hit http://pt.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://pt.archive.ubuntu.com hardy-updates/universe Packages
Hit http://pt.archive.ubuntu.com hardy-updates/universe Sources
Hit http://pt.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://pt.archive.ubuntu.com hardy-updates/multiverse Sources
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Fetched 2B in 0s (2B/s)  
Reading package lists... Done
carlos@nl10:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carlos@nl10:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carlos@nl10:~$ 

```

---

### Post by Sub101 on 2008-06-17
Have you got proposed updates checked in the software sources? -19 is still only a proposed and not a default upgrade.

---

### Post by gpuliti on 2008-06-17
Hello there,
I updated to -19, but it won't show in the menu.lst and I was forced to boot into -18. However, the -19 shows up in synaptic as installed.

Anybody had the same issue with this update? Thanks!

~Gian

---

### Post by Sub101 on 2008-06-17
When you updated did it ask you to change the grub config to the manufacturers version?

---

### Post by jou770d on 2008-06-17
I don't have proposed updates enabled and I've been promoted to update the kernel.
But as I'm on a slow connection atm I haven't tried it.

---

### Post by gpuliti on 2008-06-17
I think I selected to keep the menu.lst updated (or something like that).

Should I try to add the lines to the menu.lst manually? After all the vmlinuz-2.6.24-19-generic file exists in the boot folder.

Thanks again!

---

### Post by avtolle on 2008-06-17
Suggestion: at the terminal```
df -h
``` to see if your boot partition is full (if you have a separate boot partition). If it is, delete an older kernel with associated headers, etc., and try the update. If not, post back for additional assistance.

---

### Post by gpuliti on 2008-06-17
Thanks! It does not look like it's full:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             7.7G  5.9G  1.5G  81% /
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   72K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   38M  1.5G   3% /lib/modules/2.6.24-18-generic/volatile
/dev/sda6             6.6G  2.2G  4.2G  34% /home
/dev/sda4             4.9G  4.1G  824M  84% /media/sda3
/dev/sda1              65G   47G   19G  72% /media/Gianluca

However, the update manager says that no update is available, I guess because the -19 kernel was correctly installed, just not well linked to the grub, perhaps.

---

### Post by avtolle on 2008-06-17
Looks like you have room. Try the terminal commands earlier posted, and see if this helps at all.

EDIT: Sorry, got confused a bit with to whom I was responding. I think (I don't dual boot) you will need to edit your Grub menu file.

---

### Post by gpuliti on 2008-06-17
Thanks!
I went ahead and in the menu.lst I copied and pasted the lines of the -18 kernel and changed the -18's into -19's. 

I rebooted into it, and it works great! I still have no idea why the grub didn't automatically update (as usual), but all it matters is that it works now :)

Thanks again :)

---

### Post by avtolle on 2008-06-17
Good to know. As long as it works and doesn't break anything, right? :-)

---

### Post by avtolle on 2008-06-17
@carlos.peria, have you checked to see whether your boot partition is full?

---

### Post by carlos.pereira on 2008-06-17
> **avtolle said:**
> @carlos.peria, have you checked to see whether your boot partition is full?

Yes i also have space

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              33G   21G   10G  68% /
varrun                506M  224K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   38M  469M   8% /lib/modules/2.6.24-18-generic/volatile
gvfs-fuse-daemon       33G   21G   10G  68% /home/carlos/.gvfs
/dev/sdb3             138G  112G   27G  81% /media/DADOS
/dev/sdb1             9.9G  6.0G  3.6G  63% /media/disk

I will try edit menu.lst

---

### Post by gpuliti on 2008-06-17
ahah, right :)

---

### Post by carlos.pereira on 2008-06-17
carlos@nl10:~$ uname -a
Linux nl10 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

But I am having problems with the screen resolution:( I am getting a 800*600 resolution:|

So far the only problem detected

I will try to fix..

---

### Post by carlos.pereira on 2008-06-17
Problem solved:) everything seams normal.

Tks a lot;)

---

### Post by shareme on 2008-06-17
I have a similar problem..after upgrade to 2.6.24.19 di not boot up right X server not configured error..

menu/lst is showing kernel entries for

2.6.24.16
2.6.24.17
2.6.24.18

and two entries for 2.6.24.19 a top of list..

So how do I adjust menu.lst to get everything correct to boot?

Going to try the esc command when first booting to see if I get menu

---

### Post by shareme on 2008-06-17
According to shut down message is booting into 2.6.24.18 kernel not  the new 2.6.24.19 one

---

### Post by shareme on 2008-06-17
Okay I did a temp fix by using esc at boot up and choosing kernel 2.6.24.18 instead of kernel 2.6.24.19..

Is there any more permanent fix?? For right now my fix works and no problems..

It just will not take 2.6.24.19..

---

### Post by nom1979 on 2008-06-26
As far as i know, same problem has happened today on several machines from friends running both ubuntu 7.10 and 8.04 and on my desktop pc. All of them have updated through "update Manager" this packages:

linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
linux-headers-2.6.24-19-image

Among too many other updates, related to Security Updates(hardy-security) and Recommended Updates(hardy-updates)... nothing else on Update Manager config.
It seems that kernel package is wrongly configured/broken. As all this machines have different hard-soft configuration, but the problem is the same for all of them as far as i know... It starts loading ubuntu and then it prompts on the RAM disk with busybox. That is a kernel loading issue. It can't find image or something else... i have to digg on my desktop pc to know what's happening! 
I suggest by now to press esc key on start up (on grub loading) and enter in the kernel before 2.6.24-19 (the line after 2.6.24-19(recovery mode) i guess:P). It will start your computer as it used to do, until this kernel update. Then edit menu.lst and remove or comment(as you want...) the entry referring this kernel update... this will fix grub startup. But won't fix this kernel update... Sorry, i don't know why! But i'll try to find which is the error... googleing now...


I do apologize about my english.

---

### Post by nom1979 on 2008-06-26
I guess it's 2.6.24-19-34 update...

---

### Post by Ameneon on 2008-06-27
Add me to the tally of the broken .19 updates. The previous .19 worked just fine while this latest one drops out to commandline again prior to log in. One thing I noted during the upgrade process was that earlier upgrades have always asked me whether to update the menu.lst file, while this one didn't. I did look at the details during the update and the details there claimed that the menu.lst file was being updated. I've double checked the file names and other settings between the directory listing and menu.lst but all seems just fine and right, so I'm guessing it's something in the kernel itself that's borked. Thank goodness I keep the old kernels :P

---

