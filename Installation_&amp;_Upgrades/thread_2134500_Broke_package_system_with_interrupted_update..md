---
title: "Broke package system with interrupted update."
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by awclemen on 2013-04-11
Hello forum folks,

It seems I have broke my package system when it got stuck during an aptitude update and I interrupted it.  I have a script I run to do the update:

```
#!/bin/bash
tmpfile=$(mktemp)

echo "aptitude update" >> ${tmpfile}
aptitude update >> ${tmpfile} 2>&1
echo "" >> ${tmpfile}
echo "aptitude dist-upgrade" >> ${tmpfile}
aptitude -y dist-upgrade >> ${tmpfile} 2>&1
echo "" >> ${tmpfile}
echo "aptitude clean" >> ${tmpfile}
aptitude clean >> ${tmpfile} 2>&1

mail -s "Aptitude Updae cron $(date)" awclemen@blahblahblah.com < ${tmpfile}
rm -f ${tmpfile}

```

I ran it from the command line however, there was a prompt in it querying about the grub configuration.  Since I could not reach the prompt (or more correctly, didn't know how to), I killed the script.  However, now my package system is a total mess.  Attempts at "apt-get -f install" and "dpkg --configure -a" do not clear out the problem.  Here is what happens when I run them:

```
# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-image-2.6.32-45-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 0 B/4,306 B of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-image-3.2.0-38-generic-pae (3.2.0-38.61) ...
Internal Error: Could not find image (/boot/vmlinuz-3.2.0-38-generic-pae)
dpkg: error processing linux-image-3.2.0-38-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-38-generic-pae; however:
  Package linux-image-3.2.0-38-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.38.46); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.38.46); however:
  Version of linux-headers-generic-pae on system is 3.2.0.40.48.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
No apport report written because MaxReports is reached already
                                                               linux-image-server depends on linux-image-generic-pae; however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-generic-pae; however:
  Package linux-generic-pae is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-3.2.0-38-generic-pae
 linux-image-generic-pae
 linux-generic-pae
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
# dpkg --configure -a
Setting up linux-image-3.2.0-38-generic-pae (3.2.0-38.61) ...
Internal Error: Could not find image (/boot/vmlinuz-3.2.0-38-generic-pae)
dpkg: error processing linux-image-3.2.0-38-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.38.46); however:
  Version of linux-headers-generic-pae on system is 3.2.0.40.48.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-generic-pae; however:
  Package linux-generic-pae is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-38-generic-pae; however:
  Package linux-image-3.2.0-38-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-generic-pae; however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-38-generic-pae
 linux-generic-pae
 linux-server
 linux-image-generic-pae
 linux-image-server

```

I was able to clear the locks in /var/lib/dpkg/lock and /var/cache/debconf/config.dat, but this has not helped the problem.  I believe I have adequate room in my /boot directory:

```
y# df -h -a
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/PMPORTALTWO-root  532G   28G  478G   6% /
proc                             0     0     0    - /proc
sysfs                            0     0     0    - /sys
none                             0     0     0    - /sys/fs/fuse/connections
none                             0     0     0    - /sys/kernel/debug
none                             0     0     0    - /sys/kernel/security
udev                          997M   12K  997M   1% /dev
devpts                           0     0     0    - /dev/pts
tmpfs                         403M  760K  402M   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                         1007M  144K 1007M   1% /run/shm
/dev/sda5                     221M  139M   71M  67% /boot
binfmt_misc                      0     0     0    - /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon              0.0K  0.0K  0.0K    - /var/lib/lightdm/.gvfs

```

Not sure where to go from here.  Thanks for your help in advance!

---

### Post by awclemen on 2013-04-11
Well, I was able to fix the vmlinuz-3.2.0-38-generic-pae error by bringing that file over from another server, now when I run apt-get -f install, I get this:

t# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-image-2.6.32-45-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,306 B of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 294585 files and directories currently installed.)
Preparing to replace linux-image-generic-pae 3.2.0.38.46 (using .../linux-image-generic-pae_3.2.0.40.48_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Setting up linux-image-generic-pae (3.2.0.40.48) ...
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.38.46); however:
  Version of linux-image-generic-pae on system is 3.2.0.40.48.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.38.46); however:
  Version of linux-headers-generic-pae on system is 3.2.0.40.48.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-generic-pae; however:
  Package linux-generic-pae is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    Errors were encountered while processing:
 linux-generic-pae
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by awclemen on 2013-04-11
I may have found the fix [here]("http://askubuntu.com/questions/251862/broken-count-error-linux-generic-pae-depends-linux-image-generic-pae-3-2").  This is the result:

# dpkg --remove linux-generic-pae
(Reading database ... 294584 files and directories currently installed.)
Removing linux-generic-pae ...
# apt-get install linux-generic-pae
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-image-2.6.32-45-generic-pae
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,728 B of archives.
After this operation, 32.8 kB of additional disk space will be used.
Selecting previously unselected package linux-generic-pae.
(Reading database ... 294582 files and directories currently installed.)
Unpacking linux-generic-pae (from .../linux-generic-pae_3.2.0.40.48_i386.deb) ...
Setting up linux-generic-pae (3.2.0.40.48) ...
Setting up linux-server (3.2.0.38.46) ...

apt-get -f install and dpkg --configure -a now run without error.  Let see if she reboots.....

---

### Post by awclemen on 2013-04-11
well, that fixed it.

---

