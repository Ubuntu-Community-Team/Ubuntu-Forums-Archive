---
title: "Help needed recovering files from Ghost image"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by narrowband on 2006-07-13
I need to recover files from a Norton Ghost image created after the installation of Ubuntu died due to a corrupt file system.

For some reason I can't view the files contained in the ghost image using Ghost Explorer in Windows.  Yes I know the file system was corrupt but I was hoping that it was just Ubuntu that was lost.  I expect ghost can't read the contents of an ext3 file system so all may not be lost.

Would I have to restore the image to another drive (which I don't have so would need to get one) and mount it using another install of Ubuntu? Or is there a better way to restore the files that doesn't require a spare hard drive? (The hard drive I do have is only 10GB and doesn’t have enough room to resize and create partitions to perform this type of recovery.)

Please note that I did try to recover files before making the Ghost Image and over writing the broken installation with another. I tried using an Ubuntu Live CD but couldn't get it to mount the hard drive as it kept saying something like invalid file system.

---

### Post by x64Jimbo on 2006-07-13
I'm not sure if it would work, but you could try using g4l which is "Ghost 4 Linux"
[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

---

### Post by John.Michael.Kane on 2006-07-13
You can try one of these.
[**[COLOR="Red"]SystemRescueCd[/COLOR]**]("http://www.sysresccd.org/Main_Page")

[**[COLOR="Blue"]KNOPPIX[/COLOR]**]("http://www.knoppix.org/")

---

### Post by narrowband on 2006-07-14
All of these methods would require me to restore the partition to a drive first. I don't have a drive to use.

PS KNOPPIX is a pile is beeeeep I tried using it a while ago.

G4L sounds good but how in hell is it different to normal ghost as normal ghost is bootable and not OS specific.

---

### Post by ezsit on 2006-07-14
> For some reason I can't view the files contained in the ghost image using Ghost Explorer in Windows. Yes I know the file system was corrupt but I was hoping that it was just Ubuntu that was lost. I expect ghost can't read the contents of an ext3 file system so all may not be lost.

There could be two possible reasons why this is so. First, is your image file compressed? if so, Ghost Explorer will not read the contents of the file, it can only restore the ghost image. I've used Ghost for years and I never compress the image file for this very reason. 

Second, I forget whether Ghost really knows about linux filesystems and can read the filesystem or whether Ghost simply does a sector level image of linux filesystem. If Ghost does a sector level image, then Ghost explorer would not be able to read a linux filesystem and extract individual files.

---

### Post by x64Jimbo on 2006-07-17
Norton is notoriously Microsoft-specific. I would not expet their products to recognize Linux filesystems, and would actually be VERY surprised if they did.

---

### Post by narrowband on 2006-07-20
OK I have restored the disk from the Ghost image but I am back to where I started.  I now have an un-mountable partition that Linux (Ubuntu 6.06) thinks is not formatted.  This is what I had before I made that backup so I doubt Ghost has destroyed the data so lets assume it is as if i had never made the image.

Is there anyway at all that I can recover the data? Any Linux (ext3) data recovery tools?

---

