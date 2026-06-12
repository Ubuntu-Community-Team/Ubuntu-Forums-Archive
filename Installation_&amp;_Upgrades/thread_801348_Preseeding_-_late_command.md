---
title: "Preseeding - late_command"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by rfmx on 2008-05-20
We have hundreds of machines intalled with Fedora. Because of the LTS version of Ubuntu and other resources available in this distribution, we decided to change all of our machines to Ubuntu. As we have so many machines, we used to make many kickstart based installations, easyng the administrator work. With ubuntu, we are trying to make our first preseed file but we miss many features we used to have with kickstart. We need a pre-script to ask the user some questions used in the installation. For this, we use the chvt, echo e read variables. For adittional stuff, we use a post-script wich downloads a tar.gz file with many scripts and execute them based on the user's answers.
1) how do we do our pre-scripts in preseeding? We tried the early_command but a i cannot chvt and show questions for the user to fill in the blanks. How do we do it?
2) how do we do our post-scripts in preseeding? We tried everything in the late_command but it doesn't work. We have already tried:
-d-i preseed/late_command string echo "TESTE" >> /target/etc/ceul
-d-i preseed/late_command string echo "TESTE" >> /etc/ceul
-d-i preseed/late_command string wget [http://10.200.105.215/pos-scripts/pos-script-ubuntu804](http://10.200.105.215/pos-scripts/pos-script-ubuntu804) | chroot /target /bin/bash
-d-i preseed/late_command string wget [http://10.200.105.215/pos-scripts/pos-script-ubuntu804](http://10.200.105.215/pos-scripts/pos-script-ubuntu804) && chmod +x ./pos-script-ubuntu804 && ./pos-script-ubuntu804
-d-i preseed/late_command chvt 3; apt-get update ; apt-get upgrade;touch /root/testepos

We know we are actually reading the preseed file in the boot because we load the language settings and the username. Please, does anybody can tell us what is going wrong with our preseeding file?
Thanks for any reply.

---

### Post by Partyboi2 on 2008-05-21
There is a package called system-config-kickstart in the ubuntu repo's that you can use to create kickstart files.
[B]
[/B]

---

### Post by GooglieS on 2008-12-10
Any news? How do u solve that?

---

### Post by bazzer on 2009-01-22
The last line of my preseed file looks similar to this:
```
d-i preseed/late_command string wget ftp://username:password@192.168.0.1/myinstallscript.sh -O /target/usr/local/bin/myinstallscript.sh; chmod 777 /target/usr/local/bin/myinstallscript.sh;
```

It wgets the install script from an ftp server (192.168.0.1), meaning I can change the script without burning a new disc. When the system reboots into the new system, you log in, and run myinstallscript.sh.

Also, I think you can only have one late_command.

---

### Post by 2ormore on 2009-03-25
I'm having the exactly same problem: preseed/late_command has no effect. I've tried a whole lot of combinations, including your basic echo tests -> nothing.

There's also nothing in the logs about running this command, so no help there either. Very frustrating.

I'm doing: Customized Ubuntu 8.10 installation -> remastersys backup -> usb-creator

Any ideas anyone?

---

### Post by agger on 2010-06-07
I'm having the same problem. Will write in this thread if I find a solution :-)

---

### Post by agger on 2010-07-04
> **agger said:**
> I'm having the same problem. Will write in this thread if I find a solution :-)

The preseed/late_command works fine, I've now found. However, you can only have one! Haven't tried kickstart, but there's no need to. One just needs to take into account that the installed system is located in /target/ and commands to be run on that system need to use chroot.

---

### Post by lowrizzle on 2010-07-22
I've got this working fine in CentOS, in the %pre section of the KS file I force a switch to TTY6, the user is prompted for IP/hostname/etc information which gets saved out to /tmp/includes, which is defined earlier in the KS file as '%include /tmp/includes'

This works great in Fedora/Centos/etc, but in Ubuntu it seems it can't write to /tmp/includes.  I've set a %pre directive to make sure the folder is fully writable and even to touch the file first since initially it was complaining the file didn't exist.  Is there a way to get this to work?

---

### Post by agger on 2010-07-23
> **lowrizzle said:**
> I've got this working fine in CentOS, in the %pre section of the KS file I force a switch to TTY6, the user is prompted for IP/hostname/etc information which gets saved out to /tmp/includes, which is defined earlier in the KS file as '%include /tmp/includes'

This works great in Fedora/Centos/etc, but in Ubuntu it seems it can't write to /tmp/includes.  I've set a %pre directive to make sure the folder is fully writable and even to touch the file first since initially it was complaining the file didn't exist.  Is there a way to get this to work?

I don't know if that's your problem, but I suppose it depends om what and where "/tmp/ is supposed ti be during installation. If you mean /tmp on the new install, you need to refer to /target/tmp. Above /target I don't think you can count on being able to write anywhere.

---

### Post by gregport on 2010-07-28
You can add the "in-target" keyword after string and the debian installer will automatically chroot to the newly installed system for you.    Here's my working late_command including the original comments from the d-i config:

```

# This command is run just before the install finishes, but when there is
# still a usable /target directory. You can chroot to /target and use it
# directly, or use the apt-install and in-target commands to easily install
# packages and run commands in the target system.

d-i preseed/late_command string in-target /usr/sbin/sysv-rc-conf puppet off 

```

---

### Post by OpenThinking on 2011-08-30
Hi!

1. Check the following: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
Generally, a script run from the seed file via late_command, cannot interact with the user. If you need to interact, there are generally three options:
*    Create a custom UDEB that interacts with debconf, and include it with the CD.
*    Create a 'firstrun' script that executes the first time the system boots, and disables itself on completion.
*    Access debconf directly within your script.

2. This command format worked for me in Ubuntu 11.04:
> d-i preseed/late_command string df > /target/home/df.txt

These were the disk filesystems available during late preseed:

> Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   254000       148    253852   0% /dev
/dev/sr0                723414    723414         0 100% /cdrom
/dev/sda1             20125340   2106856  16996176  11% /target
/dev/sda1             20125340   2106856  16996176  11% /dev/.static/dev
tmpfs                   254000       148    253852   0% /target/dev
/dev/sr0                723414    723414         0 100% /target/media/cdrom

Regards, Tobias

---

