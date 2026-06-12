---
title: "Ubuntu Netbook Edition in VMs"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by JFekete9076 on 2011-02-09
Does anyone know how to set up a virtual machine which runs Ubuntu Netbook Edition?

---

### Post by Old_Grey_Wolf on 2011-02-09
You can download VirtualBox from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).

The user manual is at [http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html).

Don't let the amount of documentation deter you. If is actually easy to use.

---

### Post by wyliecoyoteuk on 2011-02-09
Not straightforward getting Unity to work on VirtualBox's available graphics emulations.

---

### Post by JFekete9076 on 2011-02-09
I've downloaded the disc image of Ubuntu Netbook Edition, and try to boot in QEMU with ARM architecture support, but I failed to set up the VM.

Here's the details of error:
```

Unable to complete install '<class 'libvirt.libvirtError'> internal error Process exited while reading console log output: char device redirected to /dev/pts/0
Kernel image must be specified

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 1555, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 973, in start_install
    return self._do_install(consolecb, meter, removeOld, wait)
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 1038, in _do_install
    "install")
  File "/usr/lib/pymodules/python2.6/virtinst/Guest.py", line 1009, in _create_guest
    dom = self.conn.createLinux(start_xml, 0)
  File "/usr/lib/python2.6/dist-packages/libvirt.py", line 1277, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: internal error Process exited while reading console log output: char device redirected to /dev/pts/0
Kernel image must be specified

```

Note: I've already tried it in Virtualbox.

---

### Post by Old_Grey_Wolf on 2011-02-09
> **wyliecoyoteuk said:**
> Not straightforward getting Unity to work on VirtualBox's available graphics emulations.

That could be true. I haven't run the Ubuntu Netbook as a VM since 9.10.

Edit: I am downloading 10.10 now and will give it a go.

---

### Post by Old_Grey_Wolf on 2011-02-09
I got Ubuntu Netbook Edition 10.10 installed. It was not a problem. I had to follow the instruction; that was embedded in the installer, to log in as user "ubuntu" without a password to get the Unity driver installed. I am posting from the VM at the moment.

I also got the Guest Additions installed; however, that did take a reboot of the VM.

---

### Post by JFekete9076 on 2011-02-10
After installing the OS and starting Unity session, the next message appeared: No required driver detected for unity.
I've also realised that Compiz doesn't work even with 3D acceleration.

I've read these sites:
[http://ubuntuforums.org/showthread.php?t=1620044](http://ubuntuforums.org/showthread.php?t=1620044)
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

And another question: How did you install the Unity driver? Can I do this in an installed OS?

Update: I have forgotten that without GCC, I can't install Guest Additions. Despite it, Unity doesn't work, and Virtualbox crashes after login.

---

### Post by Old_Grey_Wolf on 2011-02-10
> **JFekete9076 said:**
> After installing the OS and starting Unity session, the next message appeared: No required driver detected for unity.
I've also realised that Compiz doesn't work even with 3D acceleration.

I've read these sites:
[http://ubuntuforums.org/showthread.php?t=1620044](http://ubuntuforums.org/showthread.php?t=1620044)
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

And another question: How did you install the Unity driver? Can I do this in an installed OS?

Update: I have forgotten that without GCC, I can't install Guest Additions. Despite it, Unity doesn't work, and Virtualbox crashes after login.

OK, I see what you are trying to do now. You actually want to try the new Unity user interface in a VM, not just install Ubuntu Netbook Edition in a VM and use the Gnome user interface.

To actually use the Unity user interface, I believe you have to get VirtualBox v. 4.0.2 from Oracle's website. Then download a pre-release version of Ubuntu 11.04 desktop edition.

I didn't find a Netbook version, only alternate, desktop, and server versions of Natty.

---

### Post by JFekete9076 on 2011-02-13
I also want to know how can multitouch be emulated, and whether Ubuntu Netbook Edition supports it? I want to test this feature, too.

---

### Post by grahammechanical on 2011-02-13
If you want to test multitouch, first get a screen that allows multitouch.

regards.

---

