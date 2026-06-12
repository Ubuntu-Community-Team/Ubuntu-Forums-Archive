---
title: "Recovery mode goes straight to Gnome?"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by khughitt on 2009-09-16
Hello,

I recently tried to boot into recovery mode, but each time I tried, X was automatically initialized. I checked the relevant portion of the grub configuration file, and it looks okay:

```

menuentry "Ubuntu, Linux 2.6.31-10-generic-pae (recovery mode)" {
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 270e230f-7bd1-4a20-9c0d-8cbb3b7c48d2
	linux	/boot/vmlinuz-2.6.31-10-generic-pae root=UUID=270e230f-7bd1-4a20
-9c0d-8cbb3b7c48d2 ro single 
	initrd	/boot/initrd.img-2.6.31-10-generic-pae
}

```

I originally installed 9.10 Server, and then added gdm and xinit on top. Is it possible that the installation added xinit to and earlier level than usual so that it ends up being run during single user mode?

Any ideas what is going on?

-- edit --

Okay, I checked and found that there is indeed and file "S12x11-common" in /etc/rcS.d. Is is safe to move this file somewhere else, or is there a better way? Any help would be greatly appreciated.

Thanks!

---

### Post by VMC on 2009-09-16
I had the same experience yesterday. My "recoery" mode is just a simple matter of adding "single" to the end of the kernel stanza. 

I didn't go as far as looking into any rc files yet. I was going to let the updates catch up and maybe it will straighten out. Yesterday, when we had so much trouble with the updates. Thinking it was me, I complicated the matter by doing things I shouldn't have.

I'll try the recover mode and see if it is fixed now.

---

### Post by khughitt on 2009-09-22
Any suggestions?

---

