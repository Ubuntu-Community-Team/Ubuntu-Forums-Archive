---
title: "UNR 9.10 Update Errors"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by s.fox on 2009-10-12
Hello,

I have been trying out Ubuntu Netbook Remix 9.10 and seem to be getting this error when I try and run updates:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.3-0ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.3-0ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.3-0ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgomp1_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/cpp-4.4_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgcc1_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/gcc-4.4_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/g++-4.4_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.1-4ubuntu6_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_3.9.8-1ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.9.8-1ubuntu1_all.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.9.8-1ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/gcc-4.3_4.3.4-5ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/cpp-4.3_4.3.4-5ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.4-5ubuntu1_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.28.0-0ubuntu12_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xsplash/ubuntu-xsplash-artwork_0.8.2-0ubuntu2_i386.deb 404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xsplash/xsplash_0.8.2-0ubuntu2_i386.deb 404  Not Found

```

Is anyone else having this problem or can advise me on what to do? If any further information needed then please ask :)

Thank you for any help,

Silver Fox

---

### Post by dabl on 2009-10-12
Either there is a problem with the networking on your system, or else there's a problem at the GB repo.

Can you browse the Internet satisfactorily?

---

### Post by s.fox on 2009-10-12
Thank you for the response.

Yes,  I am using it right now to post on this forum.  Internet seems to be fine.  I just wasn't sure what to do so figured someone might be elaborate what the problem is and more importantly a fix if its my fault.

Thank you again,

-Silver Fox

---

### Post by maheshasolkar on 2009-10-12
There is a 404 (Not Found) response. So I think the network is fine. The files are not on the server. Not sure why the files would be missing.

May be try an 'aptitude update' once again?

---

### Post by maheshasolkar on 2009-10-12
If you look at the directory listing (e.g. [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/)) the files mentioned in the errors indeed don't exist.

May be the mirror you are using is not updated yet? Can you try to find a different mirror to get your files from?

---

### Post by s.fox on 2009-10-12
I suppose I could use a different mirror,  but I might just wait it out.   Plus I can post back when gb is sorted out to let others know.

-Silver Fox

---

### Post by s.fox on 2009-10-18
Hello,

Just to let others know,  its been 5 days and I am still getting the 404 messages.  How do I change mirror?

Many thanks,

-Silver Fox

Edit:  I found it.  All sorted now. :)

---

