---
title: "System conflict between WICD and Network Manager? Updates and Software dont work"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by Seine_Lordschaft on 2011-03-11
Hi,

I can't enter the Software Center any more or use the updates.

An error is displayed:

> E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages

'unsolvable problem'

'This signifies in general that connections between installed packages are not valid'


I recently installed Maverick Meerkat 10.10 (from the CD, using the whole harddisk). All went well, until I installed WICD from the Software-Center, and I think here is the root of my problem.

First, WICD did not find any wireless LANS. I expected conflict with Network-Manager, but which can be operated simultaneously with WICD. Therefore I deleted and-reinstalled both programms several times. But no WLAN with WICD.

A point worth mentioning is that I could not uninstall WICD using the Terminal after installing if from the Software-Center. I could only uninstall it in the Software-Center.

I thought quite a while about my Network controller, but the necessary drivers and firmware had been installed.

> 
02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

The Fwcutter driver is installed correctly.

IWconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode: Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit: 7   RTS thr:off   Fragment thr:off
          Power Management: off



Finally, I realised that Network-Manager found the available wireless networks. However I attempted only at the end to connect me because Network-Manager was until then unable to connect with my WPA enterprise WLAN with certificate. But, surprise, it was not only possible to connect, but even worked better than with the older distribution (no copying of the certicicate as root into WICD's templates-folder etc.)

That way my system worked fine for about a week, and I didn't change anything. Then, from one day to the other, appears this error described above.

It seems a serious system conflict. I can't start the update-manager anymore and also the software-center doesn't start. I assume it's because of WICD which I had installed from the Software-Center at the end but did not remove when Network-Manager started operating my WLAN.

Trying to remove WICD using the terminal, the following message appears:

> E: Encountered a section with no package: header
E: The package list or status file could not be opened.

Trying to repair the update-manager, the following happens:

> bl@Speicher:~$ sudo apt-get check
[sudo] password for bl: 
Sorry, try again.
[sudo] password for bl: 
Paketlisten werden gelesen... Fehler!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: Die Paketliste oder die Statusdatei konnte nicht eingelesen oder geöffnet werden.
bl@Speicher:~$ sudo apt-get upgrade -f
Paketlisten werden gelesen... Fehler!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: Die Paketliste oder die Statusdatei konnte nicht eingelesen oder geöffnet werden.
bl@Speicher:~$ 
bl@Speicher:~$ sudo apt-get dist-upgrade -f
Paketlisten werden gelesen... Fehler!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-i386_Packages
E: Die Paketliste oder die Statusdatei konnte nicht eingelesen oder geöffnet werden.
bl@Speicher:~$ sudo dkpg --configure -a
sudo: dkpg: command not found

Now, both the network-manager and wicd don't find WLANs. However, I can still connect by wired LAN.

Some curiousities were that the screen had become very dark when the error occurred first. But that could be corrected manually by just turning it brighter again. Another curiousity is that the time changed to January 1st, 2004.

Ah, and by the way, deactivating WICD in the autostart had no effect.

I am quite hopeful that opening the software-center and uninstalling WICD will solve my conflict. Can anyone help me how to do that? Please don't tell me that I have to reinstall it all...

---

### Post by zvacet on 2011-03-11
I´m not sure if this solve your problem,but you can remove wicd from **system>administration>synaptic**.Mark wicd for complete removal.

---

### Post by Seine_Lordschaft on 2011-03-11
thanks for the advice, but the same error message as when opening the update-messenger appears:

> E:Encountered a section with no Package: header

can't open Synaptic... :(

---

### Post by zvacet on 2011-03-12
```
sudo dpkg --remove --force-remove-reinstreq wicd
```

---

### Post by Seine_Lordschaft on 2011-03-15
that command worked but wicd stayed in the panel and menu

would still run if you click on it

no way to open the updates or software center

New install was the only way out - this time without wicd. Hope it holds on.

---

