---
title: "Update manager not working"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by ewok49 on 2011-11-01
Hi everybody,

I am running Ubuntu 11.10 64bt on a Lenovo w500 machine, this was upgraded from 11.04 which I had on this system already. I have been running Ubuntu for about 4 years now but have come across a few problems I just don't understand.

1) Update manager does not work, it launches fine, retrieves the package lists on what needs to be updated, but when I click on update nothing happens at all - and by that I mean it does not update anything at all it gives no error message it just almost ignores the fact I have selected to update things..  This has never been a problem in the past. I don't know why it's not working as it should now. Any ideas?

2) In an attempt to keep up to date I have been using a terminal, however, my sources list does not correlate with what I see when I attempt to update. My only repos I have active in /etc/apt/sources.list are:

deb [http://ftp.leg.uct.ac.za/ubuntu/](http://ftp.leg.uct.ac.za/ubuntu/) oneiric main restricted universe multiverse
deb [http://ftp.leg.uct.ac.za/ubuntu/](http://ftp.leg.uct.ac.za/ubuntu/) oneiric-security main restricted universe multiverse
deb [http://ftp.leg.uct.ac.za/ubuntu/](http://ftp.leg.uct.ac.za/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://ftp.leg.uct.ac.za/medibuntu](http://ftp.leg.uct.ac.za/medibuntu) oneiric free non-free

I must at this point mention that my /etc/apt/sources.list differs from what I see in the Update Manager>Settings>Other Software, I can't edit this at all for some reason and it appears to me like Update Manager is not using my /etc/apt/sources.list as the list for the repos. I say this beacause when I attempt to update in a terminal (sudo apt-get update) the process attempts to get packages from other resources I have not specified in /etc/apt/sources.list:

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease](http://dl.google.com/linux/talkplugin/deb/dists/stable/InRelease)  
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/InRelease](http://archive.canonical.com/ubuntu/dists/oneiric/InRelease)  
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg) 

I don't have these repos in my sources list anywhere so I am confused as to why the apt-get is looking there for updates.

3)My final problem is with the Software Centre, just like my update manager, it works up until I click install for any particular package.  Nothing happens, there is no install, however if I do a manual install via the terminal for a particular package it works fine.  Are these problems related?

Any help or advice would be greatly appreciated.

---

### Post by ashickur.noor on 2011-11-01
See the Software source, there you can find your sources. Try to use synaptic package manager.

---

### Post by matt_symes on 2011-11-01
Hi

Run both update manager and sofware center from the terminal and post back any error messages.

What is in the directory /etc/apt/sources.d/. This contains sources for PPAs.

Post the output of that as well.

Kind regards

---

### Post by ewok49 on 2011-11-01
> **matt_symes said:**
> Hi

Run both update manager and sofware center from the terminal and post back any error messages.

What is in the directory /etc/apt/sources.d/. This contains sources for PPAs.

Post the output of that as well.

Kind regards

Output from terminal execution of update manager:

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8297): Gtk-WARNING **: Attempting to add a widget with type aptdaemon+gtk3widgets+AptProgressDialog to a GtkWindow, but as a GtkBin subclass a GtkWindow can only contain one widget at a time; it already contains a widget of type GtkVBox

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8297): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed


There is no /etc/apt/sources.d/  folder.  The /etc/apt/ folder contains the following folders:
/preferences.d/
/sources.list.d/
/trusted.gpg.d/
/apt.conf.d/

There are some files in the /etc/apt/ folder, the relevant ones are:
/etc/apt/sources.list
/etc/apt/source.list.distUpgrade
/etc/apt/sources.list.save

Which are you wanting the output from? A file in /etc/apt/ or a folder located in /etc/apt/?

The software center appears to be working now for some reason - I cleaned out the in the cache using sudo rm -r /var/lib/apt/lists/*
But that hasn't done anything for the Update Manager.
EDIT: It appears to work for certain apps/packages but not others...I'm looking into this a bit more and will give details as I get them.

Thanks for your quick response

---

### Post by matt_symes on 2011-11-01
Hi

Yes it should have been /etc/apt/sources.list.d/. My bad. Fingers and brain not connected today.

I'm glad software center is working for you now.

Kind regards

---

### Post by ewok49 on 2011-11-01
> **matt_symes said:**
> Hi

Yes it should have been /etc/apt/sources.list.d/. My bad. Fingers and brain not connected today.

I'm glad software center is working for you now.

Kind regards

Output of /etc/apt/sources.list.d/ :
banshee.list
dropbox.list.save
lucid-partner.list.distUpgrade
sevenmachines-flash.list.save
ubuntu-tweak-stable.list
banshee.list.save
elegant-gnome-ppa.list
lucid-partner.list.save
shiki-mediainfo-lucid.list
ubuntu-tweak-stable.list.distUpgrade
bisigi-ppa-lucid.list
elegant-gnome-ppa.list.save
medibuntu.list
shiki-mediainfo-lucid.list.distUpgrade
ubuntu-tweak-stable.list.save
bisigi-ppa-lucid.list.distUpgrade
google-talkplugin.list
medibuntu.list.distUpgrade
shiki-mediainfo-lucid.list.save
ubuntu-x-swat-x-updates.list
bisigi-ppa-lucid.list.save
google-talkplugin.list.distUpgrade   
medibuntu.list.save                   
skype.list             
ubuntu-x-swat-x-updates.list.distUpgrade
canonical-dx-team-une.list          
google-talkplugin.list.save    
mendeleydesktop.list    
skype.list.distUpgrade
ubuntu-x-swat-x-updates.list.save
canonical-dx-team-une.list.distUpgrade 
linuxdcpp-team-ppa.list            
mendeleydesktop.list.distUpgrade    
skype.list.save
canonical-dx-team-une.list.save 
linuxdcpp-team-ppa.list.distUpgrade  
mendeleydesktop.list.save             
tualatrix-ppa-lucid.list
dropbox.list                            
linuxdcpp-team-ppa.list.save         
sevenmachines-flash.list              
tualatrix-ppa-lucid.list.distUpgrade
dropbox.list.distUpgrade                
lucid-partner.list                   
sevenmachines-flash.list.distUpgrade  
tualatrix-ppa-lucid.list.save

---

### Post by matt_symes on 2011-11-01
Hi

```
Output of /etc/apt/sources.list.d/ :
banshee.list
dropbox.list.save
lucid-partner.list.distUpgrade
sevenmachines-flash.list.save
ubuntu-tweak-stable.list
banshee.list.save
elegant-gnome-ppa.list
lucid-partner.list.save
shiki-mediainfo-lucid.list
ubuntu-tweak-stable.list.distUpgrade
bisigi-ppa-lucid.list
elegant-gnome-ppa.list.save
medibuntu.list
shiki-mediainfo-lucid.list.distUpgrade
ubuntu-tweak-stable.list.save
bisigi-ppa-lucid.list.distUpgrade
google-talkplugin.list
medibuntu.list.distUpgrade
shiki-mediainfo-lucid.list.save
ubuntu-x-swat-x-updates.list
bisigi-ppa-lucid.list.save
google-talkplugin.list.distUpgrade 
medibuntu.list.save 
skype.list 
ubuntu-x-swat-x-updates.list.distUpgrade
canonical-dx-team-une.list 
google-talkplugin.list.save 
mendeleydesktop.list 
skype.list.distUpgrade
ubuntu-x-swat-x-updates.list.save
canonical-dx-team-une.list.distUpgrade 
linuxdcpp-team-ppa.list 
mendeleydesktop.list.distUpgrade 
skype.list.save
canonical-dx-team-une.list.save 
linuxdcpp-team-ppa.list.distUpgrade 
mendeleydesktop.list.save 
tualatrix-ppa-lucid.list
dropbox.list 
linuxdcpp-team-ppa.list.save 
sevenmachines-flash.list 
tualatrix-ppa-lucid.list.distUpgrade
dropbox.list.distUpgrade 
lucid-partner.list 
sevenmachines-flash.list.distUpgrade 
tualatrix-ppa-lucid.list.save
```

I am wondering if one of the PPa's in there is causing update manager to fail. To check

Open a terminal and type (to rename the folder)

```
sudo mv /etc/apt/sources.list.d /etc/sources.list.d.old
```

Then try

```
sudo apt-get update
```

Then try to open update manager.

This will rename the folder back.

```
sudo mv /etc/apt/sources.list.d.old /etc/sources.list.d
```

Kind regards

---

### Post by ewok49 on 2011-11-01
> **matt_symes said:**
> Hi

```
Output of /etc/apt/sources.list.d/ :
banshee.list
dropbox.list.save
lucid-partner.list.distUpgrade
sevenmachines-flash.list.save
ubuntu-tweak-stable.list
banshee.list.save
elegant-gnome-ppa.list
lucid-partner.list.save
shiki-mediainfo-lucid.list
ubuntu-tweak-stable.list.distUpgrade
bisigi-ppa-lucid.list
elegant-gnome-ppa.list.save
medibuntu.list
shiki-mediainfo-lucid.list.distUpgrade
ubuntu-tweak-stable.list.save
bisigi-ppa-lucid.list.distUpgrade
google-talkplugin.list
medibuntu.list.distUpgrade
shiki-mediainfo-lucid.list.save
ubuntu-x-swat-x-updates.list
bisigi-ppa-lucid.list.save
google-talkplugin.list.distUpgrade 
medibuntu.list.save 
skype.list 
ubuntu-x-swat-x-updates.list.distUpgrade
canonical-dx-team-une.list 
google-talkplugin.list.save 
mendeleydesktop.list 
skype.list.distUpgrade
ubuntu-x-swat-x-updates.list.save
canonical-dx-team-une.list.distUpgrade 
linuxdcpp-team-ppa.list 
mendeleydesktop.list.distUpgrade 
skype.list.save
canonical-dx-team-une.list.save 
linuxdcpp-team-ppa.list.distUpgrade 
mendeleydesktop.list.save 
tualatrix-ppa-lucid.list
dropbox.list 
linuxdcpp-team-ppa.list.save 
sevenmachines-flash.list 
tualatrix-ppa-lucid.list.distUpgrade
dropbox.list.distUpgrade 
lucid-partner.list 
sevenmachines-flash.list.distUpgrade 
tualatrix-ppa-lucid.list.save
```

I am wondering if one of the PPa's in there is causing update manager to fail. To check

Open a terminal and type (to rename the folder)

```
sudo mv /etc/apt/sources.list.d /etc/sources.list.d.old
```

Then try

```
sudo apt-get update
```

Then try to open update manager.

This will rename the folder back.

```
sudo mv /etc/apt/sources.list.d.old /etc/sources.list.d
```

Kind regards

Moving the PPAs to the .old list made the update search of the repos much quicker, however it still does not make the update button work in Update Manager.  The other thing I forgot to mention is there are 3 packages to "update" but they can not be selected or de-selected.  They show up as being options but are useless - can't be installed or ignored.

---

### Post by matt_symes on 2011-11-01
Hi

The next thing i would do is to clear all the caches

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg --clear-avail
sudo apt-get update
```

Then try update manager again.

Kind regards

---

### Post by ewok49 on 2011-11-01
> **matt_symes said:**
> Hi

The next thing i would do is to clear all the caches

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg --clear-avail
sudo apt-get update
```

Then try update manager again.

Kind regards

Hi matt,

Thanks tried those commands then attempted to update and still the same issue.

Lanuched update-manager from a terminal and this is the output still

```
(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gtk-WARNING **: Attempting to add a widget with type aptdaemon+gtk3widgets+AptProgressDialog to a GtkWindow, but as a GtkBin subclass a GtkWindow can only contain one widget at a time; it already contains a widget of type GtkVBox

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:21578): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed
```

Still have those 3 packages I can't do anything with.

EDIT: 
Opened Synaptic through a terminal and found the packages that were showing up and installed them so they have now disappeared.  I have updated from CL so not sure if the issue with the buttons is still there or not.  Also re-installed the update manager from synaptic.

Will keep you all posted on it's success/failure.

---

### Post by matt_symes on 2011-11-01
Hi

I think my next move would be to reinstall it through the command line. Those critical lines look worrying when you run it from the command line.

After that i would be looking at running it through strace or gdb and see if that supplies more information.

Was this a fresh install of Ubuntu or an upgrade ?

EDIT: This was an upgrade gtk2 -> gtk3. I wonder if that is part of the problem.

Kind regards

---

### Post by wkussmaul on 2011-11-01
Update Manager won't even launch for me. Instead I get:

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.[/B] [B]

Please report this bug against the 'update-manager' package and include the following error message:[/B] [B]

'E:Encountered a section with no Package: header, [/B] [B]
E:problem with MergeList/var/lib/apt/lists/
us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'[/B]

(When it says "please report this bug..." does that mean report it to Bugzilla?

This is a dual boot HP Pavilion g7-1113cl notebook with AMD A4-3300M APU processor running Ubuntu 11.04 64 bit, Gnome 2.32.1. OS is newly installed on new computer.

I've been using Ubuntu 10 with KDE desktop on an older Toshiba; updates worked beautifully. 

Thanks for whatever help you can provide.

wk

---

### Post by matt_symes on 2011-11-02
Hi

@wkussmahl

Open a terminall and type

```
sudo rm -rf /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen.

This will removed your corrupted cache files. Then type

```
sudo apt-get update
```

This will update your cache again.

Kind regards

---

### Post by wkussmaul on 2011-11-02
Thanks. However, Update Manager still doesn't work.

Perhaps this will tell why:

wes@wes-HP-Pavilion-g7-Notebook-PC:~$ sudo rm -rf /var/lib/dpkg/lists/*
[sudo] password for wes: 
wes@wes-HP-Pavilion-g7-Notebook-PC:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                     
Get:6 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Get:8 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [31.4 kB]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [75.4 kB]        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [13.3 kB]    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [661 B]    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [211 kB]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [138 kB]        
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [51.4 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [753 B]   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [30.4 kB]   
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [1,934 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [2,317 B] 
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages [405 kB] 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages [838 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages [116 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [5,000 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 1,170 kB in 28s (41.1 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
wes@wes-HP-Pavilion-g7-Notebook-PC:~$

---

### Post by matt_symes on 2011-11-02
Hi

Try

```
sudo rm -rf /var/lib/apt/lists/*
```

I think you might have e-mail notification on. 

Check the post though just to make sure it is not edited.

I did originally ask you to type

```
sudo rm -rf /var/lib/**dpkg**/lists/*
```

but i realised my mistake and changed dpkg to apt by editing my post #13 just after i posted it. 

I think you just got the initial post by email and not the edited version. 

So please, always double check the posts on forums.

Kind regards

---

### Post by wkussmaul on 2011-11-02
Victory! Thank you!

If I knew what I was doing I'd submit a little script to trap that error and launch those two simple commands, perhaps with a little note saying "stay tuned, we need  to fix something..."

wk

---

### Post by ewok49 on 2011-11-03
So I am not sure what happened, but I went into Synaptic and edited some of the sources for the repos there and now my update manager is working like it should ie. when I click the button to install updates it no longer ignores the command but executes it...
:smile:

---

### Post by matt_symes on 2011-11-03
Hi

That's great news.:popcorn: It was the sources after all.

Please mark this thread as solved.

Kind regards

---

