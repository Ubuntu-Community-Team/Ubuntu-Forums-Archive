---
title: "post-16.04.3 installation issue: cannot upgrade system or install software"
date: 2017-12-30
forum: Installation &amp; Upgrades
---

### Post by che-ffe-muc on 2017-12-30
I have installed ubuntu 16.04.3 more or less successfully. Here is my [boot-info]("https://paste.ubuntu.com/26273263/") for this: [https://paste.ubuntu.com/26273263/](https://paste.ubuntu.com/26273263/)
The issues I faced during installation can be found in this thread: [Installation of 16.04.3 stalls at "installing grub2" ...]("https://ubuntuforums.org/showthread.php?t=2381070")

After the installation and the reboot of the computer, the basic installation with WLAN, Office, Firefox is working, but now I  cannot install new software (i.e. VLC) or upgrade existing software  (Firefox) and I cannot install any ubuntu updates (i.e. security  updates). When I click on "Ubuntu Software Center" mouse pointer gives me circles some seconds, and then nothing.

_My key requirement is to get the machine in a stable state i.e. install updates, upgrade existing software, and install new software (VLC)._ 

What I did also:
1. starting again with LiveCD and running boot-repair (creating boot-info)
2. identified that UEFI/BIOS is version is 5RCN20WW (2017-05-22), newest version is 5RCN30WW (2017-10-17). Only Windows executable found. I do not know how to upgrade (but I do not think this is the real issue)
3. I ran boot-repair within my ubuntu session according to "https://help.ubuntu.com/community/Boot-Repair" (2nd option).
*sudo apt-get update *
gets this error message:
[I]DE "E: Konnte Sperre /var/lib/apt/lists/lock nicht bekommen - open (11: Die Ressource ist zur Zeit nicht verfügbar)"
EN "could not get lock for/from  /var/lib/apt/lists/lock - open (11: ressource is temporarily/currently not available)
[/I]Next I continue with
*sudo apt-get install -y boot-repair*
and it tells me that a different process is locking 
[I]DE "E: Konnte Sperre /var/lib/dpkg/lock nicht bekommen - open (11: Die Ressource ist zur Zeit nicht verfügbar)"
DE "E: Sperren des Administrationsverzeichnisses (/var/lib/dpkg/) nicht möglich, wird es von einem anderen Prozess verwendet?"
Transcript English: could not get lock for/from/on */var/lib/dpkg/lock - open (11: ressource temporarily/currently not available). Locking of administration folder ([I]/var/lib/dpkg*) not possible. is it used by another process?[/I] 
[/I]
Ok, next try (*ps -a) *gives me:

  PID TTY          TIME CMD
 3007 pts/2    00:00:00 frontend
 3013 pts/2    00:00:00 grub-efi-amd64.
 3109 pts/2    00:00:00 grub-install
 3136 pts/2    00:00:00 efibootmgr <defunct>
 3138 pts/2    00:00:00 efibootmgr
 4452 pts/17   00:00:00 ps

Any clues what to do next? Thank you for advice!
And even if I did a lot of try and error with terminal commands, I do not know a lot about it. In case you have some hints please explain or provide links to more info. Thank you!

---

### Post by QIII on 2017-12-30
Hello!

> E: Konnte Sperre /var/lib/apt/lists/lock nicht bekommen - open (11: Die Ressource ist zur Zeit nicht verfügbar)

This indicates that you have two package management systems open at the same time.  Close one or the other and try again.

Sometimes having your system set up to do automatic updates will lead to this.  For some period of time after logging in, the package manager will attempt to either update your package database and/or, depending on the settings, attempt to update the software.

After your next boot, don't open a package manager -- either GUI or in the terminal.  Wait perhaps 10 minutes.  Then attempt to update via the terminal and let us know if you get any errors and what they are.

---

### Post by che-ffe-muc on 2017-12-30
grub-install --version
grub-install (GRUB) 2.02~beta2-36ubuntu3.14

sudo apt-get upgrade
E: Der dpkg-Prozess wurde unterbrochen; Sie müssen manuell »sudo dpkg --configure -a« ausführen, um das Problem zu beheben.

sudo dpkg --configure -a
grub-efi-amd64 (2.02~beta2-36ubuntu3.14) wird eingerichtet ...
Installing for x86_64-efi platform.
<slowly blinking cursor, waiting now 30 minutes. How long may this take?>

dpkg: Fehler beim Bearbeiten des Paketes grub-efi-amd64 (--configure):
 Unterprozess installiertes post-installation-Skript wurde unterbrochen
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von grub-efi-amd64-signed:
 grub-efi-amd64-signed hängt ab von grub-efi-amd64 (= 2.02~beta2-36ubuntu3.14); aber:
  Paket grub-efi-amd64 ist noch nicht konfiguriert.

dpkg: Fehler beim Bearbeiten des Paketes grub-efi-amd64-signed (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 grub-efi-amd64
 grub-efi-amd64-signed

Translate:
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation-script was interrupted
dpkg: dependency problems hinder configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 (= 2.02~beta2-36ubuntu3.14); but:
  Package grub-efi-amd64 is not configured.

dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - stays unconfigured
error processing these packages:
 grub-efi-amd64
 grub-efi-amd64-signed

---

### Post by che-ffe-muc on 2017-12-30
upgrade system and install updates: problem solved! Thank you.
I'll create a separate thread for the dependency issue.

---

