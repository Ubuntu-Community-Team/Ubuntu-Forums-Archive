---
title: "How do I remove failed update files?"
date: 2022-12-23
forum: Installation &amp; Upgrades
---

### Post by robert48 on 2022-12-23
Hello

When I try to run Software Updater I get an error message 'Package operation failed'

The files concerned are:-

[SIZE=5][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291444&stc=1[/IMG][/SIZE][IMG]https://ubuntuforums.org/attachment.php?attachmentid=291445&stc=1[/IMG]

How can I remove these please and check/fix the system? Ubuntu AMD64bit Jelly

---

### Post by ajgreeny on 2022-12-23
Use the terminal to run command
***sudo apt update && apt list --upgradable***
and copy back here the full output text. Please use code tags as shown in my signature below.

This will show us a lot more detail of the current situation than a GUI method.

---

### Post by robert48 on 2022-12-23
> **ajgreeny said:**
> Use the terminal to run command
***sudo apt update && apt list --upgradable***
and copy back here the full output text. Please use code tags as shown in my signature below.

This will show us a lot more detail of the current situation than a GUI method.

```
$ sudo apt update && apt list --upgradeable
```
returns:-
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease    
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease  
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease               
Hit:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-security InRelease             
Hit:6 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-security InRelease
Hit:7 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-updates InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
Listing... Done
libnih-dbus1/jammy 1.0.3-12build1 amd64 [upgradable from: 1.0.3-6ubuntu2]
libnih1/jammy 1.0.3-12build1 amd64 [upgradable from: 1.0.3-6ubuntu2]

---

### Post by ajgreeny on 2022-12-23
My apologies, I should have added the command ```
sudo apt full-upgrade
``` to the original so run that now and I suspect will simply show that the two packages have been held back (temporarily) as a result of **phased updates**.

I never use the Software Updater so I do not know for sure but it appears that SU does not override phased updates.

Just ignore those two packages for the moment and they will soon update just like everything else.
See [https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them) for some more details of this.

---

### Post by robert48 on 2022-12-23
> **ajgreeny said:**
> My apologies, I should have added the command ```
sudo apt full-upgrade
``` to the original so run that now and I suspect will simply show that the two packages have been held back (temporarily) as a result of **phased updates**.

I never use the Software Updater so I do not know for sure but it appears that SU does not override phased updates.

Just ignore those two packages for the moment and they will soon update just like everything else.
See [https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them) for some more details of this.

```
sudo apt full-upgrade
```
returned:-
[PHP]Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
#
# News about significant security updates, features and services will
# appear here to raise awareness and perhaps tease /r/Linux ;)
# Use 'pro config set apt_news=false' to hide this and future APT news.
#
The following packages will be upgraded:
  libnih-dbus1 libnih1
2 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/63.0 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing archive /var/cache/apt/archives/libnih-dbus1_1.0.3-12build1_amd64.deb (--unpack):
 package libnih-dbus1:amd64 (1.0.3-12build1) with field 'Multi-Arch: no' is not co-installable with libnih-dbus1 which has multiple installed instances
dpkg: error processing archive /var/cache/apt/archives/libnih1_1.0.3-12build1_amd64.deb (--unpack):
 package libnih1:amd64 (1.0.3-12build1) with field 'Multi-Arch: no' is not co-in
stallable with libnih1 which has multiple installed instances
Errors were encountered while processing:
 /var/cache/apt/archives/libnih-dbus1_1.0.3-12build1_amd64.deb
 /var/cache/apt/archives/libnih1_1.0.3-12build1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/PHP]

I don't understand the dpkg: error statements but if these are due to updates being held back for now then that is a learning point for me. Thank you very much for your time and Merry Christmas to you and yours!

---

### Post by ajgreeny on 2022-12-23
I think from that output
```
dpkg:*error*processing*archive*/var/cache/apt/archives/libnih-dbus1_1.0.3-12build1_amd64.deb*(--unpack):
*package*libnih-dbus1:amd64*(1.0.3-12build1)*with*field*'Multi-Arch:*no'*is*not*co-installable*with*libnih-dbus1*which*has*multiple*installed*instances
dpkg:*error*processing*archive*/var/cache/apt/archives/libnih1_1.0.3-12build1_amd64.deb*(--unpack):
*package*libnih1:amd64*(1.0.3-12build1)*with*field*'Multi-Arch:*no'*is*not*co-in
stallable*with*libnih1*which*has*multiple*installed*instances
Errors*were*encountered*while*processing:
*/var/cache/apt/archives/libnih-dbus1_1.0.3-12build1_amd64.deb
*/var/cache/apt/archives/libnih1_1.0.3-12build1_amd64.deb
```
 you have corrupt or incorrect versions of the packages so need to uninstall those libnih packages and then remove whatever packages of that name you have in your apt archives and finally reinstall both.
Try running commands ```
sudo apt purge libnih1
sudo rm /var/cache/apt/archives libnih*
sudo apt install libnih1 libnih-dbus1
```
which should do all of those actions and tell us if it works or if those commands still give you errors.

---

### Post by deadflowr on 2022-12-23
```
sudo apt clean
``` cleans up the cache directory.
If that fails, then try manually running the rm command ajgreeny posted.

Anyway you ran into these:
[https://askubuntu.com/questions/1407070/libnih-dbus1amd64-and-libnih1amd64-update-errors-after-22-04-upgrade]("https://askubuntu.com/questions/1407070/libnih-dbus1amd64-and-libnih1amd64-update-errors-after-22-04-upgrade")
[https://bugs.launchpad.net/ubuntu/+source/libnih/+bug/1948346]("https://bugs.launchpad.net/ubuntu/+source/libnih/+bug/1948346")

You can verify that you have multiple instances by running
```
dpkg -l | grep libnih
```
See if any show as libnih1:i386 or libnih-dbus:i386
You can remove those like so
```
sudo apt purge libnih1:i386 libnih-dbus:i386
```

---

### Post by robert48 on 2022-12-23
> **ajgreeny said:**
> I think from that output
```
dpkg:*error*processing*archive*/var/cache/apt/archives/libnih-dbus1_1.0.3-12build1_amd64.deb*(--unpack):
*package*libnih-dbus1:amd64*(1.0.3-12build1)*with*field*'Multi-Arch:*no'*is*not*co-installable*with*libnih-dbus1*which*has*multiple*installed*instances
dpkg:*error*processing*archive*/var/cache/apt/archives/libnih1_1.0.3-12build1_amd64.deb*(--unpack):
*package*libnih1:amd64*(1.0.3-12build1)*with*field*'Multi-Arch:*no'*is*not*co-in
stallable*with*libnih1*which*has*multiple*installed*instances
Errors*were*encountered*while*processing:
*/var/cache/apt/archives/libnih-dbus1_1.0.3-12build1_amd64.deb
*/var/cache/apt/archives/libnih1_1.0.3-12build1_amd64.deb
```
 you have corrupt or incorrect versions of the packages so need to uninstall those libnih packages and then remove whatever packages of that name you have in your apt archives and finally reinstall both.
Try running commands ```
sudo apt purge libnih1
sudo rm /var/cache/apt/archives libnih*
sudo apt install libnih1 libnih-dbus1
```
which should do all of those actions and tell us if it works or if those commands still give you errors.

I have a warning following the third command:-

```
sudo apt install libnih1 libnih-dbus1
```

returned:-

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed
  libnih-dbus1 libnih1
0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/63.0 kB of archives.
After this operation, 196 kB of additional disk space will be used.
Selecting previously unselected package libnih1.
(Reading database ... 313034 files and directories currently installed.)
Preparing to unpack .../libnih1_1.0.3-12build1_amd64.deb ...
Unpacking libnih1 (1.0.3-12build1) ...
Selecting previously unselected package libnih-dbus1.
Preparing to unpack .../libnih-dbus1_1.0.3-12build1_amd64.deb ...
Unpacking libnih-dbus1 (1.0.3-12build1) ...
Setting up libnih1 (1.0.3-12build1) ...
Setting up libnih-dbus1 (1.0.3-12build1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
W: APT had planned for dpkg to do more than it reported back (0 vs 9).
   Affected packages: libnih-dbus1:amd64 libnih1:amd64

---

### Post by robert48 on 2022-12-23
'The Software on the computer is up-to-date'

You have both fixed it for me, Thank you Moderators! You are what makes Ubuntu invincible!

---

### Post by robert48 on 2022-12-23
> **deadflowr said:**
> ```
sudo apt clean
``` cleans up the cache directory.
If that fails, then try manually running the rm command ajgreeny posted.

Anyway you ran into these:
[https://askubuntu.com/questions/1407070/libnih-dbus1amd64-and-libnih1amd64-update-errors-after-22-04-upgrade](https://askubuntu.com/questions/1407070/libnih-dbus1amd64-and-libnih1amd64-update-errors-after-22-04-upgrade)
[https://bugs.launchpad.net/ubuntu/+source/libnih/+bug/1948346](https://bugs.launchpad.net/ubuntu/+source/libnih/+bug/1948346)

You can verify that you have multiple instances by running
```
dpkg -l | grep libnih
```
See if any show as libnih1:i386 or libnih-dbus:i386
You can remove those like so
```
sudo apt purge libnih1:i386 libnih-dbus:i386
```

For the record:-

```
dpkg -l | grep libnih
```

returned:-

ii  libnih-dbus1                                         1.0.3-12build1                                      amd64        NIH D-Bus Bindings Library
ii  libnih1                                              1.0.3-12build1                                      amd64        NIH Utility Library

---

