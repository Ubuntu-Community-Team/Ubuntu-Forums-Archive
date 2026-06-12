---
title: "A newly upgraded 8.04 dependency problem"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-02-07
I have a couple 8.04.4 installs on another external for testing upgrading to 10.04.  These are clean installs with medibuntu added and installing gthumb, gparted, and ubuntu-restricted-extras.

Ran one with Update Mangler last night.

Got a few warnings but nothing that looked real bad until flashplugin-nonfree and flashplugin-installer.  These seemed to be impervious to the process but it continued anyway.

The bugger boots and looks great.

Apt does not work (so synaptic doesn't either).  In chroot this morning I did an apt-get update and tried apt-upgrade just to get this for your viewing pleasure;
```

root@sam-desktop:/# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
root@sam-desktop:/# 

```
I tried the first suggestion there last night to no avail.  I also ran dpkg --configure -a which seemed to think things were hunky dory.

This is not critical as I can turn it right back into 8.04.4 by reinstalling.

If anyone has a suggestion as to hot to fix this I would appreciate it.

---

### Post by taavikko on 2010-02-07
you're already running root, so why use sudo?

also, what's the output of the "apt-get update && apt-get -f install"

---

### Post by ranch hand on 2010-02-07
I think the "sudo" got in there as I was running an update on the 10.04 install I am on now in terminal at the same time.  A stupid typo.
```

root@sam-desktop:/# apt-get update && apt-get -f install
Get:1 http://ca.archive.ubuntu.com lucid Release.gpg [189B]                                                               
Get:2 http://ca.archive.ubuntu.com lucid/main Translation-en_CA [11.3kB]                                                  
Hit http://security.ubuntu.com lucid-security Release.gpg                                               
Ign http://security.ubuntu.com lucid-security/main Translation-en_CA                                    
Hit http://archive.canonical.com lucid Release.gpg                                                      
Ign http://archive.canonical.com lucid/partner Translation-en_CA                                        
Hit http://packages.medibuntu.org lucid Release.gpg                                                     
Ign http://packages.medibuntu.org lucid/free Translation-en_CA                                          
Ign http://packages.medibuntu.org lucid/non-free Translation-en_CA                                      
Ign http://security.ubuntu.com lucid-security/restricted Translation-en_CA                              
Ign http://security.ubuntu.com lucid-security/universe Translation-en_CA                                
Ign http://security.ubuntu.com lucid-security/multiverse Translation-en_CA                              
Hit http://security.ubuntu.com lucid-security Release                                                   
Hit http://archive.canonical.com lucid Release                                                            
Hit http://packages.medibuntu.org lucid Release                                                           
Get:3 http://ca.archive.ubuntu.com lucid/restricted Translation-en_CA [2,799B]                           
Hit http://security.ubuntu.com lucid-security/main Packages                                                                              
Get:4 http://ca.archive.ubuntu.com lucid/universe Translation-en_CA [663B]                                 
Ign http://ca.archive.ubuntu.com lucid/multiverse Translation-en_CA                                                                   
Hit http://ca.archive.ubuntu.com lucid-updates Release.gpg                                                                            
Ign http://ca.archive.ubuntu.com lucid-updates/main Translation-en_CA                                                    
Ign http://ca.archive.ubuntu.com lucid-updates/restricted Translation-en_CA                                              
Ign http://ca.archive.ubuntu.com lucid-updates/universe Translation-en_CA                                                
Ign http://ca.archive.ubuntu.com lucid-updates/multiverse Translation-en_CA                        
Hit http://ca.archive.ubuntu.com lucid-backports Release.gpg                                       
Hit http://archive.canonical.com lucid/partner Packages                                                                      
Ign http://ca.archive.ubuntu.com lucid-backports/main Translation-en_CA                    
Hit http://packages.medibuntu.org lucid/free Packages                
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Ign http://ca.archive.ubuntu.com lucid-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com lucid-backports/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com lucid-backports/multiverse Translation-en_CA
Get:5 http://ca.archive.ubuntu.com lucid Release [57.2kB]
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://ca.archive.ubuntu.com lucid-updates Release
Hit http://ca.archive.ubuntu.com lucid-backports Release
Get:6 http://ca.archive.ubuntu.com lucid/main Packages [1,414kB]
Get:7 http://ca.archive.ubuntu.com lucid/restricted Packages [6,193B]                                                                                                           
Get:8 http://ca.archive.ubuntu.com lucid/universe Packages [5,402kB]                                                                                                            
Get:9 http://ca.archive.ubuntu.com lucid/multiverse Packages [181kB]                                                                                                            
Hit http://ca.archive.ubuntu.com lucid-updates/main Packages                                                                                                                    
Hit http://ca.archive.ubuntu.com lucid-updates/restricted Packages                                                                                                              
Hit http://ca.archive.ubuntu.com lucid-updates/universe Packages                                                                                                                
Hit http://ca.archive.ubuntu.com lucid-updates/multiverse Packages                                                                                                              
Hit http://ca.archive.ubuntu.com lucid-backports/main Packages                                                                                                                  
Hit http://ca.archive.ubuntu.com lucid-backports/restricted Packages                                                                                                            
Hit http://ca.archive.ubuntu.com lucid-backports/universe Packages                                                                                                              
Hit http://ca.archive.ubuntu.com lucid-backports/multiverse Packages                                                                                                            
Fetched 7,076kB in 30s (232kB/s)                                                                                                                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1 libtotem-plparser12
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
root@sam-desktop:/# 

```
and then running an install gives;
```

root@sam-desktop:/# apt-get install nautilus-gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1 libtotem-plparser12
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnautilus-extension1
The following NEW packages will be installed:
  libnautilus-extension1 nautilus-gksu
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 66.3kB of archives.
After this operation, 225kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ca.archive.ubuntu.com lucid/main libnautilus-extension1 1:2.29.2-0ubuntu4 [60.3kB]
Get:2 http://ca.archive.ubuntu.com lucid/main nautilus-gksu 2.0.2-2ubuntu1 [6,012B]
Fetched 66.3kB in 1s (54.8kB/s)    
Selecting previously deselected package libnautilus-extension1.
(Reading database ... 57731 files and directories currently installed.)
Unpacking libnautilus-extension1 (from .../libnautilus-extension1_1%3a2.29.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package nautilus-gksu.
Unpacking nautilus-gksu (from .../nautilus-gksu_2.0.2-2ubuntu1_i386.deb) ...
Setting up libnautilus-extension1 (1:2.29.2-0ubuntu4) ...

Setting up nautilus-gksu (2.0.2-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

root@sam-desktop:/# 

```
So I believe that you have solved my problem.  Thank you very much.

An old dog learned a new trick today.  This is my second round of testing and it is a great education for a noob.

Your post came just at the right time as I am about to abuse the other 8.04.4 install with an upgrade from here using "apt-get dist-upgrade" to see how that goes.

Thank you once again, a lot of your posts have been very useful to me in the past.  Particularly in the 9.10-testing forum.

---

### Post by taavikko on 2010-02-07
no worries mate ;)

Just a quick side note. There's no need on running backports repositories as they provide something new backported for older releases. Nothing yet for an alpha LL.

You're also good to go on removing those packages that are mentioned obsolete."apt-get auto-remove They're been replaced by newer versions.
"aptitude search ~o" will list every obsolete package ((also manually installed.. be careful)).

---

### Post by plun on 2010-02-07
I haven't seen that upgrade tests are started...

According to timetable

**February 2010**
February 4th - Upgrade Testing begins

---

### Post by ranch hand on 2010-02-07
> **taavikko said:**
> no worries mate ;)

Just a quick side note. There's no need on running backports repositories as they provide something new backported for older releases. Nothing yet for an alpha LL.

You're also good to go on removing those packages that are mentioned obsolete."apt-get auto-remove They're been replaced by newer versions.
"aptitude search ~o" will list every obsolete package ((also manually installed.. be careful)).
I just switched all the "hardy" entries to "lucid".  I have a "real" 8.04 that was the first Linux I ever installed or ran (about 3 weeks after I joined the forums here).  I set the backports on the new installs as that is how the original is set up.  There were several backported thing over this time.

I will be removing them.  Probably with apt and/or synaptic.  Aptitude has never blown my skirt up, have no idea why not.

---

### Post by ranch hand on 2010-02-07
> **plun said:**
> I haven't seen that upgrade tests are started...

According to timetable

**February 2010**
February 4th - Upgrade Testing begins
I was too chicken to try it the 4th and I am glad I waited as there was a kernel update for 8.04 yesterday.  That upgrade and this post;

[http://ubuntuforums.org/showthread.php?t=1400212](http://ubuntuforums.org/showthread.php?t=1400212)

gave me the encouragement I needed to try it out.

Seems to work.  I am really impressed.  There is an awful lot of difference between these 2 OS'.  Hats off to the devs.

None of that crap about grub or grub-legacy either.

I will be doing a clean install of 10.04 and transferring my files from my "real" 8.04.  The upgrade, of coarse, leaves you in ext3.  I want ext4.  Plus, as it was my first install, it is on one partition.  Don't like that.

---

### Post by ranch hand on 2010-02-07
Just an update for those wanting to try this out.  I believe this will go very slick if you get rid of Firefox and the flash stuff in 8.04.4 first.

If it is an install you use I would copy it to another partition (or partitions) and try that one out first.  At least back up everything including your bookmarks and so forth.

I realize now that I never installed Thunder bird on those 2 so I think I will install over one of them and do it again.

If you go the "apt-get dist-upgrade route you need to login through recovery and run the dpkg broken packages option to get the same "clean up" action that Update Mangler does.  I prefer that route as you can, if your scrolling settings go back far enough, check all the minor (or major) warnings and faults that you can't review in Update Manglers display.

---

### Post by dl7und on 2010-03-19
> **ranch hand said:**
> I believe this will go very slick if you get rid of Firefox and the flash stuff in 8.04.4 first.

Just too bad I did not see this earlier... I hope it is OK to extend a "solved" thread, since I ran into very similar problems but can not solve them easily...

I too have a Hardy desktop install that I just upgraded to Lucid alpha. And I too ran into problems with flashplugin-nonfree. When I try to autoremove old packages I get this:
```
root@excalibur:/home/dl7und# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xmp: Depends: xmp-common (= 3.0.0+20090923-1ubuntu1) but 2.5.0-1 is installed
       Recommends: unmo3 but it is not installed
E: Unmet dependencies. Try using -f.
root@excalibur:/home/dl7und# 

```
Trying to run apt-get -f install yields this:
```
root@excalibur:/home/dl7und# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libopencdk10-dev mesa-utils ispell ibritish python-opengl libgnutlsxx13
  libneon27 ttf-sil-gentium ubuntu-gdm-themes libmagick++10 libgpac0.4.4
  libwvstreams4.4-base mdetect libaudclient1 libbeagle1 g++-4.2 ggzcore-bin
  python-gdata libopenexr2ldbl libmagick10 libpcap0.7 libcamel1.2-11
  libwvstreams4.4-extras openoffice.org-hyphenation-en-us
  xserver-xorg-video-psb libggzmod4 libtotem-plparser10 libx11-xcb1 libsmbios1
  xserver-xorg-video-via libglu1-xorg-dev binutils-static libcdio7 policykit
  libmysqlclient15off libdirectfb-1.0-0 libx264-57 acl libdmx1
  nvidia-kernel-common libgammu3 bluez-audio libpolkit-gnome0 libggz2
  libcrypto++7 libxul0d libaudid3tag1 libpolkit-dbus2
  openoffice.org-thesaurus-en-au libxtrap6 openoffice.org-thesaurus-en-us
  libiso9660-5 libstdc++6-4.2-dev discover1-data liblzo2-dev libkadm55
  policykit-gnome python-4suite-xml libxklavier12 vlc-plugin-pulse libggzcore9
  libgmyth0 xulrunner-1.9-gnome-support libxul-common iamerican
  linux-source-2.6.24 libpolkit-grant2 libmpeg3-1 libntfs-3g28 libpolkit2
  hwtest libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree xmp-common
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree xmp-common
2 upgraded, 1 newly installed, 0 to remove and 103 not upgraded.
2 not fully installed or removed.
Need to get 0B/47.0kB of archives.
After this operation, 49.2kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@excalibur:/home/dl7und# 

```
I also tried to force with dpkg, but I can not seem to find a solution to get rid of these errors. But at least I was able to start Firefox through a terminal, so I can use the same machine to post this...:)

---

### Post by ranch hand on 2010-03-19
If you can file a bug it would be great.

I have three installations of 8.04 that I have upgraded.  Two were fresh installs and one is a copy of my old 8.04 install.  I also had 3 others that I just wiped after the attempt as it was not going anywhere due to problems like this one of yours.

What kind of errors are you getting when you run FF through the terminal?  There may be some help there.

Was your 8.04 completely up to date when you tried this.  An update should have been run just before attempting to upgrade to 10.04.

---

### Post by dl7und on 2010-03-19
Running Firefox is no problem, and this time I even got the Gnome menu bar back. (Had to do everything through terminal last time because I had no bars at all...)

I did some more searching, this time for other parts of the error messages (Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.) and it seems I found a solution thanks to a frustrated Virtualbox user.:) From the output I posted earlier it can be seen that there are actually two packages causing trouble. The second one was easily removed with this:
```
dpkg --remove --force-depends --force-remove-reinstreq xmp-common
```
(xmp-common was the other troublemaker) This did however still not work for flashplugin-nonfree, but the Virtualbox user had something for that too:

Go to /var/lib/dpkg/info and delete all packages starting with "flashplugin", then run
```
dpkg --remove --force-depends --force-remove-reinstreq flashplugin-nonfree
```
It should not find the package any longer and let you continue upgrading/installing/removing packages. The plugin itself is of course still there and needs to be upgraded by installing the installer:
```
apt-get install flashplugin-installer
```

---

### Post by ranch hand on 2010-03-19
I had very mixed results with removing the package.  Untill it is resolved you can't install anything.

That said the last 2 times I tried the upgrade it went fine, even with the plugin left on.

This is a huge jump from 8.04 to 10.04 and I am very impressed that it works at all.  I will be installing 8.04.4 again, soon, and trying it again to see how far the process has improved, probably next week.

I may install twice so that I can try using Update Mangler to do it too.  I had all my good results so far using the old debian method with apt.  I like it better anyway but most folks will use UM.

---

### Post by dl7und on 2010-03-19
> **ranch hand said:**
> I had very mixed results with removing the package.  Untill it is resolved you can't install anything.
Right, that is frustrating, especially since this happens somehow during the upgrade process with a lot of packages left hanging.

> This is a huge jump from 8.04 to 10.04 and I am very impressed that it works at all.  I will be installing 8.04.4 again, soon, and trying it again to see how far the process has improved, probably next week.
Yes, I was surprised it went so well after all. OK, I have no sound yet, but this is alpha, and KiCAD works.:D But this was probably the last time I used LTS on the desktop. It was nice for servers, when I still had to administrate a few, but on the desktop I think I miss too many improvements. I am glad I did this only with one machine...:D

---

### Post by ranch hand on 2010-03-19
Out of curioucty, did you use apt or UM.

My best results were with apt.  You need to run "sudo dpkg --configure -a" multiple times until there is no change and then boot to the sucker in recovery and use the dpkg option there and it comes out right for me.

UM, for me, so far has just almost worked but gets stuck on the plug in problem and I have only gotten it straight one out of three tries.

When I do my "real" upgrade it will be a clean install and a transfer of files.  But this is FUN for testing.

---

### Post by dl7und on 2010-03-20
Hmm, why does notification not work...?

> **ranch hand said:**
> Out of curioucty, did you use apt or UM.
UM? For "serious work" I always prefer the command line, apt, dpkg etc. Synaptic is for convenience. But I must say that I switched to Ubuntu a number of years back for exactly this reason: convenience. (was on Gentoo before) I felt I was getting old, so this is my "old men Linux"...:-P

> My best results were with apt.  You need to run "sudo dpkg --configure -a" multiple times until there is no change and then boot to the sucker in recovery and use the dpkg option there and it comes out right for me.
Fortunately, I do not encounter such problems often. I usually prefer to stick to stable editions/packages, because I have enough trouble elsewhere.

> When I do my "real" upgrade it will be a clean install and a transfer of files.  But this is FUN for testing.
Judging from your avatar, you should still be "a few" years older than me, so I feel a little bit of hesitation in admitting that I do not "test" much due to all the trouble. Yes, I'm getting old... I had to "test" for a few years when I was administrating a university network, so I did avoid any other trouble that was avoidable. That was also when I completely switched to Linux.:biggrin:

As I said, my main reason for this "hasty" upgrade was KiCAD. I want to do some electronics and the package in Hardy was not so nice...

---

### Post by ranch hand on 2010-03-20
They are updating the indicator stuff all the time (pretty much daily) to get notifications going.

I have been told several times, in this forum that the only way to update correctly is to use Update Mangler.  I do it wrong because it works better,

You are correct I am a grumpy geezer.  My join date is from before I ever installed 8.04.  That was my first Linux.  I test because it is FUN.  I multi boot and the only distros that I really like are debian based (you should look at PhatDebian - Lenny on 2.6.30 for ext4 support - it is ext3) mainly Ubuntu and Debian but with Mandriva on board too (token RPM distro).

I need to get the new Mandriva.  2009-1 came as a live DVD with the option of installing Gnome Lxde and/or KDE.  Sweet set up.  I have all three so that I can show folks KDE with which I am not compatible (don't like it a bit).

The only time I really enjoyed MS was back in MSDos with DosShell.  I am really enjoying Ubuntu and Linux in general.  It is nice to actually own your box.

---

### Post by nanog on 2010-03-21
had this happen on my 4th hardy-lucid upgrade. it looks like this problem has been around for awhile:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841)

```
rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
dpkg --remove --force-remove-reinstreq flashplugin-nonfree
dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```

---

### Post by ranch hand on 2010-03-21
That is the bugger that keeps trying to get me.

I take it that the code in your post did take care of it.

Considering the huge jump there is with upgrading 8.04 to 10.04, I am amazed that it works at all.  It seems to get a little better all the time.

---

