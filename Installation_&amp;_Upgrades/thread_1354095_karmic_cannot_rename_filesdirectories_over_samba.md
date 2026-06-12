---
title: "karmic cannot rename files/directories over samba"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by gadg3ts on 2009-12-13
So, the other main problem I've been having since upgrading my home server to 9.10 is that samba seems to be having a bit of a fit.
Worked perfectly on 9.04, have same config files on 9.10.

While I can copy files to the samba shares and copy/duplicate files already on the same - showing that file creation is fine, attempting to rename a file or directory gives me a "File Access Denied" error from whichever client I attempt that from (XP, Win7, OSX or even another Ubuntu machine).

Tailing the relevant samba logs when trying a rename doesn't show anything and my config files are the same, so what has changed between 9.04 & 9.10 to cause this behaviour?..

files are created 766 and owned by my user, which is the same un/pw everywhere.
I'm guessing it's some internal permissions thing that has changed, although I was hoping for an easy answer instead of having to run samba with debug & using strace etc.

main bits of smb.conf:
[global]
        workgroup = INTRANET
        server string = Samba Server
        security = SHARE
        ssl CA certDir = /etc/ssl/certs
        log file = /var/log/samba/samba.%m
        max log size = 50
        dns proxy = No
        wins support = Yes
        guest account = sean
        hosts allow = 10.0.0.
        domain master = Yes
        local master = Yes
        preferred master = Yes
        printcap name = cups
        printing = cups
        load printers = yes
       
# all the shares are set the same as this one.
[storage]
        path = /mnt/storage
        read only = No
        readonly = No # added for testing
        create mask = 0777
        directory mask = 0777
        guest only = Yes
        guest ok = Yes
        writeable = Yes # added for testing

---

### Post by mtecknology on 2009-12-13
<quote>
guest only = Yes
guest ok = Yes
</quote>

Change these to No. This will force authentication to occur. If this doesn't work; make sure you're logging and go look at the logs.

---

### Post by gadg3ts on 2009-12-22
I removed them from one share and restarted samba.
Had to reconnect to the share as (obviously) now it required authentication, so now I can rename/delete files.
Which then bears the question.
"Why?"
If it's supposed to map unauthenticated users to the user I specify (ie me), then why should it have stopped working after the upgrade?..
I shall try debug level = 3 and see what it gives me...

---

