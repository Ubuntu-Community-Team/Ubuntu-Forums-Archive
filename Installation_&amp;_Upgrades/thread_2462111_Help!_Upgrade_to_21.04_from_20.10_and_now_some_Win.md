---
title: "Help! Upgrade to 21.04 from 20.10 and now some Wine applications won't open!"
date: 2021-05-13
forum: Installation &amp; Upgrades
---

### Post by tomspinelli on 2021-05-13
Looking for some help on this ... I am always hesitant on upgrading but i did and upgraded to Ubuntu 21.04 yesterday and while most windows apps work in Wine, my recording programs aren't loading anymore. Steinberg Cubase 5 and Nuendo 4 specifically begin to load then crash. Sound Forge, Photoshop an others appear to still work. All of these applications worked great before I upgraded to 21.04. Maybe the upgrade erased some files i needed? Maybe graphics issue or assuming it removed some files on the upgrade i was using before? Hoping this is an easy one. 

I am trying to decipher the error but not that savvy with those. Anyone know based on this log what i need? Worst case is there a way to go back to 20.10? I knew I shouldn't have upgraded!

All files are in the same location too ...

When loading Nuendo 4 exe ...

```
Exec string:
/usr/bin/env  WINE='/usr/bin/wine'  WINEPREFIX='/home/tom/.wine'  WINESERVER='/usr/bin/wineserver'  WINELOADER='/usr/bin/wine'  WINEDEBUG='-all'  /bin/sh -c "cd '/home/tom/.wine/drive_c/Program Files (x86)/Steinberg/Nuendo 4/' &&   '/usr/bin/wine'   'Nuendo4.exe'  2>&1 "
Exit code:
256
App STDOUT and STDERR output:
X Error of failed request:  GLXBadFBConfig
  Major opcode of failed request:  149 (GLX)
  Minor opcode of failed request:  0 ()
  Serial number of failed request:  2695
  Current serial number in output stream:  2695
wine: Unhandled page fault on write access to 07F9FA68 at address 7BC68865 (thread 0026), starting debugger...
```
When loading Cubase 5 exe ....

```
Exec string:
/usr/bin/env  WINE='/usr/bin/wine'  WINEPREFIX='/home/tom/.wine'  WINESERVER='/usr/bin/wineserver'  WINELOADER='/usr/bin/wine'  WINEDEBUG='-all'  /bin/sh -c "cd '/media/tom/OS/Program Files (x86)/Steinberg/Cubase 5/' &&   '/usr/bin/wine'   'Cubase5.exe'  2>&1 "
Exit code:
256
App STDOUT and STDERR output:
wine: Read access denied for device L"\\??\\d:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\d:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\e:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\e:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\f:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\f:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\g:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\g:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\i:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\i:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\k:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\k:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\l:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\l:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\m:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\m:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\n:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\n:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\o:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\o:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\p:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\p:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\q:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\q:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\r:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\r:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\s:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\s:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\u:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\u:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\v:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\v:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\y:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\y:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\z:\\", FS volume label and serial are not available.
wine: Read access denied for device L"\\??\\z:\\", FS volume label and serial are not available.
X Error of failed request:  GLXBadFBConfig
  Major opcode of failed request:  149 (GLX)
  Minor opcode of failed request:  0 ()
  Serial number of failed request:  3510
  Current serial number in output stream:  3510
wine: Unhandled page fault on write access to 07F9FA68 at address 7BC68865 (thread 0026), starting debugger...
```
Here is photoshop and that works:

```
Exec string:
/usr/bin/env  WINE='/usr/bin/wine'  WINEPREFIX='/home/tom/.wine'  WINESERVER='/usr/bin/wineserver'  WINELOADER='/usr/bin/wine'  WINEDEBUG='-all'  /bin/sh -c "cd '/media/tom/OS/Program Files (x86)/Adobe/Photoshop 7.0/' &&   '/usr/bin/wine'   'Photoshop.exe'  2>&1 "
Exit code:
0
App STDOUT and STDERR output:
wine: Unhandled page fault on write access to 07F9FA68 at address 7BC68865 (thread 0027), starting debugger...

```

Thanks!!

---

### Post by dino99 on 2021-05-14
At first glance, these apps still require older dependencies (libs) versions to run.

---

### Post by tomspinelli on 2021-05-14
Is there a way to find out what they are or get those dependencies back? I'm even ok with downgrading back to 20.10, if it's an easy process. I don't know if that will bring those back. I need these to be able to run.

---

### Post by grahammechanical on 2021-05-14
If I remember correctly an upgrade from one Ubuntu version to another will require the disabling of repositories like PPAs and the Wine repository. If we the user do not do it before upgrading then the upgrade script will disable those repositories.

You may need to re-enable the Wine repository. I am not saying it will solve the problem. But I suggest that you make sure that the Wine repository is pointing to the Wine repository for Ubuntu 21.04

[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

Regards

---

### Post by tomspinelli on 2021-05-20
Do you know how to accomplish this? I was on the site link you sent but but really sure what to do? Just run those commands for 21.04 or the 20.10?

---

