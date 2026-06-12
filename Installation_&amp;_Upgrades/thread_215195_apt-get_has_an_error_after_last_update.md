---
title: "apt-get has an error after last update"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by LiquidStranger on 2006-07-13
hi everyone.
i just switched my laptop on and saw that there were some new updates, so i installed them. the problem is, since then i get error messages about samba:
> marc@ubuntop:~$ sudo apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Sie möchten wahrscheinlich »apt-get -f install« aufrufen, um dies zu korrigieren.
Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  samba: Hängt ab: samba-common (= 3.0.22-1ubuntu3) aber 3.0.22-1ubuntu3.1 ist installiert
E: Nichterfüllte Abhängigkeiten. Versuchen Sie, -f zu benutzen.

so i try apt-get install -f:

> marc@ubuntop:~$ sudo apt-get install -f
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Abhängigkeit werden korrigiert... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  samba
Empfohlene Pakete:
  smbldap-tools
Die folgenden Pakete werden aktualisiert:
  samba
1 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 2845kB Archiven geholt werden.
Nach dem Auspacken werden 0B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 144841 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von samba 3.0.22-1ubuntu3 (durch .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: Warnung - altes pre-removal-Skript wurde beendet mit Fehler-Status 102
dpkg - probiere stattdessen Skript aus dem neuen Paket ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: Fehler beim Bearbeiten von /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 Unterprozess neues pre-removal Skript gab den Fehlerwert 102 zurück
Fehler traten auf beim Bearbeiten von:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

and i get nowhere. any idea how to fix this?

---

### Post by Afishionado on 2006-07-13
Ouchie.

My German is rusty, but I understand the first error to say that samba-common has unfulfilled dependencies, and the second to say that the pre-removal script failed with exit status 102.

Of course, this line doesn't need to be translated to English:

invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba

---

### Post by rcnap on 2006-07-13
I'm getting the same thing...

mnapolitano@Satellite:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 103895 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bhdenterprises on 2006-07-13
Although my problem might not be of the same topic, I think I have an apt-get  error that cannot be repaired and I am very desperate to solve this.

You see I use an internal modem to connect to the Internet (in Windows) and it is a Conexant HSF modem. In order for it to work in Ubuntu (as suggested by linmodems.org) I install it using the linuxant FREE driver which only lets me to browse at 14kbps or I have to pay for it. Living in a third -world country like the Philippines, this seems to be impractical, especially that I have to pay in US dollars using a credit card which only about 10% of the entire Philippine population are privileged to have.

And so I install the free linuxant driver. Then I browse this Ubuntu forum using my very very very slow connection in the hopes that I can find a better driver that lets me surf the Internet at a full-blown 56kbps just like in Windows. And I found this thread: [http://www.ubuntuforums.org/showthread.php?t=190728]("http://www.ubuntuforums.org/showthread.php?t=190728").

It suggested two methods for the Conexant modems. Unfortunately the first method is a No-no for me because I cannot download the file as all I get is a 404 error in an Ubuntu wiki page. It seems that it is a broken link: [https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2]("https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2").

So I downloaded the second one from the FTP site. When I tried to build it, it returns error. When I checked, I found out that the default install of Ubuntu does not include the build-essential files (like make gcc and so forth). When I tried to install it using "apt-get install build-essential" it lets me download but it would take about 38 hours to completely download it (using a 14kbps connection and a 1000+b/s download rate). So I again browse the suggested FTP site and I saw there a file named conexant_192-1ubuntu-1_i386.deb so I downloaded it and my hopes were high that it would solve my modem problem. When I installed it using "dpkg -i conexant_192-1ubuntu-1_i386.deb" it returned some errors, I was not able to copy it, but I was not sure if it was not installed. So I tried it again, then some errors still. Now, I tried Synaptic and was able to see some packages there.

I removed the linuxant driver thinking that it might be the cause of the error. Tried to install the .deb package again but it returned this error:

~$ sudo apt-get install conexant_192-1ubuntu-1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it.

When I went back to Synaptic, it returned the same error and I could not see anymore the packages that I used to see. When I run Reload, it could read the main, restricted, uniververse files from the Web but it eventually return this error again and the packages are somewhat hidden.

So I installed the linuxant driver again so that I can install the build-essential packages using "apt-get install build-essential" from the universe repository. But again, it returned the error. I don't know anymore what to do. I guess my only hope is to reinstall Ubuntu in my computer... Please I need help...

---

### Post by NiksaVel on 2006-07-14
Hey all, I have the same problem with samba in the recent update:


> 
niksavel@darth:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 101002 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by NiksaVel on 2006-07-14
I tried removing it and reinstalling, but I cant even remove samba:

> niksavel@darth:~$ sudo apt-get remove samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 101001 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
niksavel@darth:~$



I also noticed that for some reason I've lost writing permissions to my fat32 partition after the new update.

---

### Post by NiksaVel on 2006-07-14
booting to previous kernel version restors the ability to work with the fat32 partition but the problem with the samba update remains the same

---

### Post by rcarring on 2006-07-14
To remove samba, you could try booting into the text based recovery console and then doing sudo apt-get remove samba-common. I think from reading the OP comment that this is the problem, notwithstanding the symlink error. I know that I managed to remove samba-common then install from an older alternate cd I had from Beta 2.

To the user from the Phillipines, perhaps you could order a live cd from shipit, since they do not charge for the media nor the shipping. You really want the alternate cd as this could act as a repository for most of Dapper, but I guess someone would have to mail you one as they don't send it out thru shipit.

---

### Post by NiksaVel on 2006-07-14
but wouldnt I than have ubuntu with no samba?  I kinda need it :)

---

### Post by carmelo on 2006-07-14
I had similar problem.

the problem is a incorrect link in /etc/rc2.d K09samba link to /samba instead ../init.d/samba

fix the link and retry.

see [http://www.ubuntuforums.org/showthread.php?t=214848](http://www.ubuntuforums.org/showthread.php?t=214848)

---

### Post by NiksaVel on 2006-07-14
well... I booted in recovery mode, done sudo apt-get install -f and now everything works fine :-D

---

### Post by LiquidStranger on 2006-07-14
> **rcarring said:**
> To remove samba, you could try booting into the text based recovery console and then doing sudo apt-get remove samba-common. I think from reading the OP comment that this is the problem, notwithstanding the symlink error. I know that I managed to remove samba-common then install from an older alternate cd I had from Beta 2.
[...]

Thanks alot, that helped. It didn't even remove samba but updated it correctly to the new version which was what i intended to do when the trouble began.
Sorry btw for forgetting that my Ubuntu is the german version. Should have thought of that and translated my errors.

---

