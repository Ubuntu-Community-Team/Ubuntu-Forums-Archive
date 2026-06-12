---
title: "partial upgrade"
date: 2013-11-24
forum: Installation &amp; Upgrades
---

### Post by amr-elfiky on 2013-11-24
i didn't log on the internet for about a week then when i got connected to the internet i tried to update the system _i'm running ubuntu 13.10_ it said it needs partial upgrade .when i click partial upgrade ,it says that the system is up to date and cancels .
when i click "continue" , it says "software index is broken .it is impossibe to install or remove any software .please use the package manager synaptic or run  sudo apt-get install -f   in terminal to fix the issue at first .
i did that .that's the outcome in terminal..
"The following packages will be REMOVED:
  linux-image-3.11.0-12-generic linux-image-extra-3.11.0-12-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
17 not fully installed or removed.
After this operation, 136 MB disk space will be freed.
Do you want to continue [Y/n]? "
i click y but it doesn't work .that's the outcome ...
"(Reading database ... 401370 files and directories currently installed.)
Removing linux-image-extra-3.11.0-12-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.11.0-12-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.11.0-12-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.11.0-12-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.11.0-12-generic.postrm line 328.
dpkg: error processing linux-image-3.11.0-12-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.11.0-12-generic
 linux-image-3.11.0-12-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ "
can anyone help me please ?

---

### Post by fantab on 2013-11-24
Never do a 'Partial Upgrade' in future.

In Terminal run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
... and post the output here. 

Please use code tag '#' to paste your output. ['Go Advanced' at bottom to get a full editor, select your output and use # to wrap the text as code], just like I've done to wrap the above commands in code.

---

### Post by JRV on 2013-11-24
Here is more info about partial upgrades:

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by amr-elfiky on 2013-11-24
```
Ign http://archive.canonical.com saucy InReleaseIgn http://archive.ubuntu.com saucy InRelease                                  
Hit http://archive.canonical.com saucy Release.gpg                             
Hit http://deb.opera.com stable InRelease                                      
Ign http://archive.ubuntu.com saucy-updates InRelease                          
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://extras.ubuntu.com saucy InRelease                                   
Hit http://archive.canonical.com saucy Release                                 
Hit http://deb.opera.com stable InRelease                                      
Ign http://archive.ubuntu.com saucy-security InRelease                         
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://archive.ubuntu.com saucy Release.gpg                                
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://archive.ubuntu.com saucy-updates Release.gpg                        
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://archive.ubuntu.com saucy-security Release.gpg                       
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://archive.ubuntu.com saucy Release                                    
Hit http://archive.ubuntu.com saucy-updates Release                            
Hit http://archive.ubuntu.com saucy-security Release                           
Hit http://archive.ubuntu.com saucy/main Sources                               
Hit http://archive.ubuntu.com saucy/universe Sources                           
Hit http://archive.ubuntu.com saucy/multiverse Sources                         
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Hit http://archive.ubuntu.com saucy/main i386 Packages                         
Ign http://archive.canonical.com saucy/partner Translation-en                  
Hit http://archive.ubuntu.com saucy/universe i386 Packages                     
Ign http://ppa.launchpad.net saucy/main Translation-en_US                      
Hit http://archive.ubuntu.com saucy/multiverse i386 Packages                   
Ign http://ppa.launchpad.net saucy/main Translation-en               
Ign http://extras.ubuntu.com saucy/main Translation-en_US            
Ign http://extras.ubuntu.com saucy/main Translation-en               
Hit http://archive.ubuntu.com saucy/main Translation-en
Hit http://archive.ubuntu.com saucy/multiverse Translation-en
Hit http://archive.ubuntu.com saucy/universe Translation-en
Ign http://deb.opera.com stable/non-free Translation-en_US
Hit http://archive.ubuntu.com saucy-updates/main Sources
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://archive.ubuntu.com saucy-updates/universe Sources
Ign http://deb.opera.com stable/non-free Translation-en_US
Hit http://archive.ubuntu.com saucy-updates/multiverse Sources
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://archive.ubuntu.com saucy-updates/main i386 Packages
Hit http://archive.ubuntu.com saucy-updates/universe i386 Packages
Hit http://archive.ubuntu.com saucy-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com saucy-updates/main Translation-en
Hit http://archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://archive.ubuntu.com saucy-security/main Sources
Hit http://archive.ubuntu.com saucy-security/universe Sources
Hit http://archive.ubuntu.com saucy-security/multiverse Sources
Hit http://archive.ubuntu.com saucy-security/main i386 Packages
Hit http://archive.ubuntu.com saucy-security/universe i386 Packages
Hit http://archive.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://archive.ubuntu.com saucy-security/main Translation-en
Hit http://archive.ubuntu.com saucy-security/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-security/universe Translation-en
Ign http://archive.ubuntu.com saucy/main Translation-en_US
Ign http://archive.ubuntu.com saucy/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/main Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-security/main Translation-en_US
Ign http://archive.ubuntu.com saucy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-security/universe Translation-en_US
Reading package lists... Done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ 



```

thanks a lot ,but it says here that it would resolve in few hours .in my case it's been 2 weeks .maybe it's something else .thanks a lot anyway .

---

### Post by fantab on 2013-11-24
> **fantab said:**
> Never do a 'Partial Upgrade' in future.

In Terminal run:
```
sudo apt-get update
**sudo apt-get dist-upgrade**
```
... and post the output here. 



Lets see the output of 'dist-upgrade'...

---

### Post by amr-elfiky on 2013-11-25
sorry about that 
```
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get dist-upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
Need to get 47.1 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ saucy/main linux-image-3.11.0-12-generic i386 3.11.0-12.19 [13.6 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ saucy/main linux-image-extra-3.11.0-12-generic i386 3.11.0-12.19 [33.5 MB]
Fetched 47.1 MB in 12min 48s (61.2 kB/s)                                       
dpkg: error processing linux-image-3.11.0-12-generic (--configure):
 package linux-image-3.11.0-12-generic is not ready for configuration
 cannot configure (current status `half-installed')
Setting up linux-image-3.11.0-13-generic (3.11.0-13.20) ...
No apport report written because MaxReports is reached already
                                                              Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-13-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.8.0-29-generic (3.8.0-29.42) ...
No apport report written because MaxReports is reached already
                                                              Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-3.8.0-30-generic (3.8.0-30.44) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-30-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-3.8.0-31-generic (3.8.0-31.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-31-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up memtest86+ (4.20-1.1ubuntu5) ...
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.


dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up grub-pc (2.00-19ubuntu2.1) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.11.0-13-generic:
 linux-image-extra-3.11.0-13-generic depends on linux-image-3.11.0-13-generic; however:
  Package linux-image-3.11.0-13-generic is not configured yet.


dpkg: error processing linux-image-extra-3.11.0-13-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.11.0-13-generic; however:
  Package linux-image-3.11.0-13-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.11.0-13-generic; however:
  Package linux-image-extra-3.11.0-13-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.11.0.13.14); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-generic (= 3.11.0.13.14); however:
  Package linux-generic is not configured yet.


dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: error processing linux-image-extra-3.11.0-12-generic (--configure):
 package linux-image-extra-3.11.0-12-generic is not ready for configuration
 cannot configure (current status `half-installed')
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-29-generic:
 linux-image-extra-3.8.0-29-generic depends on linux-image-3.8.0-29-generic; however:
  Package linux-image-3.8.0-29-generic is not configured yet.


dpkg: error processing linux-image-extra-3.8.0-29-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-30-generic:
 linux-image-extra-3.8.0-30-generic depends on linux-image-3.8.0-30-generic; however:
  Package linux-image-3.8.0-30-generic is not configured yet.


dpkg: error processing linux-image-extra-3.8.0-30-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-31-generic:
 linux-image-extra-3.8.0-31-generic depends on linux-image-3.8.0-31-generic; however:
  Package linux-image-3.8.0-31-generic is not configured yet.


dpkg: error processing linux-image-extra-3.8.0-31-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-generic (= 3.11.0.13.14); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.11.0-12-generic
 linux-image-3.11.0-13-generic
 linux-image-3.8.0-29-generic
 linux-image-3.8.0-30-generic
 linux-image-3.8.0-31-generic
 memtest86+
 ubuntu-standard
 grub-pc
 linux-image-extra-3.11.0-13-generic
 linux-image-generic
 linux-generic
 linux-generic-pae
 linux-image-extra-3.11.0-12-generic
 linux-image-extra-3.8.0-29-generic
 linux-image-extra-3.8.0-30-generic
 linux-image-extra-3.8.0-31-generic
 linux-image-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ 



```
there it is .

---

### Post by fantab on 2013-11-25
Post the output of:
```
df -h
```

---

### Post by ian-weisser on 2013-11-25
The first 12 lines of /etc/default/grub should look like:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Is that what yours looks like?
I suspect you might be missing a quotation mark (") on line 11.

---

### Post by amr-elfiky on 2013-11-25
```
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
/dev/sda6        71G   53G   16G  78% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           297M  1.2M  296M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  876K  1.5G   1% /run/shm
none            100M   76K  100M   1% /run/user
/dev/sda3       204G  199G  5.0G  98% /media/amr/B6A4A6BEA4A6810B
/dev/sda2        20G   18G  2.7G  87% /media/amr/5E023BD1023BACC1
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ 







```

that's my[COLOR=#000000] /etc/default/grub
[/COLOR] [CODE[COLOR=#000000]# If you change this file, run 'update-grub' afterwards to update[/COLOR]# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=â€quiet splash profileâ€ 
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start [COLOR=#000000]#GRUB_INIT_TUNE="480 440 1"[/COLOR]][/CODE]

```
[COLOR=#000000]# If you change this file, run 'update-grub' afterwards to update[/COLOR]# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=â€quiet splash profileâ€ 
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start [COLOR=#000000]#GRUB_INIT_TUNE="480 440 1"[/COLOR]
```

i think i have the quotation marks . it must be something else .

---

### Post by ian-weisser on 2013-11-25
> **amr-elfiky said:**
> ```

GRUB_CMDLINE_LINUX_DEFAULT=â&#8364;quiet splash profileâ&#8364; 
GRUB_CMDLINE_LINUX=""
```

Those are definitely not quotation marks. See the line below it for comparison?

At some point, you seem to have edited this line in one of GRUBs config files. I'm not a GRUB expert, so let's hope you remember what changes you made. But you used a word processor or other non-text-editor or non-UTF-8 encoding system. They *looked* like quotes to you - but they weren't.

Edit the file in vi or nano or gedit or some other *text editor*, and replace 'â&#8364;' with plain old '"'. That will get your package manager working again...but until you fix the actual GRUB config file you changed, the problem will certainly recur.

The problem will recur (and break your package manager again) every time grub updates it's config list. That happens every time a kernel gets added or removed - a few days or weeks. Each update will re-introduce the non-quotes from the config file you originally changed...probably one of the files in /etc/grub.d/

---

### Post by amr-elfiky on 2013-11-26
i just opened [COLOR=#000000] /etc/default/grub  with thunar file manager .
forgive me ,i'm not really good with ubuntu .
anyway the outcome looks a little bit different that it was on chromium .
there it is .```
[/COLOR]# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash profile” 
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start

#GRUB_INIT_TUNE="480 440 1"[COLOR=#000000]
```[/COLOR]

---

### Post by ian-weisser on 2013-11-26
> **amr-elfiky said:**
> i just opened [COLOR=#000000] /etc/default/grub  with thunar file manager .[/COLOR][COLOR=#000000]

Don't do that. Thunar is not a text editor.
Thunar told some other application to open the file. But that application was not a text editor.
A text editor is *different* than a word processor.

Using Thunar on a notebook likely means that you use Xubuntu. Mousepad is the text editor included with Xubuntu. 
Open Mousepad using **sudo mousepad /etc/default/grub** . Don't open it using Thunar, unless you know how to open (and save) root files with a different application.

After you put real (machine-recognized) quotes and save the file, run the **sudo update-grub** command to update the config file that grub actually uses at startup. If you get an error message, stop and post the session here.


[/COLOR]> **amr-elfiky said:**
> ```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash profile&#8221; 
GRUB_CMDLINE_LINUX=""
```
Do you see how both lines have quote marks? But the marks look different?
They are different characters.
To humans, both mean the same thing: Quote Marks.
To machines, that difference prevents update-grub from working....which has cascaded into the problem you are having with your package manager.

---

### Post by amr-elfiky on 2013-11-27
i am using ubuntu 13.10 .it's just i'm really really bad with terminal and editing stuff !
i don't know how to open this.. [COLOR=#000000]/etc/default/grub...
i tried to open it with thunar file manager and it opened it with gedit text editor .
should i just edit the file with gedit ?
plus , for some reason i tried to run update manager and it worked and started updating .i don't know how .
but it keeps asking for updating "ubuntu base" .it's something nothing more than 2 [/COLOR][COLOR=#444444][FONT=arial]MB and it keeps asking for restart after installation .
does this by anyway have anything to do with grub ?[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-11-27
amr-elfiky; Hi !

As Ian is presently off-line, I will try and take up some of his slack ( I should only hope to fill his shoes !) .
Not to know is not a sin, none of us were born knowing !

Editing with gedit is just fine .. make a backup of the file to be edited first .. standard operating procedure. Never can tell what might happen !

Command line method.
```

sudo cp /etc/default/grub /etc/default/grub-orig
gksudo gedit /etc/default/grub

```
And as you are now able to update, may no longer have any relevance. But, will not hurt to look.

In respect to "asking for restart after installation" not related to grub, this is generally due to a system/kernel update in that the update cannot be completed while the file system is in use, thus the reboot to complete the update.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-11-27
It is difficult to tell if your system is now working properly, and what you did to fix it...or if you have some other problem, or what that problem may be.

We are not psychic. We cannot see your screen.

If you still have a problem, please give us a detailed description. Show us exactly what the terminal or application is telling you. Show us the entirer elevant terminal session..

---

### Post by fantab on 2013-11-27
In 13.10 'gksudo' is not installed by default. Instead use:

```
sudo gedit /etc/default/grub
```

If you are on Xubuntu then its possible that you may have 'leafpad' as your text-editor. In that case replace 'gedit' with 'leafpad'.

---

### Post by QIII on 2013-11-27
I would install gksudo and use that, personally.

You should always use gksudo with graphical apps.  Not doing so can lead to odd file permission issues.  In this case it might make no difference, but it's a bad habit to get into.

aysiu has a great little discussion of the issues [here]("http://www.psychocats.net/ubuntu/graphicalsudo").

---

### Post by amr-elfiky on 2013-11-28
hi ,Bashing-om .
i ran the commands you told me and it opened grub with gedit .
am i on the right way ?

hi,fantab .
i ran the gedit command you told me .terminal told me i'm not root !
that's the outcome ..```
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo gedit /etc/default/grub[sudo] password for amr: 


(gedit:17697): IBUS-WARNING **: The owner of /home/amr/.config/ibus/bus is not root!









```

---

### Post by fantab on 2013-11-28
Yes that is correct. After you run the command you will be prompted to enter your password after which gedit will open... just ignore the warning... its not important.

---

### Post by amr-elfiky on 2013-11-29
guys , i edited grub using gedit and saved the file then updated grub that was the output ..
```
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo gedit /etc/default/grub[sudo] password for amr: 


(gedit:470): IBUS-WARNING **: The owner of /home/amr/.config/ibus/bus is not root!
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ 





```
is this all right ?

---

### Post by ian-weisser on 2013-11-29
Yes, that looks good.
Well done!

---

### Post by amr-elfiky on 2013-11-29
thank you ,Ian ...thank you ,fantab .thanks a lot ,guys all of you .you really helped me.

---

### Post by fantab on 2013-11-29
That's good.
You have 'old & unused' kernels in there. Clean those up, use the instructions [**HERE**]("http://ubuntuforums.org/showthread.php?t=2190453&p=12859778#post12859778").

Mark the Thread as 'Solved' using Thread Tools.

---

### Post by amr-elfiky on 2013-11-30
hey,fantab ,i'm trying to remove the old kernils as you told me .
i'm not sure if it's gonna remove the kernil i'm using now .
that's the output ..```
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo update-grub[sudo] password for amr: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ uname -r
3.11.0-13-generic
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.8.0-27 linux-headers-3.8.0-27-generic
  linux-image-3.8.0-27-generic linux-image-extra-3.8.0-27-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
13 not fully installed or removed.
Remv linux-headers-3.8.0-27-generic [3.8.0-27.40]
Remv linux-headers-3.8.0-27 [3.8.0-27.40]
Remv linux-image-extra-3.8.0-27-generic [3.8.0-27.40]
Remv linux-image-3.8.0-27-generic [3.8.0-27.40]
Conf linux-image-3.11.0-13-generic (3.11.0-13.20 Ubuntu:13.10/saucy-updates [i386])
Conf linux-image-3.8.0-29-generic (3.8.0-29.42  [i386])
Conf linux-image-3.8.0-30-generic (3.8.0-30.44  [i386])
Conf linux-image-3.8.0-31-generic (3.8.0-31.46  [i386])
Conf memtest86+ (4.20-1.1ubuntu5 Ubuntu:13.10/saucy [i386])
Conf ubuntu-standard (1.307 Ubuntu:13.10/saucy [i386])
Conf grub-pc (2.00-19ubuntu2.1 Ubuntu:13.10/saucy-updates [i386])
Conf linux-image-extra-3.11.0-13-generic (3.11.0-13.20 Ubuntu:13.10/saucy-updates [i386])
Conf linux-image-extra-3.8.0-29-generic (3.8.0-29.42  [i386])
Conf linux-image-extra-3.8.0-30-generic (3.8.0-30.44  [i386])
Conf linux-image-extra-3.8.0-31-generic (3.8.0-31.46  [i386])
Conf linux-image-generic (3.11.0.13.14 Ubuntu:13.10/saucy-updates [i386])
Conf linux-image-generic-pae (3.11.0.13.14 Ubuntu:13.10/saucy-updates [i386])
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ 



```
should i proceed or reboot and check again ?

---

### Post by ian-weisser on 2013-11-30
You should not need to reboot.
Rebooting is only to change to the *current* kernel.

You seem to be running kernel 3.11.0-13-generic (uname -r)
You can delete kernels 3.8.0-29, -30, and -31
You can delete them by running the script again (proceed) a couple times, or other ways too.

---

### Post by amr-elfiky on 2013-12-01
i ran the commands and they seemed to work fine but that is one looong output !
```
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purgeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.8.0-27* linux-headers-3.8.0-27-generic*
  linux-image-3.8.0-27-generic* linux-image-extra-3.8.0-27-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
13 not fully installed or removed.
After this operation, 195 MB disk space will be freed.
(Reading database ... 302798 files and directories currently installed.)
Removing linux-headers-3.8.0-27-generic ...
Removing linux-headers-3.8.0-27 ...
Removing linux-image-extra-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-extra-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Removing linux-image-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Purging configuration files for linux-image-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Setting up linux-image-3.11.0-13-generic (3.11.0-13.20) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-3.8.0-29-generic (3.8.0-29.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-3.8.0-30-generic (3.8.0-30.44) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-3.8.0-31-generic (3.8.0-31.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up memtest86+ (4.20-1.1ubuntu5) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up ubuntu-standard (1.307) ...
Setting up grub-pc (2.00-19ubuntu2.1) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-extra-3.11.0-13-generic (3.11.0-13.20) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.11.0-13-generic /boot/vmlinuz-3.11.0-13-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-extra-3.8.0-29-generic (3.8.0-29.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-extra-3.8.0-30-generic (3.8.0-30.44) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-extra-3.8.0-31-generic (3.8.0-31.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Setting up linux-image-generic (3.11.0.13.14) ...
Setting up linux-image-generic-pae (3.11.0.13.14) ...
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get clean
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get update
Ign http://archive.canonical.com saucy InRelease
Ign http://archive.ubuntu.com saucy InRelease                                  
Ign http://extras.ubuntu.com saucy InRelease                                   
Hit http://archive.canonical.com saucy Release.gpg                             
Ign http://archive.ubuntu.com saucy-updates InRelease                          
Ign http://ppa.launchpad.net saucy InRelease                                   
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://archive.canonical.com saucy Release                                 
Hit http://deb.opera.com stable InRelease                                      
Ign http://archive.ubuntu.com saucy-security InRelease                         
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://deb.opera.com stable InRelease                                      
Hit http://archive.ubuntu.com saucy Release.gpg                                
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://archive.ubuntu.com saucy-updates Release.gpg                        
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Hit http://archive.ubuntu.com saucy-security Release.gpg                       
Hit http://archive.ubuntu.com saucy Release                                    
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://archive.ubuntu.com saucy-updates Release                            
Hit http://archive.ubuntu.com saucy-security Release                           
Hit http://archive.ubuntu.com saucy/main Sources                               
Hit http://archive.ubuntu.com saucy/universe Sources                           
Hit http://archive.ubuntu.com saucy/multiverse Sources                         
Hit http://archive.ubuntu.com saucy/main i386 Packages                         
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Hit http://archive.ubuntu.com saucy/universe i386 Packages                     
Ign http://ppa.launchpad.net saucy/main Translation-en_US                      
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign http://extras.ubuntu.com saucy/main Translation-en_US                      
Hit http://archive.ubuntu.com saucy/multiverse i386 Packages                   
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://archive.ubuntu.com saucy/main Translation-en              
Hit http://archive.ubuntu.com saucy/multiverse Translation-en
Hit http://archive.ubuntu.com saucy/universe Translation-en
Hit http://archive.ubuntu.com saucy-updates/main Sources
Hit http://archive.ubuntu.com saucy-updates/universe Sources
Ign http://deb.opera.com stable/non-free Translation-en_US
Hit http://archive.ubuntu.com saucy-updates/multiverse Sources
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://archive.ubuntu.com saucy-updates/main i386 Packages
Ign http://deb.opera.com stable/non-free Translation-en_US
Hit http://archive.ubuntu.com saucy-updates/universe i386 Packages
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://archive.ubuntu.com saucy-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com saucy-updates/main Translation-en
Hit http://archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://archive.ubuntu.com saucy-security/main Sources
Hit http://archive.ubuntu.com saucy-security/universe Sources
Hit http://archive.ubuntu.com saucy-security/multiverse Sources
Hit http://archive.ubuntu.com saucy-security/main i386 Packages
Hit http://archive.ubuntu.com saucy-security/universe i386 Packages
Hit http://archive.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://archive.ubuntu.com saucy-security/main Translation-en
Hit http://archive.ubuntu.com saucy-security/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-security/universe Translation-en
Ign http://archive.ubuntu.com saucy/main Translation-en_US
Ign http://archive.ubuntu.com saucy/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/main Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-security/main Translation-en_US
Ign http://archive.ubuntu.com saucy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-security/universe Translation-en_US
Reading package lists... Done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ 



```

---

### Post by fantab on 2013-12-01
> amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
[COLOR=#a52a2a]Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic[/COLOR]
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2

There are still some older kernels that are not being removed. Run those commands again and see if those old kernels are removed. Otherwise you are good.
When the next ubuntu version is released and when you upgrade do a Fresh install, instead of upgrading.

---

### Post by amr-elfiky on 2013-12-01
i ran ubuntu tweak's janitor .it said i still have some old kernils but their sizes were 0 MBs .anyway i ran the janitor and it said that it removed the old kernils and the system was clean ! 
just to make sure i ran your commands again, fantab .there's the output ...
```
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo update-grub[sudo] password for amr: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ uname -r
3.11.0-13-generic
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get clean
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get update
Ign http://archive.canonical.com saucy InRelease
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://extras.ubuntu.com saucy InRelease                                   
Hit http://deb.opera.com stable InRelease                                      
Hit http://archive.canonical.com saucy Release.gpg                             
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Ign http://archive.ubuntu.com saucy InRelease                                  
Hit http://deb.opera.com stable InRelease                                      
Hit http://archive.canonical.com saucy Release                                 
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Ign http://archive.ubuntu.com saucy-updates InRelease                          
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Ign http://archive.ubuntu.com saucy-security InRelease                         
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://archive.ubuntu.com saucy Release.gpg                                
Hit http://archive.ubuntu.com saucy-updates Release.gpg                        
Hit http://archive.ubuntu.com saucy-security Release.gpg                       
Hit http://archive.ubuntu.com saucy Release                                    
Ign http://archive.canonical.com saucy/partner Translation-en_US               
Ign http://ppa.launchpad.net saucy/main Translation-en_US                      
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Hit http://archive.ubuntu.com saucy-updates Release                            
Ign http://extras.ubuntu.com saucy/main Translation-en_US                      
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://archive.ubuntu.com saucy-security Release
Hit http://archive.ubuntu.com saucy/main Sources                      
Hit http://archive.ubuntu.com saucy/universe Sources
Hit http://archive.ubuntu.com saucy/multiverse Sources
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://archive.ubuntu.com saucy/main i386 Packages
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Hit http://archive.ubuntu.com saucy/universe i386 Packages
Hit http://archive.ubuntu.com saucy/multiverse i386 Packages
Hit http://archive.ubuntu.com saucy/main Translation-en
Hit http://archive.ubuntu.com saucy/multiverse Translation-en
Hit http://archive.ubuntu.com saucy/universe Translation-en
Hit http://archive.ubuntu.com saucy-updates/main Sources
Hit http://archive.ubuntu.com saucy-updates/universe Sources
Hit http://archive.ubuntu.com saucy-updates/multiverse Sources
Hit http://archive.ubuntu.com saucy-updates/main i386 Packages
Hit http://archive.ubuntu.com saucy-updates/universe i386 Packages
Hit http://archive.ubuntu.com saucy-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com saucy-updates/main Translation-en
Hit http://archive.ubuntu.com saucy-updates/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-updates/universe Translation-en
Hit http://archive.ubuntu.com saucy-security/main Sources
Hit http://archive.ubuntu.com saucy-security/universe Sources
Hit http://archive.ubuntu.com saucy-security/multiverse Sources
Hit http://archive.ubuntu.com saucy-security/main i386 Packages
Hit http://archive.ubuntu.com saucy-security/universe i386 Packages
Hit http://archive.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://archive.ubuntu.com saucy-security/main Translation-en
Hit http://archive.ubuntu.com saucy-security/multiverse Translation-en
Hit http://archive.ubuntu.com saucy-security/universe Translation-en
Ign http://archive.ubuntu.com saucy/main Translation-en_US
Ign http://archive.ubuntu.com saucy/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/main Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com saucy-security/main Translation-en_US
Ign http://archive.ubuntu.com saucy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com saucy-security/universe Translation-en_US
Reading package lists... Done
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
amr@amr-Compaq-Presario-CQ61-Notebook-PC:~$ 



```

---

### Post by fantab on 2013-12-01
Good... Its all clean. 
You can go ahead and mark this Thread as 'Solved' using Thread tools.

Regards...

---

### Post by amr-elfiky on 2013-12-02
thanks,guys . i really appreciate it .

---

