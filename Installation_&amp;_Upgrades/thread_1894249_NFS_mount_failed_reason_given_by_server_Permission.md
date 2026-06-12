---
title: "NFS mount failed reason given by server: Permission denied"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by RealityMaster on 2011-12-12
I'm attempting to install Ubuntu 11.10 amd64 via PXE boot. I've got most of it working, the machine boots gives me my list of Operating systems, let's me choose Ubuntu64 and begins booting.  When it get's to the NFS mount for the install CD I get...

```
mount: TFTPServer:/'path to extracted iso' failed, reason given by server: Permission denied
mount: mounting TFTPServer:'path to extracted iso' on /cdrom failed: Bad file descriptor
```

I'm using the IP address (now) just to avoid DNS issues.  Once it fails I get the ash prompt, so I try

```
<initramfs>
unable to find root filesystem on the network

<initramfs> mount -t nfs -o ro ip.add.re.ss:/ShareName /cdrom
mount **blah** failed, reasong given by server: Permission denied
mount **blah** failed: Bad file descriptor
```

I've tried all sorts of things, to no avail, and am beginning to believe it's got something to do with the kernel.  I can mount the NFS share from any other machine on my network (Fedora, several Ubuntu boxen, FreeBSD, OpenBSD...) none have any issue except the attempted PXE install.

I'm using syslinux.0 and copied initrd.lz and vmlinuz from casper/ extracted from the ISO to my TFTP server.

Any help would be greatly appreciated. 

*Update question*
Can I use a different kernel for this?  I believe the issue is with nfs4 (the server is nfs4.)  I tried copying the vmlinuz from / on the server but the boot failed (kernel panic), is there a syslinux kernel that supports nfs4?

---

### Post by RealityMaster on 2011-12-12
Bumpity bump

---

### Post by RealityMaster on 2011-12-13
Seems to be a lot of ppl online, so one more bump.

Also if this is related to NFS4 anyone know how to enable nfs3 as well, or is it already enabled?

---

### Post by Bucky Ball on 2011-12-13
I can't help with this issue but generally 24 hours between bumps. ;)

---

### Post by RealityMaster on 2011-12-15
I've made some progress, turns out the directory I'm sharing is on a zfs array and the bind mount is happening before the zfs store is mounted, so the bind mount is an empty directory.

My question now would be how can I make the bind mount wait for the zfs array to come online before mounting?

bind mount in fstab
```
/share  /export/share   none    bind 0 0

```

Can I put in a delay of some sort, even if it boots slower?

---

