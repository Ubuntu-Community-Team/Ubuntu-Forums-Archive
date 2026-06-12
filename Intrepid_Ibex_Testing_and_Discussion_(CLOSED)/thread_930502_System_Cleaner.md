---
title: "System Cleaner"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-09-26
So whos had a go at testing system cleaner? I like it :)

I just raised three bugs on the gtk version.

---

### Post by mc4100 on 2008-09-26
Doesn't work for me ... don't know if it's a bug, or just me:
```
$ sudo apt-get install system-cleaner-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-fstab system-cleaner
The following NEW packages will be installed
  python-fstab system-cleaner system-cleaner-gtk
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/31.0kB of archives.
After this operation, 373kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package python-fstab.
(Reading database ... 61870 files and directories currently installed.)
Unpacking python-fstab (from .../python-fstab_1.2-0ubuntu1_all.deb) ...
Selecting previously deselected package system-cleaner.
Unpacking system-cleaner (from .../system-cleaner_1.8-0ubuntu1_all.deb) ...
Selecting previously deselected package system-cleaner-gtk.
Unpacking system-cleaner-gtk (from .../system-cleaner-gtk_1.8-0ubuntu1_all.deb) ...
Setting up python-fstab (1.2-0ubuntu1) ...

Setting up system-cleaner (1.8-0ubuntu1) ...

Setting up system-cleaner-gtk (1.8-0ubuntu1) ...

$ system-cleaner-gtk
Traceback (most recent call last):
  File "/usr/bin/system-cleaner-gtk", line 28, in <module>
    app.run(systemcleaner.GtkUserInterface)
  File "/usr/lib/python2.5/site-packages/systemcleaner/app.py", line 54, in run
    setup_logging()
  File "/usr/lib/python2.5/site-packages/systemcleaner/app.py", line 38, in setup_logging
    handler = logging.handlers.SysLogHandler("/dev/log")
  File "/usr/lib/python2.5/logging/handlers.py", line 594, in __init__
    self._connect_unixsocket(address)
  File "/usr/lib/python2.5/logging/handlers.py", line 609, in _connect_unixsocket
    self.socket.connect(address)
  File "<string>", line 1, in connect
socket.error: (2, 'No such file or directory')

```

---

### Post by plun on 2008-09-26
Testing without checking any bugs....

- No icon

- sudo start OK from CLI, no gksudo start from System tools

- Kernel cleaning ?!!

```
Removing linux-headers-2.6.27-3-generic ...
Removing linux-restricted-modules-2.6.27-3-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.27-3-generic
Removing linux-image-2.6.27-3-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-4-generic
Found kernel: /boot/last-good-boot/vmlinuz
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]

```


- It just hangs....
```

Processing triggers for menu ...
Processing triggers for man-db ...
INFO: Post-cleanup: <fstab_plugin.FstabPlugin object at 0xbb23a2c>
```

No "end prompt" after cleaning


- No apt-cache cleaning


- Any blueprint or wiki for this ?


-----------------------------------------------------------------
OT !
Another little tool I saw....  USB-Creator > testing
[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007620.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007620.html)

---

### Post by ronacc on 2008-09-26
Installed ok for me via synaptic , opened ok , only wanted to remove things I wanted to keep so I didn"t hit the button:)
edit  like you always ask  bug#s ?

---

### Post by amano on 2008-09-26
Does anybody know if the system cleaner will be moved to main?

Thanks to Lars Wirzenius for this little tool.

Just for later reference: This is the spec on which the system cleaner was based on --> [https://wiki.ubuntu.com/CleanupCruft](https://wiki.ubuntu.com/CleanupCruft)

It offered to me to remove just some manually installed .debs (called "local packages" in synaptic), thus I guess that my system is rather clean :D

BUT: I unchecked the debs to be removed (and clicked the clean up button) and system cleaner removed those packages anyway (though being unchecked). :(

So I cannot recommend testing it if you have local .debs installed. Or am I the only one to have this problem?

Some problems like the missing icon were reported already above.

---

### Post by Nullack on 2008-09-26
[https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/274714](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/274714)
[https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/274715](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/274715)
[https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/274717](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/274717)

---

### Post by Nullack on 2008-09-26
> **amano said:**
> BUT: I unchecked the debs to be removed (and clicked the clean up button) and system cleaner removed those packages anyway (though being unchecked). :(

Thats an ugly bug, please consider reporting it :)

---

### Post by amano on 2008-09-26
Well. In my eyes it is related to your 3rd bug reported above. If I unchecked everything, the button shouldn't be clickable. Because that led me to the assumption it would "clean" things that are not mentioned in the list above.

Can somebody with only few local packages installed confirm my experience?

Steps to reproduce: 

1) Start Systemcleaner
2) Uncheck everything (in my case: 4 debs downloaded and installed from the desktop - stuff that still isn't in the repos)
3) Push "Clean up" anyway.

Expected behaviour: It should do nothing or even not be clickable

Actual behaviour: It removed the unchecked files.

---

### Post by autocrosser on 2008-09-26
Hmmmm---I unchecked about half of what it recommended to be removed..it worked for a bit & then regenerated the complete list again--in other words--did nothing.

I'll look a the bug reports & note accordingly.


Edit: commented & confirmed

---

### Post by autocrosser on 2008-09-26
More info--It also removed several local apps--lightscribe, bluemarine & a couple of others....I'll reinstall them....Amano, have you raised a bugreport?

---

### Post by ShirishAg75 on 2008-09-26
Hi guys, 
  It could be a good application but perhaps needs some more work. One bug which I filed :-

[https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/275034](https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/275034)

---

### Post by handaxe on 2008-09-27
The list offered by System Cleaner is the same one as offered by the 'Status -> Installed (Local or Obsolete)' option in Synaptic, at least on my setup.  So what is the point of System Cleaner if a pre-existing  and central app already does the work?  What have I missed in my admittedly cursory look at the app?

HA

I guess the answer is 'read the spec' :-) I see what it proposes to do - obsolete kernels, icons etc are not identified in synaptic. So it is work in progress ....

Logging would be nice, if not essential.

---

