---
title: "Dual Boot Question"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by sparker781 on 2011-06-30
Noob here.  I want to dual boot windows 7 and ubuntu.  My only main question is whether or not there is a minimum amount of hard drive space i need for the install to make it run as smooth as possible.

Thanks

---

### Post by Herman on 2011-06-30
As a minimum you probably need at least 5GB if you think you will hate Ubuntu and you are not planning on using it for much and you're not going to install much additional software. The file system should have at least 20% free space after you install  everything for breathing room in order to reduce fragmentation.
A Ubuntu installation can grow to say 10GB if you install a lot of free software and maybe even a second desktop or two.
The fun in Ubuntu is in installing all the nice extras, so you will need to allow room for that or you probably won't be able to enjoy the best Ubuntu experience.
With that in mind, at least 12 GB would be better.

I have Ubuntu running in a 4GB SSD in my EeePC, but I have a 16GB SD card for the /home partition. It requires special effort to keep the size of my / down to allow breathing room for the file system.

It is possible to achieve a limited amount of Windows shrinking using Windows own tools, except you need to defrag for hours first and even then it can only shrink Windows to about half way. In spite of its limitations, many here do recommend using Windows own resizing tool to shrink Windows.

If you think you'll like Ubuntu, you may want to shrink Windows more than half way.
I don't mind what tool you use, but if you use GParted or the partition editor in the Ubuntu installer you'll get the job done a lot faster, (no need to defrag first), and shrink Windows as much as you want.
I recommend running a file system check, (chkdsk /R) first though, and an automatic post-resize file system check will be induced anyway.

Most of the friends I install for ask for Windows to be deleted, or they don't care about Windows and just want it resized as small as possible as they never plan on actually using it and just want it out of the way, but don't mind it remaining taking up a wee bit of hard drive space.

---

### Post by jerrrys on 2011-06-30
5 is ok, 10 is my minimum choice

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

