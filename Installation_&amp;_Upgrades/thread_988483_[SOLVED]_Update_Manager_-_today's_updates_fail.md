---
title: "[SOLVED] Update Manager - today's updates fail"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by Devi 710 on 2008-11-20
Hi,

When I try to install the updates **Update Manager** found today (for "hpijs" HP Printing and Imaging stuff) I get the following **errors**:

------------------------------------------------------------------------
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch
-----------------------------------------------------------------

Anyone getting the same error or know what I need to do?

-I am running 7.10 Gutsy Desktop

Thanks,

Devi

---

### Post by ohzopants on 2008-11-20
I had that problem once and it turned out that my internet connection had crapped out and it was "downloading" 0 kB files.

... although, since you're posting here, I guess your internet connection probably works.

---

### Post by Partyboi2 on 2008-11-20
Have you tried changing the server you use to download from in Software Sources to another one?

---

### Post by Devi 710 on 2008-11-20
Interesting.

I changed the software source from "Main Server" to "Server for Canada" (which was much slower) then ran Update Manager and got this error:

---------------------------------------------------
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch
---------------------------------------------------------------------

Any other ideas?

Thanks

---

### Post by jimasbille on 2008-11-20
I am having the same problem.

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch

---

### Post by jruhl on 2008-11-20
I'm also having this problem with the same error messages. I have no idea how to change servers, nor to sudo-apt-get, but it looks as though no one else is making that work.
I also wonder how, if I should decide not to do a particular update, how to shut off the update icon. If you don't do an update, the icon stays on.

---

### Post by Devi 710 on 2008-11-20
There is another tread, which I think should be the one to follow so everyone is 'on the same page' so to speak:

[http://ubuntuforums.org/showthread.php?p=6220610](http://ubuntuforums.org/showthread.php?p=6220610)

---

### Post by Devi 710 on 2008-11-26
The Repos have been updated, so this issue is now solved.

Thanks for all the responses.

---

