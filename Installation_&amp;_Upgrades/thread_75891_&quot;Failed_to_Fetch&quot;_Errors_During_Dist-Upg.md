---
title: "&quot;Failed to Fetch&quot; Errors During Dist-Upgrade"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by sillgen on 2005-10-14
I have been trying to upgrade to Ubuntu 5.10 release from 5.04 using apt-get dist-upgrade. The files download okay; however, I keep getting these errors:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.6-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.6-2_i386.deb) 403 Forbidden
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp-bin_0.3.0-2ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp-bin_0.3.0-2ubuntu7_i386.deb) 403 Forbidden
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp2c2_0.3.0-2ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtunepimp/libtunepimp2c2_0.3.0-2ubuntu7_i386.deb) 403 Forbidden
Failed to fetch
[http://us.archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr2c2_1.2.2-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr2c2_1.2.2-3ubuntu1_i386.deb) 403 Forbidden
E: Unable to fetch some archives, maybe run apt-get
update or try with --fix-missing?

I couldn't find any of these in the archive. Any suggestions?

Thanks,

Steve Illgen

---

### Post by adwait on 2005-10-14
When I was uploading, there were a bunch of such errors. I just ran apt-get update after a while and everything was fine.

---

### Post by sillgen on 2005-10-14
I did that several times, but, again, these do not appear to be in the archives (I checked using Firefox).

Is there another source other than the "official" ones or is there a workaround to this?

Thanks...:KS

---

### Post by sillgen on 2005-10-14
Never mind. I found the files!:)  I'll just download them to a separate directory, run dpkg, then try the install again.

Have a great day!

---

