---
title: "CIFS Entry for FSTAB"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by measekite on 2010-11-11
I just went from Jaunty to Maverick.  I booted Maverick and manually mounted my Windows Network drives by clicking on the appropriate "mount" command in the directory /media.

I then created an fstab file like I did in Jaunty.  Here is the smb mount command that I had in the fstab file.  I had a file with the user id and password in the credentials file.
```

//???.???.??.?public_p/media/servername smbfs credentials=root,dmask=0777,fmask=0777 0 0

```

This provided me access to my server for the past 18 months.

I modified the fstab file for Maverick which was working fine for 3 days so I would automatically mount the server drives.
[COLOR=Red]
**Here is the Error:**[/COLOR]

"SMBFS is no longer supported in the kernel.  You must use CIFS.

[B]Can somebody translate the SMB code and explicitly provide me with the CIFS code and any other files including their location so I can modify my fstab file?
[/B]
Thanks in advance.

---

### Post by gzarkadas on 2010-11-13
Change in your fstab line:

`smbfs' to `cifs'
`dmask' to `dir_mode'
`fmask' to `file_mode'

You may also have to provide the following additional options: 

_netdev
iocharset=utf8

I believe the smbclient package and related ones are already installed; if not install them.

---

