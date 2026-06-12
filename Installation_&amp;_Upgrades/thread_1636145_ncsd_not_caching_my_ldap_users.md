---
title: "ncsd not caching my ldap users"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by revzalot on 2010-12-02
I can getent my ldap users but ncsd is not caching them.  

Here's the error when I do an id of an ldap user named tony.  

```
nscd -d 
Thu 02 Dec 2010 03:43:32 PM PST - 2113: handle_request: request received (Version = 2) from PID 2121
Thu 02 Dec 2010 03:43:32 PM PST - 2113:     GETFDPW
Thu 02 Dec 2010 03:43:32 PM PST - 2113: provide access to FD 5, for passwd
Thu 02 Dec 2010 03:43:32 PM PST - 2113: handle_request: request received (Version = 2) from PID 2121
Thu 02 Dec 2010 03:43:32 PM PST - 2113:     GETPWBYNAME (tony)
Thu 02 Dec 2010 03:43:32 PM PST - 2113: Haven't found "tony" in password cache!

```id does work on my local users.

SOLVED:  I added ldapns.schema to enable host based authentication and the users before the schema upgrade caused this caching to stop.  I added a new after the schema upgrade and all is well.

---

