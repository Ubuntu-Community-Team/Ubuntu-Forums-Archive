---
title: "Where can I find _ntfsfix_ as part of ntfs-3g for Ubuntu 14.04 on AMD64 ?"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by Cbhihe on 2014-06-02
Hello.

I just modified my /etc/fstab manually to mount an ntfs partition containing my Windows boot (C:), upon Lx startup. I want the fsck utility to be able to set the chkdsk flag on that volume when bad blocks are detected. For that I have set the <pass> option to 2. (default is 0 for NTFS). 

I thought that ntfsfix would have been included in the ntfs-3g package I installed, but it does not seem to be the case.
I need ntfsfix, apart from setting up the right symbolic links and having installed the ntfs-3g drivers to make rw possible on the NTFS volume.

Where can I find it for a 64 bit machine running Trusty Tahr ? I cannot find it in the default Ubuntu repositories and can not bring myself to install from unknown sites.
Thanks
-ced.

---

### Post by Cbhihe on 2014-06-02
Sorry, I forgot to mention something.
 I did come across [ntfs-3g_2012.1.15AR.1-1ubuntu1.2_amd64.deb]("http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-amd64/ntfs-3g_2012.1.15AR.1-1ubuntu1.2_amd64.deb.html") on [http://pkgs.org/ubuntu-12.04/ubuntu-main-amd64/ntfs-3g_2012.1.15AR.1-1ubuntu1_amd64.deb.html](http://pkgs.org/ubuntu-12.04/ubuntu-main-amd64/ntfs-3g_2012.1.15AR.1-1ubuntu1_amd64.deb.html)
That package does contain ntfsfix as well as many other things with dependencies.
However I don't know whether that is actually suitable for me and whether that ukrainian site is a recognized mirror of an Ubuntu repository or not.

---

### Post by oldfred on 2014-06-04
I am not sure ntfsfix will do much for you.

 On April 12, 2011 it was announced that Ntfsprogs project was merged with NTFS-3G
[http://en.wikipedia.org/wiki/Ntfsprogs](http://en.wikipedia.org/wiki/Ntfsprogs)
# Do not do install ntfsprogs as on newer versions it uninstalls ntfs-3g

see
man ntfs-3g
In my 12.04 I still show ntfsprogs
man ntfsprogs

It only does very minor fixes and sets chkdsk flag so real fixes will be done when booting into Windows.
Much better to just run chkdsk from your Windows install.

---

### Post by Cbhihe on 2014-06-04
@ oldfred
Thanks, I had read the Wiki on that (your link) and also visited the Tuxera site. So I knew that the two progs had merged. 
 I did not even try to install ntfsprogs.

In the meantime I verified that ntfsfix seems to be part of the ntfs-3g package installed by the original release of Ubuntu TT. 
It is good at what it does, i.e. checking the chkdsk flag on my NTFS volume (C:\)...... T'is all I want from it.
-ced

---

