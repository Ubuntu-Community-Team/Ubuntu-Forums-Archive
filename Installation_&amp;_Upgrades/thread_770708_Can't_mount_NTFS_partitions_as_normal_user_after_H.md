---
title: "Can't mount NTFS partitions as normal user after Hardy upgrade"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by bitter_mike on 2008-04-27
Hey all,

I just upgraded to Hardy and it mostly broke things rather than give me any new functionality or features. I used to have it set up so I could mount my external hard drive's NTFS partition as a normal user. After the upgrade, it gives me the following error:

Unprivledgwd user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivledged](http://ntfs-3g.org/support.html#unprivledged)

So I went to that site and it gave me instructions for setting the setuid bit for the ntfs-3g binary, which I remembered doing when I first fixed this problem in Gutsy. So I did that again, hoping it would fix it again but instead, I get this new error message:

Mount is denied because the setuid and setgid root ntfs-3g is insecure with the external FUSE library. Either remove the setuid/setgid bit from the binary or rebuild NTFS-3G with integrated FUSE support and setuid root.

If I'm reading this right, the first error told me to go to the website and do what they said there. Then the second error is telling me to undo what I just did. Thats stupid. Anyone know how to get this to work right or can tell me just how I'd go about getting NTFS-3g with integrated FUSE support?

EDIT:
I just realized that if I remove the line for the NTFS partition of my external HD from the /etc/fstab file, I can mount it fine as a normal user. However, it was working fine with the current fstab entry in 7.10, so I don't know what changed. This is the line from /etc/fstab:

UUID=72A81A4AA81A0CEB /mnt/External ntfs-3g rw,user,noauto 0 0

Why doesn't that work now?

---

### Post by phelge on 2008-06-12
Same problem here. Found some more infos here : [http://bugs.archlinux.org/task/9748](http://bugs.archlinux.org/task/9748)

---

