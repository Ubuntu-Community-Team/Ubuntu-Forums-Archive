---
title: "Mint 16 cinnamon - freeze after usb 3.0 external drive mounting"
date: 2014-01-02
forum: MINT
---

### Post by jack_walker on 2014-01-02
Hi,

I have mint 16 x64 with cinnamon and kernel 3.12.6.
When I  plug in my external drive Verbatim, nemo opens and mounts the drive,  after that the system freezes. So I need to unplug the drive and  cinnamon restarts after a "kill by signal 15" I saw in my log file.
Same problem witn default kernel 3.11.

In the past I had ubuntu x64 with kde and same kernel 3.12.6 on the same machine and I had no problems with my external drive.
So maybe it's a mint or cinnamon related problem.

here is my syslog: [http://pastebin.com/raw.php?i=HXGfJbEN](http://pastebin.com/raw.php?i=HXGfJbEN)

Any help?

Thanks

---

### Post by tgalati4 on 2014-01-02
I'm running Mint14 based on 12.10.  Do you have ntfs support on your machine?

```
apropos ntfs
```

It might look like:

tgalati4@Mint14-Extensa ~ $ apropos ntfs
filesystems (5)      - Linux file-system types: minix, ext, ext2, ext3, ext4, Reiserfs, XFS, JFS, xia, msdos, umsdos, vfat, ntfs, proc, nfs, iso9660, hpfs...
fs (5)               - Linux file-system types: minix, ext, ext2, ext3, ext4, Reiserfs, XFS, JFS, xia, msdos, umsdos, vfat, ntfs, proc, nfs, iso9660, hpfs...
lowntfs-3g (8)       - Third Generation Read/Write NTFS Driver
mkfs.ntfs (8)        - create an NTFS file system
mkntfs (8)           - create an NTFS file system
mount.lowntfs-3g (8) - Third Generation Read/Write NTFS Driver
mount.ntfs (8)       - Third Generation Read/Write NTFS Driver
mount.ntfs-3g (8)    - Third Generation Read/Write NTFS Driver
ntfs-3g (8)          - Third Generation Read/Write NTFS Driver
ntfs-3g.probe (8)    - Probe an NTFS volume mountability
ntfs-3g.secaudit (8) - NTFS Security Data Auditing
ntfs-3g.usermap (8)  - NTFS Building a User Mapping File
ntfscat (8)          - print NTFS files and streams on the standard output
ntfsclone (8)        - Efficiently clone, image, restore or rescue an NTFS
ntfscluster (8)      - identify files in a specified region of an NTFS volume.
ntfscmp (8)          - compare two NTFS filesystems and tell the differences
ntfscp (8)           - copy file to an NTFS volume.
ntfsfix (8)          - fix common errors and force Windows to check NTFS
ntfsinfo (8)         - dump a file's attributes
ntfslabel (8)        - display/change the label on an ntfs file system
ntfsls (8)           - list directory contents on an NTFS filesystem
ntfsprogs (8)        - tools for doing neat things with NTFS
ntfsresize (8)       - resize an NTFS filesystem without data loss
ntfsundelete (8)     - recover a deleted file from an NTFS volume.
smbcquotas (1)       - Set or get QUOTAs of NTFS 5 shares

---

### Post by jack_walker on 2014-01-02
same output for me from ```
apropos ntfs
```

I have ntfs support, indeed other usb ntfs drives work fine.
Actually I have another usb 3.0 external drive and I have just plugged it in and it works well my machine, no system freezes.

So now it is strange, I'm pretty sure it can't be a problem concerning the specific Verbatim external drive because it used to work with ubuntu and kde (same kernel 3.12.6) and it also works well in windows 7/8.

So now I'm confused ](*,)

**edit**: I have just discovered that my Verbatim drive that causes the freeze works on my laptop with same software: mint 16, cinnamon and kernel 3.12.6.
So could the issue be related to mint or cinnamon and my hardware configuration?
I have:

 
[LIST]
[*]motherboard ASUS P8P67 PRO 
[*]cpu Intel® Core&#8482; i5-2500 Processor 
[*]my OS is running on a Crucial SSD M4 
[/LIST]
 
I have just read again the syslog and maybe the problem is about the* .Trash-1000* folder content, it seems that the errors occur when trying to read some data from that folder.

what do you thing?

---

