---
title: "Samba doesn't recognize folder when mounted by crypt apps"
date: 2021-04-12
forum: Installation &amp; Upgrades
---

### Post by hikariws on 2021-04-12
Hello!

I had installed Dropbox on my Ubuntu 20.04 server and now I'm trying to mount my folder created with EncFSMP on Win10. Dropbox folder is inside a structure shared by Samba and I wanna mount the encrypted folder on a folder outside Dropbox and inside the same share, so that I can access them from VMs and Live CDs.

Before attempting it, I created a new encryption folder to make tests. As I know EncFS has security vulnerabilities, I also tried other solutions: CryFS and Cryptomator.

But all 3 failed. Locally I'm able to create files inside the folders and see changes happening inside Dropbox and being synched to my PCs. When mount is disabled, the folders are also visible from SMB. But once I mount them, they disappear from SMB, as if they were deleted.

This happened with these 3 encryption softwares, so I guess it's something related to how they mount their virtual drives. I have another folder on SMB with folders on it where I mount my external HDs and they are all used normally.

Might it be some smb.conf setting I'm missing? Or is it rly not possible?

---

