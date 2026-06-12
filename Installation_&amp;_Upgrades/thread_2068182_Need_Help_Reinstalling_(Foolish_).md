---
title: "Need Help Reinstalling (Foolish ???)"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by gopukrishnantec on 2012-10-08
Hi ,

I have installed ubuntu 12.04 before 1 month and made it suitable for me with a bunch of softwares i need. Since i am new here i did something wrong and my unity got some problem with 3D. Compiz is taking 100% cpu. So I've decided to reinstall Ubuntu.
I already spent hours before to install the softwares in current OS. So if i took a backup of all files from /usr/bin folder for the new linux installation. Will all the softwares work if i replaced the /usr/bin folder in new installation with the old backup as Linux is having special filesystem heirarchy ? (No registery i think ) Should be a foolish question!!!! Please help anyway!!!:lolflag:

---

### Post by jerrrys on 2012-10-08
There are many ways to backup your installed packages

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+install+software+packages&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+install+software+packages&as_qdr=all&sa=Google+Search&lang=en)

Also compiz can be reset
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=reset+compiz+lucid+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=reset+compiz+lucid+12.04&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by TheFu on 2012-10-08
Re-installing will usually not make things better for issues like this.  When it comes to backing up and restoring systems, there are 3 types of files.
* programs
* settings
* data

If you've always used the package manager to install programs, you want to use the package manager to track which programs are installed.  **dpkg --get-selections** will list all the installed packages. If you save that to a file, then you can use that file to automatically reinstall all the packages using **dpkg --set-selections** later.

Settings are either system or personal.  System settings are almost always stored under /etc or /usr/local, so those areas are probably what you want to backup.

Personal settings and data are almost always stored under your HOME directory, so back that up.

When you perform backups, be certain that you also backup the file permissions, owner and groups too. That means you need to use a backup program that does it and almost always that means you do not write backups to NTFS or x/v/FAT storage. You want Linux file system storage.

Compiz taking 100% of CPU can often be traced to GPU drivers.  Did you recently update your GPU drivers?  I'd try reinstalling and reconfiguring those first.  Which GPU drivers are you using?

---

### Post by gopukrishnantec on 2012-10-10
Thanks for your help.
I haven't changed anything other than an automatic update.
One more thing- Is there any software to backup the entire OS state so that if anything happened wrong, i can just insert the disk and restore the entire system to the old state even without network connectivity.

---

### Post by jerrrys on 2012-10-10
> **gopukrishnantec said:**
> Is there any software to backup the entire OS state so that if anything happened wrong, i can just insert the disk and restore the entire system to the old state even without network connectivity.

[Clonezilla]("http://clonezilla.org/") is one way.  There are several to choose from.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=system+backup&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=system+backup&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by TheFu on 2012-10-10
> **gopukrishnantec said:**
> One more thing- Is there any software to backup the entire OS state so that if anything happened wrong, i can just insert the disk and restore the entire system to the old state even without network connectivity.

Any backup program should do that, after all, that's the point.

There are 2 types of backup tools - image-based and file-based.  Image-based tools use much more storage since they don't usually support differential backups.  Clonezilla and PartImage are examples.  I think PartImage is easier to use and KNOW that if it understands the underlying file system, then it will highly compress the image backup.  It works for Linux and Windows.

For day to day backups, which can also completely restore a system, there are many file-based solutions for linux, perhaps 100.

If you want a 100% image of a HDD, then you want to use something like **dd**.  I've used this many times when I needed an exact, bit-for-bit copy of an entire OS before a major update.  Because it is bit-for-bit, the backup will take a very long time and you need to be in either single-user mode or boot of different storage, like a liveCD to avoid open file corruption of an active, running OS.  The source and target HDDs should be identical too.  There are ways to make them "close enough", but at this stage, you probably don't have the understanding.

You should use **PartImage** [http://partimage.org/Main_Page](http://partimage.org/Main_Page) if you insist on a bit-for-bit backup, that is a little smarter than **dd**.

---

