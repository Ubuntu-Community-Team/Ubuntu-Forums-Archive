---
title: "Ubantu 6.06 -vs- Fedora core 5"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by OUTRIDER on 2006-06-16
I am looking to completely dump MS as an OS on my Dell Inspiron 9100 LapTop. I have been running Fedora core 5 for the last month
and it seems to be a cool Linux OS. I recently read some technical reviews of Ubuntu and my interest was peaked in a big way. How do the two Linux OS' (Fedora & Ubuntu) compare and where can I get access to a detailed comparison between both?
Here are a few questions I have before adding Ubuntu 6.06:

1.- Why is the Ubuntu 6.06 install so small as compared to Fedora core 5? The Ubuntu full install is all on 1 CD while Fedora is on multiple CDs or 1 DVD. Is there an Ubuntu 6.06 DVD ISO?

2.- Can I boot 3 OS' with GRUB? If so how do I add Ubuntu to my selections in my GRUB boot loader (and make it work)? I am currently running XP Pro and Fedora core 5. GRUB has been written to my MBR (Master Boot Record) and is working fine with XP Pro. 

Any ideas or help from the Pros out there will be greatly appreciated. :confused:

---

### Post by 23meg on 2006-06-16
> 1.- Why is the Ubantu 6.06 install so small as compared to Fedora core 5? The Ubantu full install is all on 1 CD while Fedora is on multiple CDs or 1 DVD. Is there an Ubantu 6.06 DVD ISO?Ubuntu has a "one app per task" principle and ships its preferred apps on a single CD, letting you install everything else from the repositories if you need, whereas many other distros ship just about everything on separate CDs and let you choose packages at install time. In a default Ubuntu install you don't select packages.

There's a DVD available but AFAIK it doesn't include the Universe and Multiverse components. For more info on components, see [this page]("http://www.ubuntu.com/ubuntu/components").

---

### Post by timozilla on 2006-06-16
Trust me. Stick to Fedora Core 5. You will be glad you did.

---

### Post by x64Jimbo on 2006-06-16
[QUOTE=timozilla]Trust me. Stick to Fedora Core 5. You will be glad you did.[/QUOTE]
What a negative thing to say. I personally have used both Fedora and Ubuntu, and I have to say that I am much happier with Ubuntu than I ever was with Fedora. I really love the package management system that debian-based linuxes like Ubuntu use, and the 64 bit support in Ubuntu is pretty incredible, which means that it will probably be very favored in the near future when 64 bit processors become more common.

---

### Post by glotz on 2006-06-16
2. I think there's nothing you need to do besides just install. I believe GRUB will automagically pick up all the 3 OSes. Haven't tested it myself though.

---

### Post by x64Jimbo on 2006-06-16
[QUOTE=glotz]2. I think there's nothing you need to do besides just install. I believe GRUB will automagically pick up all the 3 OSes. Haven't tested it myself though.[/QUOTE]
On initial install, Ubuntu will auto-detect your existing operating systems and write your menu.lst accordingly. Unfortunately, this does not happen when you do grub-update, so I suggest you back up your initial menu.lst so you don't lose those entries. If you ever need to grub-update, you can just cp+pst the entries list over from your backup version into your real version.

---

### Post by glotz on 2006-06-16
Oh, I see. Thanks for the heads up. I don't think there will be any issues besides this little handiwork...

---

### Post by OUTRIDER on 2006-06-17
Thanks All... I appreciate the insight. Please keep it coming, the more Info, the better...

---

### Post by xyzzy_bill on 2006-06-24
[QUOTE=OUTRIDER]1.- Why is the Ubuntu 6.06 install so small as compared to Fedora core 5? The Ubuntu full install is all on 1 CD while Fedora is on multiple CDs or 1 DVD. Is there an Ubuntu 6.06 DVD ISO?[/QUOTE]

The Ubuntu team very wisely decided to focus on a reduced set of software, and to really polish it.  This is why they are able to make it so reliable and easy to use.  This is what makes it a great end-user desktop system.

To compete with bigger distributions like Fedora Core, Ubuntu relies heavily on the open-source community.  They seamlessly integrate many thousands of downloadable packages into the Synaptic Package Manager.  I personally find that packages I want and need are more often available for Ubuntu than Fedora.

The initial CD is small, and quick to install, but all those other packages are just a click away.  One of my favorites, Nvu (a GREAT web site editor) never did work on my Fedora Core 4 system, after many hours of trying.  Same goes for WengoPhone.  A real bear of an installation for Fedora/RedHat Enterprise (gschem and friends - gEDA) has caused me many days worth of support every year.  On Ubuntu, it's literally select and go.  It's almost easier to convert the user to Ubuntu!  Not only that, but downloads and upgrades are rocket-fast.  Fedora always seemed to want to download at 20Kbytes/sec instead of 400Kbytes/sec.

I've been so impressed, I dumped Fedora from my workstation and server machines, and now only run Ubuntu.

---

### Post by OUTRIDER on 2006-06-24
Bill, Thanks for the great input. It does help...

---

### Post by zxee on 2006-06-24
I used FC3 thru FC5. I personally didn't like FC5 although 3 was very well done IMO.
There are lots of arguments about package management on both forums. I do think that debian's/ubuntu's apt-get is faster and easier to work with. Fedora has a brand new package manager, pirut, that I haven't tried. Fedora is the front runner for red hat while ubuntu borrows from debian but it's also more independent of the influence of a bigger organization (red hat) that uses fedora like a lab rat.  
I have installed and multibooted a lot of distros-at one time over a dozen so yes grub will let you add as many entries as you want to /boot/grub/menu.lst. I don't know what the maximum amount of entries is. For me the easiest way to set up multiboot is to have the primary grub on the mbr (I don't have a windows install) then with each successive distro I just have the installer put grub on the boot partition. You can then use the grub commands rootnoverify (hdX,X)  chainloader +1 to boot your 2nd, & 3rd distro.

---

