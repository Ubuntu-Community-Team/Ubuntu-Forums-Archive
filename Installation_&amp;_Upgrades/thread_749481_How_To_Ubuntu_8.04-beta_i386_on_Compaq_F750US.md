---
title: "How To: Ubuntu 8.04-beta i386 on Compaq F750US"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by AlanB66 on 2008-04-08
This is a how-to with regards to the long-threaded post "[_[COLOR="Blue"]So has anybody successfully installed Ubuntu or Kubuntu on a Compaq F700 #f750us ?[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=687833")"

**_What you'll need:_**
* Compaq F750US
* Ubuntu 8.04 i386 ISO burned to CD (do NOT use AMD64 unless you have patience to iron other things out)

**_What versions are covered:_**
* Ubuntu 8.04 beta  Kernel 2.6.24-15-generic
* NDisWrapper 1.52

**_What you'll have:_**
At the end of these steps, you will have a Ubuntu installation that:
[LIST]
[*]Has wired and wireless LAN access
[*]Has the Wireless LAN supporting non-broadcasting SSID's
[*]Has the i386 OS to support Canon MP520 (for MX700) drivers
[*]Has the capability for other i386 apps that are otherwise hard to come by in AMD64-bit mode
[/LIST]

**_Steps:_**
[LIST=1]
[*]Download and Burn CD for i386 Ubuntu 8.04-beta


[*]Install from CD


[*]Reboot


[*]Open Hardware Manger
   [LIST=a]
   [*]Enable Nvidia Display adapter
   [*]DISABLE HAL & Atheros Wireless
   [/LIST]


[*]Open linux-restricted-modules-common:
     [LIST=a]
     [*]sudo gedit /etc/default/linux-restricted-modules-common )
     [*]Disable both ath_hal and ath_pci            ( DISABLE_MODULES="ath_hal ath_pci" )
     [/LIST]


[*]Reboot


[*]Run Update Manager and update EVERYTHING
    [LIST=a]
    [*]Run "Software Sources" Manager and uncheck/re-check "Universe". During "close" allow "Reload" of sources.
    [*]Run Update Manager, kick of a "Check", and now all updates are now available to download/install.
    [/LIST]


[*]Using Firefox, download to /tmp:
   [LIST=a]
   [*]xp32-5.3.0.56-whql.zip (available here: [[COLOR="Blue"]_http://www.atheros.cz/download.php?atheros=AR5007EG&system=1_[/COLOR]]("http://www.atheros.cz/download.php?atheros=AR5007EG&system=1"))
   [*]ndiswrapper-1.52.tar.gz (available here: [[COLOR="blue"]_http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=573476_[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=573476"))
   [/LIST]


[*]Unravel packages
   [LIST=a]
   [*]cd /tmp
   [*]unzip xp32-5.3.0.56-whql.zip
   [*]tar xvfz ndiswrapper-1.52.tar.gz
   [/LIST]


[*]Get "Make" capabilities updated:
   [LIST=a]
   [*]sudo apt-get update && sudo aptitude install build-essential
   [*]sudo apt-get install subversion
   [/LIST]



**(Picking up from Step #4 on [http://ubuntuforums.org/showpost.php?p=2801168&postcount=86](http://ubuntuforums.org/showpost.php?p=2801168&postcount=86) ...)**


[*]Make and Install ndiswrapper
     [LIST=a]
     [*]cd /tmp/ndiswrapper-1.52
     [*]sudo make all
     [*]sudo make install
     [/LIST]


[*]Do **[COLOR="Red"]_NOT_[/COLOR]** Update /etc/network/interfaces with these lines:
[I][INDENT]     auto eth0
     iface eth0 inet dhcp

     auto wlan0
     iface wlan0 inet dhcp[/INDENT][/I]

[*]Install xp32-5.3.0.56-whql drivers
     [LIST=a]
     [*]cd /tmp
     [*]sudo ndiswrapper -i net5211.inf
     [*]sudo ndiswrapper -l (see item was installed)
     [/LIST]


[*]Load ndiswrapper and check if it worked.
    [LIST=a]
    [*]sudo modprobe ndiswrapper 
    [*]sudo dmesg (shows that the card is installed (hopefully)) 
    [/LIST]


[*] Do [COLOR="Red"]**NOT **[/COLOR]run "ndiswrapper -m"



**At this point, you should be able to use the Network Manager to configure your connection.** :guitar:


[*]Enable ndiswrapper at startup:
    [LIST=a]
    [*]sudo gedit /etc/init.d/ndiswrapper
    [*]add these lines:
[INDENT][I]#!/bin/sh
PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

case "$1" in
start)
        modprobe ndiswrapper
        ;;

*)
        echo "Usage: /etc/init.d/ndiswrapper {start}"
        exit 1
        ;;
esac

exit 0[/I][/INDENT]
    [*]sudo chmod 755 /etc/init.d/ndiswrapper
    [*][COLOR="Gray"]Create link in /etc/rc2.d/S41ndiswrapper --> /etc/init.d/ndiswrapper:[/COLOR]   sudo  ln -s  /etc/init.d/ndiswrapper  /etc/rc2.d/S41ndiswrapper
    [*]Reboot and see if you get on wireless automatically
    [/LIST]
[/LIST]

---

### Post by fhantazm on 2008-04-20
Thanks for the step by step! This came in very useful on my install!!

I should note there are others on the net posting instructions on using Mad WiFi, its has been my experience this does not work. The ndiswrapper technique stated above works wonderful.

---

### Post by AlanB66 on 2008-04-22
Thanks for the positive feedback.

I can't count the hours I lost trying to fiddle with MadWifi. So, when I got it working in almost no time with Ndiswrapper, I knew I had to share the good news.

Thanks again. Hope this helps even more people.

---

### Post by fhantazm on 2008-04-22
One other off-topic question. Is your paint starting to wear off where you place your wrists? Ive had this notebook for like 2 months and its starting to look terrible. I had a Gateway that did that once, but not this bad.

---

### Post by DarKnyht on 2008-04-26
Thanks for the extremely helpful post.  I was getting frustrated with my new laptop's performance until I rad your post.  Now it is running like a champ.

---

### Post by AlanB66 on 2008-04-27
Excellent. As long as one person found this useful and helpful, it's been well worth the time to post it.

Enjoy Ubuntu.

---

### Post by AlanB66 on 2008-05-02
Microphone Bug:

Submitted [[COLOR="Blue"]_Bug #225926_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/225926"), as I cannot get my microphone - internal or external - to work with the Gnome Sound Recorder.

NOTE: I do not have a F750 with a built-in webcam. So, if you're having issues with that, too, you'll need to submit a bug report for that, as I cannot attest to that condition/situation.

If when a solution comes for the microphone, I'll update it here. But, if you are having the same issues, you might comment on the aforementioned bug to show the developers of Ubuntu that it's not just me having problems with the microphone.

Thanks!

---

### Post by kcoxie on 2008-05-03
All I can say is THANK YOU!!!! I had tried madwifi posts to absolutely no avail. I am using a Toshiba A215 with same video setup and Atheros driver. 

This procedure worked perfectly. I have it printed out for future reference.

KSCoxie

---

### Post by schibros on 2008-05-08
Thanks AlanB66,

Got wireless working on the F750us with Gutsy 7.10. The steps were easy and straight forward. Everything is running just fine. As a matter of fact im using wireless to post this now. Ill just have to rboot and hope it comes up automatically. 

Thanks once again.

---

### Post by AlanB66 on 2008-05-08
You may have to disconnect your wired LAN cable for wireless to automatically start on boot-up.

Otherwise, the conflict will knock BOTH items out, I've seen.

---

### Post by AlanB66 on 2008-05-08
UPDATE: Enabling the TouchPad

[[COLOR="Blue"]_http://ubuntuforums.org/showpost.php?p=4911487&postcount=471_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4911487&postcount=471")

[INDENT]**[SIZE="4"]Synaptics Touchpad[/SIZE]**
[I][COLOR="Sienna"]1) Install GSynaptics (or KSynaptics if you use KDE) through Synaptic Package Manager

2) Edit xorg.conf to enable Touchpad app to use touchpad.
[INDENT]sudo gedit /etc/X11/xorg.conf[/INDENT]

3) Scroll down to the "Synaptic Touchpad" section and add the following line:
[INDENT]Option         "SHMConfig" "true"Save xorg.conf[/INDENT]

4) Xserver must be restarted for this to take effect. You can do this by pressing Ctrl-Alt-Backspace.[/COLOR][/I][/INDENT]

My wife is really big on using the double-click on the touchpad to drag items ... and I'm trying to make Ubuntu friendly for her so she one day says those magical words, "Please change my laptop from Windows to Linux." :lolflag:


UPDATE 1: I noticed that after my screen-saver kicks in, getting back into Ubuntu has disabled my double-click touchpad for the move capability. I'm going to investigate if this bug is already submitted and, if not, open one on this issue.

UPDATE 2: Cannot consistently reproduce this issue. No bug reporting, yet.

---

### Post by bapoumba on 2008-05-09
[http://ubuntuforums.org/showthread.php?p=4914261]("http://ubuntuforums.org/showthread.php?p=4914261")
Hello everyone, the first post of this thread has been copied out of the archive section to the new support area. Please continue there, thanks to AlanB66 :)

---

