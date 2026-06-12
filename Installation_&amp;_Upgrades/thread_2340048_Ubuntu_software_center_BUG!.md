---
title: "Ubuntu software center BUG!"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by 243750496 on 2016-10-15
[ATTACH=CONFIG]271617[/ATTACH][ATTACH=CONFIG]271618[/ATTACH]
i used synaptic to update firstly then the install button still show up then i cliked it and it just reload the page and the install button still there,
how to solve it? btw i try to change server to main server it still there after i restart and reclick , it just like zombies there doing nothing (nothing intalled)

---

### Post by RobGoss on 2016-10-15
Did you let the install complete? is look like it wanted to update the system let it run then reboot your machine

---

### Post by 243750496 on 2016-10-15
i have reboot for several times and do reboot click (install button) then  the button still there seems nothing happened and nothing  up  to date

---

### Post by vasa1 on 2016-10-15
Open a terminal and run```
sudo apt-get update
``` and then run ```
sudo apt-get upgrade
```Post the entire output including the commands you type here between code tags. Maybe that information will give people some hints.

---

### Post by 243750496 on 2016-10-15
```
cc@CC:~$ sudo apt-get update
[sudo] password for cc: 
Hit:1 [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Hit:3 [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:4 [http://archive.ubuntukylin.com:10006/ubuntukylin](http://archive.ubuntukylin.com:10006/ubuntukylin) xenial InRelease [18.1 kB]
Hit:5 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease                     
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Ign:4 [http://archive.ubuntukylin.com:10006/ubuntukylin](http://archive.ubuntukylin.com:10006/ubuntukylin) xenial InRelease        
Hit:7 [http://ppa.launchpad.net/costales/anoise/ubuntu](http://ppa.launchpad.net/costales/anoise/ubuntu) xenial InRelease         
Hit:8 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:9 [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) xenial InRelease         
Hit:10 [http://ppa.launchpad.net/dhor/myway/ubuntu](http://ppa.launchpad.net/dhor/myway/ubuntu) xenial InRelease             
Hit:11 [http://ppa.launchpad.net/freecad-maintainers/freecad-daily/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-daily/ubuntu) xenial InRelease
Hit:12 [http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu](http://ppa.launchpad.net/librecad-dev/librecad-daily/ubuntu) xenial InRelease
Hit:13 [http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu) xenial InRelease
Hit:14 [http://ppa.launchpad.net/wiznote-team/ppa/ubuntu](http://ppa.launchpad.net/wiznote-team/ppa/ubuntu) xenial InRelease
Fetched 113 kB in 3s (35.9 kB/s)
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: GPG error: [http://archive.ubuntukylin.com:10006/ubuntukylin](http://archive.ubuntukylin.com:10006/ubuntukylin) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E40EBBA24FF2FC69
W: The repository 'http://archive.ubuntukylin.com:10006/ubuntukylin xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
```
cc@CC:~$ sudo dpkg --configure -a
Setting up librecad (2.1.1+20161015.416-0~ubuntu16.04.1) ...
Setting up shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up gimp-ufraw (0.22-2dhor~xenial) ...
Setting up linux-image-4.4.0-43-generic (4.4.0-43.63) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
Error! Your kernel headers for kernel 4.4.0-43-generic cannot be found.
Please install the linux-headers-4.4.0-43-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
done

```
```
cc@CC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
  linux-signed-image-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic xnconvert
The following packages will be upgraded:
  linux-image-extra-4.4.0-43-generic linux-libc-dev
2 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0 B/39.8 MB of archives.
After this operation, 162 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 297849 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-4.4.0-43-generic_4.4.0-43.63_amd64.deb ...
Unpacking linux-image-extra-4.4.0-43-generic (4.4.0-43.63) over (4.4.0-43.63) ...
Preparing to unpack .../linux-libc-dev_4.4.0-43.63_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-43.63) over (4.4.0-42.62) ...
Setting up linux-image-extra-4.4.0-43-generic (4.4.0-43.63) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
Error! Your kernel headers for kernel 4.4.0-43-generic cannot be found.
Please install the linux-headers-4.4.0-43-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-43-generic /boot/vmlinuz-4.4.0-43-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
done
Setting up linux-libc-dev:amd64 (4.4.0-43.63) ...
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
```

---

### Post by RobGoss on 2016-10-15
> [COLOR=#000000][FONT=&amp]Error! Your kernel headers for kernel 4.4.0-43-generic cannot be found.
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]Please install the linux-headers-4.4.0-43-generic package,[/FONT][/COLOR]

What I see is the following described above it seems like something when wrong with the kernel installation or was removed did you remove anything for your system or maybe delete something?

Is this a new installation? and what distribution are you currently running?

---

### Post by 243750496 on 2016-10-15
> **RobGoss said:**
> What I see is the following described above it seems like something when wrong with the kernel installation or was removed did you remove anything for your system or maybe delete something?

Is this a new installation? and what distribution are you currently running?

 Still there the install buttons

---

### Post by RobGoss on 2016-10-15
> **243750496 said:**
> Still there the install buttons


Is this a new installation? you might want to consider doing a **fresh** installation if needed I'n not sure what version you're using

---

### Post by 243750496 on 2016-10-15
> **RobGoss said:**
> Is this a new installation? you might want to consider doing a **fresh** installation if needed I'n not sure what version you're using
 ubuntu16.04 and afterclick the refresh button on top left on updats  page  it  still there

no error not breaked pacages no  new update in synaptic but the button still  there

```
cc@CC:~$ sudo ubuntu-software
[sudo] password for cc: 

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: mypaint.desktop changing management plugin PackageKit->apt

(ubuntu-software:4405): Gs-WARNING **: gimp.desktop changing management plugin PackageKit->apt

(ubuntu-software:4405): Gs-WARNING **: blender.desktop changing management plugin PackageKit->apt

(ubuntu-software:4405): GsPlugin-WARNING **: Failed to get changelog for xnconvert version 1.73-dhor1~xenial from changelogs.ubuntu.com: Not Found

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): GsPlugin-WARNING **: Failed to get changelog for xnconvert version 1.73-dhor1~xenial from changelogs.ubuntu.com: Not Found

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): GsPlugin-WARNING **: Failed to get changelog for xnconvert version 1.73-dhor1~xenial from changelogs.ubuntu.com: Not Found

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered

(ubuntu-software:4405): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered


```

[ATTACH=CONFIG]271625[/ATTACH]
```
cc@CC:~$ sudo apt-get install xnconvert
[sudo] password for cc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
xnconvert : Depends: libicu52 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

```

cc@CC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
  linux-signed-image-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
```
cc@CC:~$ sudo apt-get install libicu52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libicu52 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libicu52' has no installation candidate
```

```

cc@CC:~$ sudo apt-get install xnconvert
[sudo] password for cc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xnconvert : Depends: libicu52 but it is not installable
E: Unable to correct problems, you have held broken packages.
```
```

cc@CC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
  linux-signed-image-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
cc@CC:~$ sudo apt-get install libicu52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libicu52 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libicu52' has no installation candidate
```
```

cc@CC:~$ sudo apt-get remove libicu52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libicu52' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
  linux-signed-image-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

```
cc@CC:~$ cd Downloads
cc@CC:~/Downloads$ cd '/home/cc/Downloads/FlareGet/Applications' 
cc@CC:~/Downloads/FlareGet/Applications$ sudo dpkg -i *.deb (to install the libicu52.deb that i'm lacking)
Selecting previously unselected package libicu52:amd64.
(Reading database ... 330819 files and directories currently installed.)
Preparing to unpack libicu52_52.1-3ubuntu0.4_amd64.deb ...
Unpacking libicu52:amd64 (52.1-3ubuntu0.4) ...
Setting up libicu52:amd64 (52.1-3ubuntu0.4) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
```
```

cc@CC:~/Downloads/FlareGet/Applications$ sudo apt-get install xnconvert
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
  linux-signed-image-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  xnconvert
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.0 MB of archives.
After this operation, 71.0 MB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/dhor/myway/ubuntu xenial/main amd64 xnconvert amd64 1.73-dhor1~xenial [19.0 MB]
Fetched 19.0 MB in 3min 39s (86.9 kB/s)                                        
(Reading database ... 330840 files and directories currently installed.)
Preparing to unpack .../xnconvert_1.73-dhor1~xenial_amd64.deb ...
Unpacking xnconvert (1.73-dhor1~xenial) over (1.73) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up xnconvert (1.73-dhor1~xenial) ...
cc@CC:~/Downloads/FlareGet/Applications$
```

Pacage address:

[http://packages.ubuntu.com/trusty-updates/amd64/libicu52/download](http://packages.ubuntu.com/trusty-updates/amd64/libicu52/download)

---

