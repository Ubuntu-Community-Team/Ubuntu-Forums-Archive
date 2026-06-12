---
title: "Sleep 'invalid number 0.1', busybox problem. Can't boot."
date: 2009-06-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2009-06-24
Ok guys, here's another one for you ...

Boot fails with multiple, sleep 'invalid number 0.1' errors.. This is related to busybox as suggested [here.]("https://wiki.ubuntu.com/Grub2")

So I need to upgrade busybox from this [PPA. ]("https://launchpad.net/~dupondje/+archive/ppa")

So probably I need to chroot into my root partition. But I only have a hardy live cd. [COLOR="Red"]And my root partition is EXT4[/COLOR]

Any escape routes ? I guess for chrooting I would need to mount my root partition ?

---

### Post by vikrant82 on 2009-06-24
Or should I rather be asking - How to mount an ext4 partition in hardy ?

---

### Post by Martey on 2009-06-24
If you converted your root partition from ext3 and did not enable extents or any other ext4-specific features, I think you might be able to still mount it as ext3.

Have you tried booting into recovery mode and using the root prompt there to fix the issue?

---

### Post by vikrant82 on 2009-06-24
Yes, tried recovery mode.. Same error.

Well I guess, I played around with quite a few mount options with ext4. So it fails to mount with ext3 or ext2. I can however mount the partition in windows as ext2.

---

### Post by budluva04 on 2009-06-24
ermmm i was going to point you to the ppa, but you've found it...

can you not boot any previous kernels? as it only affects the 30-10 kernel, 30-09 should be fine

---

### Post by ghindo on 2009-06-24
I experienced the same error, but (somehow) was able to finally boot in recovery mode and run updates, which seems to have solved the problem (for now).

My suggestion would be...persistence? :?

---

### Post by vikrant82 on 2009-06-24
> 30-09 should be fine
yeah, but on a 60G hard drive, those 160MB look like treasure, so removed it. Lessons learnt. But I guess this would be there even on previous kernels.

> My suggestion would be...persistence?
> but (somehow) was able
Did you use any other boot options ? 

I guess my limited options include downloading and burning Karmic alpha. What else?

---

### Post by doctordruidphd on 2009-06-24
The problem appears to be that the boot-by-uuid process is broken. If you can get to your grub menu (such as with a live-cd or another system), change the uuid stuff to /dev/sda notation, and it should boot fine.
Alternatively, at the grub menu you can hit 'c' to enter the command mode, then type the following:
```
kernel   /vmlinuz root=/dev/sda1 ro
initrd   /initrd.img
boot
```
Substituting your own partition for the /dev/sda1 part.
If you are using proprietary video drivers, you may need to get into recovery mode by adding 'single' to the end of the kernel line.

There are also problems with the fact that the kernel was compiled with gcc-4.3, and karmic recently upgraded to gcc-4.4. You can fix this problem by changing the gcc symbolic link in /usr/bin to point to gcc-4.3

That's how I got it up and running.

---

### Post by ghindo on 2009-06-24
> **vikrant82 said:**
> Did you use any other boot options ?Nope.  I tried "nomodeset" (as suggested [here]("http://ubuntuforums.org/showpost.php?p=7507279&postcount=12")), but it didn't do anything.  I just kept trying recovery mode until I got something.

---

### Post by rumblered on 2009-06-24
When I got stuck in busybox, I just typed 'exit' and it booted.

---

### Post by autocrosser on 2009-06-24
Same thing here--tried several other fixes--just typing "exit" at the busy-box worked.... The -10 kernel is working here.

---

### Post by vikrant82 on 2009-06-24
:o, Damn. 

Eventually I was able to chroot through the shell thrown by busybox, but could not get my connection working. 

But then next time it simply worked without anything, as ghindo suggested.

Anyways, I will upgrade all the packages, in this boot itself. 

Another thing I noticed was that KMS enabled by defaut in 2.6.30-10. Is it ? Or its just the resolution.

But ubuntu loading screen was in 1027x768 and then it booted into same resolution in my KDE. I had to manually change my reso to 1280x800. But that's a diff story and none of my concerns right now.

EDIT : The busybox PPA and updates didnt make any difference, the boot still fails. "exit" works..

EDIT 2 : Hadn't run the update-initramfs, doing it fixes the problem.

---

### Post by knarf on 2009-06-24
You can often get out of these situations by booting in single user mode while replacing init with a shell. Use whatever method your boot manager provides to access the kernel parameters used on boot and add

```
init=/bin/busybox
```

(or init=/bin/ash or whatever shell you have in place) at the end. As long as you have access to this shell (from an initrd or your regular boot disk) you should be presented with a shell prompt. From there you can try to bring the system back up.

---

### Post by caryb on 2009-06-24
Mine boots to GSOD green screen of death with 2.6.30.x if I boot to recovery it boots to busybox, It does boot to the .27 kernel.


Cary

---

### Post by zika on 2009-06-24
> **caryb said:**
> Mine boots to GSOD green screen of death with 2.6.30.x if I boot to recovery it boots to busybox, It does boot to the .27 kernel.


CaryDid You refresh *busybox* from the **PPA** given above and afterwards done **update-initramfs -uk all** ... ? [http://ubuntuforums.org/showthread.php?p=7507578#post7507578](http://ubuntuforums.org/showthread.php?p=7507578#post7507578)

---

### Post by caryb on 2009-06-24
> **zika said:**
> Did You refresh *busybox* from the **PPA** given above and afterwards done **update-initramfs -uk all** ... ? [http://ubuntuforums.org/showthread.php?p=7507578#post7507578](http://ubuntuforums.org/showthread.php?p=7507578#post7507578)

zika thanks for the post, I followed it only as far as adding the ppa & following on from there as I was able to boot to a .29 kernel & I can confirm that it fixes the problem

Cheers Cary

---

### Post by xebian on 2009-06-24
Had the same problem last night.  Just exit from the busybox terminal and it will continue on.

---

### Post by MacUntu on 2009-06-24
"invalid number 0.1" is gone, "error inserting i915" is there - hooray! :D

---

