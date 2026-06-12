---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by daidera on 2016-11-11
**Hi i'm trying to instal git :**
sudo apt-get install git
(if i try sudo apt-get upgrade see the same problem)
**But i'm getting error like this :**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'runit' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libpango1.0-0 libpangox-1.0-0
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-4.4.0-47-generic (4.4.0-47.68) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-47-generic
) points to /boot/initrd.img-4.4.0-47-generic
 (/boot/initrd.img-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-47-generic
) points to /boot/vmlinuz-4.4.0-47-generic
 (/boot/vmlinuz-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/vboxadd 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: failed to exec /etc/kernel/postinst.d/vboxadd: Exec format error
run-parts: /etc/kernel/postinst.d/vboxadd exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-47-generic:
 linux-image-extra-4.4.0-47-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-47-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-47-generic; however:
  Package linux-image-extra-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.47.50); however:
  Package linux-image-generic is not configured No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                        No apport report written because MaxReports has already been reached
            yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-4.4.0-47-generic
 linux-image-extra-4.4.0-47-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
osboxes@osboxes:~$ --configure
--configure: command not found
osboxes@osboxes:~$ cd /usr/bin/dpkg
bash: cd: /usr/bin/dpkg: Not a directory
osboxes@osboxes:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  test  Videos
osboxes@osboxes:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpango1.0-0 libpangox-1.0-0
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-4.4.0-47-generic (4.4.0-47.68) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-47-generic
) points to /boot/initrd.img-4.4.0-47-generic
 (/boot/initrd.img-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-47-generic
) points to /boot/vmlinuz-4.4.0-47-generic
 (/boot/vmlinuz-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/vboxadd 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: failed to exec /etc/kernel/postinst.d/vboxadd: Exec format error
run-parts: /etc/kernel/postinst.d/vboxadd exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-47-generic:
 linux-image-extra-4.4.0-47-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-47-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-47-generic; however:
  Package linux-image-extra-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.47.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-4.4.0-47-generic
 linux-image-extra-4.4.0-47-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
osboxes@osboxes:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version (1:2.7.4-0ubuntu1).
The following packages were automatically installed and are no longer required:
  libpango1.0-0 libpangox-1.0-0
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-4.4.0-47-generic (4.4.0-47.68) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-47-generic
) points to /boot/initrd.img-4.4.0-47-generic
 (/boot/initrd.img-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-47-generic
) points to /boot/vmlinuz-4.4.0-47-generic
 (/boot/vmlinuz-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/vboxadd 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: failed to exec /etc/kernel/postinst.d/vboxadd: Exec format error
run-parts: /etc/kernel/postinst.d/vboxadd exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-47-generic:
 linux-image-extra-4.4.0-47-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-47-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-47-generic; however:
  Package linux-image-extra-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:No apport report written because the error message indicates it's a follow-up error from a previous failure.

 linux-generic depends on linux-image-generic (= 4.4.0.47.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-4.4.0-47-generic
 linux-image-extra-4.4.0-47-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
osboxes@osboxes:~$ ^C
osboxes@osboxes:~$ clean
No command 'clean' found, did you mean:
 Command 'clear' from package 'ncurses-bin' (main)
 Command 'pclean' from package 'pbuilder-scripts' (universe)
 Command 'uclean' from package 'svn-buildpackage' (universe)
clean: command not found
osboxes@osboxes:~$ clear
[3;J
osboxes@osboxes:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version (1:2.7.4-0ubuntu1).
The following packages were automatically installed and are no longer required:
  libpango1.0-0 libpangox-1.0-0
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-4.4.0-47-generic (4.4.0-47.68) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-47-generic
) points to /boot/initrd.img-4.4.0-47-generic
 (/boot/initrd.img-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-47-generic
) points to /boot/vmlinuz-4.4.0-47-generic
 (/boot/vmlinuz-4.4.0-47-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/vboxadd 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: failed to exec /etc/kernel/postinst.d/vboxadd: Exec format error
run-parts: /etc/kernel/postinst.d/vboxadd exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-47-generic:
 linux-image-extra-4.4.0-47-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-47-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-47-generic; however:
  Package linux-image-4.4.0-47-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-47-generic; however:
  Package linux-image-extra-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:No apport report written because the error message indicates it's a follow-up error from a previous failure.

 linux-generic depends on linux-image-generic (= 4.4.0.47.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-4.4.0-47-generic
 linux-image-extra-4.4.0-47-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I'm working on Oracle VM VirtualBox and have Lubuntu 16.04 (64bit) some1 maybe know how to help me and fix it :?

PS: im totaly newbie :P

---

### Post by ian-weisser on 2016-11-11
Have you noticed that it's the same error every time?
> [B][COLOR=#000000]run-parts: failed to exec /etc/kernel/postinst.d/vboxadd: Exec format error[/COLOR]
[/B][COLOR=#000000]**run-parts: /etc/kernel/postinst.d/vboxadd exited with return code 1**
[/COLOR][COLOR=#000000]Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-47-generic.postinst line 1052.[/COLOR]

I see two possibilities:
1) A typo has crept in to the /etc/kernel/postinst.d/vboxadd script (Solution: Reinstall the package)
2) The package providing that script has introduced a bug (Solution: File a bug report, edit the script by hand to fix)

What package provides the vboxadd file?
```
dpkg -S /etc/kernel/postinst.d/vboxadd
```

---

### Post by daidera on 2016-11-11
Probably i know where is a problem when i try move to :
```
cd /etc/kernel/postinst.d
```
It's all okey but when i write
```
cd /etc/kernel/postinst.d/vboxadd
```
Then i see this :
```
bash: cd: /etc/kernel/postinst.d/vboxadd: Not a directory
```
Soooo i dont have it ? or what?

---

### Post by ian-weisser on 2016-11-11
It's a file, not a directory. You cannot cd to a file.
Read the file using 'less' or 'cat'

---

### Post by daidera on 2016-11-11
```

osboxes@osboxes:/etc/kernel/postinst.d$ cat > vboxadd
bash: vboxadd: Permission denied
osboxes@osboxes:/etc/kernel/postinst.d$ cat >> vboxadd
bash: vboxadd: Permission denied

```
but when i write less then i see this 
```

~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)


```

---

### Post by ian-weisser on 2016-11-11
Try 'sudo less /etc/kernel/postinst.d/vboxadd' or 'sudo cat cd /etc/kernel/postinst.d/vboxadd'
The system will ask you for your password. Provide it.

Wile you are in the Terminal, please post the complete output of the command:
```
dpkg -S /etc/kernel/postinst.d/vboxadd
```
This will tell us which package provided the broken script, so we can try to reinstall it.

---

### Post by daidera on 2016-11-11
```
osboxes@osboxes:/$ sudo less cd /etc/kernel/postinst.d/vboxadd
[sudo] password for osboxes: 
cd: No such file or directory
/etc/kernel/postinst.d/vboxadd  (press RETURN)





































[1]+  Stopped                 sudo less cd /etc/kernel/postinst.d/vboxadd
osboxes@osboxes:/$ sudo cat cd/etc/kernel/postinst.d/vboxadd
cat: cd/etc/kernel/postinst.d/vboxadd: No such file or directory
osboxes@osboxes:/$ 


```

and when i write your code i see this 
```

osboxes@osboxes:/$ dpkg -S /etc/kernel/postinst.d/vboxadd
dpkg-query: no path found matching pattern /etc/kernel/postinst.d/vboxadd
```

---

### Post by ian-weisser on 2016-11-11
Not cd. It's not a directory. (Sorry for the typo). Do it again without the 'cd'.

vboxadd looks like a VirtualBox hook file. Do you have VirtualBox installed? If so, from the Ubuntu repos or from someplace else? If not, how did you delete Virtualbox?

---

### Post by daidera on 2016-11-12
without cd
```
osboxes@osboxes:~$ sudo less /etc/kernel/postinst.d/vboxadd
[sudo] password for osboxes: 

[1]+  Stopped                 sudo less /etc/kernel/postinst.d/vboxadd
osboxes@osboxes:~$ sudo cat /etc/kernel/postinst.d/vboxadd
osboxes@osboxes:~$ sudo cat >  /etc/kernel/postinst.d/vboxadd
bash: /etc/kernel/postinst.d/vboxadd: Permission denied
osboxes@osboxes:~$ sudo cat >>  /etc/kernel/postinst.d/vboxadd
bash: /etc/kernel/postinst.d/vboxadd: Permission denied


```

Then reinstall virtualbox? i have it from here [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

