---
title: "yet another mounting at root filesystem problem"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by jeremytaylor on 2006-06-07
Hi there, 
apologies for creating another thread on this but as I'm not had no problems with the installation only booting afterwards I didn't think it quite fit into the other thread.

I've tried both the graphical installer and the text one and end up with the same result. An unbootable system. If I wait for long enough I get into a very basic shell. From reading the forums it looks like this is a problem where the drives are mapped to the wrong places. Looking through /dev the only possible candidates for disks are sda but this is the one in grub and it doesn't boot. 

I get the message /bin/sh: can't access tty: job control turned off that others have had before. 

Does anyone have any actual solutions to this? Do the developers know about it? 

Any suggestions welcome before I tear my hair out. 

jeremy.

---

### Post by sinaen on 2007-06-24
I have a similar error. my disks all seem to be mounted but at the wrong places. but the system works and indicates the / root system to be a 80 gb disk but i know that it olny is to be a 10. gig disk it seems like the partitions are reversely mounted. in some kind of way 

df -h gives this
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.0G  6.6G  2.0G  78% /
varrun                506M  188K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  112K  506M   1% /proc/bus/usb
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sdb1             229G  182G   38G  83% /yoshi/naruto
/dev/sdd1             114G   98G   11G  91% /yoshi/bebop
/dev/sdc1              74G   31G   40G  44% /yoshi/trrnt

ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdb1  /dev/sdc  /dev/sdc1  /dev/sdd  /dev/sdd1  /dev/sde  /dev/sde1  /dev/sde2  /dev/sde5

                                                             cfdisk 2.12r

                                                          Disk Drive: /dev/sda
                                                    Size: 81964302336 bytes, 81.9 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 9964

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sdb
                                                   Size: 320072933376 bytes, 320.0 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 38913

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sdc
                                                    Size: 80026361856 bytes, 80.0 GB
                                          Heads: 16   Sectors per Track: 63   Cylinders: 155061

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sdd
                                                   Size: 123522416640 bytes, 123.5 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 15017

                                                              cfdisk 2.12r

                                                          Disk Drive: /dev/sde
                                                    Size: 10242892800 bytes, 10.2 GB
                                          Heads: 255   Sectors per Track: 63   Cylinders: 1245

---

