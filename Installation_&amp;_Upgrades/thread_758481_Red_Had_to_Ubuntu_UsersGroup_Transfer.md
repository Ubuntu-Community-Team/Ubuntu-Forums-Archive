---
title: "Red Had to Ubuntu: Users/Group Transfer"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by Overboardkiller on 2008-04-18
I have desided to change from Red hat to Ubutnu seeing as our server is nearing end of lease. I need to know can i copy the users from red hat to ubuntu ? 

I know the files that i need 

/etc/group
/etc/gshadow
/etc/shadow
/etc/passwd

can this be done? i havn't tried it as i do not want to stuff up the users then i will not be able to log in and stuff the new install up.

---

### Post by kidders on 2008-04-19
Hi there,

You're on the right track. Bear in mind that *overwriting* Ubuntu's user management files with your Red Hat ones is a bad idea though ... you should gather together the lines that refer to real people (normally UIDs & GIDs above 1000) and append them to Ubuntu's user configuration.

Essentially, you'll want to avoid deleting or reconfiguring system accounts (eg those used for hardware hotplugging, web/mail servers, etc.), or clogging your system up with redundant ones that won't get used.

---

### Post by DantePasquale on 2008-04-23
I have a related question. I lost my /etc/group and /etc/gshadow files somehow (ISPConfig?). I restored /etc/group from a backup, but /etc/gshadow was already trashed. How can I resync /etc/gshadow to /etc/group?

---

