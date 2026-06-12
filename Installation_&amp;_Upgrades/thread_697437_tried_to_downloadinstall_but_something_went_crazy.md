---
title: "tried to download/install but something went crazy"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Ck.asdf on 2008-02-15
I think ... something happened that wasn't supposed to.  I was attempting to install an xbox controller on my computer, and a tutorial suggested I grab something called "usbmgr." Well ... it started UNinstalling packages.
I killed it after a while with ctrl + C, knowing something was going wrong.


```
ck@ck-buntu:~/downloads/xpad$ sudo apt-get install usbmgr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-system-data1.0-cil libmono1.0-cil libmysqlclient15off
  libtaglib2.0-cil libmono-cairo2.0-cil libavahi1.0-cil
  libmono-system-web1.0-cil ruby1.8 ruby boo libmono-data-tds1.0-cil
  libmono-security1.0-cil libifp4 libpq5 libruby1.8 mysql-common libnjb5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  amarok amarok-xine apparmor apparmor-utils audacious-plugins-extra banshee
  banshee-daap brltty brltty-x11 console-setup dkms f-spot foomatic-db-hpijs
  gnome-mount gnome-power-manager gnome-session gnome-volume-manager grub hal
  hal-device-manager hpijs hplip hplip-gui hwdb-client-common
  hwdb-client-gnome initramfs-tools ipod libgphoto2-2 libmtp6 libsane
  linux-image-2.6.22-14-rt linux-image-rt
  linux-restricted-modules-2.6.22-14-rt linux-restricted-modules-rt linux-rt
  linux-ubuntu-modules-2.6.22-14-rt pcmciautils sound-juicer ubuntu-minimal
  ubuntustudio-audio ubuntustudio-desktop ubuntustudio-graphics udev
  update-notifier usplash usplash-theme-ubuntustudio volumeid xsane
The following NEW packages will be installed:
  usbmgr
0 upgraded, 1 newly installed, 48 to remove and 0 not upgraded.
Need to get 53.3kB of archives.
After unpacking 255MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/universe usbmgr 1.0.0-6 [53.3kB]
Fetched 53.3kB in 3s (15.2kB/s)
(Reading database ... 136217 files and directories currently installed.)
Removing apparmor-utils ...
Removing apparmor ...
Unloading AppArmor profiles : done.
update-initramfs: deferring update (trigger activated)
Removing ubuntustudio-audio ...
Removing audacious-plugins-extra ...
Removing banshee-daap ...
Removing banshee ...
Removing brltty-x11 ...
Removing brltty ...
Removing ubuntu-minimal ...
Removing console-setup ...
Removing dkms ...
0
Removing ubuntustudio-graphics ...
Removing f-spot ...
Removing ubuntustudio-desktop ...
Removing foomatic-db-hpijs ...
Removing ipod ...
Removing gnome-volume-manager ...
Removing gnome-mount ...
Removing gnome-session ...
Removing gnome-power-manager ...
Removing grub ...
Removing sound-juicer ...
Removing hal-device-manager ...
Removing hwdb-client-gnome ...
Removing hwdb-client-common ...
Removing update-notifier ...
Removing hal ...
 * Stopping Hardware abstraction layer hald                              [ OK ] 
Removing hpijs ...
Removing hplip-gui ...
Removing hplip ...
Removing linux-rt ...
Removing linux-restricted-modules-rt ...
Removing linux-restricted-modules-2.6.22-14-rt ...
Removing linux-image-rt ...
Removing linux-ubuntu-modules-2.6.22-14-rt ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
find: /lib/firmware/2.6.22-14-rt: No such file or directory
find: /lib/firmware/2.6.22-14-rt: No such file or directory
find: /lib/firmware/2.6.22-14-rt: No such file or directory
find: /lib/firmware/2.6.22-14-rt: No such file or directory
find: /lib/firmware/2.6.22-14-rt: No such file or directory
find: /lib/firmware/2.6.22-14-rt: No such file or directory
dpkg: error processing linux-ubuntu-modules-2.6.22-14-rt (--remove):
 subprocess post-removal script killed by signal (Interrupt)
Removing linux-image-2.6.22-14-rt ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Could not find postrm hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Removing usplash-theme-ubuntustudio ...
update-initramfs: deferring update (trigger activated)
Removing usplash ...
update-initramfs: deferring update (trigger activated)
Removing pcmciautils ...
Removing xsane ...
E: Sub-process /usr/bin/dpkg exited unexpectedly

```

What atrocity has been committed, and is there any easy way I can reverse this mass uninstallation?

---

### Post by Borbus on 2008-02-15
Right, ok, this happened to me once, the Debian package manager thing decided to do it.

Anyway, don't panick, it is completely recoverable, hold on while I make a list of packages for you with vim.

---

### Post by Borbus on 2008-02-15
Ok, I didn't really have to do much becaue apt listed the packages it was going to remove at the top. When I did it I had to find the list of packages in dpkg.log, I made a quick macro with vim to isolate the names of the packages.

Anyway, first you should do:

sudo apt-get update

Now apt will probably tell you that some packages were broken and what you should do. Follow this instruction.

Now do:

sudo apt-get install amarok amarok-xine apparmor apparmor-utils audacious-plugins-extra banshee banshee-daap brltty brltty-x11 console-setup dkms f-spot foomatic-db-hpijs gnome-mount gnome-power-manager gnome-session gnome-volume-manager grub hal hal-device-manager hpijs hplip hplip-gui hwdb-client-common hwdb-client-gnome initramfs-tools ipod libgphoto2-2 libmtp6 libsane linux-image-2.6.22-14-rt linux-image-rt linux-restricted-modules-2.6.22-14-rt linux-restricted-modules-rt linux-rt linux-ubuntu-modules-2.6.22-14-rt pcmciautils sound-juicer ubuntu-minimal ubuntustudio-audio ubuntustudio-desktop ubuntustudio-graphics udev update-notifier usplash usplash-theme-ubuntustudio volumeid xsane

And that will install all of the packages that were deleted again. It should be just like it was before now.

---

### Post by Ck.asdf on 2008-02-15
> **Borbus said:**
> Right, ok, this happened to me once, the Debian package manager thing decided to do it.

Anyway, don't panick, it is completely recoverable, hold on while I make a list of packages for you with vim.


Why did it decide I didn't need all those packages? And the next time I try to install it, or something else, how do I make it not uninstall things that I want to stay?

just a moment ago, I tried
apt-get install joystick

it told me it wanted to remove one package, and that x amount of memory would be freed.
so I told it no, and it wasn't deleted, and joystick wasn't downloaded.


blah, I don't understand.  but I'll read what you have to say next, when you say it. thanks for the quick response. :)

---

### Post by Ck.asdf on 2008-02-15
you suggested I do an update ... amusing part is, at the end of it, it said "suggest update"
log ...

```
ck@ck-buntu:~$ sudo apt-get update
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/multiverse Translation-en_US                           
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/restricted Translation-en_US                           
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/universe Translation-en_US                             
Get:1 http://www.getautomatix.com gutsy Release.gpg [189B]                                                                            
Ign http://www.getautomatix.com gutsy/main Translation-en_US                                                                          
Hit http://www.getautomatix.com gutsy Release                                                                                         
Get:2 http://download.tuxfamily.org gutsy Release.gpg [189B]                                                                          
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                                                                           
Ign http://archive.canonical.com gutsy/partner Translation-en_US                                                                      
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]                                                                    
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US                                                                  
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US                                                            
Get:5 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]                                                                    
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US                                                                  
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US                                                            
Hit http://www.getautomatix.com gutsy/main Packages                                                                                   
Get:6 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                                                                           
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                                                    
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US                                              
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US                                 
Hit http://archive.canonical.com gutsy Release                                                                   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US                                       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US                 
Hit http://security.ubuntu.com gutsy-security Release                                                            
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US                                         
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US                 
Hit http://archive.ubuntu.com gutsy-backports Release                                      
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US                                               
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US                        
Get:7 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]                        
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US                                            
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US                                      
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US                  
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US                
Get:8 http://download.tuxfamily.org gutsy Release [10.9kB]                                                       
Hit http://archive.canonical.com gutsy/partner Packages                                                                
Hit http://security.ubuntu.com gutsy-security/main Packages                                                            
Hit http://archive.ubuntu.com gutsy-backports/main Packages                                      
Hit http://us.archive.ubuntu.com gutsy Release                             
Hit http://us.archive.ubuntu.com gutsy-updates Release                                                                
Hit http://security.ubuntu.com gutsy-security/restricted Packages                                                     
Hit http://security.ubuntu.com gutsy-security/main Sources           
Hit http://security.ubuntu.com gutsy-security/restricted Sources     
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages    
Hit http://archive.ubuntu.com gutsy-backports/universe Packages                            
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages                          
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://us.archive.ubuntu.com gutsy/restricted Packages           
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Get:9 http://download.tuxfamily.org gutsy/avant-window-navigator Packages [2840B]
Hit http://security.ubuntu.com gutsy-security/universe Packages            
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://us.archive.ubuntu.com gutsy/universe Packages             
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Get:10 http://download.tuxfamily.org gutsy/avant-window-navigator Sources [1351B]
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 15.3kB in 1s (14.4kB/s)
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/main Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/multiverse Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/universe Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_universe_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by Borbus on 2008-02-15
> **Ck.asdf said:**
> Why did it decide I didn't need all those packages? And the next time I try to install it, or something else, how do I make it not uninstall things that I want to stay?

just a moment ago, I tried
apt-get install joystick

it told me it wanted to remove one package, and that x amount of memory would be freed.
so I told it no, and it wasn't deleted, and joystick wasn't downloaded.


blah, I don't understand.  but I'll read what you have to say next, when you say it. thanks for the quick response. :)

I'm not sure, maybe a misconfigured package. When it happened to me I was using the Debian installation tool (can't remember the name of it now) and it decided to remove EVERY package on my system. It removed 175 packages before I decided to stop it. I could literally see the gnome desktop fall apart bit by bit. After I got a list of the packages from dpkg.log with vim I installed all 175 again and watched Gnome reassemble bit by bit :) I'm still using the same installation now. Just shows you the power of apt.

---

### Post by Borbus on 2008-02-15
> **Ck.asdf said:**
> you suggested I do an update ... amusing part is, at the end of it, it said "suggest update"
log ...

```
ck@ck-buntu:~$ sudo apt-get update
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/main Translation-en_US
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/multiverse Translation-en_US                           
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/restricted Translation-en_US                           
Ign cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/universe Translation-en_US                             
Get:1 http://www.getautomatix.com gutsy Release.gpg [189B]                                                                            
Ign http://www.getautomatix.com gutsy/main Translation-en_US                                                                          
Hit http://www.getautomatix.com gutsy Release                                                                                         
Get:2 http://download.tuxfamily.org gutsy Release.gpg [189B]                                                                          
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]                                                                           
Ign http://archive.canonical.com gutsy/partner Translation-en_US                                                                      
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]                                                                    
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US                                                                  
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US                                                            
Get:5 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]                                                                    
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_US                                                                  
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US                                                            
Hit http://www.getautomatix.com gutsy/main Packages                                                                                   
Get:6 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                                                                           
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                                                    
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US                                              
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US                                 
Hit http://archive.canonical.com gutsy Release                                                                   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US                                       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US                 
Hit http://security.ubuntu.com gutsy-security Release                                                            
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_US                                         
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US                 
Hit http://archive.ubuntu.com gutsy-backports Release                                      
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US                                               
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US                        
Get:7 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]                        
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US                                            
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US                                      
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US                  
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US                
Get:8 http://download.tuxfamily.org gutsy Release [10.9kB]                                                       
Hit http://archive.canonical.com gutsy/partner Packages                                                                
Hit http://security.ubuntu.com gutsy-security/main Packages                                                            
Hit http://archive.ubuntu.com gutsy-backports/main Packages                                      
Hit http://us.archive.ubuntu.com gutsy Release                             
Hit http://us.archive.ubuntu.com gutsy-updates Release                                                                
Hit http://security.ubuntu.com gutsy-security/restricted Packages                                                     
Hit http://security.ubuntu.com gutsy-security/main Sources           
Hit http://security.ubuntu.com gutsy-security/restricted Sources     
Hit http://archive.ubuntu.com gutsy-backports/restricted Packages    
Hit http://archive.ubuntu.com gutsy-backports/universe Packages                            
Hit http://archive.ubuntu.com gutsy-backports/multiverse Packages                          
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://us.archive.ubuntu.com gutsy/restricted Packages           
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Get:9 http://download.tuxfamily.org gutsy/avant-window-navigator Packages [2840B]
Hit http://security.ubuntu.com gutsy-security/universe Packages            
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://us.archive.ubuntu.com gutsy/universe Packages             
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Get:10 http://download.tuxfamily.org gutsy/avant-window-navigator Sources [1351B]
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 15.3kB in 1s (14.4kB/s)
Reading package lists... Done
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/main Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_main_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/multiverse Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release amd64 (20071015) gutsy/universe Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20amd64%20(20071015)_dists_gutsy_universe_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

```

You should remove the CD images from your /etc/apt/sources.list file.

I thought apt would complain about broken packages with an update, maybe it doesn't. You will probably find that it will when you try to install.

---

