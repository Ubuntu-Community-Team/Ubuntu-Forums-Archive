---
title: "vmware doesn't start"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by WaWeeT on 2006-07-15
I have problem with starting vmware server

```
waweet@ubuntu:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

waweet@ubuntu:~$
```


so I do this:

```
waweet@ubuntu:~$ sudo /usr/bin/vmware-config.pl
Password:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
```



so I don't know which directory to choose!  This default doesn't work
](*,)

---

### Post by rcarring on 2006-07-15
Before you run this command again, install gcc and make, also install the correct linux-headers for your kernel. All of these are required for vmware to compile and/or re-compile its own modules and drivers.

---

### Post by tappad on 2006-07-15
Funny, i was just doing the same thing..
run 
sudo apt-get install linux-headers-`uname -r`

then when prompted : What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

enter: /usr/src/linux-headers-2.6.15-26-k7/include

---

### Post by WaWeeT on 2006-07-16
thanks guys....in working

---

