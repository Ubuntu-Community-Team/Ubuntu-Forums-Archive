---
title: "Issues after upgrading to hoary"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by bloodroses75 on 2005-05-30
Hey, i recently upgraded from warty to hoary using the installation CD and I am now having problems.

First, when i tried to just do an apt-get dist-upgrade, it would bomb out about when xorg was to be installed. So, I installed xorg first by an apt-get install xorg. Afterwards, dist-upgrade would run, but alot of files did not pass verification and a couple of others had to be forced. Once ubuntu rebooted, i tried to run the ubuntu update manager, but would give me a huge list of files that are not possible to be upgraded. So, i went to my friend's house to try and run update and dist-upgrade through his broadband and following [HTML]http://ubuntuguide.org[/HTML] . Now im down to these files left when i run ubuntu update manager again..

```

libavcodeccvs
libpostproc0
libxvidcore4

``` 

and also says they are kept back when running apt-get. So, i looked further into this by running apt-get -s install libavcodeccvs and this is what printed out...

```

root@sunfire:/home # apt-get -s install libavcodeccvs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavcodeccvs: Depends: libc6 (>= 2.3.2.ds1-21)
                 Depends: libpostproc0 (>= 2:20050427-0.0) but 1:1.0-sargepre5.1 is to be installed
                 Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
                 Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
E: Broken packages
root@sunfire:/home #

```

I get similar issues w/ the other 2 files. When i try to update libc6 or any of the other files that it depends on, it says that they are up to date already. These files are also preventing a couple other programs from installing properly even though they download okay. Anyone have any suggestions as to how to fix this?  ](*,) 


Thank you in advance

---

### Post by bloodroses75 on 2005-05-30
also, i forgot to mention as i dont know if this is a similar issue or not, when i do an apt-get dist-upgrade now i get alot of files that still cannot be authenticated. here is my listing from apt-get dist-upgrade

```


root@sunfire:/home # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libavcodeccvs libpostproc0 libxvidcore4
The following packages will be upgraded:
  fluxbox gaim gaim-data gimp gimp-data gimp-python gnome-btdownload libgcc1
  libgimp2.0 libsmbclient libwine mozilla-firefox
  mozilla-firefox-gnome-support python2.3-samba samba samba-common smbclient
  synaptic totem totem-gstreamer wine xchat xchat-common
23 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 52.5MB/52.6MB of archives.
After unpacking 1460kB disk space will be freed.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libgcc1 fluxbox gaim gaim-data gimp gimp-data libgimp2.0 gimp-python
  gnome-btdownload wine libwine mozilla-firefox-gnome-support mozilla-firefox
  python2.3-samba smbclient samba samba-common synaptic totem totem-gstreamer
  xchat xchat-common libsmbclient
Install these packages without verification [y/N]? N
E: Some packages could not be authenticated
root@sunfire:/home #


``` 

and again... thank you in advance.

---

### Post by Leif on 2005-05-30
OK, I'm not sure about all of them, but the unauthenticated packages should be from the backports repositories, assuming you have them enabled. If so, there's no cause for concern, go ahead and install.

As for the libxvid etc. stuff, if you have marillat repos, it's because they're a bit out of synch with ubuntu atm. I've disabled them, and things started making a bit more sense. Or you can look into forcing a version using synaptic.

---

### Post by bloodroses75 on 2005-05-31
removed the marillat references from the repositories list as suggested... worked like a charm, ubuntu is no longer nagging about those 3 files.. thank you  :D 

hopefully they'll get the marillat source back in sync with ubuntu soon so i can add them again later....


As for the unauthenticated packages.. they are now installed and i havent seen a problem with the system yet, so I should be good to go

---

