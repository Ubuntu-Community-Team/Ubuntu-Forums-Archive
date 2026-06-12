---
title: "[SOLVED] xubuntu installation process halts on older asus laptop"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by RavanH on 2008-01-28
Hi,

I recently got hold of an older Asus laptop with only 256Mb memory. It has Windows XP pre-installed (whatever did they think of, putting an elephant in a toy car :confused: )  so decided to throw beloved Ubuntu on it... Rather Xubuntu, as the specs  do not yield much room ;)

Anyway, I found that I needed the F6 boot option **nolapic** for the Live CD session to run. But after hitting Install and going through all the setup dialogs, the process hangs at 15% 'Detecting filesystems'

I have checked the CD with the self-check and found no errors. I tried a Ubuntu install (also with the **nolapic** option) and that went fine... So I have two options now:
1. Convert/strip-down the installed Ubuntu to Xubuntu 
2. Try and make the pure Xubuntu process work after all

Trying the first option, I have done a 'sudo apt-get xubuntu-desktop' and indeed, XFce is now installed and working... but still there remain some Gnome processes/programs running on the background that I feel are not necessary. How can I get rid of Gnome as much as possible?

I would prefer to go with the second option because that would give me the best setup instantly (I suppose). Can anyone help me with this installation hang issue? I tried to boot the Live CD with the boot options **noapic** and **acpi=off** in various combinations too, but with the exact same result...

Thanks for any suggestions :)
--ravan

---

### Post by overdrank on 2008-01-28
> **RavanH said:**
> Hi,


1. Convert/strip-down the installed Ubuntu to Xubuntu 


Trying the first option, I have done a 'sudo apt-get xubuntu-desktop' and indeed, XFce is now installed and working... but still there remain some Gnome processes/programs running on the background that I feel are not necessary. How can I get rid of Gnome as much as possible?

Thanks for any suggestions :)
--ravan

HI and I believe this link will help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Of course you are wanting to remove gnome so I would just replace xubuntu with ubuntu.

---

### Post by RavanH on 2008-01-31
> **overdrank said:**
> HI and I believe this link will help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Of course you are wanting to remove gnome so I would just replace xubuntu with ubuntu.
Thankyou for your reply overdrank. The link tells me how to completely remove XFce and get back to pure Ubuntu/Gnome, but (as you know) I want it the other way around: remove Gnome and keep a pure Xubuntu/XFce. For that purpose,the command ```
sudo apt-get remove abiword abiword-common abiword-plugins brasero dbus-x11 gnumeric-common gnumeric-gtk gqview gtk2-engines-murrine gtk2-engines-xfce libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-4 libgsf-gnome-1-114 libgtkmathview0c2a libjpeg-progs liblink-grammar4 libmodplug0c2 libmpcdec3 libots0 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage python-exo tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman thunderbird totem-xine vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
``` is suggested. Simply replacing every xubuntu with ubuntu (or is that not what you are suggesting?) will not result in a pure Xubuntu - I am sure... 

I have tried to do a ```
sudo apt-get remove ubuntu-desktop
``` before but that did not do the trick :(

---

### Post by RavanH on 2008-01-31
> **overdrank said:**
> HI and I believe this link will help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Of course you are wanting to remove gnome so I would just replace xubuntu with ubuntu.

Ok, I was to hasty in my reply... Looking closer on that website, I found [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) which looks promising enough to try :) 

Thanks! I will report with results for anyone interested.

---

### Post by overdrank on 2008-01-31
> **RavanH said:**
> Ok, I was to hasty in my reply... Looking closer on that website, I found [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) which looks promising enough to try :) 

Thanks! I will report with results for anyone interested.

Thanks and great, Please post back with results. :)

---

### Post by RavanH on 2008-02-04
Ok, I did try the command as given on [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) and sure enough it did remove Gnome Desktop. After reinstalling openoffice and evolution, I had indeed have a system with only XFce... 

But there were still those gnome-specific processes running on the background and I noticed some very WEIRD session-management behaviour. Some processes would start up multiple times while others would not start up at all. (Cairo Dock about 5 times, Skype and Wengophone twice while Wicd refused to start up after login)

I really like to see a pure XFce setup running without any trace of Gnome so I will have a go at installing Linux Mint XFce 3.0 from a live CD. More later ;)

---

### Post by Carl H on 2008-02-04
> **RavanH said:**
> Anyway, I found that I needed the F6 boot option **nolapic** for the Live CD session to run. But after hitting Install and going through all the setup dialogs, the process hangs at 15% 'Detecting filesystems'

Try using the "alternate install" CD instead of the Live CD. 

In my experience you need at least 512Mb of RAM for the Live CD to work properly / at all.

---

### Post by RavanH on 2008-02-07
OK, I tried the Linux Mint XFce 3.0 live CD and the install process ran fine. Weird éh?

Only after installing Linux Mint XFce 3.0, logging in to an X session was not possible. A terminal session and editing the sources.list file and doing a dist-upgrade finally resulted in an full XFce/ubuntu (Minted in alpha stage ;) ) setup... :rolleyes:

Anyway, it works fine now. Thanks all.

---

### Post by cryptozoologist on 2008-02-07
i had a system that would hang during install and the solution that worked for me was to have a .iso file of the xubuntu alternate on the other partition.  if you poke around in advanced options on the xubuntu alternate installer you will find the option to point to a .iso instead of the cd.

peace
cryptozoologist

---

