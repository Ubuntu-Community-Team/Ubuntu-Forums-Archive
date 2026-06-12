---
title: "Problem with Disk &amp; Filesystems - can't load module. Any help is appreciated here..."
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by melsen on 2007-08-17
Alright... I just did a brand new install of feisty, and after doing all the recommended upgrades, my disk & filesystems doesnt load anymore...

When I try to start it up, it says:

> The module Disk & Filesystems could not be loaded.

The diagnostics is:

Possible Reasons:
* An error occured during your last KDE upgrade leaving an orphaned control module
* You have old third party modules lying around


I tried reinstall the kde-guidance.. that didnt help... 

And when I go to a console and type 'mountconfig' I get this:

> X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Traceback (most recent call last):
  File "/usr/bin/mountconfig", line 3302, in <module>
    sysvapp = MountConfigApp()
  File "/usr/bin/mountconfig", line 2950, in __init__
    self.__updateMountList()
  File "/usr/bin/mountconfig", line 3160, in __updateMountList
    groupitem = MountGroupListViewItem(self.mountlist,blockdevice)
  File "/usr/bin/mountconfig", line 2830, in __init__
    KListViewItem.__init__(self,parentitem,self.haldevice.getName(),"","","","")
  File "/usr/share/python-support/kde-guidance/MicroHAL.py", line 384, in getName
    return "Disk "+self.getModelName()
TypeError: cannot concatenate 'str' and 'NoneType' objects
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/mountconfig", line 3302, in <module>
    sysvapp = MountConfigApp()
  File "/usr/bin/mountconfig", line 2950, in __init__
    self.__updateMountList()
  File "/usr/bin/mountconfig", line 3160, in __updateMountList
    groupitem = MountGroupListViewItem(self.mountlist,blockdevice)
  File "/usr/bin/mountconfig", line 2830, in __init__
    KListViewItem.__init__(self,parentitem,self.haldevice.getName(),"","","","")
  File "/usr/share/python-support/kde-guidance/MicroHAL.py", line 384, in getName
    return "Disk "+self.getModelName()
TypeError: cannot concatenate 'str' and 'NoneType' objects


I'd really appreciate it if anyone could help me out with this....

Thanks...

---

### Post by dabl on 2007-08-17
Is this a Ubuntu, or Kubuntu, or Ubuntu-plus-KDE something installation?  It's a bit unusual to have such KDE-related problems on a Ubuntu system.  (It would be unusual to have them on Kubuntu as well ...).

---

### Post by melsen on 2007-08-17
> **dabl said:**
> Is this a Ubuntu, or Kubuntu, or Ubuntu-plus-KDE something installation?  It's a bit unusual to have such KDE-related problems on a Ubuntu system.  (It would be unusual to have them on Kubuntu as well ...).

A pure Kubuntu Feisty Spawn

---

### Post by melsen on 2007-08-17
Everyone drawing a blank here??

---

### Post by dabl on 2007-08-17
I have not heard of this problem before, but I guess if it were me, I'd remove kde-guidance and kde-guidance-powermanager, then I'd run the following to make sure my package manager is clean:

sudo dpkg-configure -a
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install

And then, observing (hopefully) no errors, I would install kde-guidance, and hope for a better result.  :)

---

### Post by melsen on 2007-08-18
> **dabl said:**
> I have not heard of this problem before, but I guess if it were me, I'd remove kde-guidance and kde-guidance-powermanager, then I'd run the following to make sure my package manager is clean:

sudo dpkg-configure -a
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install

And then, observing (hopefully) no errors, I would install kde-guidance, and hope for a better result.  :)

Didnt work either... still same error in the end.

---

### Post by PATRIK J. A. on 2007-09-16
Hi!

I had the same problem on Debian Unstable. After some searching I found it seems to be an error in the Debian and K-/Ubuntu package of kde-guidance, in that it is some other packages it should have depended on.

Anyway, installing the following solved the problem for me:
python-sip4-dev (which also installs python-dev)
python-qt-dev

If it doesn't work for you, maybe you can find more info here:

[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/136561](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/136561)

[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/109273](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/109273)

---

### Post by deadjones on 2007-12-22
i found a very interesting fix for this problem.

do you have your ipod plugged in? unplug it.  or other similar device/s.

check this out. this guy figured out why it was affecting him (and me). 
[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/124856](https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/124856)

---

