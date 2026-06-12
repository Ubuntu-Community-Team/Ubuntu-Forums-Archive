---
title: "Newbie problems - kubuntu asks for password when mounting drives"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by Istrebitel on 2010-05-29
Greetings.

I am a newbie to linux and i decided to try kubuntu after reading over the webs. I got lastest 10.04 release of kubuntu installed (downloaded yesterday). 

My current problem is that when i try to ask my windows drive (got dualboot, some hdd's are left for windows and one for linux) it asks for password. I've googled and everybody seems to fix it with editing some file called "org.freedesktop.devicekit.disks.policy" from /usr/share/...

But there is NO such file in my system! I have another file, org.freedesktop.udisks.policy, which contains something similar to that of the org.freedesktop.devicekit.disks.policy i am supposed to have.

Okay, then, i do all required changes (i switch auth_admin to yes in    <allow_active>yes</allow_active> block of Mount a device, Mount a system-internal device actions) but NOTHING! It still asks for password. Then somewhere on the webs i found that i should edit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla file and set i there to yes. It was already set to yes. 

Still i have yes set everywhere and i am promted for password over and over again to mount that drive.

So how can i finally make it not ask me for password to look at my drives? This is home pc used by 1 person so indeed i dont want it to bother me every time i wanna listen to my music...

my  /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla file:
```
[Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yes

[Change CPU Frequency scaling]
Identity=unix-group:admin
Action=org.gnome.cpufreqselector
ResultActive=yes

[Setting the clock]
Identity=unix-group:admin
Action=org.gnome.clockapplet.mechanism.*
ResultActive=yes

```

my /usr/share/polkit-1/actions/org.freedesktop.udisks.policy file:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>The udisks Project</vendor>
  <vendor_url>http://udisks.freedesktop.org/</vendor_url>
  <icon_name>drive-removable-media</icon_name>

  <action id="org.freedesktop.udisks.filesystem-mount">
    <description>Mount a device</description>
    <description xml:lang="da">Montér en enhed</description>
    <description xml:lang="de">Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.filesystem-check">
    <description>Check file system on a device</description>
    <description xml:lang="da">Check fil system for en enhed</description>
    <description xml:lang="de">Dateisystem auf einem Gerät prüfen</description>
    <message>Authentication is required to check the file system on the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at checke fil systemet på en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Dateisystem auf dem Gerät zu prüfen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.filesystem-check-system-internal">
    <description>Check file system of a system-internal device</description>
    <description xml:lang="da">Check fil system for en intern enhed</description>
    <description xml:lang="de">Dateisystem auf einem eingebauten Gerät prüfen</description>
    <message>Authentication is required to check the file system on the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at checke fil systemet på en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Dateisystem auf dem Gerät zu prüfen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.filesystem-unmount-others">
    <description>Unmount a device mounted by another user</description>
    <description xml:lang="da">Afmontér en enhed monteret af en anden bruger</description>
    <description xml:lang="de">Gerät eines anderen Benutzers aushängen</description>
    <message>Authentication is required to unmount devices mounted by another user</message>
    <message xml:lang="da">Autorisering er påkrævet for at afmontere enheder monteret af en anden bruger</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um ein Gerät auszuhängen, das ein anderer Benutzer eingehängt hat</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.filesystem-lsof">
    <description>List open files</description>
    <description xml:lang="da">Vis åbne filer</description>
    <description xml:lang="de">Offene Dateien anzeigen</description>
    <message>Authentication is required to list open files on a mounted file system</message>
    <message xml:lang="da">Autorisering er påkrævet for at liste åbne filer</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um offene Dateien auf einem eingehängen Dateisystem anzuzeigen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.filesystem-lsof-system-internal">
    <description>List open files on a system-internal device</description>
    <description xml:lang="da">Vis åbne filer på en intern enhed</description>
    <description xml:lang="de">Offene Dateien auf einem eingebauten Gerät anzeigen</description>
    <message>Authentication is required to list open files on a mounted file system</message>
    <message xml:lang="da">Autorisering er påkrævet for at liste åbne filer</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um offene Dateien auf einem eingehängen Dateisystem anzuzeigen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.drive-eject">
    <description>Eject media from a device</description>
    <description xml:lang="de">Medium aus Gerät auswerfen</description>
    <message>Authentication is required to eject media from the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at skubbe medie ud af en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Medium aus dem Gerät auszuwerfen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.drive-detach">
    <description>Detach a drive</description>
    <description xml:lang="de">Laufwerk trennen</description>
    <message>Authentication is required to detach the drive</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Laufwerk zu trennen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.change">
    <description>Modify a device</description>
    <description xml:lang="da">Modificér en enhed</description>
    <description xml:lang="de">Gerät ändern</description>
    <message>Authentication is required to modify the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at ændre en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät zu ändern</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.change-system-internal">
    <description>Modify a system-internal device</description>
    <description xml:lang="da">Modificér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät ändern</description>
    <message>Authentication is required to modify the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at ændre en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät zu ändern</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.drive-ata-smart-refresh">
    <description>Refresh ATA SMART data</description>
    <description xml:lang="da">Læs ATA SMART data</description>
    <description xml:lang="de">ATA-SMART-Daten aktualisieren</description>
    <message>Authentication is required to refresh ATA SMART data</message>
    <message xml:lang="da">Autorisering er påkrævet for at læse ATA SMART data</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um ATA-SMART-Daten zu aktualisieren</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.drive-ata-smart-selftest">
    <description>Run ATA SMART Self Tests</description>
    <description xml:lang="da">Kør ATA SMART selv checks</description>
    <description xml:lang="de">ATA-SMART-Selbsttest starten</description>
    <message>Authentication is required to run ATA SMART self tests</message>
    <message xml:lang="da">Autorisering er påkrævet for at køre ATA SMART selvcheck</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um ATA-SMART-Selbsttests zu starten</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.drive-ata-smart-retrieve-historical-data">
    <description>Retrieve historical ATA SMART data</description>
    <description xml:lang="da">Hent historisk ATA SMART data</description>
    <description xml:lang="de">Historische ATA-SMART-Daten holen</description>
    <message>Authentication is required to retrieve historical ATA SMART data</message>
    <message xml:lang="da">Autorisering er påkrævet for at hente historisk ATA SMART data</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um historische ATA-SMART-Daten zu holen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.luks-unlock">
    <description>Unlock an encrypted device</description>
    <description xml:lang="da">Åbn en krypteret enhed</description>
    <description xml:lang="de">Verschlüsseltes Gerät entsperren</description>
    <message>Authentication is required to unlock an encrypted device</message>
    <message xml:lang="da">Autorisering er påkrævet for at åbne en krypteret enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um ein verschlüsseltes Gerät zu entsperren</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.luks-lock-others">
    <description>Lock an encrypted device unlocked by another user</description>
    <description xml:lang="da">Lås en krypteret enhed åbnet af en anden bruger</description>
    <description xml:lang="de">Verschlüsseltes Gerät eines anderen Benutzers sperren</description>
    <message>Authentication is required to lock an encrypted device unlocked by another user</message>
    <message xml:lang="da">Autorisering er påkrævet for at låse en krypteret enhed åbnet af en anden bruger</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um ein verschlüsseltes Gerät zu sperren, das ein anderer Benutzer entsperrt hat</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.linux-md">
    <description>Configure Linux Software RAID</description>
    <description xml:lang="da">Konfigurér Software RAID</description>
    <description xml:lang="de">Linux Software-RAID konfigurieren</description>
    <message>Authentication is required to configure Linux Software RAID devices</message>
    <message xml:lang="da">Autorisering er påkrævet for at konfigurere RAID enheder</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um Linux Software-RAID-Geräte zu konfigurieren</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.linux-lvm2">
    <description>Configure Linux LVM2</description>
    <message>Authentication is required to configure Linux LVM2</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.cancel-job-others">
    <description>Cancel a job initiated by another user</description>
    <description xml:lang="da">Afbryd job påbegyndt af en anden bruger</description>
    <description xml:lang="de">Auftrag eines anderen Benutzers abbrechen</description>
    <message>Authentication is required to cancel a job initiated by another user</message>
    <message xml:lang="da">Autorisering er påkrævet for at afbryde et job påbegyndt af en anden bruger</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um einen Auftrag eines anderen Benutzers abzubrechen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.inhibit-polling">
    <description>Inhibit media detection</description>
    <description xml:lang="da">Undertryk medie detektion</description>
    <description xml:lang="de">Medium-Erkennung unterdrücken</description>
    <message>Authentication is required to inhibit media detection</message>
    <message xml:lang="da">Autorisering er påkrævet for at undertrykke medie detektion</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um Mediumerkennung zu unterdrücken</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.udisks.drive-set-spindown">
    <description>Set drive spindown timeout</description>
    <description xml:lang="de">Laufwerks-Zeitabschaltung setzen</description>
    <message>Authentication is required to configure drive spindown timeout</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um die Laufwerks-Zeitabschaltung zu konfigurieren</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>
  </action>

</policyconfig>

```

---

### Post by darkod on 2010-05-29
I'm not sure if it also works in kubuntu, but there is a package you can install for setting up automounting of ntfs partition(s).

sudo apt-get install ntfs-config

After installation it will be in System-Administration.

The first time you run it, it will show you all ntfs partition and ask which you want to mount, and whether to automount on every boot. But when you run it the first time, the partitions have to be UNMOUNTED. So, unmount them first (if mounted) and then run the software.

After that they will mount automatically and without needing a password.

---

### Post by Istrebitel on 2010-05-29
I know it i can do it from KDE gui(system settings -> advanced -> removable devices) but i want not the automount, but i want to remove the need of entering the password when i mount. 

Because i want to understand why the solution that works for everybody (changing admin_auth to yes) does not work for me at all... Otherwise i'm just running from the problem instead of solving it

---

### Post by kansasnoob on 2010-05-29
Not sure, but is this helpful:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Istrebitel on 2010-05-31
No no i understand how to mount or automount. Please, my problem is simple and it does not involve "how to mount" or "how to automount" at all.

---

I have just installed Kubuntu 10.04 and didnt change settings apart from grub or installing nvidia drivers. But when mounting a disk Kubuntu 10.04 will ask a password from me (a prompt will pop up from kdesudo). 

I want it not ask me a password every time i want to mount something. I want it just to mount it. I dont need this bit of security.

For that i googled i found that in Kubuntu 10.04 by default it shouldnt ask and most ppl actually are looking for a solution on how to make it ask the password, not how to prevent it from asking. But anyway, i found out how to do it - by changing the values in the files, which contents i supplied in the first post for clarification. I did the change that works for everybody, but STILL i am prompted for password when mounting.

My question is - how to make i so that i am not promted for password, now that i've done the changes to the files suggested in the webs (files are provided) and i am still being prompted for password (unlike most ppl for whom theese changes seemingly removed the prompt)

---

### Post by Istrebitel on 2010-05-31
Update: I've stumbled upon a forum entry where person shouts "DO NOT USE SUDO IN KUBUNTU IT WILL RUIN EVERYTHING" and gives a link to this [http://kubuntuforums.net/forums/index.php?topic=3089088.0](http://kubuntuforums.net/forums/index.php?topic=3089088.0)

In particular this part of the post is interesting to me: 
> You should never use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs. 

In fact, when i tried to follow the faqs and edit the files, i looked for a notepad analog (i forgot vi exists in any linux) and then i found kate. I launched it but it complained that it cannot make a backup of the file and cannot save the file when i did the edit. So i understood that it must be that i am trying to edit something i need root privelleges for. 

So i remembered stuff like su or sudo exists in linux. I googled it and learned how to use it in ubuntu (supply my password instead of root's) and it worked fine (sudo kate), although terminal complained about some files having incorrect owners (1000 instead of 0) and stuff, but it launched kate and it had let me edit the files all right.

Now may it have corrupted the whole thing, this use of sudo kate?  And what should i do to check if its the culprit, and how to reverse/fix it? 

I also used sudo kate to edit grub config files, can that do any harm to me in any way and should i do something asap about it?

PS: Could someone also explain why should i not use sudo, why should i use kdesudo, and when should i use sudo and why?

---

### Post by Istrebitel on 2010-05-31
Okay all those files are owned by root and since i only changed one of them, i cannot suspect running kate from sudo did the damage.

But now i stumbled upon this: [https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054)

Now this is exactly my situation! And it says something about a fix but HOW do i install that fix? 

PS: actually i made it work for me this way: the last post on the page i linked to there is a person saying this:
> Waiting for an update in karmic, as said by Doug, the patch for lucid also works for me:
Put the following in /var/lib/polkit-1/localauthority/10-vendor.d/org.freedesktop.DeviceKit.Disks.pkla
[No password required for admins]
 Identity=unix-group:admin
 Action=org.freedesktop.devicekit.disks.filesystem-*
 ResultActive=yes
And reboot. (reconnect ?)

The file did not exist and i created it and now IT WORKS! It doesnt bugger me with prompt to input password anymore!

---

### Post by Istrebitel on 2010-06-03
Okay, well, it has appeared again. I suppose it was not that anything has solved the problem, it was that i just used sudo somewhere and the password got remembered.

Now, i tried to use System Settings -> Advanced -> removable devices  and make those auto-mount but the result is i get numerous (4, one for each disk) password prompts right after login into kde

Now i tried to install the "sudo apt-get install ntfs-config"
The result is it had mounted those partitions at rubbish names

/dev/sdi1 on /media/DISK_IMG type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)
/dev/sdd1 on /media/M_PM_%M_QM__CM_PM_9_M_PM__RM_PM__M_PM_4M_PM__M_PM_2M_PM__M_PM_7M_PM_=M_QM__KM_PM_9 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/M_PM__M_QM__BM_PM___M_PM_7M_PM_0_M_PM__M_PM_8M_PM_:M_QM__CM_QM__A!? type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/M_PM___M_Q&#65533;M_PM__M_PM_3M_Q&#65533;M_PM_0M_PM__M_PM_=M_QM__KM_PM_9_M_PM__PM_QM__DM_PM_5M_Q&#65533;M_PM_8M_QM__AM_QM__B type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdj1 on /media/&#1055;&#1088;&#1080;&#1082;&#1083;&#1072;&#1076;&#1085;&#1086;&#1081; &#1052;&#1086;&#1079;&#1075;&#1086;&#1089;&#1086;&#1089; type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)   

well, what now? should i try to manually edit my fstab file to add "user" to the list of options to allow user mounting of the drives?
PS: It appears the ntfs-config already tweaked my /fstab file and added some entries with those rubbish names in it...

my fstab looks like this :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb1 :
UUID=f7aae94e-dfc7-41a4-bdd8-d3b9e5a4d769    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdd1 :
UUID=84983C23983C1660    /media/M_PM_%M_QM__CM_PM_9_M_PM__RM_PM__M_PM_4M_PM__M_PM_2M_PM__M_PM_7M_PM_=M_QM__KM_PM_9    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=A42C6CD12C6C9FD2    /media/M_PM__M_QM__BM_PM___M_PM_7M_PM_0_M_PM__M_PM_8M_PM_:M_QM__CM_QM__A!?    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=32C47895C4785D53    /media/M_PM___M_Q&#65533;M_PM__M_PM_3M_Q&#65533;M_PM_0M_PM__M_PM_=M_QM__KM_PM_9_M_PM__PM_QM__DM_PM_5M_Q&#65533;M_PM_8M_QM__AM_QM__B    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
#Entry for /dev/sdj1 :
UUID=7604309904305DF5    /media/&#1055;&#1088;&#1080;&#1082;&#1083;&#1072;&#1076;&#1085;&#1086;&#1081;\040&#1052;&#1086;&#1079;&#1075;&#1086;&#1089;&#1086;&#1089;    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb5 :
UUID=67209fde-281a-4b32-acfb-44dfa9c5bf6e    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0

```

What should i do to have a simple option to mount those ntfs drives without inputting any password, please?

---

### Post by Istrebitel on 2010-06-03
i tried to make my fstab file look like this to allow users mount the devices as i've read in faqs:

this is my fstab now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sdb1 :
UUID=f7aae94e-dfc7-41a4-bdd8-d3b9e5a4d769    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdd1 :
UUID=84983C23983C1660    /media/sdd1    ntfs-3g    user,users,defaults,noauto,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=A42C6CD12C6C9FD2    /media/sda1    ntfs-3g    user,users,defaults,noauto,locale=en_US.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=32C47895C4785D53    /media/sdc1    ntfs-3g    user,users,defaults,noauto,locale=en_US.UTF-8    0    0
#Entry for /dev/sdj1 :
UUID=7604309904305DF5    /media/sdj1    ntfs-3g    user,users,defaults,noauto,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb5 :
UUID=67209fde-281a-4b32-acfb-44dfa9c5bf6e    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0



```But it still asks for password. if i try mount /dev/sda1 as my user it says:

```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```
and if i remove noauto part it sometimes hangs at boot because it cannot mount /dev /sdj (this is an external drive connected via some strange port with an indication of a circle, surrounded by three squares, one square is solid filled and others only consist of two lines (like an = sign). It has to wait for this outer drive to identify itself (it means about 10 seconds more boot time and error messages at boot time like "drive is not ready wait or do a manual something")

---

### Post by Istrebitel on 2010-06-03
And on the suggested website it says:

> **Why can&#8217;t unprivileged**  users mount block devices? or
 **Why do I get &#8220;fusermount: option  blkdev is privileged&#8221; error?** Unprivileged block device mounts work only if all the below  requirements are met:
 
[LIST=1]
[*]ntfs-3g is compiled with integrated FUSE support
[*]the ntfs-3g binary is at least version 1.2506
[*]the ntfs-3g binary is set to setuid-root
[*]the user has access right to the volume
[*]the user has access right to the mount point
[/LIST]
 The root user can make an ntfs-3g binary setuid-root as shown below
chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g) In such case the driver will also be  able
 
[LIST]
[*]to fix common FUSE kernel module loading problems
[*]to create the required but sometimes incorrectly removed or missing  FUSE device file
[/LIST]
 Please note that using setuid-root can result unforeseen privilege  escalation and its usage is discouraged. Only the absolutely trusted  users must be granted such access. Below is an example how this can be  done for users in the ntfsuser group to be able to mount any NTFS volume  if they have also the needed volume access rights.  chown  root.ntfsuser $(which ntfs-3g)
chmod 4750 $(which ntfs-3g) The setuid-root ntfs-3g driver applies  the principle of least privilege during its lifetime as a safety  measure.
 [B]
Why don&#8217;t the &#8216;user&#8217; and &#8216;users&#8217;  options work in /etc/fstab?[/B] 
The &#8216;mount&#8217; command doesn&#8217;t invoke the ntfs-3g binary with the needed  privilege after it has checked and approved the user is entitled to  mount a given device on a specified mount point, hereby the user can&#8217;t  open the device he got the approval in /etc/fstab. This is a problem in  the &#8216;mount&#8217; utility.
 Solution: Use at least NTFS-3G 1.2506 with [setuid-root]("http://www.tuxera.com/community/ntfs-3g-faq/#useroption")  set and make sure the user has access rights to the volume and mount  point.


i dont quite understand what should i do out of all commands supported, but maybe someone could decypher it for me?
what should i do in order to finally be able to mount this stuff as my regular user????

---

### Post by Istrebitel on 2010-06-03
and when i tried the commands offered it said:
```
istrebitel@dom-tux:~$ mount /dev/sda1
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root.
Please see more information at http://ntfs-3g.org/support.html#unprivileged

```
but if i remove the setuid/setgid bit, this will bring me back to previous problem?

how do i rebuild ntfs-3g with integrated fuse support? why is it not included in kubuntu distributive by default (is it not a commonly wanted option)? or is it included but i dont know how to use it?

PS: I understand my questions may be simple and prove my lack of knowledge in the basics, but if i dont fully understand:
- how to correctly install something for which a "Stable Source Release" is provided. Especially when options are to be set
- how to get knowledge about what version of something (in this case, ntfs-3g) is installed in my system, and what kind of options were set when it was installed
- what exactly is ran when i type "make", what exactly is ran when i type "make install", how does it know where to put what files, and how to undo what it has done (because i had already corrupted one installation of kubuntu by simply doing an unsuccessfull make install of an x-fi driver package and then an alsa package)

Because if i get it right, my problem is either having an old ntfs-3g drivers (without builtin fuse) or uptodate drivers, but compiled with an option to use external fuse (which prevents allowing users mounting the ntfs partitions).

---

