---
title: "Testing needed: new chroot procedure"
date: 2009-11-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-11-14
**[COLOR="Red"]I'm using this to document changes to known procedures. Stay tuned for the results![/COLOR]**

From the release notes:

> Upstart jobs cannot be run in a chroot

Upstart jobs cannot be started in a chroot because upstart acts as a service supervisor, and processes within the chroot are unable to communicate with the upstart running outside of the chroot (430224). This will cause some packages that have been converted to use upstart jobs instead of init scripts to fail to upgrade within a chroot. Users are advised to configure their chroots with /sbin/initctl pointing to /bin/true, with the following commands run within the chroot:

dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

So I've run into trouble twice and actually helped totally hose already broken systems.

Modified version of mount and chroot (using my sda11/Mint8 as an example):

```
sudo mount /dev/sda11 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

```
sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).

When done:

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

Partial output (more to follow):

> lance@lance-desktop:~$ sudo mount /dev/sda11 /mnt
[sudo] password for lance: 
lance@lance-desktop:~$ sudo mount --bind /dev /mnt/dev
lance@lance-desktop:~$ sudo mount --bind /proc /mnt/proc
lance@lance-desktop:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
lance@lance-desktop:~$ sudo chroot /mnt
lance-desktop / # dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
lance-desktop / # ln -s /bin/true /sbin/initctl
lance-desktop / # apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
lance-desktop / # 


**[COLOR="Red"]I'm posting this partial output now so if this crashes things we can see what went haywire![/COLOR]**

---

### Post by kansasnoob on 2009-11-14
Well, update and dist-upgrade ran OK (I chose no on upgrade because I don't want to upgrade grub-common):

> lance-desktop / # apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release.gpg                           
Get:1 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena Release.gpg [198B]                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Translation-en_US                
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Translation-en_US            
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Translation-en_US              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                           
Get:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena Release [7,227B]                    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Translation-en_US      
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Packages                       
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Packages                         
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release                               
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Packages
Ign [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Packages
Get:3 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/main Packages [4,579B]  
Get:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/upstream Packages [6,790B]     
Get:5 [http://packages.linuxmint.com](http://packages.linuxmint.com) helena/import Packages [4,463B]       
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages                         
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Packages
Fetched 23.3kB in 3s (6,358B/s)
Reading package lists... Done
lance-desktop / # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  grub-common mintinstall pidgin-facebookchat
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 452kB/1,446kB of archives.
After this operation, 164kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


Trying to use gedit for sources.list didn't:

> lance-desktop / # gedit etc/apt/sources.list
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-rfmz01L5xo: Connection refused)


And that message kept repeating until I hit the tab key, then gedit popped up with the sources.list.

Now I'll try more.

**[COLOR="Red"]Still just testing![/COLOR]**

---

### Post by kansasnoob on 2009-11-14
Well, nano worked fine:

[ATTACH]136230[/ATTACH]

I'm just wondering if this is something we should incorporate into all future chroot instructions?????

Testing and feedback appreciated.

If someone can think of a **reasonable** test scenario I'll be the guinea pig.

---

### Post by kansasnoob on 2009-11-14
Unmounting worked just fine also!

This really is something we all need to consider.

Old dogs can learn new tricks :)

---

### Post by ranch hand on 2009-11-14
This is the first i have heard of this problem.  With upstart being the coming thing, this is a definite concern.  Particularly if it screws up.

Ah, silly me, it will not screw up.

I will have to study on this some more.  I am just getting comfortable with chroot and anything that changes it I better "study on".

It looks like you have a handle on it though.

---

### Post by VMC on 2009-11-14
Just in case someone wants to read the links you posted from. Here are the links in question:

[URL="http://www.ubuntu.com/getubuntu/releasenotes/910#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot"]Upstart jobs cannot be run in a chroot
[/URL]
[URL="https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224"]Launchpad bug (430224)
[/URL]

Thanks for pointing this out.

---

### Post by kansasnoob on 2009-11-14
Well , I thought it was important enough to use up some real estate here at the forums.

As I said I ill advised two people looking for solutions and in one case it resulted in the OP having to backup and reinstall.

So IMHO this needs to be a lesson learned for all.

I do think it needs to be tested in more scenarios however.

---

### Post by ranch hand on 2009-11-14
Well, I wouldn't really know what should be upgraded but wasn't.

However, i update in the morning, starting with my "other" 10.04, I'll log in here and chroot update that bugger.  I can then go over and see if it needs more.

---

### Post by ranch hand on 2009-11-15
Ok, so I tried this in updating Lounge Lizard;
> 
larry@larry-desktop:~$ sudo mount /dev/sda7 /mnt
[sudo] password for larry: 
larry@larry-desktop:~$ sudo mount --bind /dev /mnt/dev
larry@larry-desktop:~$ sudo mount --bind /proc /mnt/proc
larry@larry-desktop:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
larry@larry-desktop:~$ sudo chroot /mnt
root@larry-desktop:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@larry-desktop:/# ln -s /bin/true /sbin/initctl

With 2 small updates, not real exciting but it did work.  There  seems to be a missing command though because of this;
> 
Can not write log, openpty() failed (/dev/pts not mounted?)

from the upgrade.

I usually use a cheat sheet to chroot and do not have it on this drive (dumb- note to self - GET IT) and I know that the /pts does get mounted.

---

### Post by VMC on 2009-11-15
> **ranch hand said:**
> There  seems to be a missing command though because of this;

Can not write log, openpty() failed (/dev/pts not mounted?)


You needed this:
mount --bind /dev/pts /mnt/disk/dev/pts

---

### Post by ranch hand on 2009-11-15
Thank you so much, I was sure that was it.

---

### Post by slakkie on 2009-11-16
I have one question, when you boot into the chrooted OS, I assume the pkg-divert is still active and so is the symlink to /bin/true. 

I suppose you need to undo this when you are done with the chroot:

```

rm /sbin/initctl 
dpkg-divert --local --remove /sbin/initctl

```

???

---

### Post by philinux on 2009-11-16
> **kansasnoob said:**
> Unmounting worked just fine also!

This really is something we all need to consider.

Old dogs can learn new tricks :)

Thanks for the thread. I'd not seen this anywhere else. I'll be changing my script to suit. cheers.

---

### Post by kansasnoob on 2009-11-16
> **slakkie said:**
> I have one question, when you boot into the chrooted OS, I assume the pkg-divert is still active and so is the symlink to /bin/true. 

I suppose you need to undo this when you are done with the chroot:

```

rm /sbin/initctl 
dpkg-divert --local --remove /sbin/initctl

```

???

I don't know.

That's why I tossed this out for discussion.

Basically none of us here in testing get too freaked out if things implode on us, so I figured this would be a good place to bring it up.

I posed this question at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224)

Kudos to VMC for putting up the link.

---

### Post by philinux on 2009-11-16
> **slakkie said:**
> I have one question, when you boot into the chrooted OS, I assume the pkg-divert is still active and so is the symlink to /bin/true. 

I suppose you need to undo this when you are done with the chroot:

```

rm /sbin/initctl 
dpkg-divert --local --remove /sbin/initctl

```

???

I have a unmount script for when I'm done chrooting but to be honest I forget to run it as rebooting unmounts it all.

---

### Post by VMC on 2009-11-16
> **philinux said:**
> I have a unmount script for when I'm done chrooting but to be honest I forget to run it as rebooting unmounts it all.

Exactly. I have a chroot.sh & unchoot.sh that reverses the process. 

slakkie brings up a good point. I know to reverse what I have mounted, but this new added procedure of " dpkg-divert", does it also need to be backed out.

---

### Post by kansasnoob on 2009-11-16
> **VMC said:**
> You needed this:
mount --bind /dev/pts /mnt/disk/dev/pts

Thanks I obviously missed that also.

Would this potentially be right then:

&#65279;
sudo mount /dev/sdaX /mnt

sudo mount --bind /dev /mnt/dev

sudo mount --bind /proc /mnt/proc

sudo mount --bind /dev/pts /mnt/disk/dev/pts

sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

sudo chroot /mnt

&#65279;dpkg-divert --local --rename --add /sbin/initctl

&#65279;ln -s /bin/true /sbin/initctl

RUN NEEDED COMMANDS

rm /sbin/initctl 

dpkg-divert --local --remove /sbin/initctl

exit

**sudo umount /mnt/disk/dev/pts**

sudo umount /mnt/dev

sudo umount /mnt/proc

sudo umount /mnt

sudo reboot

---

### Post by slakkie on 2009-11-16
> **VMC said:**
> Exactly. I have a chroot.sh & unchoot.sh that reverses the process. 

slakkie brings up a good point. I know to reverse what I have mounted, but this new added procedure of " dpkg-divert", does it also need to be backed out.

I tweaked my chroot script for a second, in theory this should work (haven't tested it). If someone wants to test it, if you break it you buy it btw :)

[http://pb.opperschaap.net/93](http://pb.opperschaap.net/93)

---

### Post by sisco311 on 2009-11-16
you also need to mount /sys
```
mount -t sysfs none /mnt/sys
```

if one uses a static resolv.conf, it's better to bind it, rather than overwrite:
```
mount --bind /etc/resolv.conf /mnt/etc/resolv.conf
```

---

### Post by kansasnoob on 2009-11-16
> **VMC said:**
> You needed this:
mount --bind /dev/pts /mnt/disk/dev/pts

I'm being particularly dense this morning, but here we go:

> lance@lance-desktop ~ $ sudo mount /dev/sda3 /mnt
[sudo] password for lance: 
lance@lance-desktop ~ $ sudo mount --bind /dev /mnt/dev
lance@lance-desktop ~ $ sudo mount --bind /proc /mnt/proc
lance@lance-desktop ~ $ sudo mount --bind /dev/pts /mnt/disk/dev/pts
mount: mount point /mnt/disk/dev/pts does not exist
lance@lance-desktop ~ $ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
lance@lance-desktop ~ $ sudo chroot /mnt
root@lance-desktop:/# mount --bind /dev/pts /mnt/disk/dev/pts
mount: mount point /mnt/disk/dev/pts does not exist


Then I run update & upgrade:

> ................................The following packages will be upgraded:
  lftp
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 432kB of archives.
After this operation, 147kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main lftp 4.0.2-1 [432kB]
Fetched 432kB in 2s (180kB/s)
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 201338 files and directories currently installed.)
Preparing to replace lftp 3.7.15-1ubuntu2 (using .../archives/lftp_4.0.2-1_i386.deb) ...
Unpacking replacement lftp ...
Processing triggers for man-db ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up lftp (4.0.2-1) ...


Then:

> root@lance-desktop:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@lance-desktop:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@lance-desktop:/# mount --bind /dev/pts /mnt/disk/dev/pts
mount: mount point /mnt/disk/dev/pts does not exist


I clearly need more coffee and I'm unclear when and where to use "mount --bind /dev/pts /mnt/disk/dev/pts".

Sorry for being so dense:)

BTW I got the following reply at Launchpad:

> If you're running a chroot or some other environment where you never
want upstart jobs to run, you shouldn't un-divert the initctl.

---

### Post by ranch hand on 2009-11-16
Well, just in time to update nextdoor too.

Makes you wonder if we just do this for the FUN.

---

### Post by ranch hand on 2009-11-16
Try replacing "disk" with "sdaX".

EDIT;
Not working.

I have;
  	 	 	 	 	 	  sudo mount -o bind /dev/pts /mnt/Zenix-root/dev/pts


That I used yesterday to get to this drive and it worked fine.  Changing it to "Lounge-root" fails too work.

---

### Post by kansasnoob on 2009-11-16
> **ranch hand said:**
> Well, just in time to update nextdoor too.

Makes you wonder if we just do this for the FUN.

I do actually do this for fun! That and it's great to keep learning.

I also get antsy if I go more than a week without seriously breaking an OS:p

---

### Post by philinux on 2009-11-16
Here's my current script. Not changed it yet.

```
#!/bin/sh

##sudo mkdir /mnt/lucid
sudo mount /dev/sdb1 /mnt/lucid/
sudo mount -o bind /proc /mnt/lucid/proc
sudo mount -o bind /dev /mnt/lucid/dev
sudo mount -o bind /dev/pts /mnt/lucid/dev/pts
sudo mount -o bind /sys /mnt/lucid/sys
sudo cp /etc/resolv.conf /mnt/lucid/etc/resolve.conf
sudo chroot /mnt/lucid /bin/bash

fi
```

---

### Post by sisco311 on 2009-11-16
here is mine:
```
#!/bin/bash
sudo -u sisco -i xhost +

if [ ! -e /mnt/lucid ]; then
  mkdir /mnt/lucid
fi

if [ ! "$(mount | grep /mnt/lucid)" ]; then
  mount /dev/sda2 /mnt/lucid 
else
  echo "lucid already  mounted"
fi

if [ ! "$(mount | grep /mnt/lucid/dev)" ]; then 
  mount --bind /dev/ /mnt/lucid/dev 
else
  echo "lucid/dev already mounted"
fi

if [ ! "$(mount | grep /mnt/lucid/dev/pts)" ]; then 
  mount --bind /dev/pts /mnt/lucid/dev/pts
else
  echo "lucid/dev/pts already mounted"
fi

if [ ! "$(mount | grep /mnt/lucid/proc)" ]; then
  mount -t proc none /mnt/lucid/proc
else
  echo "lucid/proc already mounted"
fi

if [ ! "$(mount | grep /mnt/lucid/sys)" ]; then
  mount -t sysfs none /mnt/lucid/sys
else
  echo "lucid/sys already mounted" 	
fi

if [ ! "$(mount | grep /etc/resolv.conf)" ]; then
  mount -o bind /etc/resolv.conf /mnt/lucid/etc/resolv.conf
else
  echo "lucid/etc/resolve.conf already mounted"
fi

chroot /mnt/lucid

```

---

### Post by kansasnoob on 2009-11-16
Well it appears that for me it works if I just do:

> sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt

But now for some reason when I run the new stuff I get this:

> root@lance-desktop:/# &#65279;dpkg-divert --local --rename --add /sbin/initctl
dpkg-divert: command not found
root@lance-desktop:/# &#65279;ln -s /bin/true /sbin/initctl
ln: command not found


I had previously tried the suggested:

> rm /sbin/initctl 

dpkg-divert --local --remove /sbin/initctl

But I don't see why it would refuse to recognize "ln" or any dpkg command.

That was my Lucid so maybe I should boot it and see if I borked anything.

---

### Post by kansasnoob on 2009-11-16
Nothing appears to be borked, at least it's not obvious, but can someone tell this blind old man what the difference is here:

> lance@lance-desktop:~$ sudo mount /dev/sda11 /mnt
[sudo] password for lance: 
lance@lance-desktop:~$ sudo mount --bind /dev /mnt/dev
lance@lance-desktop:~$ sudo mount --bind /proc /mnt/proc
lance@lance-desktop:~$ sudo mount --bind /dev/pts /mnt/dev/pts
lance@lance-desktop:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
lance@lance-desktop:~$ sudo chroot /mnt
lance-desktop / # cat /etc/issue
Linux Mint 8 Helena - Main Edition \n \l
lance-desktop / # &#65279;dpkg-divert --local --rename --add /sbin/initctl
dpkg-divert: command not found
lance-desktop / # dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
lance-desktop / # &#65279;ln -s /bin/true /sbin/initctl
ln: command not found
lance-desktop / # ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
lance-desktop / # 


I don't see the difference between the two dpkg and ln commands. One is copied from my original post here, the other from my unfinished script that I'm in the process of building/testing in gedit.

I can't see any difference.

Odd things sometimes ;)

---

### Post by slakkie on 2009-11-16
I've tested my chroot script, and it seems to work. I haven't upgraded any package yet, but the simple mechanics work. 

Do the dpkg-divert action and undo it again. Made a small posting about it on my blog.

---

### Post by ranch hand on 2009-11-16
I am appearently not ready to use a script for this.  All I can get them to do is instantly crash/close terminal.

I think I will stick with just doing it the "hard way".

---

### Post by slakkie on 2009-11-16
> **ranch hand said:**
> I am appearently not ready to use a script for this.  All I can get them to do is instantly crash/close terminal.

I think I will stick with just doing it the "hard way".

Or you could copy the scripts and try/change them to your own liking.

---

### Post by sisco311 on 2009-11-16
The only thing that's not working properly in my chroot environment is update-grub. It detects the Lucid installation but not my ArchLinux. :(

------------------------------------------------------------------

I don't like to be logged in as root, so I su to my admin account:
```
sudo chroot /mnt/lucid su ubuntu-username -
```

Before chrooting I run:
```
xhost +SI:localuser:ubuntu-username
```
to allow my user to connect to the x server. (Only needed if you want to run GUI apps)

In ArchLinux the gid of the video and audio group is not the same as the gid in Ubuntu.

So I've created a two new groups audio0 (gid 92) and video0 (gid 91) and added my user to the groups.

---

### Post by ranch hand on 2009-11-16
> **slakkie said:**
> Or you could copy the scripts and try/change them to your own liking.
That is what I am doing.  All I am getting is screwing things up.

I have 2 others, besides yours.  They are simpler but all I can do is get my terminal to crash.  I realize that they need to match my box.

I can modify the individual commands in either of them and use them manually quite well.

Beats me.  I have wasted about 3 days, so far, screwing with this and decided it is just quicker to forget it for now.

I'll give it another whack in the next testing cycle.  I may have learned more by then.

---

