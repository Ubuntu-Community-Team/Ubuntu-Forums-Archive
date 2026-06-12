---
title: "No usplash, Hoary to Breezy upgrade"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by valfader on 2005-10-13
Hi
Usplash is not working when I made a upgrade from Hoary.
Usplash and all the dependencies is installed and seem to be correct.

"sudo dpkg-reconfigure linux-image-2.6.12-9-386" gives this output...

```
Not touching initrd symlinks since we are being reinstalled (2.6.12-9.23)
Not updating image symbolic links since we are being updated (2.6.12-9.23)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
**Searching for splash image... none found, skipping...**
Found kernel: /vmlinuz-2.6.12-9-386
Found kernel: /vmlinuz-2.6.10-5-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Any Ideas?

---

### Post by invalid on 2005-10-13
It didn't work for me at first, until I manually reinstalled usplash.

sudo apt-get --reinstall install usplash

Maybe this will work for you as well.

Cheers,
Cb

---

### Post by valfader on 2005-10-13
Already try it, didnt work :(

---

### Post by delhi.9 on 2005-10-13
Hi!

The output just means that there wasn't found any grubsplash (a background for grub), it doesn't have anything to do with the usplash. For me, manually reinstalling the kernel solved the problem. I don't know why it worked... weird :-k

---

### Post by valfader on 2005-10-13
It worked, thanks!

---

### Post by TheIdiotThatIsMe on 2005-10-14
[QUOTE=delhi.9]Hi!

The output just means that there wasn't found any grubsplash (a background for grub), it doesn't have anything to do with the usplash. For me, manually reinstalling the kernel solved the problem. I don't know why it worked... weird :-k[/QUOTE]

I'm not sure what you mean by manually reinstalling the kernel?

---

### Post by ilans on 2005-10-14
I did the following command that fix the usplash problem:

sudo dpkg-reconfigure linux-image-$(uname -r)

---

### Post by DoddyUK on 2005-10-14
[QUOTE=TheIdiotThatIsMe]I'm not sure what you mean by manually reinstalling the kernel?[/QUOTE]

Yeah, could you please elaborate on that? By "manually reinstalling the kernel", do you mean **sudo apt-get --reinstall install linux-image-2.6.12-9-386**, reinstalling the kernal image, then doing **sudo dpkg-reconfigure linux-image-$(uname -r)**?

---

### Post by foxiness on 2005-10-14
thank you TheIdiotThatIsMe it work with me after i did what you say about reinstalling the linux-image .

but can i do this with the other kernel i have Hoary kernel ?

---

