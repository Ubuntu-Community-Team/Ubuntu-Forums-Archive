---
title: "http segmentation fault"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by spd106 on 2010-08-07
Hello,

For the last couple of weeks I've been unable to use apt-get and Evolution. Both fail with segmentation faults, but I can't seem get to the cause of the problem. I've tried running memtest, but it doesn't find any errors.

e.g.
```
:~$ sudo apt-get update
Get: 1 http://security.ubuntu.com lucid-security Release.gpg [189B]
E: Method http has died unexpectedly!                                         
E: Sub-process http received a segmentation fault.

```

Synaptic starts, but also fails to reload/update the package lists.

For Evolution it's slightly different
```
:~$ evolution
** (evolution:20533): DEBUG: mailto URL command: evolution %s
** (evolution:20533): DEBUG: mailto URL program: evolution
Segmentation fault

```

When I start it in gdb I get this
```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb3881b70 (LWP 20356)]
0x016fec7c in ?? () from /lib/tls/i686/cmov/libc.so.6
(gdb) back
#0  0x016fec7c in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0x016fe5c0 in strtoul () from /lib/tls/i686/cmov/libc.so.6
#2  0x005a74bd in ?? () from /usr/lib/libcamel-1.2.so.14
#3  0x00655788 in sqlite3_exec () from /usr/lib/libsqlite3.so.0
#4  0x005a7676 in camel_db_select () from /usr/lib/libcamel-1.2.so.14
#5  0x005a7e97 in camel_db_get_folder_uids_flags () from /usr/lib/libcamel-1.2.so.14
#6  0x0033b7b8 in camel_folder_summary_load_from_db () from /usr/lib/libcamel-provider-1.2.so.14
#7  0x02aba4a8 in camel_imap_summary_new () from /usr/lib/evolution-data-server-1.2/camel-providers/libcamelimap.so
#8  0x02aa9c83 in camel_imap_folder_new () from /usr/lib/evolution-data-server-1.2/camel-providers/libcamelimap.so
#9  0x02ab8364 in ?? () from /usr/lib/evolution-data-server-1.2/camel-providers/libcamelimap.so
#10 0x0035e218 in camel_store_get_folder () from /usr/lib/libcamel-provider-1.2.so.14
#11 0x026fdbb2 in mail_tool_uri_to_folder () from /usr/lib/evolution/2.28/libevolution-mail-shared.so.0
#12 0x026f3af3 in ?? () from /usr/lib/evolution/2.28/libevolution-mail-shared.so.0
#13 0x026f8aa0 in ?? () from /usr/lib/evolution/2.28/libevolution-mail-shared.so.0
#14 0x0166bcec in ?? () from /lib/libglib-2.0.so.0
#15 0x01669dcf in ?? () from /lib/libglib-2.0.so.0
#16 0x0086096e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0x0179ba4e in clone () from /lib/tls/i686/cmov/libc.so.6

```
I've tried re-installing these libraries and their dependencies via dpkg, but it makes no difference.

Any ideas? 

I don't like to give up so easily, but I'm considering a full wipe and re-install of Ubuntu. 

It might also be worth mentioning that I did get an error in the scheduled fsck run just a few days before this started.  But I've run fsck manually several times since then and it tells me everything's clean. I also had an issue with Python segfaults, but I was able to fix that by reinstalling python2.6-minimal.
 
I'm using Ubuntu 10.04 Netbook edition with EXT4 on a SSD with Discard (Trim) support enabled.

---

### Post by spd106 on 2010-08-11
Okay, looks like they weren't related issues.

I was able to download and reinstall the Apt packages and their dependencies from [http://archive.ubuntu.co](http://archive.ubuntu.co), which fixed Apt. For some reason I was unable to search for packages in lucid-updates at [http://packages.ubuntu.com](http://packages.ubuntu.com), which would have made life easier than having to match the latest version from the archive listings.

Then I deleted everything under ~/.evolution, which meant I could refresh the IMAP database from scratch.

---

