---
title: "New Linux User Needs Some Install Help"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by mayb on 2006-07-23
First of all, from what I've seen of the layout of UBUNTU I must say it looks quite nice. I'm sure there are many other great features, BUT I can't quite get to that point.

I downloaded the .iso and burned it, changed BIOS to boot from CD-ROM. It ran to UBUNTU from the CD. I then chose install, went through all that jazz and it spit the CD out when done. Cool! However, I went back to the BIOS changed it to boot from HD again and then it gave me a GRUB error 17. I did some searching around on here and couldn't quite find the exact answer. So I went in and tried reinstalling, same thing.

So let me outline what I'm doing.
I have 2 - 20 GB HDs on IDE1. The master is my windows boot volume. I was attempting to set-up the slave as my linux boot volume. 

Also I have a SATA 100 GB HD, that I use for storage etc. 

So in the set-up I would click to install ubuntu to my slave HD and had it erase everything that was previously on it. Should I be doing something different?

Also, the last time I installed I chose the last option when I booted from the CD again, something like, boot from first disk or something, and I had the choice of ubuntu 6.06, ubuntu 6.06 (recovery mode), Windows XP Pro, and a couple other things I don't remember. I chose ubuntu 6.06 and it loaded up. Now once I was in there this Synaptic thing loaded, no idea what to do with that. But once in there I couldn't really do much, hard to view screen, it was in 640x480 on my 19" LCD so hard to read. But anyways I had no wireless card support or any of that so perhaps I need to do more reading. But first I'd like to get it booting happily.

Sorry for the long first post, but I'm looking forward to using this OS. I know OS's whether it is windows or whatever are prone to difficulty, so it's no worry!

Thanks to anyone who can offer some assistance! :KS

---

### Post by Sef on 2006-07-23
> However, I went back to the BIOS changed it to boot from HD again and then it gave me a GRUB error 17.

From the Grub Manual:  

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

So what file system type are you using?

[GRUB Manual]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html")

---

### Post by mayb on 2006-07-24
> **Sef said:**
> From the Grub Manual:  

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

So what file system type are you using?

[GRUB Manual]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html")

I honestly am not sure what file system type. I just selected the drive from the UBUNTU installation and told it to erase it. I believe the rest of my drives, Primary Master, and the SATA are all NTFS.

---

### Post by John.Michael.Kane on 2006-07-24
You may want to try re-installing with-out the sata drive's connected.there has been issues when sata,and ide drives are mixed.

---

### Post by mayb on 2006-07-24
So disconnect my SATA and then once UBUNTU is installed re attach them?

---

### Post by mayb on 2006-07-24
well problem solved. Did some moving around on my main HD and installed UBUNTU onto it and now things are working smoothly.

Now just getting all the hardware working right, ah but yes that is the fun part! Thanks all!

---

