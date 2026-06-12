---
title: "Kernel panic-not syncing"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by Samundra_Shrestha on 2013-08-19
I recently did a force installation of locale using command

```
#$ dpkg -i --force-depends locale.deb - first tried this one as it failed I used another command listed below.

$ dpkg -i --force-all locale.deb
```

The installation went fine and showed no problem. It was then after around 10 minutes my GUI stopped working and I noticed No window and application would work. There were error reports that libdbus couldn't sync.

I then restarted my laptop and got the Kernel panic error.

Just above the call trace, I have these following lines

```
/usr/bin/init: error while loading shared libraries: libdbus-1.so.3:
Kernel panic - not syncing: Attempted to kill init!
```

Below is the attached screenshot of the Kernel Panic

[ATTACH=CONFIG]245497[/ATTACH]

I then boot through the live USB and looked into the log files and it seems there are bunch of errors in the log files.

Contents of casper.log
```

stdin: error 0
/init: line 3: can't open /dev/sr0: No medium found
/init: line 3: can't open /dev/sr0: No medium found
stdin: error 0
stdin: error 0
stdin: error 0
umount: can't umount /cdrom: Device or resource busy
/init: line 3: can't open /dev/sr0: No medium found
stdin: error 0
/init: line 3: can't open /dev/sr0: No medium found
stdin: error 0
umount: can't umount /cdrom: Device or resource busy
/init: line 3: can't open /dev/sr0: No medium found
stdin: error 0
/init: line 3: can't open /dev/sr0: No medium found
stdin: error 0
umount: can't umount /cdrom: Device or resource busy
/init: line 3: can't open /dev/sr0: No medium found
ln: /root/media/cdrom/cdrom: File exists
adduser: The user `custom' already exists.
Could not create certificate. Openssl output was:
unable to load 'random state'
This means that the random number generator has not been seeded
with much random data.
Generating a 2048 bit RSA private key
Error Generating Key
3073947800:error:24064064:random number generator:SSLEAY_RAND_BYTES:PRNG not seeded:md_rand.c:524:You need to read the OpenSSL FAQ, http://www.openssl.org/support/faq.html
3073947800:error:04081003:rsa routines:RSA_BUILTIN_KEYGEN:BN lib:rsa_gen.c:208:
Traceback (most recent call last):
  File "/usr/bin/fontconfig-voodoo", line 102, in <module>
    main()
  File "/usr/bin/fontconfig-voodoo", line 88, in main
    fc.setConfigBasedOnLocale()
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/FontConfig.py", line 114, in setConfigBasedOnLocale
    lang = self.li.getUserDefaultLanguage()[1]
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py", line 244, in getUserDefaultLanguage
    bus = dbus.SystemBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 202, in __new__
    private=private)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 88, in apport_excepthook
    pr.add_proc_info()
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 386, in add_proc_info
    raise ValueError('invalid process')
ValueError: invalid process

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/fontconfig-voodoo", line 102, in <module>
    main()
  File "/usr/bin/fontconfig-voodoo", line 88, in main
    fc.setConfigBasedOnLocale()
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/FontConfig.py", line 114, in setConfigBasedOnLocale
    lang = self.li.getUserDefaultLanguage()[1]
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py", line 244, in getUserDefaultLanguage
    bus = dbus.SystemBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 202, in __new__
    private=private)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
Using CD-ROM mount point /cdrom/
Identifying.. [31dfadc5c2162950cff41684f01d29ed-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?
ln: /root/usr/sbin/update-initramfs: File exists
chmod: /root/usr/sbin/update-initramfs: No such file or directory

```

Please help how should I approach this problem.

---

### Post by MG&amp;TL on 2013-08-20
I seem to recall seeing this before, although I can't remember where. I did find an LQ thread here though: [https://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-attempted-to-kill-init-313273/](https://www.linuxquestions.org/questions/linux-kernel-70/kernel-panic-not-syncing-attempted-to-kill-init-313273/)

A couple of points from the thread:
[LIST]
[*]*init* hasn't actually been *killed* per se, it has merely died.
[*]*init *isn't allowed to die, hence the kernel panic.
[*]Try holding Shift during boot and booting an older kernel
[*]Check hardware (i.e. *memtest*)
[/LIST]

Can you try the last two points and post back the results?

---

### Post by Samundra_Shrestha on 2013-08-20
I tried various suggestions given in the forums and I followed the instructions here. [http://technotalk.tumblr.com/post/546121052/recovering-kernel-from-crashed-ubuntu-kernel-panic-not-s](http://technotalk.tumblr.com/post/546121052/recovering-kernel-from-crashed-ubuntu-kernel-panic-not-s)

I could chroot in the /mnt/linux which is my linux partition mounted locally.

But then any command I try to run gives error such as 

```

root@custom:/# ls
ls: error while loading shared libraries: libattr.so.1: cannot open shared object file: No such file or directory
root@custom:/# man ls
man: error while loading shared libraries: libpipeline.so.1: cannot open shared object file: No such file or directory
root@custom:/# find
Segmentation fault (core dumped)
root@custom:/#
root@custom:/# mv
mv: error while loading shared libraries: libattr.so.1: cannot open shared object file: No such file or directory

```

It seems like it cannot find the library files required to execute those commands. I also tried to copy and paste few library files from my live usb disk but It seems go in infinite loop and never end. Is there anything I can do to make those command work so that I can carry out other instructed tasks.

i also haven't ran any memory test. Currently I am backing up my data, if I couldn't find any solution then I am going to re-install Ubuntu.

---

### Post by MG&amp;TL on 2013-08-20
> **Samundra_Shrestha said:**
> 
It seems like it cannot find the library files required to execute those commands. I also tried to copy and paste few library files from my live usb disk but It seems go in infinite loop and never end. Is there anything I can do to make those command work so that I can carry out other instructed tasks.

i also haven't ran any memory test. Currently I am backing up my data, if I couldn't find any solution then I am going to re-install Ubuntu.

To be honest, I'm not really sure what's happened. You appear to have a completely wrecked library system. :confused:

Your suggestion to reinstall may be the best and safest option, regretfully.

---

