---
title: "F2FS multidrive installation"
date: 2020-05-20
forum: Installation &amp; Upgrades
---

### Post by spupazza on 2020-05-20
[COLOR=#121112][FONT=&quot]So I'm trying to take advantage of the F2FS multi drive capabilipties, which will basically will let F2FS
see 2 of my drives as one .
The 2 nvme drives are formatted to the f2fs file-system with a partition created in each of the drives.
Then I run the command: sudo mkfs.f2fs -f -c /dev/nvme0n1 /dev/nvme1n1, and the format is successful.
The problem is that the installer doesn't detect the new 'volume' but still see the 2 disks as separate entities.
Is it possible to make see the installer the 2 drives as one? If so how do I do that?[/FONT][/COLOR]
[COLOR=#121112][FONT=&quot]F2fs-tools is installed, in case anyone is wondering.[/FONT][/COLOR]

---

### Post by TheFu on 2020-05-20
When did f2fs become supported for boot or OS partitions?

I've only used f2fs for data.  To have a file system span multiple partitions, I'd use lvm, then format an lv with whatever fs I want.  But that wouldn't magically make booting work.  For that the initrd would need to updated to support whatever else you need.  Sorry, don't know the details well enough to advise on specifics.

---

