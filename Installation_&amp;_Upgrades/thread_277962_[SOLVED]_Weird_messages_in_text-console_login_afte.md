---
title: "[SOLVED] Weird messages in text-console login after upgrade Breezy-&amp;gt;Dapper"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by jdackle on 2006-10-15
Hi,

I've only upgraded to Dapper from Breezy about a couple weeks ago. Like the result of course. :)

But I get these weird messages when logging into a text-console.
Just after entering the username and before being asked for the password I get this:
```
configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)
```
Whjat is this about? How do I fix it?

Thanks in advance,

---

### Post by jdackle on 2006-10-18
FIXED!

Got this fixed and thought I'd post it here for whoever might need it too...

I looked for files in */etc* containing the given items and found only one: *login.defs*
Checked to see if there were other similar files and found one other: *login.defs.dpkg-dist* (remember this one did NOT contain those items)
Looked at the diff between the two files and all I could find, aside from the probelmatic items, was differences in the commented lines (#) and in style (e.g. tabs instead of spaces).

So I replaced *login.defs* with *login.defs.dpkg-dist* and got it FIXED. :)

---

### Post by cesine on 2006-12-06
i have the same problem, but my files dont date from my upgrade (061202), rather the login.defs.dpkg-dist is dated 060711 but the login.defs is 060206.

replacing the files didnt remove the error messages :( 

i'm also getting errors from mysql, it has stopped running twice since the upgrade. now i tried stopping it

# ./mysqladmin -u username -p shutdown

that worked, but this doesnt:

 # mysqld -start
mysqld: Can't read dir of 'art/' (Errcode: 2)
mysqld: Can't create/write to file 'art/ib3gLMec' (Errcode: 2)
061206 14:56:53  InnoDB: Error: unable to create temporary file; errno: 2
061206 14:56:53 [ERROR] Can't init databases
061206 14:56:53 [ERROR] Aborting

061206 14:56:53 [Note] mysqld: Shutdown complete

 #      

this also doesnt work:
# mysqld -restart
061206 14:57:39 [ERROR] chroot: No such file or directory
061206 14:57:39 [ERROR] Aborting

Segmentation fault
#


anyone know if these errors are related to the following replacement i got while upgrading from breezy badger to dapper drake?
----------------------------------------------------------

(Reading database ... 83002 files and directories currently installed.)
Preparing to replace base-passwd 3.5.10 (using .../base-passwd_3.5.11_i386.deb)
...
Unpacking replacement base-passwd ...
Setting up base-passwd (3.5.11) ...

update-passwd has found some differences between your system accounts
and the current Debian defaults. It is advisable to allow update-passwd
to change your system; without those changes some packages might not work
correctly.  For more documentation on the Debian account policies please
see /usr/share/doc/base-passwd/README.

The list of proposed changes is:

Changing GECOS of www-data from "Our servers name" to "www-data".
Would commit 1 changes

It is highly recommended that you allow update-passwd to make these changes
(a backup file of modified files is made with the extension .org so you can
always restore the current settings).

May I update your system? [Y/n] y
Okay, I am going to make the necessary updates now
Changing GECOS of www-data from "Our servers name" to "www-data".
1 changes have been made, rewriting files
Writing passwd-file to /etc/passwd
Writing shadow-file to /etc/shadow
Writing group-file to /etc/group

---

