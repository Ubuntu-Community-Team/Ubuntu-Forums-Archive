---
title: "Re-started during update"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by danbar on 2008-08-12
I was updating Ubuntu when the computer re-started (probably because of the extremely hot weather).  Now a message appears: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now when I tried to do so in the terminal with the root password it said the *requested operation requires superuser privilege* ??!!!

Any idea ?

---

### Post by iaculallad on 2008-08-12
> **danbar said:**
> I was updating Ubuntu when the computer re-started (probably because of the extremely hot weather).  Now a message appears: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now when I tried to do so in the terminal with the root password it said the *requested operation requires superuser privilege* ??!!!

Any idea ?

In your terminal, try:

```
sudo dpkg --configure -a
```

Had you manually enabled the root account? Do you see the # in your terminal?

---

### Post by danbar on 2008-08-13
thanks for answering.  Well I don't know why but there is no root sign in the terminal!

I'm using the following page for the root password ([http://www.nukesilo.com/2007/03/06/enabling-the-root-user-password-on-ubuntu/](http://www.nukesilo.com/2007/03/06/enabling-the-root-user-password-on-ubuntu/))

---

### Post by danbar on 2008-08-13
Sorry, I forgot to do the su command!!

Yes I was successful.  

This was the output...

Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-rt


Is it ok now?
Thanks for your time and patience!

---

### Post by danbar on 2008-08-13
NO it's not ok!  Now I have the one-way red sign on the task bar.  It says that error: BrokenCount > 0

This usually means that your installed packages have unmet dependencies. ??

---

### Post by danbar on 2008-08-13
When I started the Package Manager it said: 

You have one broken package on your system.  Use the the "broken filter" to locate it.  

How?

---

### Post by danbar on 2008-08-13
Yes I solved it!!

Open synaptic.
select the edit tab and click Fix broken package.  Finally Apply.

---

