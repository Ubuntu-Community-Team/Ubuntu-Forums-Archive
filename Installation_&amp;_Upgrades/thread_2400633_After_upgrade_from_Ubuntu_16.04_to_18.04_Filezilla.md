---
title: "After upgrade from Ubuntu 16.04 to 18.04 Filezilla does not list files. (Worked prior"
date: 2018-09-08
forum: Installation &amp; Upgrades
---

### Post by arthurjohnston on 2018-09-08
[COLOR=#242729][FONT=Arial][CENTER][FONT=inherit]
[COLOR=#6A737C][FONT=inherit]0[/FONT][/COLOR]down vote[favorite]("https://askubuntu.com/questions/1072957/after-upgrade-from-ubuntu-16-04-to-18-04-filezilla-does-not-list-files-it-work#")
[/FONT][/CENTER]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit]Tried everything I could think of: (1) Changed /etc/apache2/apache2.conf to include Options +Indexes and "Require All Granted"; (2) Purged and reinstalled VSFTPD; and (3) Deleted and reinstalled Filezilla.[/FONT]
[FONT=inherit]The following is a capture of my session[/FONT]

[/FONT][/COLOR]
Tried everything I could think of: (1) Changed /etc/apache2/apache2.conf to include Options +Indexes and "Require All Granted"; (2) Purged and reinstalled VSFTPD; and (3) Deleted and reinstalled Filezilla.


The following is a capture of my session.  Anything special to v18.04 that was not required in 16.04?

Thanks in advance.

Arthur

```

Status: Connecting to 192.168.1.200:21...
Status: Connection established, waiting for welcome message...
Status: Initializing TLS...
Status: Verifying certificate...
Status: TLS connection established.
Status: Logged in
Status: Retrieving directory listing...
Command:    PWD
Response:   257 "/home/arthur" is the current directory
Command:    TYPE I
Response:   200 Switching to Binary mode.
Command:    PASV
Response:   227 Entering Passive Mode (192,168,1,200,169,214).
Command:    LIST
Error:  Connection timed out after 20 seconds of inactivity
Error:  Failed to retrieve directory listing
Status: Disconnected from server


```

---

