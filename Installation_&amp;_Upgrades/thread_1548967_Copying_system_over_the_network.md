---
title: "Copying system over the network"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Almucard on 2010-08-09
Hi, 
The goal I want to achieve is to copy Ubuntu from one computer to another using a network. (I have seven exactly the same computers without CD drives).

The procedure I am using  is as follows:
1. Install Ubuntu (and required software) on one computer [lab1]
2. Backup system (using backup.sh) [lab1]
3. Untar all backup (system) files on the server [server]
```

tar xvpjf ubuntu-2.tar.bz2 -C /diskless/eta64/NEW/
tar xvpjf home.tar.bz2 -C /diskless/eta64/NEW/home/

```4. Boot diskless Gentoo system from the server (using PXE /diskless/eta64/) [lab2]
5. Then using install_ubuntu.py I am: [lab2]
 a) creating and formating partitions
 b) copying files from  /diskless/eta64/NEW/ to drive
 c) update-grub and grub-install

After this I can boot Ubuntu on lab2 but system is not working properly e.g.:
 - no sound
 - reboot / shutdown not working (just restarts X)
 - sudo /usr/bin/jockey-gtk
```

Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 417, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 428, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 101, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 277, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 772, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 98, in backend
    self._dbus_iface = Backend.create_dbus_client()
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 686, in create_dbus_client
    obj = bus.get_object(DBUS_BUS_NAME, '/DeviceDriver')
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success

```

backup.sh:
```

#! /bin/bash
mkdir /mnt/ubuntu
mount /dev/sda7 /mnt/ubuntu
mount /dev/sda5 /mnt/ubuntu/boot

tar cpjf /mnt/home/system_boot.tar.bz2 --exclude=/mnt/ubuntu/proc --exclude=/mnt/ubuntu/lost+found --exclude=/mnt/ubuntu/mnt --exclude=/mnt/ubuntu/tmp --exclude=/mnt/ubuntu/sys --exclude=/mnt/ubuntu/media /mnt/ubuntu/
tar cpjf /mnt/home/home.tar.bz2 --exclude=/mnt/home/home.tar.bz2 --exclude=/mnt/home/system_boot.tar.bz2 --exclude=/mnt/home/backup.sh --exclude=/mnt/home/backup_tar.sh --exclude=/mnt/home/backup_boot --exclude=/mnt/home/backup_system /mnt/home/
 
```

install_ubuntu.py
```

#! /usr/bin/python

from sys import argv, exit
from os import system
from datetime import datetime

def main():

    if (len(argv)<2):
        print "[Please set host name, for example: ./install_ubuntu.py lab01 ]"
        exit(-1)

    ask1 = raw_input("\n[Install ubuntu? (this script will erese sda5, sda6,sda7)]y/n\n")
    if ask1=="y":
        
        start = datetime.now()

    #Remove all partitions and create new ones..
    #system("sfdisk /dev/hda -uM <<EOF\n,2000,0B\n,200\n,15000\n,,E\n,20000\n,,S\nEOF")
    
    # Format partitions
        system("mkfs.ext3 /dev/sda5" )
        system("mkswap /dev/sda6" )
        system("mkfs.ext4 /dev/sda7" )
        #system("mkfs.ext4 /dev/sda8" ) /home disk

        print "\n[Format - done]\n"

        system("mount /dev/sda7 /mnt/ubuntu")
        system("mkdir /mnt/ubuntu/boot")
        system("mkdir /mnt/ubuntu/home")

        system("mount /dev/sda5 /mnt/ubuntu/boot")
        system("mount /dev/sda8 /mnt/ubuntu/home")
        
        # make some dirs which are not in backup
        system("mkdir /mnt/ubuntu/dev")
        system("mkdir /mnt/ubuntu/sys")
        system("mkdir /mnt/ubuntu/proc")
        system("mkdir /mnt/ubuntu/mnt")
        system("mkdir /mnt/ubuntu/media")
        system("mkdir /mnt/ubuntu/tmp")
        system("chmod 777 /mnt/ubuntu/tmp")
        #system("mkdir /mnt/ubuntu/lost+found") already ther after format

        system("ls /mnt/ubuntu/ -la")

        ask2 = raw_input("\n[Disks ready copy files? (check above for errors!!!)]y/n\n")
        if ask2=="y":
            
            #remove all configs and Desktop (Better format home - DONE!!)
            system("rm /mnt/ubuntu/home/student/.* -rf") # TODO errors while rm . and rm ..
            system("rm /mnt/ubuntu/home/student/Desktop/ -rf")

            #copy system
            start_copy = datetime.now()
            system("cp /NEW/* /mnt/ubuntu/ -rp")
            end_copy = datetime.now()
            print "\n[ copy dt=%s ]\n"%str(end_copy-start_copy)

           
            #set host name
            system('echo %s > /mnt/ubuntu/etc/hostname'%argv[1])
            
            # mount drives in chroot
            system("mount -o bind /dev /mnt/ubuntu/dev")
            system("mount -t proc /proc /mnt/ubuntu/proc")

            print "\n[System has been copied... Running chroot - please run 'update-gurb and grub_install' ]\n"
            system("chroot /mnt/ubuntu/ /bin/bash")

            print "\n[Done - unmounting all drives]\n"
            system("umount /mnt/ubuntu/boot/ /mnt/ubuntu/home /mnt/ubuntu/dev /mnt/ubuntu/proc /mnt/ubuntu")
        
        end = datetime.now()
        print "\n[ full dt=%s ]\n"%str(end-start)

    print "Bye"

if __name__=='__main__':
    main()

```

Thank you in advance for your help..

P.S. Is there a batter way to copy the whole system over the net?

---

### Post by Almucard on 2010-08-09
The problem was with  /lib/dbus-1.0/dbus-daemon-launch-helper permissions:

```

student@lab03:~$ ls /lib/dbus-1.0/dbus-daemon-launch-helper -la
-rwxr-xr-- 1 root 1005 47520 2010-03-30 20:43 /lib/dbus-1.0/dbus-daemon-launch-helper
```While untaring system backup on PXE server group ID has been changed to host messagebus group ID (107 --> 1005)

To fix this just run:
```

chgrp messagebus /lib/dbus-1.0/dbus-daemon-launch-helper
chmod u+s /lib/dbus-1.0/dbus-daemon-launch-helper

```and in the long run use:
```

tar xvpjf system_boot.tar.bz2 -C /diskless/eta64/NEW/ --numeric-owner

```to extract files on PXE server...

Thank you for your attention

---

