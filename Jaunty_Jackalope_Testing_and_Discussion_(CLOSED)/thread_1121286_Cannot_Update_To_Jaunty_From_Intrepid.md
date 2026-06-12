---
title: "Cannot Update To Jaunty From Intrepid"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aliencam on 2009-04-09
I'm using 8.10 Intrepid x64 and I cannot do the "update-manager -d" upgrade to Jaunty. 

 It gets to the "setting new software channels" item, then stops with this error: 

```
Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources.bz2  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.


```


I have checked my network, reconnected to a different network, switched between wireless and ethernet, changed servers a dozen times, and I get this error every time I try to upgrade. 

I am able to 

```
wget http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources.bz2
```

without a problem, it seems only the upgrade cannot connect. 


the contents of the file that cannot be downloaded are  as follows: 


```
Package: adobe-flashplugin
Binary: adobe-flashplugin
Version: 10.0.12.36-1intrepid2
Priority: optional
Section: partner/web
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Build-Depends: cdbs, debhelper (>= 5), libgtk2.0-0, libice6, libnspr4-0d, libnss3-1d, libsm6, libxt6
Architecture: i386 lpia
Standards-Version: 3.7.2
Format: 1.0
Directory: pool/partner/a/adobe-flashplugin
Files:
 e704736a067380e62989f1b20413ca75 725 adobe-flashplugin_10.0.12.36-1intrepid2.dsc
 265748a1f8ab6fd4474a70fa24b69569 3933621 adobe-flashplugin_10.0.12.36.orig.tar.gz
 031f7d48e9546cd0adac572639383bef 2304 adobe-flashplugin_10.0.12.36-1intrepid2.diff.gz
```

---

### Post by majamba on 2009-04-09
it might be best to wait,
because when i tried it killed my linux system totaly

---

### Post by aliencam on 2009-04-09
well I've already tried a fresh install on this laptop with a spare hdd I have, so I know everything in Jaunty works.  I don't care as long as I don't loose data.

---

### Post by majamba on 2009-04-09
i agree it does work pretty well from a fresh install on my desktop

i guess the update did not like my kde 4.2 on 8.10 interpid because i got a bynch of erors than the system died so endup reinstalling

---

### Post by willrobbo on 2009-04-10
> **aliencam said:**
> I'm using 8.10 Intrepid x64 and I cannot do the "update-manager -d" upgrade to Jaunty. 

 It gets to the "setting new software channels" item, then stops with this error: 

```
Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources.bz2  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.


```


I have checked my network, reconnected to a different network, switched between wireless and ethernet, changed servers a dozen times, and I get this error every time I try to upgrade. 

I am able to 

```
wget http://archive.canonical.com/ubuntu/dists/jaunty/partner/source/Sources.bz2
```

without a problem, it seems only the upgrade cannot connect. 


the contents of the file that cannot be downloaded are  as follows: 


```
Package: adobe-flashplugin
Binary: adobe-flashplugin
Version: 10.0.12.36-1intrepid2
Priority: optional
Section: partner/web
Maintainer: DL-Flash Player Ubuntu <FlashPlayerUbuntu@adobe.com>
Build-Depends: cdbs, debhelper (>= 5), libgtk2.0-0, libice6, libnspr4-0d, libnss3-1d, libsm6, libxt6
Architecture: i386 lpia
Standards-Version: 3.7.2
Format: 1.0
Directory: pool/partner/a/adobe-flashplugin
Files:
 e704736a067380e62989f1b20413ca75 725 adobe-flashplugin_10.0.12.36-1intrepid2.dsc
 265748a1f8ab6fd4474a70fa24b69569 3933621 adobe-flashplugin_10.0.12.36.orig.tar.gz
 031f7d48e9546cd0adac572639383bef 2304 adobe-flashplugin_10.0.12.36-1intrepid2.diff.gz
```

I had the exact same problem.

To get around this, edit your Repositories with Synaptic. Disable the Partner repository until your update has been completed.

Hope this helps.

---

### Post by Wiley99 on 2009-04-10
> **willrobbo said:**
> I had the exact same problem.

To get around this, edit your Repositories with Synaptic. Disable the Partner repository until your update has been completed.

Hope this helps.

This worked for me, it's updating a Remastersys copy of my desktop in VirtualBox right now! Thanks alot!!

---

### Post by aliencam on 2009-04-10
that worked, thanks!

---

### Post by willrobbo on 2009-04-13
> **aliencam said:**
> that worked, thanks!

No problem at all, glad you got things sorted out.

I'm running the Jaunty Beta at the moment and haven't had any problems so far. Just to confirm, you can re-enable the Partner repository after the update and things will work as normal.

---

