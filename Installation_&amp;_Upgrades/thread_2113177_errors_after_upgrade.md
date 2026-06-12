---
title: "errors after upgrade"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by bluedalek on 2013-02-06
Hi All

I've just upgraded from 10.04 to 12.10 and am now getting errors when running apt-get anything.  I've spent a couple hours this afternoon trying to fix it, but so far, I've not found anything.

I've added all the details I can below:

```

tv@ubuserv:~$ sudo apt-get install python-software-properties pkg-config
[sudo] password for tv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
python-software-properties is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.99ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-37-generic (3.2.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-37-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic
cp: cannot stat `/lib/libacl*': No such file or directory
E: /usr/share/initramfs-tools/hooks/live failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.2.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-37-generic; however:
  Package linux-image-3.2.0-37-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.37.45); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up xbmc-live (2:11.0~git20120423.cd20772-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
   sed: can't read /etc/uxlaunch/uxlaunch: No such file or directory
dpkg: error processing xbmc-live (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-45-generic
cp: cannot stat `/lib/libacl*': No such file or directory
E: /usr/share/initramfs-tools/hooks/live failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.32-45-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.2.0-37-generic
 linux-image-generic
 linux-generic
 xbmc-live
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and it's not a disk space issue:

```

tv@ubuserv:~$ df
Filesystem                                              1K-blocks       Used  Available Use% Mounted on
rootfs                                                   38467220    6536936   29976236  18% /
none                                                       505452          4     505448   1% /dev
/dev/disk/by-uuid/8a33f9c7-453d-4b9f-af25-1c1ec4027ee4   38467220    6536936   29976236  18% /
tmpfs                                                      512992      68808     444184  14% /tmp
none                                                       102600        416     102184   1% /run
none                                                         5120          0       5120   0% /run/lock
none                                                       512992          0     512992   0% /run/shm
192.168.1.122:/mnt/storage/media                       8351293184 2732044960 5619248224  33% /mnt/media

```

and now when I try to re-add the xbmc repo, I get the following:

```

tv@ubuserv:~$ sudo apt-add-repository ppa:team-xbmc/unstable
Traceback (most recent call last):
  File "/usr/bin/apt-add-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 53, in <module>
    from ppa import AddPPASigningKeyThread, expand_ppa_line
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 31, in <module>
    import pycurl
ImportError: librtmp.so.0: cannot open shared object file: No such file or directory
tv@ubuserv:~$ sudo add-apt-repository ppa:team-xbmc/unstable
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 53, in <module>
    from ppa import AddPPASigningKeyThread, expand_ppa_line
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 31, in <module>
    import pycurl
ImportError: librtmp.so.0: cannot open shared object file: No such file or directory

```

If anyone can shed some light on what's gone wrong, it would be greatly appreciated!

---

### Post by lindend on 2013-09-20
I've run into the same problem after an upgraded from 10.04 to 12.04.  Were you ever able to solve this problem?

---

### Post by lindend on 2013-09-20
The solution described in the thread below solved the problem for me.  [http://ubuntuforums.org/showthread.php?t=2079130](http://ubuntuforums.org/showthread.php?t=2079130)

---

