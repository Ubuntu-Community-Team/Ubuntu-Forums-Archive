---
title: "Tailored OS+ on a dvd or thumb dirve"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by dr01tspc on 2013-02-15
I would like to run Ubuntu, with my added programs and files, on my MacBook Pro (MBP) - from a thumb drive or dvd.

That is, in place of the downloadable Ubuntu demo/installer that can be downloaded from Ubuntu, I would like to create a usb source that can use the programs I have added to my installation (several key ones, including my own).

I currently run Ubuntu 12.10 on VMFusion 5, on my MBP.

I have a parallel program that I would like to run on all 4 cores: I am limited to 2 of the 4, as might be expected. 

So, I would like to run Ubuntu directly on the MBP, so I might access the 4 cores.

My proposed solution is to create an image on a usb device that will contain the items I need. 
If this is possible, I can also carry it to computers to which I have access, but do not want to load my software onto.

Possible?

Regards,
Tim

---

### Post by MAFoElffen on 2013-02-15
Yes, possible.

Possible ways are to either install live Image as persistant or full blown treating your USB storage device as a bootable USB drive (installing as a drive). If you are portably transporting between different machines, you just need to be careful about installing hardware specific drivers that might make it hardware dependant.

On DVD, I've never tried. USB storage is so inexpensive now. DVD+/- is write/read, but written linear = permanent. DVD read/write/rewrite is changable, but I've never had much luck playing with it as bootable ever-changing storage... Besides the read/write/rewrite DVD disks cost more. Because of that, I've even changed burning ISO's from regular CD/DVD to USB thumb drives. So like I said before, for that I use USB thumb drives.

Does that answer the question or do you need direction to instructions how? If needed, there's GB's of tutorials on either USB direction if you search for it.

---

### Post by dr01tspc on 2013-02-15
Aside: I am new to Ubuntu Forums. I am posting this as a "New Reply".

MAFoEllfen: Thanks for your response.  Unfortunately, I don't undertand the contents of your 
first paragraph. I do plan on using a thumb drive in general, but that may not always be 
feasible.

Just to make sure: I intend to run Mountain Lion on my MBP most of the time. I also want to 
be able walk into a potential customer's site and demo my software. If that is consistent with 
your suggestion, then I don't understand what "install" means. 

BTW: I probably don't understand what to look for in terms of locating the useful information 
that you (no doubt correctly) say is on the web, but I will give it a go.  

BUT - a slightly different view. If I boot my MBP using ubuntu live (as downloaded from Ubuntu 
on to a thumb drive), will I have access to (and do you see danger in accessing) the part of 
the MBP's hard disk that has been set aside for Ubuntu 12.10?

If that sort of thing will work, then perhaps a general solution might lay in using the ubuntu 
live drive to boot, and having a second drive containing other needed software (gfortran, 
paraview, etc.) as well as my codes?

I can see becoming very confused about what commands are being run - say in a bash script - 
but I assume that is established at boot to be the live drive?

Regards,
Tim

---

### Post by C.S.Cameron on 2013-02-16
You can install Ubuntu to a flash drive the same as to an internal drive.

You can then install any of the programs you wish from the repositories.

---

### Post by dr01tspc on 2013-02-16
Thank you C.S.Cameron:

I actually do what you suggest, in the sense of carrying hard-drives between computers at 
different sites at which I work.

So, I guess that may be the best solution for demos. (Though I did read up on customizing 
liveCD, persistent images, etc.) 

But I like maintaining one instance of my software/environment, and I develop on my MBP.

My real goal:
I have a parallel program. I (apparently) can only set aside 2 of the 4 MBP core for VMFusions. 
i would like to boot straight to linux to have access to all 4 cores.

I also would rather not maintain several instances of my code, nor supporting software (paraview, 
etc.).

So, do you think can I boot my MBP from a liveCD, then safely use the linux partition on the MBP?
I could just try it, but I worry about serious damage to my system software.

OR perhaps I can make an image of the Ubuntu partition that will be bootable by my MBP? That 
would solve my client demo, core access, and maintenance concerns.

Thanks,
Tim

---

### Post by gordintoronto on 2013-02-16
> **dr01tspc said:**
> ....But I like maintaining one instance of my software/environment, and I develop on my MBP.



In that case, you should investigate "portable apps."

[http://portablelinuxapps.org/](http://portablelinuxapps.org/)

---

