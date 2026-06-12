---
title: "link to SMB filie"
date: 2018-12-20
forum: MINT
---

### Post by kakashi_12 on 2018-12-20
I am currently running Mint 18.3 on a laptop.
Tried to create a link to a file, located on the SMB share. It said that it wasn't supported.

Is there a way to get around this so I can put links/shortcuts in my Home Folder OR in another SMB share folder?

I read something about NFS as a solution. But I'm not sure if that is a type of File Manager or Application or what.
I don't want to replace my current/default File Manager. Wouldn't mind having a 2nd one along side my existing though if that fixes it.
Thanks in advance for any help.

---

### Post by TheFu on 2018-12-20
I don't know if this is helpful.  I don't use CIFS with links.

Symbolic links are part of the file system, not something any GUI adds.  They work regardless of the program being used, but the file system must support it.

And SMB share is an implementation of the CIFS protocol.

NFS is the native way that Unix systems share files. NFS retains almost all the expected Unix file system capabilities, including symbolic link support and full file ownership, groups, permissions and ACLs.  NFS is usually about 10-20% faster than CIFS too.  I'm positive that symlinks work with NFS.

If you have 2 Unix systems and want to share files, using NFS is the natural solution.  The only time when I'd choose CIFS over NFS is when I have Windows clients on the same LAN.

---

### Post by kakashi_12 on 2018-12-28
How do I create a link/shortcut with NFS then? Or you're telling me to use NFS on my client PC?

Windows clients are on the same LAN. It's 99% Windows. Pretty sure I'm the only Linux client with a few Linux servers.

---

