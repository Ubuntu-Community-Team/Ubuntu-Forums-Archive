---
title: "mdadm complains whenever I upgrade packages..."
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by SBFC on 2007-04-02
Whenever I upgrade packages (doesn't matter what they are) I get all sorts of complaints from mdadm, and I was wondering if I should be worried.

Here's a sample output:

```

Setting up wacom-tools (0.7.7.7-0ubuntu1) ...

Setting up xorg (7.2-0ubuntu11) ...
Setting up libdevmapper1.02 (1.02.08-1ubuntu6) ...

Setting up lvm2 (2.02.06-2ubuntu9) ...
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gnome -- is libgnome2-perl installed?)
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Backing up any LVM2 metadata that may exist...done.
update-initramfs: Generating /boot/initrd.img-2.6.20-13-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.

Setting up dmsetup (1.02.08-1ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-13-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.

```

As I said before, it doesn't matter what packages I'm upgrading, or installing for that matter. I always get those mdadm complaints.

I have LVM setup, not sure how much mdadm relates to that, if at all. I just wanted to know if this is something that should be worrying me.

Thanks in advance for any help offered.

---

### Post by SjRaptor on 2007-04-02
I have the same issue on Feisty Beta

```

The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-gtk compiz-plugins dmsetup gthumb
  hwdb-client-common hwdb-client-gnome libdecoration0 libdevmapper1.02
  libgphoto2-2 libgphoto2-port0 libvolume-id0 lvm-common lvm2 mdadm rhythmbox
  udev volumeid
20 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
Need to get 8319kB of archives.
After unpacking 106kB of additional disk space will be used.
Do you want to continue [Y/n]? 

< snip >

Unpacking replacement hwdb-client-gnome ...
Preparing to replace mdadm 2.5.6-7ubuntu4 (using .../mdadm_2.5.6-7ubuntu5_i386.deb) ...
 * Stopping MD monitoring service mdadm --monitor                        [ OK ] 
Unpacking replacement mdadm ...
Preparing to replace rhythmbox 0.9.8-0ubuntu3 (using .../rhythmbox_0.10.0-0ubuntu1_i386.deb) ...
Unpacking replacement rhythmbox ...
Setting up libvolume-id0 (108-0ubuntu1) ...
Setting up volumeid (108-0ubuntu1) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-10-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
cpio: ./etc/udev/rules.d/*-lvm.rules: No such file or directory

Setting up udev (108-0ubuntu1) ...
Installing new version of config file /etc/udev/rules.d/20-names.rules ...
Installing new version of config file /etc/udev/rules.d/25-iftab.rules ...
Installing new version of config file /etc/udev/rules.d/40-permissions.rules ...
Installing new version of config file /etc/udev/rules.d/60-symlinks.rules ...
Installing new version of config file /etc/udev/rules.d/80-programs.rules ...
Installing new version of config file /etc/udev/rules.d/90-modprobe.rules ...
Installing new version of config file /etc/udev/rules.d/00-init.rules ...
Installing new version of config file /etc/udev/rules.d/65-persistent-storage.rules ...
update-initramfs: Generating /boot/initrd.img-2.6.20-10-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
cpio: ./etc/udev/rules.d/*-lvm.rules: No such file or directory

Setting up lvm-common (1.5.20ubuntu12) ...

Setting up compiz-core (0.3.6-1ubuntu12) ...
Setting up libdecoration0 (0.3.6-1ubuntu12) ...

Setting up compiz-gtk (0.3.6-1ubuntu12) ...

Setting up compiz-gnome (0.3.6-1ubuntu12) ...
Setting up compiz-plugins (0.3.6-1ubuntu12) ...

Setting up compiz (0.3.6-1ubuntu12) ...
Setting up libgphoto2-port0 (2.3.0-0ubuntu4) ...

Setting up libgphoto2-2 (2.3.0-0ubuntu4) ...

Setting up gthumb (2.10.1-0ubuntu1) ...

Setting up hwdb-client-common (0.6.7) ...

Setting up hwdb-client-gnome (0.6.7) ...
Setting up mdadm (2.5.6-7ubuntu5) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-10-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
cpio: ./etc/udev/rules.d/*-lvm.rules: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.20-9-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
cpio: ./etc/udev/rules.d/*-lvm.rules: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.17-11-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
cpio: ./etc/udev/rules.d/*-lvm.rules: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.17-10-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
cpio: ./etc/udev/rules.d/*-lvm.rules: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.15-27-386
W: udev hook script requires at least kernel version 2.6.17
W: not generating requested initramfs for kernel 2.6.15-27-386
update-initramfs: Generating /boot/initrd.img-2.6.15-26-386
W: udev hook script requires at least kernel version 2.6.17
W: not generating requested initramfs for kernel 2.6.15-26-386
update-initramfs: Generating /boot/initrd.img-2.6.15-23-386
W: udev hook script requires at least kernel version 2.6.17
W: not generating requested initramfs for kernel 2.6.15-23-386
 * Starting MD monitoring service mdadm --monitor                        [ OK ] 
 * Assembling MD array mdarrays...                                       [ OK ] 

Setting up rhythmbox (0.10.0-0ubuntu1) ...

Setting up libdevmapper1.02 (1.02.08-1ubuntu6) ...

Setting up lvm2 (2.02.06-2ubuntu9) ...
Backing up any LVM2 metadata that may exist...done.
update-initramfs: Generating /boot/initrd.img-2.6.20-10-386
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.

Setting up dmsetup (1.02.08-1ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-10-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.


```

---

### Post by Cippa Lippa on 2007-04-04
I have the same problem. During update I get

Setting up libvolume-id0 (108-0ubuntu3) ...
Setting up volumeid (108-0ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-13-generic
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory

Setting up udev (108-0ubuntu3) ...
Installing new version of config file /etc/udev/rules.d/40-permissions.rules ...
Adding nvram group...
update-initramfs: Generating /boot/initrd.img-2.6.20-13-generic
cp: cannot stat `/etc/udev/rules.d/25-dmsetup.rules': No such file or directory

Please somebody let us know if you have any clue what is this about

Cippa

---

### Post by SBFC on 2007-04-04
```
The following packages were automatically installed and are no longer required:
  libxcb1 libxcb-xlib0 binfmt-support [COLOR="Red"]mdadm[/COLOR]
Use 'apt-get autoremove' to remove them.

```

Now whenever I install something I get that, so I'm just going to do what it says, and hopefully it won't hose something.

---

### Post by SBFC on 2007-04-04
Good news! I think auto-removing mdadm borked my system! Sweetness.

Attempting to recover...*grumbles*

Well, I shouldn't say that. Only, that last major thing I did before a reboot was perform an 'apt-get autoremove'...

Upon booting, I receive the following error:

> Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/*blah*) = sda6(8,6)
kinit: trying to resume from /dev/disk/by-uuid/*blah*
kinit: No resume image, doing normal boot...

And then it hangs...

Suggestions anyone?

---

### Post by huygens on 2007-04-04
SBFC, you could try to watch this other thread: [http://ubuntuforums.org/showthread.php?t=401044](http://ubuntuforums.org/showthread.php?t=401044) they both might be related...

As for your particular problem. I think I saw the message today too. What I did was to use the recovery mode in grub. It was hung also in this mode. But when I press Ctrl+Alt+Del, it seems to kill the service which is currently stuck and then continue booting.
You will be then logged-in as root. You can check your file systems by mounting them or not. The log messages, etc.
What I have found out is that when I removed mdadm, the /boot was not mounted (I have /boot as a dedicated partition) thus my system was a mess. To solve this issue, I unmounted /boot and re-installed mdadm. Then, I have mounted /boot and removed mdadm. Finally, I had a proper state.
Well, now I have some troubles with LVM, but at least I do not have mdadm installed anymore and upgrading packages is now fast (mdadm not complaining and hogging the CPU...)

---

### Post by SBFC on 2007-04-04
Thanks for the response huygens. It turns out my system will actually boot and load everything up properly if I wait long enough. Took around 5 minutes...seriously. Just hangs on the loading up part, and 5 minutes later finally continues.

Going to follow the thread you posted.

---

### Post by Mateo on 2007-04-13
same problem here:

```
update-initramfs: Generating /boot/initrd.img-2.6.20-14-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
```

anyone know what's up?  happens to several packages during installs.

---

### Post by thriff on 2007-04-13
look in /usr/share/doc/mdadm/README.upgrading-2.5.3.gz as it tells you too:

Systems with a mdadm.conf file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
If an existing configuration file is found, it is *ignored* until you checked
it and gave mdadm permission to use it.
.
.
.
then it has some things it want you to check with the config-file
.
.
.
Once you have verified that the configuration file is accurate, you need to
let mdadm know, and update the initial ramdisk. This is accomplished with the
following two commands:
```

  rm -f /var/lib/mdadm/CONF-UNCHECKED
  update-initramfs -u -k all
```

---

### Post by Mateo on 2007-04-13
wow, talk about a lot of work.  this is what it all says to do:

```
Systems with a mdadm.conf file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
If an existing configuration file is found, it is *ignored* until you checked
it and gave mdadm permission to use it. Even though this is a nuisance to some
users, it is a necessary measure: previous versions of mdadm did not
necessarily use the information in this file, even if it existed; thus there
is no guarantee that the file properly describes the system's configuration.

Therefore, you are required to inspect /etc/mdadm/mdadm.conf or
/etc/mdadm.conf (whichever one is present, the first gets priority if both are
present) and ensure that all arrays are properly identified. Here are a number
of recommended checks:

  - Verify that all arrays referenced by /etc/fstab, /etc/crypttab, your LVM
    metadata, and whatever other subsystem uses MD arrays (RAIDs) on your
    machine have a corresponding line in the configuration file.

    Make sure to verify that your bootloader refers to the proper device name,
    in case your root filesystem is on an MD array.

    In particular, verify that the device node name is exactly the same;
    /dev/md6 is *not* identical to /dev/md/6. Partitionable arrays are
    a slight exception: if /dev/md_d0p3 is referenced, you need an entry for
    /dev/md_d0 in the configuration file.

  - Compare your file with the output of /usr/share/mdadm/mkconf . In
    particular, make sure that the UUID matches for each array, whenever
    a UUID is specified. Also compare the values of super-minor, name, and
    devices. Only one match identifier (UUID, super-minor, name, devices) is
    needed for each array, but if multiple identifiers are specified, all must
    match. See mdadm.conf(5).

    Identifying arrays by UUID is the preferred method.

Once you have verified that the configuration file is accurate, you need to
let mdadm know, and update the initial ramdisk. This is accomplished with the
following two commands:

  rm -f /var/lib/mdadm/CONF-UNCHECKED
  update-initramfs -u -k all

Depending on your setup, mdadm should print an appropriate informational
message. Please make sure that it is in accordance with what you would expect.
```

what a load of .... i'm angry that they make you do all that.  i don't even know what any of that means!  all my file says is:

```
DEVICE partitions
MAILADDR root
```

---

### Post by thriff on 2007-04-13
thats what i should say unless you have some special raid arrays i think... i 'checked' my conf and rebooted, worked fine. no hichups with any fsmounts.

---

### Post by huygens on 2007-04-13
Mateo, do you use md array or the mdadm package?
If you happen to know the answer and the answer is no, then you can safely remove the package from your system.
If you do not know or the answer is yes, then do not remove it (you will not be able to access your data then). Instead verify that you have the latest updates installed.

Also do not get it bad ;-) Feisty is still at an unstable stage, it is expectable that such error occurs at this point in time. If you do not like such error and you would like to have a stable system, please use Ubuntu 6.10 or Ubuntu 6.06 instead. :-) so you do not have to read this "load of ..." ;-) No offense though, it is nice to have volunteer to test Ubuntu before it is stable :-)

---

