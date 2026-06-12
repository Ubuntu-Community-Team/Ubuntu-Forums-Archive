---
title: "netdump make error"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by bobbyt87 on 2009-12-30
Has anyone seen this error when trying to install netdump. Actually working on a homework assignment and all it says is to download netdump.tar - tar xvf netdump.tar and make. Well that is fine and dandy I can do that, however I get the following when I run make: 
gcc    -c ./netdump.c
./netdump.c:27: error: conflicting types for ‘bpf_dump’
/usr/include/pcap/pcap.h:342: note: previous declaration of ‘bpf_dump’ was here
make: *** [netdump.o] Error 1


Can anyone give me some insite to this issue. I have encountered this very same issue in Ubuntu and Fedora not sure where to go from here.

Thanks
Bob

---

