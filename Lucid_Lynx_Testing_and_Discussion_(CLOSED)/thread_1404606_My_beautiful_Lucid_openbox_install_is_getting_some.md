---
title: "My beautiful Lucid openbox install is getting some cracks in it after recent updates."
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Mustard on 2010-02-11
It was a nice install for a while after the release of Alpha 2. :)

Now I'm back to using 'xdm' to login, as 'slim' is sometimes locking up, or not behaving as directed anyway.

The latest 'nitrogen' build is segfaulting, so I've lost my desktop background.

...and the seemingly ominipresent 'gvfs-gdu-volume' segfault is still around..

Not to mention the new grub packages that asked me a question I didnt really fully understand, subsequently choosing an option I shouldnt have.  I vainly attempted to reconfigure the package with dpkg-reconfigure and then found I can't boot windows anymore....so much fun in one day!! :)

Probably going to restrore the mbr and do a clean install I think. :D

I briefly contemplated filing some bug reports on launchpad for nitrogen and others, but the jargonese they are all speaking atm is going over my head, so I'm not sure how useful it would be for me to contribute my own comments.

```
Feb 12 06:51:11 lucidtest kernel: [  105.028578] gvfs-gdu-volume[2048]: segfault at 18 ip 00007f556ad43d21 sp 00007fffd314af60 error 4 in libgdu.so.0.0.0[7f556ad39000+21000]
Feb 12 06:51:26 lucidtest kernel: [  119.948546] nitrogen[1965]: segfault at 8 ip 0000000000417cde sp 00007fff5351c270 error 4 in nitrogen[400000+4f000]
Feb 12 06:52:34 lucidtest kernel: [  188.097531]  [2516]: segfault at 18 ip 00007f6077018d21 sp 00007fffc3be5ea0 error 4 in libgdu.so.0.0.0[7f607700e000+21000]
Feb 12 06:53:00 lucidtest kernel: [  214.744394] nitrogen[2317]: segfault at 8 ip 0000000000417cde sp 00007ffff5f29940 error 4 in nitrogen[400000+4f000]
Feb 12 06:53:44 lucidtest kernel: [  258.904651] nitrogen[2723]: segfault at 20aa000 ip 00007f7e6487e0cf sp 00007fffb125a4b8 error 4 in libc-2.11.1.so[7f7e647f8000+175000]

```

---

### Post by ibuclaw on 2010-02-23
I can confirm this, have you raised a bug? If not, I'll happily do one for you. :)

---

### Post by ibuclaw on 2010-02-23
Impatient me, I've raised a bug with a fixed attached.

[https://bugs.launchpad.net/ubuntu/+source/nitrogen/+bug/526655](https://bugs.launchpad.net/ubuntu/+source/nitrogen/+bug/526655)

Regards
Iain

---

### Post by Mustard on 2010-02-24
I filed my bug here...

[https://bugs.launchpad.net/ubuntu/+source/nitrogen/+bug/520861](https://bugs.launchpad.net/ubuntu/+source/nitrogen/+bug/520861)

---

### Post by ibuclaw on 2010-02-25
> **Mustard said:**
> I filed my bug here...

[https://bugs.launchpad.net/ubuntu/+source/nitrogen/+bug/520861](https://bugs.launchpad.net/ubuntu/+source/nitrogen/+bug/520861)

That bug is private, so am unable to see it. :)

---

### Post by Mustard on 2010-02-25
> **ibuclaw said:**
> That bug is private, so am unable to see it. :)

Oh..I didnt realise.  It's set to public now.

---

### Post by ibuclaw on 2010-02-25
> **Mustard said:**
> Oh..I didnt realise.  It's set to public now.

No probs. But seriously, this has been fixed upstream. (I tracked down the issue, then realised nitrogen released a new version with the same fix). I'll link the two bugs, as they are the same issue / same fix.

Regards

---

