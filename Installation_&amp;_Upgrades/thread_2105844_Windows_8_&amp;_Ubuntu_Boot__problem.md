---
title: "Windows 8 &amp; Ubuntu Boot  problem"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by MMShreyas on 2013-01-17
hi guys i am new to the forum.
i had windows 7 installed on my laptop hp envy 17
i installed ubuntu 12.10 in windows 7 by using wubi installer
in another partion F drive
it worked fine.. 
after this i installed windows 8
ubuntu does not appears in the menu now (uefi is not enabled)

i tried boot-repair it did not worked
here is the report [http://paste.ubuntu.com/1540570/](http://paste.ubuntu.com/1540570/)
screen shot of that folder
[http://i1279.photobucket.com/albums/y535/MMShreyas/Untitled_zps2a77b94c.png](http://i1279.photobucket.com/albums/y535/MMShreyas/Untitled_zps2a77b94c.png)

---

### Post by Warren Hill on 2013-01-17
When you installed Windows assuming you did not overwrite your Ubuntu the MBR (Master boot record) gets replaced.  So It no longer knows about Ubuntu.

Windows does that.  Microsoft assume you only want their OS.

Fortunately it's easy to fix.  See here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Warren Hill on 2013-01-17
Sorry Ignore my last post.  If you installed with Wubi and then replaced Win7 with Win8 its gone and will need to be installed again.

There is more info here
[https://help.ubuntu.com/community/ReinstallWindowsWithoutLosingUbuntu](https://help.ubuntu.com/community/ReinstallWindowsWithoutLosingUbuntu)

---

### Post by oldfred on 2013-01-17
It looks like you installed wubi to a separate partition sda6, so it was not inside the Windows 7 partition. Wubi does not work with gpt partitions which new pre-installed Windows have, but I think it will work with Windows 8.

Most installs of wubi are inside the main Windows install to avoid the partitioning issues of a full partitioned install. 

You may just need to update the BCD with new wubi entry.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

            bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

