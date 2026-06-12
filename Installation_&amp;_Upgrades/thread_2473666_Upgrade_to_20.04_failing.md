---
title: "Upgrade to 20.04 failing"
date: 2022-04-09
forum: Installation &amp; Upgrades
---

### Post by fred66 on 2022-04-09
I am (finally) trying to upgrade my laptop, running Ubuntu 18.04 (with a Cinnamon desktop) to 20.04, but the upgrade fails with them message that I am attaching ("an unresolvable problem occurred...", most likely due to an unofficial package...). I disabled all depositories in sources.list.d, but that did not change anything.  I submitted a bug report, as suggested in the message attached, but I still would like to do the upgrade as soon as possible. I believe I had something similar occurring with another laptop (running the Mate desktop) quite a while ago (I dragged my feet on this laptop since it's working as my second daily active one, and i was busy and did not want to rock the boat), but I don't remember how that was solved.

Thank you for any suggestion!

---

### Post by #&amp;thj^% on 2022-04-09
Disable all your PPA's and run:
```
sudo apt update  ###show any errors back here
sudo apt clean
sudo apt update  ###yes twice
sudo apt dist-upgrade
```

---

### Post by fred66 on 2022-04-09
Thank you for your quick reply.
I followed your directions, and got the following error message:
"The following packages have unmet dependencies:
 libomp5-9 : Breaks: libomp5 (< 44) but 5.0.1-1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages."
In fact, an earlier inspection of my log files seemed to flag libomp as the sticking point. I don't know enough about it to know how to handle this issue.

---

### Post by fred66 on 2022-04-10
After writing the previous comment, I tried to delete the package that the upgrade was complaining about, and started a new upgrade. It went on for quite a while, but ended with the following message:

"[FONT=monospace][COLOR=#000000]/tmp/apt-dpkg-install-KEJCkm/01-mpich_3.3.2-2build1_amd64.deb [/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I don't know if the last messages before this one would be helpful, but here is the last snippet reporting the events:

"[/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]Unpacking gfortran-9 (9.4.0-1ubuntu1~20.04.1) ... [/COLOR]
Preparing to unpack .../06-gfortran_4%3a9.3.0-1ubuntu2_amd64.deb ... 
Unpacking gfortran (4:9.3.0-1ubuntu2) over (4:7.4.0-1ubuntu2.3) ... 
Selecting previously unselected package g++-9. 
Preparing to unpack .../07-g++-9_9.4.0-1ubuntu1~20.04.1_amd64.deb ... 
Unpacking g++-9 (9.4.0-1ubuntu1~20.04.1) ... 
Preparing to unpack .../08-g++_4%3a9.3.0-1ubuntu2_amd64.deb ... 
Unpacking g++ (4:9.3.0-1ubuntu2) over (4:7.4.0-1ubuntu2.3) ... 
Selecting previously unselected package libboost-filesystem1.71.0:amd64. 
Preparing to unpack .../09-libboost-filesystem1.71.0_1.71.0-6ubuntu6_amd64.deb ... 
Unpacking libboost-filesystem1.71.0:amd64 (1.71.0-6ubuntu6) ... 
Selecting previously unselected package libboost-iostreams1.71.0:amd64. 
Preparing to unpack .../10-libboost-iostreams1.71.0_1.71.0-6ubuntu6_amd64.deb ... 
Unpacking libboost-iostreams1.71.0:amd64 (1.71.0-6ubuntu6) ... 
Selecting previously unselected package libboost-chrono1.71.0:amd64. 
Preparing to unpack .../11-libboost-chrono1.71.0_1.71.0-6ubuntu6_amd64.deb ... 
Unpacking libboost-chrono1.71.0:amd64 (1.71.0-6ubuntu6) ... 
Selecting previously unselected package libboost-timer1.71.0:amd64. 
Preparing to unpack .../12-libboost-timer1.71.0_1.71.0-6ubuntu6_amd64.deb ... 
Unpacking libboost-timer1.71.0:amd64 (1.71.0-6ubuntu6) ... 
Preparing to unpack .../13-fenics_1%3a2019.1.0.3_amd64.deb ... 
Unpacking fenics:amd64 (1:2019.1.0.3) over (1:2017.2.0.1) ... 
Preparing to unpack .../14-dolfin-bin_2019.1.0-10build2_all.deb ... 
Unpacking dolfin-bin (2019.1.0-10build2) over (2017.2.0.post0-2) ... 
Preparing to unpack .../15-dolfin-doc_2019.1.0-10build2_all.deb ... 
Unpacking dolfin-doc (2019.1.0-10build2) over (2017.2.0.post0-2) ... 
Errors were encountered while processing: 
 /tmp/apt-dpkg-install-KEJCkm/01-mpich_3.3.2-2build1_amd64.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Any help would be greatly appreciated.

[/FONT][/FONT]

---

### Post by #&amp;thj^% on 2022-04-10
Well it's a start, please now run:
```
sudo dpkg --configure -a
```
Then see if can fix-broken:
```
sudo apt-get install -f
```
Please please use code tags for terminal pastes

---

### Post by fred66 on 2022-04-10
Thank you. I really appreciate your patience. It was a long promising run, but it ended up with too many errors (apologies for the missing code tags - I had completely forgotten):

```

[FONT=monospace][COLOR=#000000]Failed to restart grub-common.service: Unit grub-common.service is not loaded properly: Exec format error. [/COLOR]
See system logs and 'systemctl status grub-common.service' for details. 
invoke-rc.d: initscript grub-common, action "restart" failed. 
&#9679; grub-common.service - Record successful boot for GRUB 
     Loaded: [COLOR=#ff5454]**error**[/COLOR][COLOR=#000000] (Reason: Exec format error) [/COLOR]
     Active: inactive (dead) 

Apr 09 21:48:36 auden grub-common[1291]:    ...done. 
Apr 09 21:48:36 auden systemd[1]: Started LSB: Record successful boot for GRUB. 
Apr 10 11:02:13 auden systemd[1]: Stopping LSB: Record successful boot for GRUB... 
Apr 10 11:02:13 auden systemd[1]: Stopped LSB: Record successful boot for GRUB. 
Apr 10 11:02:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:14 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
dpkg: error processing package grub-common (--configure): 
 installed grub-common package post-installation script subprocess returned error exit status 1 
No apport report written because MaxReports is reached already 
                                                              Setting up libgcc-9-dev:amd64 (9.4.0-1ubuntu1~20.04.1) ... 
dpkg: dependency problems prevent configuration of apparmor: 
 apparmor depends on python3:any; however: 
  Package python3 is not configured yet. 

dpkg: error processing package apparmor (--configure): 
 dependency problems - leaving unconfigured 
dpkg: too many errors, stopping 
No apport report written because MaxReports is reached already 
                                                              Errors were encountered while processing: 
 udev 
 gnome-bluetooth 
 kpartx 
 initramfs-tools-core 
 snapd 
 initramfs-tools 
 xserver-xorg-core 
 python3 
 xserver-xorg-core-hwe-18.04 
 python3-dolfin 
 mayavi2 
 libadios-bin 
 python3-tables 
 blueman 
 cwltool 
 python3-mpi4py 
 code-saturne-data 
 python3-chm 
 python3-newt:amd64 
 python3-cysignals-pari 
 python3-admesh 
 python3-jupyter-console 
 python3-pyface 
 python3-networkx 
 python3-markupsafe 
 python3-cyarray 
 python3-ldap3 
 libguestfs0:amd64 
 python3-setuptools-scm 
 openprinting-ppds 
 python3-minieigen 
 software-properties-common 
 python3-psutil 
 python3-fpylll 
 python3-tz 
 python3-fisx 
 python3-prov 
 python3-cypari2 
 fenics:amd64 
 libpetsc3.12-dev-common 
 python3-png 
 python3-mock 
 python3-routes 
 python3-beaker 
 xserver-xorg-input-wacom 
 python3-mysqldb 
 python3-six 
 python3-simplejson 
 grub-common 
 apparmor 
Processing was halted because there were too many errors. 
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I hoped I could upgrade, rather than installing from scratch, but now I don't know...

[/FONT]

---

### Post by #&amp;thj^% on 2022-04-10
Yikes, give this a go and show errors again:
```
sudo dpkg --configure apparmor 
sudo dpkg --configure grub-common
```

---

### Post by fred66 on 2022-04-10
It's quite a mouthful... From apparmor:
```

[FONT=monospace][COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of apparmor: [/COLOR]
 apparmor depends on python3:any; however: 
  Package python3 is not configured yet. 

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package apparmor (--configure): [/COLOR]
 dependency problems - leaving unconfigured 
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ... 
Processing triggers for mime-support (3.64ubuntu1) ... 
Processing triggers for hicolor-icon-theme (0.17-2) ... 
Processing triggers for doc-base (0.10.8) ... 
Processing 14 removed doc-base files, 39 changed doc-base files, 17 added doc-base files... 
Error in `/usr/share/doc-base/pdl', line 14: all `Format' sections are invalid. 
Note: `install-docs --verbose --check file_name' may give more details about the above error. 
Registering documents with scrollkeeper... 
Processing triggers for dictionaries-common (1.28.1) ... 
ispell-autobuildhash: Processing 'american-huge' dict. 
ispell-autobuildhash: Processing 'ngerman' dict. 
aspell-autobuildhash: processing: de [de-common]. 
aspell-autobuildhash: processing: de [de_AT-only]. 
aspell-autobuildhash: processing: de [de_CH-only]. 
aspell-autobuildhash: processing: de [de_DE-only]. 
aspell-autobuildhash: processing: en [en-common]. 
aspell-autobuildhash: processing: en [en-variant_0]. 
aspell-autobuildhash: processing: en [en-variant_1]. 
aspell-autobuildhash: processing: en [en-variant_2]. 
aspell-autobuildhash: processing: en [en-w_accents-only]. 
aspell-autobuildhash: processing: en [en-wo_accents-only]. 
aspell-autobuildhash: processing: en [en_AU-variant_0]. 
aspell-autobuildhash: processing: en [en_AU-variant_1]. 
aspell-autobuildhash: processing: en [en_AU-w_accents-only]. 
aspell-autobuildhash: processing: en [en_AU-wo_accents-only]. 
aspell-autobuildhash: processing: en [en_CA-variant_0]. 
aspell-autobuildhash: processing: en [en_CA-variant_1]. 
aspell-autobuildhash: processing: en [en_CA-w_accents-only]. 
aspell-autobuildhash: processing: en [en_CA-wo_accents-only]. 
aspell-autobuildhash: processing: en [en_GB-ise-w_accents-only]. 
aspell-autobuildhash: processing: en [en_GB-ise-wo_accents-only]. 
aspell-autobuildhash: processing: en [en_GB-ize-w_accents-only]. 
aspell-autobuildhash: processing: en [en_GB-ize-wo_accents-only]. 
aspell-autobuildhash: processing: en [en_GB-variant_0]. 
aspell-autobuildhash: processing: en [en_GB-variant_1]. 
aspell-autobuildhash: processing: en [en_US-w_accents-only]. 
aspell-autobuildhash: processing: en [en_US-wo_accents-only]. 
aspell-autobuildhash: processing: it [it]. 
Processing triggers for libc-bin (2.31-0ubuntu9.7) ... 
Processing triggers for man-db (2.8.3-2ubuntu0.1) ... 
Processing triggers for ureadahead (0.100.0-21) ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for ca-certificates (20210119~20.04.2) ... 
Updating certificates in /etc/ssl/certs... 
0 added, 0 removed; done. 
Running hooks in /etc/ca-certificates/update.d... 

done. 
Updating Mono key store 
Linux Cert Store Sync - version 4.6.2.0 
Synchronize local certs with certs from local Linux trust store. 
Copyright 2002, 2003 Motus Technologies. Copyright 2004-2008 Novell. BSD licensed. 

I already trust 132, your new list has 128 
Import process completed. 
Done 
done. 
Processing triggers for cracklib-runtime (2.9.2-5build1) ... 
Processing triggers for plymouth-theme-ubuntu-text (0.9.3-1ubuntu7.18.04.2) ... 
update-initramfs: deferring update (trigger activated) 
Processing triggers for plymouth-theme-ubuntu-mate-text (18.04.11) ... 
update-initramfs: deferring update (trigger activated) 
Processing triggers for plymouth-theme-kubuntu-text (1:18.04ubuntu11) ... 
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#ffff54]**warning:**[/COLOR][COLOR=#000000] version '/etc/lsb-release' has bad syntax: version number does not start with digit [/COLOR]
rmdir: failed to remove '/lib/plymouth/': No such file or directory 
update-initramfs: deferring update (trigger activated) 
Processing triggers for sgml-base (1.29) ... 
Processing triggers for install-info (6.7.0.dfsg.2-5) ... 
install-info: warning: no info dir entry in `/usr/share/info/ocaml.info.hocaml.info.kwd.hind.gz' 
install-info: warning: no info dir entry in `/usr/share/info/ocaml.info.haux.gz' 
install-info: warning: no info dir entry in `/usr/share/info/gnash_ref.info.gz' 
install-info: warning: no info dir entry in `/usr/share/info/ocaml.info.hocaml.info.hind.gz' 
install-info: warning: no info dir entry in `/usr/share/info/axe.info.gz' 
install-info: warning: no info dir entry in `/usr/share/info/gnash_user.info.gz' 
Processing triggers for xpdf (3.04-7) ... 
Processing triggers for menu (2.1.47ubuntu2.1) ... 
Errors were encountered while processing: 
 apparmor


```

From grub-common
```

[FONT=monospace][COLOR=#000000]Setting up grub-common (2.04-1ubuntu26.15) ... [/COLOR]
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults 
Failed to restart grub-common.service: Unit grub-common.service is not loaded properly: Exec format error. 
See system logs and 'systemctl status grub-common.service' for details. 
invoke-rc.d: initscript grub-common, action "restart" failed. 
&#9679; grub-common.service - Record successful boot for GRUB 
     Loaded: [COLOR=#ff5454]**error**[/COLOR][COLOR=#000000] (Reason: Exec format error) [/COLOR]
     Active: inactive (dead) 

Apr 10 11:02:13 auden systemd[1]: Stopped LSB: Record successful boot for GRUB. 
Apr 10 11:02:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:13 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 13:07:14 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 16:44:16 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 16:44:16 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
Apr 10 16:44:16 auden systemd[1]: [COLOR=#ff5454]**/lib/systemd/system/grub-common.service:10: Executable path is not absolute: grub-editenv /boot/grub/grubenv unset recordfail**[/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package grub-common (--configure): [/COLOR]
 installed grub-common package post-installation script subprocess returned error exit status 1 
Errors were encountered while processing: 
 grub-common

```[/FONT]
[/FONT]Thank you - I am very grateful for your support.

---

### Post by Impavidus on 2022-04-11
Don't spend more than an hour on an upgrade (three if you really want to learn). A fresh install will be quicker.

---

### Post by #&amp;thj^% on 2022-04-11
> **Impavidus said:**
> Don't spend more than an hour on an upgrade (three if you really want to learn). A fresh install will be quicker.

Words of Wisdom. ;)

---

