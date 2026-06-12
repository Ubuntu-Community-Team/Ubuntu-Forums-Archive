---
title: "Using Group IDs other than the default"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by pwaldo on 2007-06-12
Hi all,

I have a NAS box that is serving files over my network to a number of Kubuntu boxes.  Each of these shares is mounted via CIFS.  The problem is that the user and group IDs are set by the NAS box, and cannot be changed.  Changing the UID of users on the clients is not a big deal, but group IDs are more problematic.

The NAS box defines groups starting at ID 102 and increases from there.  Unfortunately, this range of group IDs is taken by the Kubuntu installation.  For example, group ID 102 is syslog, 103 is klog, 104 is scanner, etc.

The only way I see to fix this is to re-map each of the groups that the NAS box defines (psuedocode below):

```
for each group ID that NAS box defines {
    edit /etc/group to map existing group ID to an unused ID
    find / -gid old_gid -exec chgrp new_gid {} \;
    hope that existing processes are not too disturbed by the GID change
}

```
And of course this procedure has to be done every time a new group gets created on the NAS box...


Is there any way to tell the Kubuntu install that all group IDs should start at a different number, say 500?  Thanks in advance!

---

### Post by pwaldo on 2007-06-12
I may have found part of the answer.  I assume that the installation program uses "addgroup" to create groups.  I can modify the /etc/adduser.conf file to make GIDs start and end wherever I want.  

The real question, is there anyway to do this *before* the groups are created on install?

---

