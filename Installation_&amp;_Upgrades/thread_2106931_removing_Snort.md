---
title: "removing Snort"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by drazenmozart on 2013-01-20
hi,

months before i installed snort-mysql(engine-2.9.2) with apt-get. A few days ago i tried to install a newer version (snort-2.9.4 tarball) from source. 
But i did something stupid. I rm -rf the old snort directories without removing the packages with apt-get remove(if i try this now,it cannot find the directories), and then installed the new snort version. As a result, when i start snort, the old version gets started.

How can i completely remove the old snort version??

thanks in advance!!

---

### Post by iponeverything on 2013-01-20
apt-get install --reinstall the package, then remove it.

---

### Post by drazenmozart on 2013-01-20
tried it but got this error:

"After this operation, 0 B of additional disk space will be used.
Get:1 [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) precise/universe snort-mysql i386 2.9.2-3ubuntu1 [709 kB]
Fetched 709 kB in 1s (449 kB/s)      
Preconfiguring packages ...
Selecting previously unselected package snort-mysql.
(Reading database ... 239914 files and directories currently installed.)
Preparing to replace snort-mysql 2.9.2-3ubuntu1 (using .../snort-mysql_2.9.2-3ubuntu1_i386.deb) ...
/etc/init.d/snort: 65: cd: can't cd to /etc/snort
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
usermod: no changes
Unpacking replacement snort-mysql ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up snort-mysql (2.9.2-3ubuntu1) ...
snort: not updating /etc/snort/snort.debian.conf; file does not exist
snort: not updating /etc/snort/database.conf; file does not exist
chown: cannot access `/etc/snort/snort.conf': No such file or directory
dpkg: error processing snort-mysql (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already

                                                              Errors were encountered while processing:
 snort-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)"

---

### Post by iponeverything on 2013-01-20
reinstall snort in addition to snort-mysql

---

### Post by drazenmozart on 2013-01-20
root@alex-VirtualBox:/home/alex# **apt-get install --reinstall snort**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  snort-doc
The following packages will be REMOVED:
  snort-mysql
The following NEW packages will be installed:
  snort
0 upgraded, 1 newly installed, 1 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 0 B/696 kB of archives.
After this operation, 45.1 kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 239913 files and directories currently installed.)
Removing snort-mysql ...
 * Stopping Network Intrusion Detection System  snort                            *  - No running snort instance found
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Selecting previously unselected package snort.
(Reading database ... 239894 files and directories currently installed.)
Unpacking snort (from .../snort_2.9.2-3ubuntu1_i386.deb) ...
usermod: no changes
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up snort (2.9.2-3ubuntu1) ...
 * Stopping Network Intrusion Detection System  snort                            *  - No running snort instance found
 * Starting Network Intrusion Detection System  snort                    [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by iponeverything on 2013-01-20
looks like it removed snort-mysql you should now be able to do:

sudo apt-get remove --purge snort snort-mysql

---

### Post by drazenmozart on 2013-01-20
root@alex-VirtualBox:/home/alex# **apt-get remove --purge snort snort-mysql**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  snort-rules-default libdumbnet1 snort-common oinkmaster libprelude2
  snort-common-libraries
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  snort* snort-mysql*
0 upgraded, 0 newly installed, 2 to remove and 21 not upgraded.
1 not fully installed or removed.
After this operation, 1,794 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 239912 files and directories currently installed.)
Removing snort ...
 * Stopping Network Intrusion Detection System  snort                            *  - No running snort instance found
Purging configuration files for snort ...
Removing snort-mysql ...
Purging configuration files for snort-mysql ...
The group `snort' does not exist.
dpkg: error processing snort-mysql (--purge):
 subprocess installed post-removal script returned error exit status 128
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 snort-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)


just can't understand..

---

### Post by iponeverything on 2013-01-21
is this worked out?

If not, create a "snort" group using the groupadd command -- then try again.

At this point, I am sure no one needs to explain what problems caused by manual program removal..

---

