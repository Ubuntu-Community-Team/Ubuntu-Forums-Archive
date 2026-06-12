---
title: "Installing /home on 2nd hd (eee 901)"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by JacquiOh on 2008-11-04
Hi

I'm trying to install Intrepid on our new eee 901. 

It has 2 HDs, one is 4GB and the other is 16GB.

I want it to boot from the 4GB drive but have the /home on the 16GB drive.

After I go into manual partition during installation, what do I need to do?

I'm a bit of a newbie and just want to get this right!

Thanks

Jacqui

---

### Post by taurus on 2008-11-04
Just tell the installer to _mount_ the 4GB as / and the 16GB as /home.  Don't forget to format both as ext3 filesystem.  I assume you have a swap partition for your machine?

---

### Post by Coreigh on 2008-11-04
You would only want to do this if both disks are _always_ in the netbook.

You can define this in the installation process by choosing manual or assisted partitioning at the partitioning section. And then specifying the which-ever /dev/<disk> is the 16 that it should be mounted as /home.

If the install is done you can modify the fstab (/etc/fstab) to mount the /dev/<disk> as /home.

Finally you could mount the 16 on an other mount point and add an alias or shortcut from the /home/<username> folder. This of course is not a true move of the /home and would not relocate all the user files.

anything I enclosed in <> is a variable that you will have to determine for your system.

---

### Post by JacquiOh on 2008-11-04
Assumptions are dangerous!

I've read elsewhere that swap can damage SSD and that they're not necessary?

Thanks so much for your advice, that's exactly what I was looking for. Is the swap an issue?

---

### Post by Coreigh on 2008-11-04
After doing a little googling about swap and SSD the only thing I found negative were people who had swap on removable SSD. If the used the SSD between a netbook and a camera or other device the lost files that were left on the SSD. This led me to think that they meant swapping the SSD in and out, not using a swap file (memory cache).

In fact some posts indicated that solid state memory excels at the type of random read/write that is needed for a swap file.

Most said that the "sweet-spot" is lots of system memory (RAM, 2GB or more) and a small swap space (256MB - 1GB) because you will rarely need it but some applications just expect it to be there and slow down a lot if they cant find it.

For the record my google search was [SSD swap file]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&hs=DAU&q=SSD+swap+file&btnG=Search")

---

