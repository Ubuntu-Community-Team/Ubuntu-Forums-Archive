---
title: "format and mount sata"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by shickidyshade on 2007-01-06
hey guys 

I'm trying to mount a second hard drive in on my new computer Its a seagate and its connected via sata wire into the hd

---

### Post by taurus on 2007-01-06
What filesystem does it have?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by shickidyshade on 2007-01-06
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

thanks

---

### Post by taurus on 2007-01-06
So you want to format /dev/sdb!  What filesystem do you plan to use?  You can use gparted from Ubuntu to format it either fat32/vfat, ntfs, or even ext3 if you wish...

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
Then, it will be in System -> Administration.

---

### Post by shickidyshade on 2007-01-06
oops missed something at the bottom 

shade@shade-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS


thanks

---

### Post by shickidyshade on 2007-01-06
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by shickidyshade on 2007-01-06
ive had a lot of issues with the sun-java5-bin package

any ideas

---

### Post by taurus on 2007-01-06
Let's try to mount the /dev/sdb1 first, shall we...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line to it.

```
/dev/sdb1   /media/sdb1   ntfs   ntfs nls=utf8,umask=0222   0   0
```
Save it.  Then create a mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

---

### Post by shickidyshade on 2007-01-06
what about the sun-java5-bin

---

### Post by taurus on 2007-01-06
What's the output if you run this command from a terminal?

```
sudo aptitude update
```

p.s.  I take it the mounting process is good then!

---

### Post by shickidyshade on 2007-01-06
havent tried to mount because i haven't formatted it yet the update went fine but the 
sudo aptitude install gparted
 resulted in 
</code>

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  skype 
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  libcairomm-1.0-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a 
The following packages have been kept back:
  avahi-daemon capplets-data dbus dbus-1-utils evince firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-control-center 
  gnome-games gnome-games-data gnome-system-tools gnupg info 
  language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libdbus-1-3 libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnspr4 libnss3 libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  sun-java5-bin tar ttf-opensymbol vino w3m x11-common xbase-clients xorg 
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all xutils 
The following NEW packages will be installed:
  gparted libcairomm-1.0-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a 
0 packages upgraded, 4 newly installed, 0 to remove and 91 not upgraded.
Need to get 0B of archives. After unpacking 6201kB will be used.
The following packages have unmet dependencies:
  skype: Depends: libqt3-mt but it is not installable or
                  libqt3c102-mt (>= 3:3.3.3.2) which is a virtual package.
Resolving dependencies...
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
The following actions will resolve these dependencies:

Install the following packages:
libqt3-mt [3:3.3.6-3ubuntu3 (edgy)]

Score is -19

Accept this solution? [Y/n/q/?] 

</code>
I have no idea what to say to that

---

### Post by taurus on 2007-01-06
Can you post your /etc/apt/sources.list here?  I assume you installed Edgy from fresh, not upgrading from Dapper to Edgy, right?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by shickidyshade on 2007-01-06
shade@shade-desktop:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END


and yes sir i installed edgy from the start how did u get the code box i know its html but can remeber the code

---

### Post by taurus on 2007-01-06
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.  You can use one of those icons on top of your editing window...

---

### Post by shickidyshade on 2007-01-06
This is what happens

> shade@shade-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                      
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US   
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 9B in 1s (7B/s)
Reading package lists... Done
shade@shade-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have unmet dependencies:
  skype: Depends: libqt3-mt but it is not installable or
                  libqt3c102-mt (>= 3:3.3.3.2) which is a virtual package.
shade@shade-desktop:~$ 


---

### Post by taurus on 2007-01-07
What happens if you install that package first?

```
sudo aptitude install libqt3-mt
sudo aptitude upgrade
```

---

### Post by shickidyshade on 2007-01-07
shade@shade-desktop:~$ sudo aptitude install libqt3-mt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following packages have been kept back:
  avahi-daemon capplets-data dbus dbus-1-utils evince firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-control-center 
  gnome-games gnome-games-data gnome-system-tools gnupg info 
  language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libdbus-1-3 libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnspr4 libnss3 libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  sun-java5-bin tar ttf-opensymbol vino w3m x11-common xbase-clients xorg 
  xserver-xorg xserver-xorg-input-all xserver-xorg-video-all xutils 
The following NEW packages will be installed:
  libqt3-mt 
0 packages upgraded, 1 newly installed, 0 to remove and 91 not upgraded.
Need to get 0B of archives. After unpacking 8921kB will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by taurus on 2007-01-07
Did you try to install Sun java 5.0 or something?  See if you can run this command

```
sudo aptitude remove sun-java5-bin
```

---

### Post by shickidyshade on 2007-01-07
> shade@shade-desktop:~$ sudo aptitude remove sun-java5-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  skype 
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following packages have been kept back:
  avahi-daemon capplets-data dbus dbus-1-utils evince firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-control-center 
  gnome-games gnome-games-data gnome-system-tools gnupg info 
  language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libdbus-1-3 libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnspr4 libnss3 libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  tar ttf-opensymbol vino w3m x11-common xbase-clients xorg xserver-xorg 
  xserver-xorg-input-all xserver-xorg-video-all xutils 
The following packages will be REMOVED:
  sun-java5-bin 
0 packages upgraded, 0 newly installed, 1 to remove and 90 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  skype: Depends: libqt3-mt but it is not installable or
                  libqt3c102-mt (>= 3:3.3.3.2) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libqt3-mt [3:3.3.6-3ubuntu3 (edgy)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following packages have been automatically kept back:
  linux-image-2.6.17-10-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  libqt3-mt 
The following packages have been kept back:
  avahi-daemon capplets-data dbus dbus-1-utils evince firefox 
  firefox-gnome-support gdm gimp gimp-data gimp-python gnome-control-center 
  gnome-games gnome-games-data gnome-system-tools gnupg info 
  language-pack-en language-pack-gnome-en libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 
  libdbus-1-3 libgimp2.0 libgnome-window-settings1 libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common 
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libmagick9 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnspr4 libnss3 libpng12-0 
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic mono-common 
  mono-gac mono-jit mono-runtime openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common 
  openoffice.org-math openoffice.org-style-default 
  openoffice.org-style-industrial openoffice.org-writer python-uno screen 
  tar ttf-opensymbol vino w3m x11-common xbase-clients xorg xserver-xorg 
  xserver-xorg-input-all xserver-xorg-video-all xutils 
The following NEW packages will be installed:
  libqt3-mt 
The following packages will be REMOVED:
  sun-java5-bin 
0 packages upgraded, 1 newly installed, 1 to remove and 90 not upgraded.
Need to get 3138kB of archives. After unpacking 8921kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libqt3-mt 3:3.3.6-3ubuntu3 [3138kB]
Fetched 3138kB in 25s (122kB/s)                                                 
dpkg: error processing sun-java5-bin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 sun-java5-bin
Aborted (core dumped)
shade@shade-desktop:~$ 


This it displayed looks kinda funny i was using automatix2 to install some programs and it froze in the middle of one of them so that might be what the problem is

---

### Post by taurus on 2007-01-07
Why don't you open Automatix2 again, Applications -> System Tool -> Automatix, and see if you can delete that package or reinstall that package again!!!  It looks to me like the Sun java 5.0 is the problem...

---

### Post by shickidyshade on 2007-01-07
i just ran the synaptic manager duhh!!!!!!!   lol and it fixed two or three broken packages and is now updating im gonna let it run and then try to install gparted again after

---

### Post by shickidyshade on 2007-01-07
> **taurus said:**
> So you want to format /dev/sdb!  What filesystem do you plan to use?  You can use gparted from Ubuntu to format it either fat32/vfat, ntfs, or even ext3 if you wish...

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
Then, it will be in System -> Administration.

Ok so i went back to this step and this is what the temrinal replied
> shade@shade-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                      
Hit [http://dl.google.com](http://dl.google.com) stable Release                                         
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                               
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                        
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 9B in 1s (8B/s)  
Reading package lists... Done
shade@shade-desktop:~$ sudo aptitude install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libcairomm-1.0-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a 
The following NEW packages will be installed:
  gparted libcairomm-1.0-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1602kB of archives. After unpacking 6201kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libcairomm-1.0-1 1.2.0-0ubuntu1 [40.5kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libglibmm-2.4-1c2a 2.12.2-0ubuntu1 [136kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main libgtkmm-2.4-1c2a 1:2.10.2-0ubuntu1 [1104kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main gparted 0.2.5-1.1ubuntu11 [322kB]  
Fetched 1602kB in 7s (211kB/s)                                                  
Selecting previously deselected package libcairomm-1.0-1.
(Reading database ... 89587 files and directories currently installed.)
Unpacking libcairomm-1.0-1 (from .../libcairomm-1.0-1_1.2.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglibmm-2.4-1c2a.
Unpacking libglibmm-2.4-1c2a (from .../libglibmm-2.4-1c2a_2.12.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkmm-2.4-1c2a.
Unpacking libgtkmm-2.4-1c2a (from .../libgtkmm-2.4-1c2a_1%3a2.10.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package gparted.
Unpacking gparted (from .../gparted_0.2.5-1.1ubuntu11_i386.deb) ...
Setting up libcairomm-1.0-1 (1.2.0-0ubuntu1) ...

Setting up libglibmm-2.4-1c2a (2.12.2-0ubuntu1) ...

Setting up libgtkmm-2.4-1c2a (2.10.2-0ubuntu1) ...

Setting up gparted (0.2.5-1.1ubuntu11) ...



However gparted is not in the system --> adminstartion

---

### Post by shickidyshade on 2007-01-07
is it called the gnome partion editor

---

### Post by shickidyshade on 2007-01-07
so now im using the gnome partion editor since i think that what i should be using and i want to format the /dev/sdb    drive which is the secondary sata drive should i press delete to get this to work

---

### Post by taurus on 2007-01-07
Right now, your /dev/sdb1 has a ntfs filesystem on it.  So, do you plan to format it to something else?  If you do, you first need to unmount it before you can use gparted (Gnome Partition Editor) to reformat it.

```
sudo umount /media/sdb1
```
Then, fire up gparted and point it to /dev/sdb1...  However, if you want to format it to ext3, then you don't need gparted because you can do that from a terminal/commandline.

---

### Post by shickidyshade on 2007-01-07
I'm not sure what i want I would just like to be able to use the space on the hardrive to backup the information as a separate hd

---

### Post by taurus on 2007-01-07
Are you planing to share that harddrive with Windows?  If you only use that extra harddrive exclusively in Ubuntu, then I recommend you go with ext3 filesystem although Windows can read and write to ext2/ext3 with [http://www.fs-driver.org/](http://www.fs-driver.org/) now.

---

### Post by shickidyshade on 2007-01-07
eventually i will be sharing with windows how ever im being cheap right now and waiting for vista ultimate to come out before i install windows on my machine

so im guessing all i have left to do is mount

---

### Post by taurus on 2007-01-07
If you plan to install Vista on it later, probably a good idea to just leave it as ntfs for now...

---

### Post by shickidyshade on 2007-01-07
ok i just did this 

> **taurus said:**
> Let's try to mount the /dev/sdb1 first, shall we...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line to it.

```
/dev/sdb1   /media/sdb1   ntfs   ntfs nls=utf8,umask=0222   0   0
```
Save it.  Then create a mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```

and now i feel stupid because i cant find where it mounted it should be in the filesystem correct in a folder named sdb1

---

### Post by taurus on 2007-01-07
It's under /media/sdb1.  If not sure, you can always run this command from a terminal to determine where it is.

```
df -h
```
And by the way, there should be an icon on your Desktop for that harddrive--/media/sdb1!  You may have to reboot for it to show up though.

---

### Post by shickidyshade on 2007-02-02
Im trying to add a shared drive to my computer how do I make this folder called shared

This is the sudo fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18701   150215751   83  Linux
/dev/sdb2           18702       19457     6072570    5  Extended
/dev/sdb5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001    c  W95 FAT32 (LBA)
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18701   150215751   83  Linux
/dev/sdb2           18702       19457     6072570    5  Extended
/dev/sdb5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001    c  W95 FAT32 (LBA)


```

Hey is the sudo gedit /etc/stab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a9c6a64e-fe7f-4d20-a58c-96ea97da87bb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=64025352-1a65-46cf-ad80-6556fb353546 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```

---

### Post by campidg on 2007-04-13
I am also trying to mount a second hard drive.  I have followed this thread and got the following results:

> campidg@campidg-desktop:~$ sudo mkdir /media/hdc1
campidg@campidg-desktop:~$ sudo mount -a
[mntent]: line 12 in /etc/fstab is bad
campidg@campidg-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             146G  2.4G  136G   2% /
varrun                221M   88K  221M   1% /var/run
varlock               221M     0  221M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   18M  203M   8% /lib/modules/2.6.17-11-generic/volatile
campidg@campidg-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19293   154970991   83  Linux
/dev/sda2           19294       19457     1317330    5  Extended
/dev/sda5           19294       19457     1317298+  82  Linux swap / Solaris

Disk /dev/hdc: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         637     5116671    c  W95 FAT32 (LBA)
/dev/hdc2             638        2354    13791802+  83  Linux
/dev/hdc3            2355        2482     1028160   82  Linux swap / Solaris
campidg@campidg-desktop:~$ sudo mount /media/hdc1
[mntent]: line 12 in /etc/fstab is bad
mount: can't find /media/hdc1 in /etc/fstab or /etc/mtab
campidg@campidg-desktop:~$ sudo mount /media/hdc2
[mntent]: line 12 in /etc/fstab is bad
mount: can't find /media/hdc2 in /etc/fstab or /etc/mtab
campidg@campidg-desktop:~$ 

I want to mount my old hard disk in my new machine so that I can access files on it that I thought I had backed up but didn't.

Something seems to wrong with my fstab file.
 
Thanks,

Cam

---

### Post by robenroute on 2007-04-13
> **campidg said:**
> I am also trying to mount a second hard drive.  I have followed this thread and got the following results:



I want to mount my old hard disk in my new machine so that I can access files on it that I thought I had backed up but didn't.

Something seems to wrong with my fstab file.
 
Thanks,

Cam

So what does your fstab say then?

---

### Post by campidg on 2007-04-13
Sorry, I thought this was in my previous post:

> campidg@campidg-desktop:~$ gksudo gedit /etc/fstab
(gedit:6354): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


 I don't understand what is going on here but the fstab scrip opened anyway and I edited it thusly:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=961a16e9-db35-49dc-8649-dc8831d3f6cf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b9e9abc3-12c1-4fe4-8bf8-bcbc979c14fc none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1   /media/hd1   ntfs   ntfs nls=utf8,umask=0222   0   0


And now I see whhat I did wrong.  I entered hd1 instead of hdc1 and didn't change ntfs to FAT32,  I just cut and pasted from Taurus's directions from earlier on in this thread, changed only one part of the last line to suit my situation and did *that* incorrectly.

How should the last line of /etc/fstab look if I want to mount this partition?  What is the format for entering other partitions in fstab that I want to mount from my old hard drive?.  What does nls=utf8,unmask=0222 mean and should I change this for my situation?

Thanks for your quick reply,

Cam

---

### Post by robenroute on 2007-04-13
"man fstab" (without the quotes) in a terminal will give you plenty of info. There's also lots of info on the web:

[here]("http://www.informatik.uni-freiburg.de/~mader/FSTAB-Tuning.html"), [here]("http://en.wikipedia.org/wiki/Fstab"), and [here]("http://www.humbug.org.au/talks/fstab/fstab.html") (especially the links at the bottom of this last page).

BTW, the reason I'm not presenting it to you on a silver platter is the simple fact that I think that people who want to tinker with the fstab, should read up on it in order to understand what they're doing. Sorry if this sounds somewhat condescending....

---

### Post by campidg on 2007-04-13
Hi robenroute

Like I said, I was just following the instructions from the previous posts.  But your point is well taken.  I've had a quick look at man fstab and the links you gave and things are already a bit clearer.  I'll work through it all when I have more time and may be back with more informed queries.

Thanks again,

Cam

---

