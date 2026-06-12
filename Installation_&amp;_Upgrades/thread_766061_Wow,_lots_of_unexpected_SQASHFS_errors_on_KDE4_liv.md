---
title: "Wow, lots of unexpected SQASHFS errors on KDE4 live-cd boot"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by meanburrito920 on 2008-04-25
last month I tried out the Kubuntu hardy beta and it booted great, everything worked. Today I just downloaded the final ISO and checked it out. It displayed the boot splash with the bouncing bar (It didnt get to the progress bar) for about 5 min and then started shooting out error messages like a machine gun, it was ridiculous. It was giving me a SQAUSHFS error for every single sector on the disk, so I shut it off after about 30 secs because the text was scrolling so fast it was near impossible to read. Needless to say, I immediately did a md5sum of my disk and it all checked out. My question is- what the heck happened between the beta and now that gave the live-cd a heart attack? and how do I fix the SQUASHFS errors (I am trying the safe-boot as I type). Any suggestions or ideas? Thanks in advance.

EDIT: Decided to try a error-check on the disk first.
EDIT2: error check came back clean, attempting safe boot.

---

### Post by Nidding on 2008-04-25
I get the exact same on my Ubuntu install. Though my DVD checks out as well, I'm trying to burn a new CD instead to see if that has anything to do with it. Any suggestions would be appreciated indeed, though.

---

### Post by meanburrito920 on 2008-04-25
Sorry I havent responded earlier, my internet went down for a while. I tried a reboot and started in normal mode after the disk check and everything worked. I'm suspecting that I may have gotten dirt on the disk or something, because I hadn't changed anything since I tried the first time besides take out the CD and clean it off. Hopefully this becomes a non-issue in future releases.

---

### Post by Nidding on 2008-04-26
After a few tries it seems like my first DVD is finally working. Appearently the problems were just due to some disk reading problems, I guess.

---

### Post by Nidding on 2008-04-28
> **Nidding said:**
> After a few tries it seems like my first DVD is finally working. Appearently the problems were just due to some disk reading problems, I guess.

Seems like I was sadly mistaken. I only got a single step furter in the process, before I got a new message telling me the disk was faulty. This is the case for 2 DVD's, both burned on lowest speed and on premium medias.

---

### Post by Jim Danner on 2008-04-28
Same problem here (or a variant of it). Ubuntu live CD burned from ubuntu-8.04-desktop-i386.iso; checked the MD5-sum of the CD and it comes out correct. I can boot from the CD on one computer, but on another one it gets into the SQUASHFS errors "reading block 0x7a397" and "reading block 1e8da709" (and this is the computer on which the MD5 sum was checked, so it is able to read this CD).

The difference with the cases above is that a disk check reports 3 errors on the disk (which can't be there, as proven by the correct MD5 sum and the correct boot on the other computer).

This computer doesn't have a problem with the Ubuntu 7.04 and 7.10 live CDs. A Knoppix CD has a problem, and I have to start that with "nodma" as an additional option. Tried that here (with F6), but it didn't make a difference.

See also [CDCheck Fails but MD5 is Correct! 8.04]("http://ubuntuforums.org/showthread.php?t=767183").

---

### Post by svasanth on 2008-04-29
I'm getting the squashfs error while trying to install the kubuntu dvd as well as kde remix. Refer the bug at [https://bugs.launchpad.net/bugs/214237](https://bugs.launchpad.net/bugs/214237)

---

### Post by dstew on 2008-04-29
> The difference with the cases above is that a disk check reports 3 errors on the disk (which can't be there, as proven by the correct MD5 sum and the correct boot on the other computer).No, the errors can be there. Different CD-ROM drives have different optical systems, and there is variation in how well they can "see". If your CD has some bits that are borderline-visible, they might be read fine in one drive, but not in another.

---

### Post by Jim Danner on 2008-04-29
> **dstew said:**
> No, the errors can be there. Different CD-ROM drives have different optical systems, and there is variation in how well they can "see". If your CD has some bits that are borderline-visible, they might be read fine in one drive, but not in another.But what if the same drive that gets read errors also gave the correct MD5 sum? Also, it happens in exactly the same way on three different CDs I have burned from the iso. Any thoughts about this?

---

### Post by dstew on 2008-04-29
I don't know about checking the MD5 sum of the CD. Is it just like checking the sum on the .iso file? I thought that once the CD was burned it was not a single file like the .iso, and I didn't know you could do a checksum on it, but maybe I am wrong. Is the Check CD integrity test different than the checksum test? I thought it was a different test from the MD5 sum.

When you do an md5 sum, maybe the disk reader is doing a data dump operation, but the CD integrity check is using the filesystem, so the reader has to jump, and maybe there is an issue there. That might explain why there is a difference. Anyway, I have never heard of anybody being able to install a system from a CD that failed the integrity test, but I might be wrong.

---

### Post by Jim Danner on 2008-04-29
> **dstew said:**
> I don't know about checking the MD5 sum of the CD. Is it just like checking the sum on the .iso file? I thought that once the CD was burned it was not a single file like the .iso, and I didn't know you could do a checksum on it, but maybe I am wrong. Is the Check CD integrity test different than the checksum test? I thought it was a different test from the MD5 sum.

When you do an md5 sum, maybe the disk reader is doing a data dump operation, but the CD integrity check is using the filesystem, so the reader has to jump, and maybe there is an issue there. That might explain why there is a difference.Hey you must be right, it has to be something like this. I burned the same iso to a CD with a different drive, and this time the install worked.

By the way, you can check the MD5 sum of a CD in Linux by finding the device in /dev and simply getting the checksum:
```
md5sum /dev/scd0
```
The path of the CD drive (/dev/scd0 in this case) can be found in /etc/fstab.

Thanks for your help.

---

