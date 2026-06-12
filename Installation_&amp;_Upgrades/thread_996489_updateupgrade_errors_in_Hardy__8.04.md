---
title: "update/upgrade errors in Hardy  8.04"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by mediajunkie on 2008-11-28
Hi all

I've been running 8.04 for some time with good success on my Acer Aspire 8920. But recently my upgrades seem to fail and every time I run new upgrades there seem to fail more and more modules every time. 

it started with kernel update issues ,  then clamav , samba now also postgresql. 


> E: clamav-base: subprocess post-installation script returned error exit status 1 
E: clamav-freshclam: dependency problems - leaving unconfigured 
E: clamav: dependency problems - leaving unconfigured 
E: clamtk: dependency problems - leaving unconfigured 
E: samba-common: subprocess post-installation script returned error exit status 1 
E: smbclient: dependency problems - leaving unconfigured 
E: linux-image-2.6.24-22-generic: subprocess post-installation script returned error exit status 1 
E: linux-ubuntu-modules-2.6.24-22-generic: dependency problems - leaving unconfigured 
E: linux-image-generic: dependency problems - leaving unconfigured 
E: linux-restricted-modules-2.6.24-22-generic: dependency problems - leaving unconfigured 
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured 
E: linux-generic: dependency problems - leaving unconfigured 
E: postgresql-client-8.3: subprocess post-installation script returned error exit status 2 
E: postgresql-8.3: dependency problems - leaving unconfigured 
E: postgresql-contrib-8.3: dependency problems - leaving unconfigured 
E: postgresql-plperl-8.3: dependency problems - leaving unconfigured 
E: postgresql-plpython-8.3: dependency problems - leaving unconfigured 
E: postgresql-pltcl-8.3: dependency problems - leaving unconfigured 


Does anybody have any Idea what is going on here? 

I would like to get my system up-to-date again. 

Thanks for your help in advance.

---

### Post by Partyboi2 on 2008-11-30
Open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get -f install 
```
then ```
sudo dpkg --configure -a 
```
then 
```
sudo apt-get upgrade
``` and post any errors.

---

### Post by mediajunkie on 2008-12-01
Hi Partyboi2,

Thanks for your reply. 

Below are the results from the 3 commands you suggested. 
All 3 of them gave a long error list. 
I also get a crash report icon. The strange thing is that it started with one upgrade issue (linux-image-2.6.24-21-generic) then clamav, samba and postgresql came on top of it. the list seems to grow. 




```
sudo apt-get -f install 

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
18 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic 
Running postinst hook script /sbin/update-grub. 
usage: tr [--verbose] [--name | --stdout] 
User postinst hook script [/sbin/update-grub] exited with value 1 
dpkg: error processing linux-image-2.6.24-22-generic (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic: 
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up clamav-base (0.92.1~dfsg2-1.1ubuntu0.3) ... 
usage: tr [--verbose] [--name | --stdout] 
dpkg: error processing clamav-base (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of clamav-freshclam: 
 clamav-freshclam depends on clamav-base (>= 0.92.1~dfsg2-1.1ubuntu0.3); however: 
  Package clamav-base is not configured yet. 
dpkg: error processing clamav-freshclam (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of clamav: 
 clamav depends on clamav-freshclam | clamav-data; however: 
  Package clamav-freshclam is not configured yet. 
  Package clamav-data is not installed. 
  Package clamav-freshclam which provides clamav-data is not configured yet. 
dpkg: error processing clamav (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of clamtk: 
 clamtk depends on clamav (>= 0.90); however: 
  Package clamav is not configured yet. 
 clamtk depends on clamav-freshclam (>= 0.90) | clamav-data (>= 0.90); however: 
  Package clamav-freshclam is not configured yet. 
  Package clamav-data is not installed. 
dpkg: error processing clamtk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however: 
  Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic: 
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic: 
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-22-generic; however: 
  Package linux-restricted-modules-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.24.22.24); however: 
  Package linux-image-generic is not configured yet. 
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.22.24); however: 
  Package linux-restricted-modules-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up postgresql-client-8.3 (8.3.5-0ubuntu0.8.04) ... 
usage: tr [--verbose] [--name | --stdout] 
update-alternatives: priority must be an integer 

Usage: update-alternatives [<option> ...] <command> 

Commands: 
  --install <link> <name> <path> <priority> 
    [--slave <link> <name> <path>] ... 
                           add a group of alternatives to the system. 
  --remove <name> <path>   remove <path> from the <name> group alternative. 
  --remove-all <name>      remove <name> group from the alternatives system. 
  --auto <name>            switch the master link <name> to automatic mode. 
  --display <name>         display information about the <name> group. 
  --list <name>            display all targets of the <name> group. 
  --config <name>          show alternatives for the <name> group and ask the 
                           user to select which one to use. 
  --set <name> <path>      set <path> as alternative for <name>. 
  --all                    call --config on all alternatives. 

<link> is the symlink pointing to /etc/alternatives/<name>. 
  (e.g. /usr/bin/pager) 
<name> is the master name for this link group. 
  (e.g. pager) 
<path> is the location of one of the alternative target files. 
  (e.g. /usr/bin/less) 
<priority> is an integer; options with higher numbers have higher priority in 
  automatic mode. 

Options: 
  --altdir <directory>     change the alternatives directory. 
  --admindir <directory>   change the administrative directory. 
  --verbose                verbose operation, more output. 
  --quiet                  quiet operation, minimal output. 
  --help                   show this help message. 
  --version                show the version. 
dpkg: error processing postgresql-client-8.3 (--configure): 
 subprocess post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of postgresql-8.3: 
 postgresql-8.3 depends on postgresql-client-8.3; however: 
  Package postgresql-client-8.3 is not configured yet. 
dpkg: error processing postgresql-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-contrib-8.3: 
 postgresql-contrib-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-contrib-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-plperl-8.3: 
 postgresql-plperl-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-plperl-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-plpython-8.3: 
 postgresql-plpython-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-plpython-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-pltcl-8.3: 
 postgresql-pltcl-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-pltcl-8.3 (--configure): 
 dependency problems - leaving unconfigured 
Setting up samba-common (3.0.28a-1ubuntu4.7) ... 
usage: tr [--verbose] [--name | --stdout] 
dpkg: error processing samba-common (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of smbclient: 
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.7); however: 
  Package samba-common is not configured yet. 
dpkg: error processing smbclient (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 linux-image-2.6.24-22-generic 
 linux-ubuntu-modules-2.6.24-22-generic 
 clamav-base 
 clamav-freshclam 
 clamav 
 clamtk 
 linux-image-generic 
 linux-restricted-modules-2.6.24-22-generic 
 linux-restricted-modules-generic 
 linux-generic 
 postgresql-client-8.3 
 postgresql-8.3 
 postgresql-contrib-8.3 
 postgresql-plperl-8.3 
 postgresql-plpython-8.3 
 postgresql-pltcl-8.3 
 samba-common 
 smbclient 
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



```
sudo dpkg --configure -a 
Setting up samba-common (3.0.28a-1ubuntu4.7) ... 
usage: tr [--verbose] [--name | --stdout] 
dpkg: error processing samba-common (--configure): 
 subprocess post-installation script returned error exit status 1 
Setting up clamav-base (0.92.1~dfsg2-1.1ubuntu0.3) ... 
usage: tr [--verbose] [--name | --stdout] 
dpkg: error processing clamav-base (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of smbclient: 
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.7); however: 
  Package samba-common is not configured yet. 
dpkg: error processing smbclient (--configure): 
 dependency problems - leaving unconfigured 
Setting up postgresql-client-8.3 (8.3.5-0ubuntu0.8.04) ... 
usage: tr [--verbose] [--name | --stdout] 
update-alternatives: priority must be an integer 

Usage: update-alternatives [<option> ...] <command> 

Commands: 
  --install <link> <name> <path> <priority> 
    [--slave <link> <name> <path>] ... 
                           add a group of alternatives to the system. 
  --remove <name> <path>   remove <path> from the <name> group alternative. 
  --remove-all <name>      remove <name> group from the alternatives system. 
  --auto <name>            switch the master link <name> to automatic mode. 
  --display <name>         display information about the <name> group. 
  --list <name>            display all targets of the <name> group. 
  --config <name>          show alternatives for the <name> group and ask the 
                           user to select which one to use. 
  --set <name> <path>      set <path> as alternative for <name>. 
  --all                    call --config on all alternatives. 

<link> is the symlink pointing to /etc/alternatives/<name>. 
  (e.g. /usr/bin/pager) 
<name> is the master name for this link group. 
  (e.g. pager) 
<path> is the location of one of the alternative target files. 
  (e.g. /usr/bin/less) 
<priority> is an integer; options with higher numbers have higher priority in 
  automatic mode. 

Options: 
  --altdir <directory>     change the alternatives directory. 
  --admindir <directory>   change the administrative directory. 
  --verbose                verbose operation, more output. 
  --quiet                  quiet operation, minimal output. 
  --help                   show this help message. 
  --version                show the version. 
dpkg: error processing postgresql-client-8.3 (--configure): 
 subprocess post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of postgresql-8.3: 
 postgresql-8.3 depends on postgresql-client-8.3; however: 
  Package postgresql-client-8.3 is not configured yet. 
dpkg: error processing postgresql-8.3 (--configure): 
 dependency problems - leaving unconfigured 
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic 
Running postinst hook script /sbin/update-grub. 
usage: tr [--verbose] [--name | --stdout] 
User postinst hook script [/sbin/update-grub] exited with value 1 
dpkg: error processing linux-image-2.6.24-22-generic (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic: 
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-contrib-8.3: 
 postgresql-contrib-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-contrib-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-pltcl-8.3: 
 postgresql-pltcl-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-pltcl-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-plpython-8.3: 
 postgresql-plpython-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-plpython-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-plperl-8.3: 
 postgresql-plperl-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-plperl-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of clamav-freshclam: 
 clamav-freshclam depends on clamav-base (>= 0.92.1~dfsg2-1.1ubuntu0.3); however: 
  Package clamav-base is not configured yet. 
dpkg: error processing clamav-freshclam (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic: 
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however: 
  Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic: 
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-22-generic; however: 
  Package linux-restricted-modules-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.24.22.24); however: 
  Package linux-image-generic is not configured yet. 
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.22.24); however: 
  Package linux-restricted-modules-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of clamav: 
 clamav depends on clamav-freshclam | clamav-data; however: 
  Package clamav-freshclam is not configured yet. 
  Package clamav-data is not installed. 
  Package clamav-freshclam which provides clamav-data is not configured yet. 
dpkg: error processing clamav (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of clamtk: 
 clamtk depends on clamav (>= 0.90); however: 
  Package clamav is not configured yet. 
 clamtk depends on clamav-freshclam (>= 0.90) | clamav-data (>= 0.90); however: 
  Package clamav-freshclam is not configured yet. 
  Package clamav-data is not installed. 
dpkg: error processing clamtk (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 samba-common 
 clamav-base 
 smbclient 
 postgresql-client-8.3 
 postgresql-8.3 
 linux-image-2.6.24-22-generic 
 linux-restricted-modules-2.6.24-22-generic 
 postgresql-contrib-8.3 
 postgresql-pltcl-8.3 
 postgresql-plpython-8.3 
 postgresql-plperl-8.3 
 clamav-freshclam 
 linux-ubuntu-modules-2.6.24-22-generic 
 linux-image-generic 
 linux-restricted-modules-generic 
 linux-generic 
 clamav 
 clamtk 

```



```
$ sudo apt-get upgrade 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
18 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Setting up linux-image-2.6.24-22-generic (2.6.24-22.45) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic 
Running postinst hook script /sbin/update-grub. 
usage: tr [--verbose] [--name | --stdout] 
User postinst hook script [/sbin/update-grub] exited with value 1 
dpkg: error processing linux-image-2.6.24-22-generic (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-22-generic: 
 linux-ubuntu-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up clamav-base (0.92.1~dfsg2-1.1ubuntu0.3) ... 
usage: tr [--verbose] [--name | --stdout] 
dpkg: error processing clamav-base (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of clamav-freshclam: 
 clamav-freshclam depends on clamav-base (>= 0.92.1~dfsg2-1.1ubuntu0.3); however: 
  Package clamav-base is not configured yet. 
dpkg: error processing clamav-freshclam (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of clamav: 
 clamav depends on clamav-freshclam | clamav-data; however: 
  Package clamav-freshclam is not configured yet. 
  Package clamav-data is not installed. 
  Package clamav-freshclam which provides clamav-data is not configured yet. 
dpkg: error processing clamav (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of clamtk: 
 clamtk depends on clamav (>= 0.90); however: 
  Package clamav is not configured yet. 
 clamtk depends on clamav-freshclam (>= 0.90) | clamav-data (>= 0.90); however: 
  Package clamav-freshclam is not configured yet. 
  Package clamav-data is not installed. 
dpkg: error processing clamtk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however: 
  Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-22-generic: 
 linux-restricted-modules-2.6.24-22-generic depends on linux-image-2.6.24-22-generic; however: 
  Package linux-image-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-2.6.24-22-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic: 
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-22-generic; however: 
  Package linux-restricted-modules-2.6.24-22-generic is not configured yet. 
dpkg: error processing linux-restricted-modules-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.24.22.24); however: 
  Package linux-image-generic is not configured yet. 
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.22.24); however: 
  Package linux-restricted-modules-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up postgresql-client-8.3 (8.3.5-0ubuntu0.8.04) ... 
usage: tr [--verbose] [--name | --stdout] 
update-alternatives: priority must be an integer 

Usage: update-alternatives [<option> ...] <command> 

Commands: 
  --install <link> <name> <path> <priority> 
    [--slave <link> <name> <path>] ... 
                           add a group of alternatives to the system. 
  --remove <name> <path>   remove <path> from the <name> group alternative. 
  --remove-all <name>      remove <name> group from the alternatives system. 
  --auto <name>            switch the master link <name> to automatic mode. 
  --display <name>         display information about the <name> group. 
  --list <name>            display all targets of the <name> group. 
  --config <name>          show alternatives for the <name> group and ask the 
                           user to select which one to use. 
  --set <name> <path>      set <path> as alternative for <name>. 
  --all                    call --config on all alternatives. 

<link> is the symlink pointing to /etc/alternatives/<name>. 
  (e.g. /usr/bin/pager) 
<name> is the master name for this link group. 
  (e.g. pager) 
<path> is the location of one of the alternative target files. 
  (e.g. /usr/bin/less) 
<priority> is an integer; options with higher numbers have higher priority in 
  automatic mode. 

Options: 
  --altdir <directory>     change the alternatives directory. 
  --admindir <directory>   change the administrative directory. 
  --verbose                verbose operation, more output. 
  --quiet                  quiet operation, minimal output. 
  --help                   show this help message. 
  --version                show the version. 
dpkg: error processing postgresql-client-8.3 (--configure): 
 subprocess post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of postgresql-8.3: 
 postgresql-8.3 depends on postgresql-client-8.3; however: 
  Package postgresql-client-8.3 is not configured yet. 
dpkg: error processing postgresql-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-contrib-8.3: 
 postgresql-contrib-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-contrib-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-plperl-8.3: 
 postgresql-plperl-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-plperl-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-plpython-8.3: 
 postgresql-plpython-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-plpython-8.3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of postgresql-pltcl-8.3: 
 postgresql-pltcl-8.3 depends on postgresql-8.3; however: 
  Package postgresql-8.3 is not configured yet. 
dpkg: error processing postgresql-pltcl-8.3 (--configure): 
 dependency problems - leaving unconfigured 
Setting up samba-common (3.0.28a-1ubuntu4.7) ... 
usage: tr [--verbose] [--name | --stdout] 
dpkg: error processing samba-common (--configure): 
 subprocess post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of smbclient: 
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.7); however: 
  Package samba-common is not configured yet. 
dpkg: error processing smbclient (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 linux-image-2.6.24-22-generic 
 linux-ubuntu-modules-2.6.24-22-generic 
 clamav-base 
 clamav-freshclam 
 clamav 
 clamtk 
 linux-image-generic 
 linux-restricted-modules-2.6.24-22-generic 
 linux-restricted-modules-generic 
 linux-generic 
 postgresql-client-8.3 
 postgresql-8.3 
 postgresql-contrib-8.3 
 postgresql-plperl-8.3 
 postgresql-plpython-8.3 
 postgresql-pltcl-8.3 
 samba-common 
 smbclient 
E: Sub-process /usr/bin/dpkg returned an error code (1) 




```

---

### Post by emanresu on 2008-12-01
mediajunkie,

i did one upgrade last week to the ..24-21 kernel aka 8.04.1. it didn't work at all. posted about it [here.]("http://ubuntuforums.org/showpost.php?p=6245190&postcount=193") after not getting answers and seeing more dismal results from other users, i just opted to stick with ..24-16 kernel aka 8.04. 

today, i installed the next upgrade and got kernel ..24-22. i tried to restart into that and still got nowhere, same error as before. so i commented all the newer kernels, all v8.04.1, out of /boot/grub/menu.lst and still just use kernel ..24-16. 

i downloaded an iso for 8.04.1, not sure which kernel version it is, but i'm not sure i want to use it. 8.04 still works fine for me and it looks like the "updates" had some effect, because i have a *control center* now under *system* on the upper toolbar. just not ready to try for any other major changes, since it seems like there are lots of problems left. if you look at the thread i linked to, in case you haven't yet, you'll see lots of people who are struggling with the upgrades. 

good luck

---

### Post by mediajunkie on 2008-12-21
The story continues, and keeps getting worse.
every update that comes out and I try to install will result in a nasty dependency error. I use 2 systems and one does fine on the updates and the other not. I have no clue what is going on. I could of course re-install the machine just like MS$ would suggest. But I want to know what is the reason for this issue so I can prevent it.

I there anybody out there that would know where to start?

Note: the traditional dpkg --configure -a and so on all fail.

---

### Post by stoian on 2008-12-25
can anybody post a solution here, for Jesus' sake?

---

