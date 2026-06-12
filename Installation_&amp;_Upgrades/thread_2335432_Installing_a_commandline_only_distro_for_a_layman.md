---
title: "Installing a commandline only distro for a layman"
date: 2016-08-28
forum: Installation &amp; Upgrades
---

### Post by ChancellorTaco on 2016-08-28
Hello community, working in the tech department of my school district, provides me with a rather nice resource: I have access to the entire outflow of technology from the whole school district. This presents the idea from time to time "what if I put linux on these?" However, many of them are not only old as dirt, being bought by the district(secondhand...at best) were pretty poor quality across the board to begin. So what I'm looking for, and have found in much more words than I really know at this point in time, is a way to instal the command line interface, but not a gui that can potentially prove too taxing for the computers I'm working with. From what I've seen, is that you can just get a disk for debian and just skip clicking the guis to install, but I'm not 100% certain I understood correctly. Presently I have two usbs with ubuntu 12 and 15 respectively, but I think I got rid of the optical disk I had debian on. If you could point me in the right dffection so that I might carry on wiht my pursuit of s&g. Thank you much.

---

### Post by TheFu on 2016-08-28
15.xx support ended.
12.04 and 12.10 support ends in a few months.
14.04 Server and 16.04 server would be options.  Avoid any odd-year releases - these get only 9 months of support from the release date. Generally, not worth the time. [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life) explains. Be sure to scroll down and check out the different parts of what is and isn't supported as time goes forward.

You'll want PAE-compatible hardware to run Ubuntu.  There are ways to install non-PAE CPUs, but ... that is probably not worth the effort for just a few systems.

OTOH, most of these old systems are crap and a $100 new box would have 5x the performance and none of the hassles.

I would start by making a HW inventory to know what we're working with.  CPU, RAM, Disk, USB, Networking, .... are each important to determining which systems should easily do it and which will be a challenge.  Here's a system info script: [http://blog.jdpfu.com/sysinfo](http://blog.jdpfu.com/sysinfo) which you'll probably want to modify.

---

### Post by grahammechanical on 2016-08-28
You might also want to consider the Ubuntu mini ISO image. That will install Linux and nothing else if you so choose. Or it will also add a range of desktop environments. Some of which are very minimalistic with nothing added other than a few system utilities and a terminal emulator.

In this way you can decide exactly what software to install. These machine may have small hard drives. The server edition comes complete with various server type applications. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It is also called a netboot because next to nothing is installed from the CD/USB stick. It is all done online.

[http://cdimages.ubuntu.com/netboot/](http://cdimages.ubuntu.com/netboot/)


Regards.

---

### Post by Bucky Ball on 2016-08-28
> **grahammechanical said:**
> You might also want to consider the Ubuntu mini ISO image.

+1. If you just want a CLI install, you've found it. :) It installs the Ubuntu kernel and that's it. The rest is up to you.

It's simple. Start the install, fill in the partitioning and other details, let it roll. It will get to a bit where you can choose a machine profile called 'tasksel'. Ignore it and just keep going. When finished, reboot and you'll be at a CLI. Log in and that's it. Have fun. :)

Install what you want with

```
sudo apt install <app_name>
```

For instance 'sudo apt install htop'. As mentioned, go for 16.04 LTS. Five years support until 2021. Good luck.

---

### Post by sudodus on 2016-08-29
The following link might help you select suitable computers to test with linux.

[Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

If you have computers below the limits in that link (typically Pentium 4 and 512 MB RAM for a graphical desktop environment), or Pentium III and 256 MB RAM for a text user interface, please specify their

- brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and we can suggest methods and/or ultra light linux distros, that might work.

---

