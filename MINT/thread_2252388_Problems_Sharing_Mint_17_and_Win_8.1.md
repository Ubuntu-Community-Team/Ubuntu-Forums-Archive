---
title: "Problems Sharing Mint 17 and Win 8.1"
date: 2014-11-11
forum: MINT
---

### Post by ben124 on 2014-11-11
I had previously set up a shared folder on my Mint 17 machine and my Windows 8.1 lap top. Whenever my Mint machine would get shut down reconnecting the shared folders was kind of random - sometimes it would work right away, other times I'd have to restart the windows machine a few times. Typically I got an error message.

Now I've got a different problem. When I try to open my "Windows Network" file, I get essentially an empty folder. It's acting like it found the folder, but it's empty. I've changed no settings on either computer. I can't seem to get it working. Any help? I'm network illiterate and my Linux background is poor so simplicity would be helpful.

Thanks.

---

### Post by ben124 on 2014-11-11
wincycle@Lenovo-3000J ~ $ testparm -$
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Despicable.Me.2.2013.DVDRip.XviD-iNViNCiBLE]"
Processing section "[Muzak]"
Processing section "[Shared]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Linux Mint)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Despicable.Me.2.2013.DVDRip.XviD-iNViNCiBLE]
    path = /home/wincycle/Desktop/Download/Despicable.Me.2.2013.DVDRip.XviD-iNViNCiBLE
    guest ok = Yes

[Muzak]
    path = /home/wincycle/Desktop/Download/Muzak
    read only = No
    guest ok = Yes

[Shared]
    path = /home/wincycle/Desktop/Shared
    read only = No
    guest ok = Yes

---

