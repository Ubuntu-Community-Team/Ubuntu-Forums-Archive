---
title: "Provisioning samba 4.1 and get ACL error"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by yoyorhino on 2013-11-19
I am installing a new server with Samba 4.1 to be used as an Active Directory and a Domain Controller.  

I use ```
/usr/local/samba/bin/samba-tool domain provision
``` to provision Samba, but after I put in my inputs using BIND9_DLZ I receive This error

```
 Server Role (dc, member, standalone) [dc]: DNS backend (SAMBA_INTERNAL, BIND9_FLATFILE, BIND9_DLZ, NONE) [SAMBA_INTERNAL]: BIND9_DLZ
Administrator password:
Retype password:
Looking up IPv4 addresses
Looking up IPv6 addresses
No IPv6 address will be assigned
ldb: module schema_load initialization failed : No such object
ldb: module rootdse initialization failed : No such object
ldb: module samba_dsdb initialization failed : No such object
ldb: Unable to load modules for /usr/local/samba/private/sam.ldb: (null)
samdb_connect failed
VFS connect failed!
ERROR(<class 'samba.provision.ProvisioningError'>): Provision failed - ProvisioningError: Your filesystem or                                 build does not support posix ACLs, which s3fs requires.  Try the mounting the filesystem with the 'acl' optio                                n.
  File "/usr/local/samba/lib/python2.7/site-packages/samba/netcmd/domain.py", line 398, in run
    use_rfc2307=use_rfc2307, skip_sysvolacl=False)
  File "/usr/local/samba/lib/python2.7/site-packages/samba/provision/__init__.py", line 2052, in provision
    raise ProvisioningError("Your filesystem or build does not support posix ACLs, which s3fs requires.  Try                                 the mounting the filesystem with the 'acl' option.")



```

Here is my /etc/fstab

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/duncan--vg-root /               ext4  defaults,user_xattr,acl,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=14b30d16-6648-4422-8300-45d90eb34edd /boot           ext2    defaults        0       2
/dev/mapper/duncan--vg-swap_1 none          swap    sw              0       0



```

I am lost on what to try/do to fix this. 

Thanks

---

### Post by yoyorhino on 2013-11-20
I changed the command and it went through this time.  Hopefully the rest goes smoothly.

```
sudo /usr/local/samba/bin/samba-tool domain provision --use-rfc2307 --interactive --use-ntvfs

```

---

