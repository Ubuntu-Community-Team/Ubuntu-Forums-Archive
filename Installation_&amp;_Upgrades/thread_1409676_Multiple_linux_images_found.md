---
title: "Multiple linux images found?"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by Camaguey on 2010-02-17
I found that I had serveral versions of...? the linux kernel? 
```

GLaDOS, sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-18-generic
Found initrd image: /boot/initrd.img-2.6.31-18-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```
Is it safe to delete all but the most recent one?

---

### Post by adam814 on 2010-02-17
Yes, if everything works for you in the newest kernel you can remove the packages associated with the older ones.  It wouldn't be safe to have the package manager remove them automatically, but you can do it yourself.

---

### Post by Satoru-san on 2010-02-17
> **Camaguey said:**
> I found that I had serveral versions of...? the linux kernel? 
{snip}
Is it safe to delete all but the most recent one?
Why? Why would you delete them? They are there just incase something breaks and allow you to fix your system! They aren't hurting you and are taking up less than 5 megs each, not to mention that they are on a completly different partiton. 

If you must delete, delete only the oldest one*. Keep the newer one!

*only if you run out of space

> **adam814 said:**
> Yes, if everything works for you in the newest kernel you can remove the packages associated with the older ones. {snip}

bad advice is bad.

---

### Post by ubunterooster on 2010-02-17
I got rid of mine. for more details go to my profile (by clicking on my avatar) and look at recent post " too many boot entries"

---

### Post by adam814 on 2010-02-17
Well, if you have the kernel images and the headers for them installed they can take up to 200MB each.  If you have 5 or 6 old kernels it might be time to start pruning some of the older ones.

---

### Post by Satoru-san on 2010-02-17
> **adam814 said:**
> Well, if you have the kernel images and the headers for them installed they can take up to 200MB each.  If you have 5 or 6 old kernels it might be time to start pruning some of the older ones.

here is the thing, you do NOT need the kernel source to boot a kernel that is already compiled. I unmerged my old kernel sources, but I can still boot my old kernels, just dont delete from the /boot/ folder.

---

### Post by ubunterooster on 2010-02-17
just keep the 2 most recent. old kernels are backups and how many backups are needed?

---

### Post by Satoru-san on 2010-02-17
> **ubunterooster said:**
> just keep the 2 most recent. {snip}
This, except just mv them into your /home/ folder don't rm them.

---

### Post by kenji_03 on 2010-03-05
Here is Ubunterooster's thread and the way to do this for us Ubuntu noobs

> **smerral said:**
> To get rid of an older kernel (using 2.6.31-16-generic as an example) do:

sudo apt-get purge linux-image-2.6.31-16-generic

[http://ubuntuforums.org/showthread.php?t=1397934&highlight=boot+entries](http://ubuntuforums.org/showthread.php?t=1397934&highlight=boot+entries)

I was able to find a list of my entries using the "/boot/grub/menu.lst" file

---

### Post by adam814 on 2010-03-05
You can always find out which ones you have installed using "dpkg --list | grep linux-image".  Only legacy GRUB users will have a menu.lst file.

---

