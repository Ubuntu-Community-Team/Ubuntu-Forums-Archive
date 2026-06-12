---
title: "lubuntu live CD problem?"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by jfloydb on 2011-10-24
I'm trying to run a lubuntu live CD on a Window XP machine without installing. The program loads, asks me which language to use (I chose english), and, instead of a GUI, I get a command prompt on a black screen. ubuntu@ubuntu:~$. Is this what is to be expected? Because I don't know what to do with it. Any ideas? Thanks.

---

### Post by tartalo on 2011-10-24
No, a graphical environment is what you should expect. 

First test if the iso you downloaded has the right md5 hash: 
[http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/MD5SUMS](http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/MD5SUMS)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If there are no defects in the image, Lubuntu might have trouble with your hardware (is it very old?) in the first screen when you boot the Live you can press F6 and try some of the options there (disabling ACPI used to work for me in a very old laptop)

---

### Post by Megaptera on 2011-10-24
When this happend to me I selected "install" instead of "try" at boot. Then when the install menu appeared I selected "quit" and then confirmed "quit" at next pop-up.
this route then launched the "try" option and all worked on the live CD.
So that's what's worked for me with the past 3 or 4 Lubuntu releases.

---

### Post by jfloydb on 2011-10-24
Thanks guys. I'm writing now from the live CD. I tried megaptera's trick and it worked. I would have never thought that...

---

### Post by Megaptera on 2011-10-25
> **jfloydb said:**
> Thanks guys. I'm writing now from the live CD. I tried megaptera's trick and it worked. I would have never thought that...

I'm pleased it worked for you & I hope it helps others too. I've no idea why I first tried it or why it works but never mind!! :D

---

### Post by amjjawad on 2011-10-26
> **jfloydb said:**
> I'm trying to run a lubuntu live CD on a Window XP machine without installing. The program loads, asks me which language to use (I chose english), and, instead of a GUI, I get a command prompt on a black screen. ubuntu@ubuntu:~$. Is this what is to be expected? Because I don't know what to do with it. Any ideas? Thanks.

Hi,

What release of Lubuntu are you using? 11.10?
I have tested 11.10 while it was Beta2 and after the final release and I got this problem with one of my PCs while it worked on the other one. I came to know that the CD-Drive was actually falling and that explains why it didn't work on one machine while it worked on the other.

I'm in Lubuntu Team and very interested to know whether users are still facing the same issue with the Live-CD.

The problem also disappears while booting from Live-USB by the way.

I think I'll update the Wiki Pages and add this as a work-around.

---

### Post by Megaptera on 2011-10-26
> **amjjawad said:**
> 
I'm in Lubuntu Team and very interested to know whether users are still facing the same issue with the Live-CD. 

Have you seen my work-around at #3 above? Not sure if that's what yourreferring to?

---

### Post by amjjawad on 2011-10-26
> **Megaptera said:**
> Have you seen my work-around at #3 above? Not sure if that's what yourreferring to?

I've been advising the same to users since I first discovered that and put it right but this is not what I was referring to.
I want to know whether users in general are still having that issue and still have to do some work-around to get it to work.

I tested 11.10 Live-CD on my two machines. It worked on one but didn't on the other and had to do that work-around that I used to do with previous releases.
However, on both PCs, I didn't have that issue when I used Live-USB.

---

### Post by mörgæs on 2011-10-26
Always read the release notes :-)

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot)

---

### Post by Billxyzzy on 2011-10-26
I have been using the latest release (oneiric
amd64) of lubuntu.  My problem is that when trying
the iso (both on a cd rom or direct dd to a usb
hard disk)  I get the following error.
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: no such device
can not mount /dev/loop0 (/cdrom/casper/filesystem
squashfs) on //filesystem.squashfs

I have tried this on more than one computer and always get the same error. I have made more than one
download and the results are always the same.

BTW cannot find a MD5sum file for this download
However each download has the same size and
seems to be a complete duplicate.
By trying Try Lubuntu,  Install Lubuntu or Test
disk for defects I always get the same error.
Three days lost now

---

### Post by amjjawad on 2011-10-26
> **mörgæs said:**
> Always read the release notes :-)

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/OneiricOcelot)

OMG, my memory is so rusty ... I remember I updated something but couldn't remember what was it so THANK YOU for reminding me of what I've done :)
I do need to sleep more than 3 hours and eat more than 1 meal :P

---

### Post by mörgæs on 2011-10-26
> **Billxyzzy said:**
> I have been using the latest release (oneiric
amd64) of lubuntu.  My problem is that when trying
the iso (both on a cd rom or direct dd to a usb
hard disk)  I get the following error.
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: no such device
can not mount /dev/loop0 (/cdrom/casper/filesystem
squashfs) on //filesystem.squashfs

I have tried this on more than one computer and always get the same error. I have made more than one
download and the results are always the same.

BTW cannot find a MD5sum file for this download
However each download has the same size and
seems to be a complete duplicate.
By trying Try Lubuntu,  Install Lubuntu or Test
disk for defects I always get the same error.
Three days lost now


What happens if you create a USB stick with Unetbootin and boot from it?

---

### Post by tacantara on 2012-02-27
I tried the workaround in post #3, and it (Lubuntu 11.10 Onieric.) worked just fine on my girlfriend's Sony Vaio desktop, with a Pentium 4 CPU and 1GB of memory.  The live session ran well with no hardware conflicts. Just finished the install, and getting updates now. I guess it wouldn't be *buntu without a few idiosyncrasies LOL. 

One more older model desktop to refurb with Lubuntu - looking forward to it!

---

