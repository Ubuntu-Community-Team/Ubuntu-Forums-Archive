---
title: "clamd error while starts - ERROR: setgroups() failed."
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by kosc on 2010-03-19
I have problem starting clamd
It's unable to execute setgroups()
/etc/group , /etc/password files are world readable

any idea how to fix/debug ?


*************************************************
here is output after starting clamd:
sudo clamd
[COLOR="DarkRed"]ERROR: setgroups() failed.[/COLOR]

here is strace **clamd **output:
...
[COLOR="DarkRed"]open("/etc/passwd", O_RDONLY|0x80000 /* O_??? */) = 3
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
_llseek(3, 0, [0], SEEK_CUR)            = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=1616, ...}) = 0
mmap2(NULL, 1616, PROT_READ, MAP_SHARED, 3, 0) = 0xb7f6d000
_llseek(3, 1616, [1616], SEEK_SET)      = 0
munmap(0xb7f6d000, 1616)                = 0
close(3)                                = 0
setgroups32(1, [120])                   = -1 EPERM (Operation not permitted)
write(2, "ERROR: setgroups() failed.\n", 27ERROR: setgroups() failed.) = 27
exit_group(1)                           = ?
Process 29002 detached[/COLOR]

ls -al **/etc/group**:
[COLOR="DarkRed"]-rw-r--r-- 1 root root 1013 2010-03-19 11:38 /etc/group[/COLOR]

ls -al **/etc/passwd**:
[COLOR="DarkRed"]-rw-r--r-- 1 root root 1616 2010-03-05 12:39 /etc/passwd[/COLOR]

**/etc/passwd**:
[COLOR="DarkRed"]clamav:x:108:120::/var/lib/clamav:/bin/false[/COLOR]

**/etc/group**:
[COLOR="DarkRed"]clamav:x:120:[/COLOR]

---

### Post by dino99 on 2010-03-19
into console, run: ubuntu-bug clamav-daemon

watch the details when the rapport is done (before sending it) and add what you have in your post above if the rapport have not it.

What you can do then, (after you have sent the bug-report), is to go into synaptic and:

- completly remove every package installed about clam*
- then reinstall those packages : clamtk, freshmeat and clamav-daemon
(all the dependencies might be installed, but you can list those installed)

- reboot
- run again clamd to see if the problem still exist.

note: you have not specified which distro you use nor gnome or else. Have you some usefull info logged into /var/log or .xsession-errors ?

and finally dont forget to run:

sudo dpkg-reconfigure clamav-base

---

### Post by kosc on 2010-03-19
all clam* packages have been removed.

manually deleted /etc/clamav directory

ubuntu server (command line only) have been restarted

installing clamav-daemon:
[COLOR="DarkRed"]**apt-get install clamav-daemon**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  clamav-base clamav-freshclam libclamav6
Suggested packages:
  clamav-docs daemon libclamunrar6
Recommended packages:
  clamav
The following NEW packages will be installed:
  clamav-base clamav-daemon clamav-freshclam libclamav6
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/28,5MB of archives.
After this operation, 36,2MB of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
Selecting previously deselected package clamav-base.
(Reading database ... 39529 files and directories currently installed.)
Unpacking clamav-base (from .../clamav-base_0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3_all.deb) ...
Selecting previously deselected package libclamav6.
Unpacking libclamav6 (from .../libclamav6_0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3_i386.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3_i386.deb) ...
Selecting previously deselected package clamav-daemon.
Unpacking clamav-daemon (from .../clamav-daemon_0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3_i386.deb) ...
Setting up clamav-base (0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3) ...

Setting up libclamav6 (0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3) ...

Setting up clamav-freshclam (0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3) ...
Replacement succeeded for "/usr/bin/freshclam".
 * Starting ClamAV virus database updater freshclam
   ...done.

Setting up clamav-daemon (0.96~rc1+dfsg-0ubuntu1~hardy1~ppa3) ...
Replacement succeeded for "/usr/sbin/clamd".
 * Starting ClamAV daemon clamd
WARNING: Ignoring deprecated option MailFollowURLs at line 39
   ...done.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[/COLOR]

same error remains:
[COLOR="DarkRed"]/usr/sbin/clamd
WARNING: Ignoring deprecated option MailFollowURLs at line 39
ERROR: setgroups() failed[/COLOR]


ubuntu-bug requires to send something online and this command line browsers are horror to say at least :(
I'm unable to get any response to send it here.

---

### Post by mjb2600 on 2010-04-20
I'm having this same error when doing a fresh install of 0.96 and haven't been able to figure out a solution.

Anyone have any ideas?

---

### Post by glenstewart on 2010-09-07
In /etc/clamav/clamd.conf

delete the line:  MailFollowURLs [true|false]

This fix worked for me, and is per advice at [http://blog.gmane.org/gmane.mail.getmail.user/month=20100501](http://blog.gmane.org/gmane.mail.getmail.user/month=20100501)

---

