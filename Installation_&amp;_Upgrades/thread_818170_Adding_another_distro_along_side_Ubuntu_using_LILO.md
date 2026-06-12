---
title: "Adding another distro along side Ubuntu using LILO"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by Jabb3r on 2008-06-04
Not sure if it's already been asked, but I couldn't find exactly what I was lookin for so as things stand my Lilo boot menu is basically

Linux
LinuxOLD
WindowsXP

What I want is to be able to add another distro to my sys that I can play with and boot into from the lilo menu so it will be

Linux
LinuxOLD
(New Linux Distro Here)
WindowsXP


I know that as things stand I don't have a free partition available so I guess GParted will be my best bet for that, but thats about as much as I'm sure about.

So I wanted to know the steps I have to take to accomplish this.

Would I be right in thinking the following would work

* resize my / partition and create another XFS from the space freed up
* install the new distro without boot loader to the new partition e.g/dev/hda2 or whatever
* Edit /etc/lilo.conf in ubuntu and add a new entry pointing to the image of my new distro to boot e.g....

image=/vmlinuz
        label=(New Distro)
        read-only
        append="root=/dev/hda2  "
        initrd=/initrd.img

And that should be gravy?


I should note that I have a /home partition so could I use that for both distros save creating another?

Thanks

---

### Post by dstew on 2008-06-04
> And that should be gravy?Yes, that should be gravy. The only problem might be the image and initrd paths. I am not real sure about how Lilo reads paths, or if it searches for kernel images like grub can, but usually the kernel images and initrd files are in the /boot directory of an Ubuntu filesystem, and not in the root directory.

And, you should be able to use the same /home partition in the different systems. It is recommended that you use a different username in the two systems to avoid conflicts with config files.

---

### Post by Jabb3r on 2008-06-04
Oh thats great, I'll get to work on that then, I'll double check the lilo thing you mentioned I just based iit on what I saw in mine.

I'll use a diff username of course.

Thanks for the quick reply :)

---

