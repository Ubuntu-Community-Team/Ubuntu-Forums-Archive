---
title: "Installer doesn't reboot: Failed unmounting cdrom.mount"
date: 2024-04-08
forum: Installation &amp; Upgrades
---

### Post by bradley-coder7 on 2024-04-08
Hello all. I've been working with Ubuntu Server for a while now and have been mildly annoyed by one issue during install.

On both physical and virtual machines, when installing from a USB drive, the installer produces an error after completing the install that says:[INDENT][FAILED] Failed unmounting cdrom.mount - /cdrom.
[/INDENT]

If you are on physical machines or connected via a serial console, you will also see:[INDENT]Please remove the installation medium, then press ENTER:
[/INDENT]

Unless you press enter, it fails to reboot.

When doing installs on physical hardware or over a serial console, this is easy to ignore and you just hit enter. Despite this, it's also troubling when training other admins or writing install procedures to just tell people to ignore a big red "FAILED" message on every single interactive install, even though it is a non-issue. For DR and business continuity, we have to regularly go through bootstrapping our systems from scratch, so automation mechanisms are not in place for the first few installs and this shows up every time.

On VMs, if you are running through VNC or similar, you can't just hit enter. The installer hangs, and you are stuck with no feedback. Depending on the options you have set up, you can drop into the alternate TTY with Ctrl+Alt+F2 and hit enter there, or you can console in and hit enter there. Neither option is apparent to someone who doesn't know this error occurs every install.

My base system is currently ubuntu-server-22.04. I've encountered this with both 22.04 and 24.04 beta installs. I'm running my VMs with this command:
virt-install \
        --name testunit2 \
        --os-variant ubuntu24.04 \
        --hvm \
        --vcpus 2 \
        --cpu host \
        --memory 4096 \
        --location ./ubuntu.iso,kernel=casper/vmlinuz,initrd=casper/initrd \
        --network default,model=virtio \
        --disk size=20 \
        --graphics vnc

When doing autoinstalls, this issue doesn't become apparent. Reboots and shutdowns happen without issue. An error might get logged somewhere, but it does not interfere with the process. This only shows up during interactive installs.

So, what's going? Is there a proper fix to avoid this?

---

### Post by MAFoElffen on 2024-04-08
Welcome to Ubuntu Forums. When I was a Moderator here, one of the sections I supported was the Virtualization Section. As such, I actively supported KVM, VirtualBox, VMware Workstation, vSphere & ESXi, Xen, Hyper-V, hosts & VM's. That included various ways to connect to VM's.

I've used KVM since 2010. I have 4 KVM servers up on 22.04.4. I am one of the DEV testers for 24.04. Since I've been on the Ubuntu Server Team since 2012, some of the things I feel responsible for (personally) is to support the Server Section, and make sure there are no problems with Ubuntu Server VM's. <-- Even more of a priority to me than Desktop.

I do not see a problem with your build script... Per-say. Except when it gets to the end of the line, where you tell it to connect via VNC. You said you pass 
```

-graphics vnc \

```
That is a bit abbreviated... If I am doing a virt-install script, I do at least
```

--graphics vnc,listen=0.0.0.0 --noautoconsole \

```
Or doing and XML define, then something like this (if ot settig a VNC password) in the device section
```

<graphics type='vnc' port='-1' autoport='yes' keymap='en-us'/>

```
If you are really stuck on using VNC to connection to your Server VM's, then I would try adding more connection options. You also did not mention which VNC client you are using as your go-to. Please tell us.

I usually do Virt-Manager or connect from virt-viewer
```

/usr/bin/virt-viewer --connect qemu+ssh://<kvm-server-ip> <domain_name> &

```
Or straight via shh, like I do most of my servers.

Personally, with my own experience, I have not recommended using VNC to connect to VM's since around 2012 and Ubuntu 12.04 LTS. Honestly, it is slow and has always been a bit buggy for me. I get better graphics on Desktops, and better performance, setting Desktop VMs up with Spice & QXL... Except if I'm doing VirGL, or GPU pass-through. I do support some of my own Users with XRDP and RDP. Other Members I respect recommend X2Go.

I do not get that error. But then again, I personally have not used VNC to connect to VM's in decades... Except when I have to support a connection issue with VNC itself.

---

### Post by bradley-coder7 on 2024-04-09
Thanks for the response.

Personally, I do not care for using VNC either. My preference is to SSH into the VM and not even use serial consoles, though I usually build them anyway as a backup plan. But, the "[FAILED]" error occurs with or without the use of VNC, with or without the serial console, and even on bare-metal installations.

For reference, I am using TightVNC 2.8.81 when I am in a situation where I want a quick way to mimic a monitor hooked up to a machine. I rarely do this, so the defaults work fine for me. Even my homelab runs headless. When using VNC for testing, I just connect to my homelab on 192.168.0.x:5900. I don't use VNC in production. But, I'm also not having any real problem with VNC. The use of a remote graphical interface just highlights the problem under some conditions.

After a few more rounds of intentionally trying to reproduce this issue, I've found that the installer only truly "hangs" when another TTY is present for the error message. So, for example, if I attach a serial console configuration. I've been able to trigger it a couple of other ways as well, such as dropping to a shell with Ctrl+Alt+F2, doing nothing there, then switching back to the installer with Ctrl+Alt+F1. 

My ordinary VM installs look like this (with $unit set to an instance name and $ts set to a timestamp for auto-generated CIDATA images):
virt-install \
        --name $unit \
        --os-variant ubuntu24.04 \
        --hvm \
        --vcpus 2 \
        --cpu host \
        --memory 4096 \
        --location ./ubuntu-server.iso,kernel=casper/vmlinuz,initrd=casper/initrd \
        --network default,model=virtio \
        --disk size=20 \
        --disk path=./cidata.$ts.img,format=raw,cache=none \
        --graphics none \
        --extra-args='console=ttyS0,115200n8 autoinstall'

But, in this instance, I am trying to document the process of bootstrapping from scratch. I don't have a dozen spare machines laying around my homelab, so I'm doing it through virtualization. The problem occurs on both bare-metal and VM installs when they are interactive. All four of the bare-metal machines I recently built on 22.04 displayed the error at the end of the install. All of the VMs I've installed interactively show this on both 22.04 and 24.04.

 Building a CIDATA image from Linux is extremely easy, and autoinstall either avoids or masks the problem. But building a CIDATA image from Windows is a bit more tricky. The environment I'm working in requires users to have Windows on their workstations. So, the first couple of machines are assumed to be manually installed from just a downloaded Ubuntu Server ISO written to a USB drive with something like balenaEtcher. From that point on, there are Linux systems that can use autoinstall and avoid/mask the cdrom error. But those first couple of installs aways show the user the [FAILED] message after the install is completed, and you have to hit enter to reboot.

I've made a video showing the issue where I can cause the installer to apparently hang.

[https://drive.google.com/file/d/1ZoVXZ-ITpCoW5pQi4-eZHEDGI8mx3Cas/view?usp=sharing](https://drive.google.com/file/d/1ZoVXZ-ITpCoW5pQi4-eZHEDGI8mx3Cas/view?usp=sharing)

 In this video, I'm still building a serial console, but using VNC to do the install like I would on a bare-metal machine with a keyboard and mouse hooked up. At the end of the video, I have to switch to another window, console in, and hit enter. If I had the console attached the entire time, you'd see the error output there.

If no other console option is attached, then the error is actually written to the console you get through VNC, and pressing enter works.

But, despite the fact that I have half a dozen ways to work around this, the issue remains the same. Why is the installer always producing the error and asking the user to hit enter again?

---

### Post by bradley-coder7 on 2024-04-09
I should also note that most of the machines I work with these days don't even have a physical CD drive, and even when they do, I never use it for installation media (or at all, tbh). I use USB flash drives, as do most people, and that is how almost every tutorial I've seen suggests you do it. So there isn't even a CD drive (virtual or otherwise) that is being used or that has media loaded, yet the installer still tries to eject it and fails to do so.

---

### Post by ajgreeny on 2024-04-09
I may be getting the details wrong here but whe  installing a Linux distro in KVM, using an iso file such as the current dev versions of 24.04, the iso is added to a virtual cdrom.

I don't know if this is relevant to your query but thought it worth mentioning.  I expect MafoElffen will have some comment to make as he understands KVM much better than i do.

---

### Post by MAFoElffen on 2024-04-09
+1 -- I do about 5+ installs a day, usually 24x7. Mostly with KVM... But also on Metal.

I use ISO files on all Virt Hosts. LiveUSB only on metal. The last time I had to burn an optical disk was... I'm not positive, but was at least over a year ago for a customer, that had some sentimental attachment to an old laptop that didn't support USB boot. There were 3-4 times where I added a USB pass-through to a USB Drive and tested booting USB to a VM, for installing a vSphere Server to a VM...

Dang, I even use ISO files on my Dell and SuperMicro servers through iDRAC and the BMC management util's.

The Ubuntu ISO files haven't really supported booting and installing from optical disks in years. The oversized size of the ISO file is larger than a DVD. And if you do, it takes forever, and usually times out (work-arounds for that.)

Is about 5 am right now, and getting ready for work. I will investigate this further tonight. I'll spin up a few servers using your settings and see what happens in my hosts. I'll try to recreate it. If I can recreate it consistently, then I'll file the bug report myself and have you join it.

*** Question: Which specific ISO Installer file? Server 22.04.4?

Note: I have come up with that "problem" before, from time to time. I can't say that it doesn't happen. But I usually ignore it and just kill/restart the VM (with virsh) to go on. At that point, it has already installed and is ready for the reboot. It usually just comes back up fine, with rare exceptions. It doesn't happen enough consistently that I thought it was enough to report as a Bug. That was usually when I was testing the daily builds in the DEV builds...

---

### Post by bradley-coder7 on 2024-04-09
I've encountered this with the daily build of 24.04 downloaded on April 7, 2024. But the same exact behavior has been observed on my 22.04.3 ISO.

Regarding the ISO being treated as a cdrom image, that is true when I spin things up in VMWare. I haven't seen the error there, but wasn't looking.

I went and checked through virsh for the instance created in the video I posted, and yes, the xml shows it is being attached as a type=cdrom even though the image is bootable as a regular USB drive. The eject command is failing, despite the ISO being connected as a cdrom drive.

On bare metal, the server has no cdrom drive. The ISO is written to a USB flash drive, which is used during boot. So in that scenario I described, there is no virtual cdrom. Yet the same behavior occurs.

---

### Post by MAFoElffen on 2024-04-10
I must be confused... 

You say that you are physically booting the installer LiveUSB for a (VM)? 

You say that, but... That is not what your script says:
> **bradley-coder7 said:**
> 
```

virt-install \
--name testunit2 \
--os-variant ubuntu24.04 \
--hvm \
--vcpus 2 \
--cpu host \
--memory 4096 \
[COLOR=#ff0000]--location ./ubuntu.iso,kernel=casper/vmlinuz,initrd=casper/initrd \[/COLOR]
--network default,model=virtio \
--disk size=20 \
--graphics vnc

```

That looks like an ISO file right? If it where a LiveUSB, yo uwould have the path to it there... And it would not have 'a filename'. RightEspeciall one ending in *.iso...

Like this example:
```

# virt-install --virt-type kvm --name centos --ram 1024 \
  --disk /tmp/centos-7-01.qcow2,format=qcow2 \
  --network network=default \
  --graphics vnc,listen=0.0.0.0 --noautoconsole \
  --os-type=linux --os-variant=centos7.9 \
  --location=/data/iso/CentOS-7.9-x86_64-DVD-2009.iso

```
The '--location' is smarter than you are giving it credit
```

       --location OPTIONS
           Distribution tree installation source. virt-install can recognize certain distribution
           trees and fetches a bootable kernel/initrd pair to launch the install.

           With libvirt 0.9.4 or later, network URL installs work for remote connections.  virt-
           install will download kernel/initrd to the local machine, and then upload the media to
           the remote host. This option requires the URL to be accessible by both the local and
           remote host.

           --location allows things like --extra-args for kernel arguments, and using
           --initrd-inject. If you want to use those options with CDROM media, you have a few
           options:

           * Run virt-install as root and do --location ISO

           * Mount the ISO at a local directory, and do --location DIRECTORY

           * Mount the ISO at a local directory, export that directory over local http, and do
           --location http://localhost/DIRECTORY

           The "LOCATION" can take one of the following forms:

           http://host/path
               An HTTP server location containing an installable distribution image.

           ftp://host/path
               An FTP server location containing an installable distribution image.

           nfs:host:/path or nfs://host/path
               An NFS server location containing an installable distribution image. This requires
               running virt-install as root.

           DIRECTORY
               Path to a local directory containing an installable distribution image. Note that
               the directory will not be accessible by the guest after initial boot, so the OS
               installer will need another way to access the rest of the install media.

           ISO Mount the ISO and probe the directory. This requires running virt-install as root,
               and has the same VM access caveat as DIRECTORY.

           Some distro specific url samples:

           Fedora/Red Hat Based
               http://download.fedoraproject.org/pub/fedora/linux/releases/21/Server/x86_64/os

           Debian
               http://ftp.us.debian.org/debian/dists/stable/main/installer-amd64/

           Ubuntu
               http://us.archive.ubuntu.com/ubuntu/dists/wily/main/installer-amd64/

           Suse
               http://download.opensuse.org/distribution/11.0/repo/oss/

           Mandriva
               ftp://ftp.uwsg.indiana.edu/linux/mandrake/official/2009.0/i586/

           Mageia
               ftp://distrib-coffee.ipsl.jussieu.fr/pub/linux/Mageia/distrib/1

```
You could have gotten away with 
```

--location ./ubuntu.iso

```
If it were an installer LiveUSB, it would have been some like /dev/sgb1 or mounted to a directory, something like /media/$USER/samsung-16gb/ or /mnt...

I use ISO files. I  don't usually use option '--location', but rather --cdrom or --disk... but  none is wrong between those 3. Just different ways to to that.
```

--cdrom=/data/ISO/Fedora-14-x86_64-Live-Desktop.iso 

```
```

       --cdrom OPTIONS
           File or device used as a virtual CD-ROM device.  It can be path to an ISO image, or to
           a CDROM device. It can also be a URL from which to fetch/access a minimal boot ISO
           image. The URLs take the same format as described for the "--location" argument. If a
           cdrom has been specified via the "--disk" option, and neither "--cdrom" nor any other
           install option is specified, the "--disk" cdrom is used as the install media.

--disk OPTIONS
           Specifies media to use as storage for the guest, with various options. The general
           format of a disk string is

               --disk opt1=val1,opt2=val2,...

           The simplest invocation to create a new 10G disk image and associated disk device:

               --disk size=10

           virt-install will generate a path name, and place it in the default image location for
           the hypervisor. To specify media, the command can either be:

               --disk /some/storage/path[,opt1=val1]...

           or explicitly specify one of the following arguments:

           path
               A path to some storage media to use, existing or not. Existing media can be a file
               or block device.

               Specifying a non-existent path implies attempting to create the new storage, and
               will require specifying a 'size' value. Even for remote hosts, virt-install will
               try to use libvirt storage APIs to automatically create the given path.

               If the hypervisor supports it, path can also be a network URL, like
               http://example.com/some-disk.img . For network paths, they hypervisor will
               directly access the storage, nothing is downloaded locally.

           pool
               An existing libvirt storage pool name to create new storage on. Requires
               specifying a 'size' value.

           vol An existing libvirt storage volume to use. This is specified as
               'poolname/volname'.

           Other available options:

           device
               Disk device type. Value can be 'cdrom', 'disk', 'lun' or 'floppy'. Default is
               'disk'. If a 'cdrom' is specified, and no install method is chosen, the cdrom is
               used as the install media.

           boot_order
               Guest installation with multiple disks will need this parameter to boot correctly
               after being installed. A boot_order parameter will take values 1,2,3,... Devices
               with lower value has higher priority.

           bus Disk bus type. Value can be 'ide', 'sata', 'scsi', 'usb', 'virtio' or 'xen'.  The
               default is hypervisor dependent since not all hypervisors support all bus types.

           removable
               Sets the removable flag (/sys/block/$dev/removable on Linux). Only used with QEMU
               and bus=usb. Value can be 'on' or 'off'.

           readonly
               Set drive as readonly (takes 'on' or 'off')

           shareable
               Set drive as shareable (takes 'on' or 'off')

           size
               size (in GiB) to use if creating new storage

           sparse
               whether to skip fully allocating newly created storage. Value is 'yes' or 'no'.
               Default is 'yes' (do not fully allocate) unless it isn't supported by the
               underlying storage type.

               The initial time taken to fully-allocate the guest virtual disk (sparse=no) will
               be usually balanced by faster install times inside the guest. Thus use of this
               option is recommended to ensure consistently high performance and to avoid I/O
               errors in the guest should the host filesystem fill up.

           backing_store
               Path to a disk to use as the backing store for the newly created image.

           cache
               The cache mode to be used. The host pagecache provides cache memory.  The cache
               value can be 'none', 'writethrough', 'directsync', 'unsafe' or 'writeback'.
               'writethrough' provides read caching. 'writeback' provides read and write caching.
               'directsync' bypasses the host page cache. 'unsafe' may cache all content and
               ignore flush requests from the guest.

           discard
               Whether discard (also known as "trim" or "unmap") requests are ignored or passed
               to the filesystem. The value can be either "unmap" (allow the discard request to
               be passed) or "ignore" (ignore the discard request). Since 1.0.6 (QEMU and KVM
               only)

           format
               Disk image format. For file volumes, this can be 'raw', 'qcow2', 'vmdk', etc. See
               format types in <http://libvirt.org/storage.html> for possible values. This is
               often mapped to the driver_type value as well.

               If not specified when creating file images, this will default to 'qcow2'.

               If creating storage, this will be the format of the new image. If using an
               existing image, this overrides libvirt's format auto-detection.

           driver_name
               Driver name the hypervisor should use when accessing the specified storage.
               Typically does not need to be set by the user.

           driver_type
               Driver format/type the hypervisor should use when accessing the specified storage.
               Typically does not need to be set by the user.

           io  Disk IO backend. Can be either "threads" or "native".

           error_policy
               How guest should react if a write error is encountered. Can be one of "stop",
               "ignore", or "enospace"

           serial
               Serial number of the emulated disk device. This is used in linux guests to set
               /dev/disk/by-id symlinks. An example serial number might be: WD-WMAP9A966149

           startup_policy
               It defines what to do with the disk if the source file is not accessible.  See
               possible values in <http://www.libvirt.org/formatdomain.html#elementsDisks>

           See the examples section for some uses. This option deprecates -f/--file,
           -s/--file-size, --nonsparse, and --nodisks.

           Use --disk=? to see a list of all available sub options. Complete details at
           <http://libvirt.org/formatdomain.html#elementsDisks>

```
Like this:
```

# virt-install \
--name=FE --ram=756 --vcpus=1 \
--file=/var/lib/libvirt/images/FE.img  --network bridge:br0 \
--nographics --os-type=linux  \
--extra-args='console=tty0' -v \
--cdrom=/data/ISO/Fedora-Workstation-Live-x86_64-39-1.5.iso

```

---

### Post by him610 on 2024-04-11
> [FAILED] Failed unmounting cdrom.mount - /cdrom.
If you are on physical machines or connected via a serial console, you will also see:
Please remove the installation medium, then press ENTER:

These are not errors. I have seen messages like (or similar to them several times.
IMHO, in your BIOS there are still references to a cdrom; when the system cannot dismount it,  it provides a 'why not' message.
The second message is merely a prompt advising you to remove the installation medium before rebooting to avoid booting from the installation medium again instead of your newly installed OS on your system.
Does that seem logical to you?

---

### Post by bradley-coder7 on 2024-04-15
@MAFoElffen

The same exact behavior is present regardless of whether I plug in a physical USB drive to a physical machine or use the --location option in a VM.

The location option with the kernel and initrd options specified is the suggestion I found on various tutorials when you want to pass extra kernel options to the ubuntu installer (e.g., options for enabling a console port). Passing --cdrom will fail with:
ERROR    Kernel arguments are only supported with location or kernel installs.

Passing --location without the kernel and initrd options fails with:
ERROR    Couldn't find kernel for install tree.

I can fire off an instance with --cdrom and --graphics vnc, without the extra-args, and it can work. But, then I have no console and must use vnc. That's fine for mimicking a physical machine, which also doesn't have a console port by default. But regardless, the point I've been trying to make is that the "[FAILED]" message occurs even in a physical machine with a physical USB drive, which is how I presume the overwhelming majority of people install their first instance of ubuntu in a given environment. And there are conditions where this failed message and the subsequent prompt to hit enter are not displayed to the user.

---

### Post by bradley-coder7 on 2024-04-15
@him610

I'm not sure why a KVM instance would reference a non-existent cdrom drive. Above, I acknowledged that with the particular options I'm passing, virt-install is treating it as a cdrom. But, as I've indicated, I see this same output on physical hardware with no media in the cdrom drive. I don't have a machine handy that has no cdrom drive at all to test right now, but I believe I've seen the same output in that situation as well.

There is no reason to try and unmount a cdrom drive when no cdrom was ever mounted, regardless of whether the BIOS or installer "sees" a cdrom drive present in the system. It's not being used, so why even try to unmount it? I think this is an artifact from when the use of cdroms was the most common way of installing, and the assumption that a cdrom was mounted just never got updated as installation procedures migrated away from that practice.

"[FAILED]" in red letters may not be a formal "error" in the strictest sense of the word, but it still indicates a problem to the user.

The second message makes perfect sense in some respects. But, there are various conditions (mentioned in previous posts) where this message gets diverted away from the user. E.g., when a serial console is present or the user switches to an alternate TTY, then switches back to the main TTY to finish the install. I haven't tested an SSH-based install to figure out where the message might be displayed in that scenario. In addition, the installer already prompts the user to choose whether to "reboot". I don't have the media necessary to test whether the installer presents the second message only when the attempt to eject the media fails, but if I recall correctly (after many years), various Debian and Ubuntu installers did not present such a message when an optical drive was used for installation and successfully ejected. Back then, choosing "reboot" on the final screen of the installer just worked. I only recall seeing this behavior pop up when I started using USB drives. At that time, this was a fairly new approach, so the messages and extra prompt were just seen as something to put up with. But now it is standard practice to use USB drives, and almost no one uses cdroms.

---

