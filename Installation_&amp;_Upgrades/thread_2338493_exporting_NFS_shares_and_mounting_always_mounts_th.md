---
title: "exporting NFS shares and mounting always mounts the first export folder"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by egandt on 2016-09-28
My export looks like:
/raid6/public/WORKSTATION/btdownloads 10.120.25.121(rw,fsid=0,sync,no_root_squash,no_subtree_check)
/raid6/public/WORKSTATION/Graphics/Wallpapers 10.120.25.121(ro,fsid=0,sync,no_root_squash,no_subtree_check)
/raid6/public/HTPC/Videos 10.120.25.121(ro,fsid=0,sync,no_root_squash,no_subtree_check)
exportfs -ua
exportfs -a

So I have 3 directories shared 
However no matter what I do to mount them, for instance:
mount -t nfs 10.120.25.61:/raid6/public/WORKSTATION/Graphics/Wallpapers /storage/wallpapers/
mount -t nfs 10.120.25.61:/raid6/public/WORKSTATION/btdownloads /storage/btdownloads/
mount -t nfs 10.120.25.61:/raid6/public/HTPC/Videos /storage/video/

They all are mount incorrectly as only ever "/raid6/public/WORKSTATION/btdownloads" is actually present, the other while listed as mounted are actually copies of "/raid6/public/WORKSTATION/btdownloads" and not what I want.  

For instance:
I run on the client:
TESTME:~/.config/system.d # mount -t nfs 10.120.25.61:/raid6/public/WORKSTATION/Graphics/Wallpapers /storage/wallpapers/
TESTME:~/.config/system.d # mount -t nfs 10.120.25.61:/raid6/public/HTPC/Videos /storage/videos/
TESTME:~/.config/system.d # mount -t nfs 10.120.25.61:/raid6/public/WORKSTATION/btdownloads /storage/btdownloads/

if I do I df I see:
10.120.25.61:/raid6/public/WORKSTATION/btdownloads
                     15479726080 9321282560 5378286592  63% /storage/wallpapers
10.120.25.61:/raid6/public/WORKSTATION/btdownloads
                     15479726080 9321282560 5378286592  63% /storage/videos
10.120.25.61:/raid6/public/WORKSTATION/btdownloads
                     15479726080 9321282560 5378286592  63% /storage/btdownloads

but I ran 3 different exports, the name listed is always the last entry run for instance, unmount all and then run:

TESTME:~/.config/system.d # mount -t nfs 10.120.25.61:/raid6/public/WORKSTATION/Graphics/Wallpapers /storage/wallpapers/
TESTME:~/.config/system.d # mount -t nfs 10.120.25.61:/raid6/public/HTPC/Videos /storage/videos/
Displays as:
10.120.25.61:/raid6/public/HTPC/Videos
                     15479726080 9321282560 5378286592  63% /storage/wallpapers
10.120.25.61:/raid6/public/HTPC/Videos
                     15479726080 9321282560 5378286592  63% /storage/videos

but is still the contents of "/raid6/public/WORKSTATION/btdownloads".


This is driving me crazy, as I need multiple shares and I can not seem to get it to work.  It will only share what ever is first in the exportfs file for that host and then the client does not show the proper data either.

Ubuntu 16.04lts fully patched is the source which seems to be the cause as both ubuntu 14.04 and ubuntu 16.04 do not mount properly.  If I simply export only 1 folder then it works fine.

Thanks,
ERIC

---

