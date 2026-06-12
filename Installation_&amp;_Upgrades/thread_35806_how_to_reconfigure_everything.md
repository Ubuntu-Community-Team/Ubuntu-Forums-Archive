---
title: "how to reconfigure everything"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by nortoncillo on 2005-05-20
finally i changed my motherboard and cpu, so now what kind of 
dpkg should i run to reconfigure everything ?

---

### Post by tozzer on 2005-05-20
I'm sure people will correct me here, but I don't think that you need to change anything. Unless you had a custom kernel, or your new motherboard isn't supported by the stock kernel then it should all still work. As long as all your hardware is still being recognised, I expect you are fine.


Christopher

---

### Post by Zelut on 2005-05-20
Agreed.  Unless you have a custom kernel put together (which I haven't read much about at all under ubuntu) then you should be just fine.  Plus, compiling a new kernel takes forever and I never bother unless I absolutely need to.

---

### Post by nortoncillo on 2005-05-20
... i changed my motherboard and cpu, from an HP celeron with integrated video, to a foxcon MB and a P3 cpu with nvidia video card,  i really think that i should reconfigure something...

besides, when i turned it on, i get only console as root..

and as far as i know.. during the installation the linux Kernel compiles himself in acordance with the machine type/spec's.....  

im 90% shure that i must reconfigure something....

but what ... and deep important.... how

---

### Post by SickTwist on 2005-05-20
The kernel is not compiled during installation (although I've often thought that it would be an interesting idea) but you can install a custom kernel for your processor.  For a Pentium III it is this simple command:

sudo apt-get install linux-686

You also need to change the X.org video driver for your nvidia card.  If you want to use the non-free (as in freedom) driver from nvidia, directions are on the [Ubuntu Guide](http://ubuntuguide.org/#installnvidiadriver).

Hope you enjoy your new hardware!

---

### Post by grakhul on 2005-05-21
*sick twist*> The kernel is not compiled during installation (although I've often thought that it would be an interesting idea) but you can install a custom kernel for your processor. For a Pentium III it is this simple command:

sudo apt-get install linux-686

You also need to change the X.org video driver for your nvidia card. If you want to use the non-free (as in freedom) driver from nvidia, directions are on the Ubuntu Guide.

Hope you enjoy your new hardware!

I take it that I have a 386 kernel because i ran uname and that's what it told me.  I have an Inten Celeron Processor rated at 2.2 GHz.  I was wondering if I should do the command performed above to install an upgraded kernel.  
1.  How long does the install take?
2.  Does it leave any residual log files, temp files or garbage behind?
3.  What are the benefits of using linux-686 over linux-386?
4.  Will I gain application speed?  Will limited amount of memory be used more efficiently?
5.  WIll I have to reinstall the applications I already have installed?

---

### Post by SickTwist on 2005-05-21
[QUOTE=grakhul]
I take it that I have a 386 kernel because i ran uname and that's what it told me.  I have an Inten Celeron Processor rated at 2.2 GHz.  I was wondering if I should do the command performed above to install an upgraded kernel.  
1.  How long does the install take?
2.  Does it leave any residual log files, temp files or garbage behind?
3.  What are the benefits of using linux-686 over linux-386?
4.  Will I gain application speed?  Will limited amount of memory be used more efficiently?
5.  WIll I have to reinstall the applications I already have installed?[/QUOTE]

1.  I'm not sure if the 686 optimized kernel is on the install CD or not.  If it is not or if you do not have the CD, apt-get will automatically download the file from the Ubuntu repositories.  I think that the kernel is about 15 MB so how long it takes depends on how fast your internet connection is.  Once it is downloaded, apt-get will automatically install it.  The actual installation takes a minute or two.

2.  After you install the new kernel, Ubuntu will use the new one by default during the boot.  However, the original 386 kernel is still installed (which is a good thing in case the 686 version does not work).  If you press the escape key at the Grub menu during boot, you can select the 386 kernel in case the 686 gives you problems.

3.  The 686 optimized kernel may run more efficiently on your processor.  Try it out.  If you don't notice a difference, it's easy to remove:
sudo apt-get remove linux-686

4.  Programs may run faster.  I don't think memory consumption will change but I might be wrong.  If you don't notice a difference or if it actually seems to run slower, it is very easy to go back to the 386 kernel.

5.  No, you will not need to re-install any other programs.

---

### Post by Kyral on 2005-05-21
Interesting idea. Now it has me wondering which kernel I should install to get the best out of my Athlon XP 2700. The i686 or the k7? (I don't know if there is an Athlon XP kernel)

---

### Post by SickTwist on 2005-05-21
[QUOTE=Kyral]Interesting idea. Now it has me wondering which kernel I should install to get the best out of my Athlon XP 2700. The i686 or the k7? (I don't know if there is an Athlon XP kernel)[/QUOTE]
That topic has been discussed [here](http://www.ubuntuforums.org/showthread.php?t=3810).

---

### Post by Kyral on 2005-05-21
[QUOTE=SickTwist]That topic has been discussed [here](http://www.ubuntuforums.org/showthread.php?t=3810).[/QUOTE]

oops, hehe, sorry. Thanks for the info

---

### Post by grakhul on 2005-05-22
Thanks for the info Sick Twist will do that shortly.  I had another question:
So let's say I install the i686 kernel and it works fine.  But I still have the 386 entries in menu.list.   Can I:
1.  Remove the entries in menu.list without any issues?
2.  Delete all of the extra kernel in the /boot directory?

---

### Post by SickTwist on 2005-05-23
[QUOTE=grakhul]Thanks for the info Sick Twist will do that shortly.  I had another question:
So let's say I install the i686 kernel and it works fine.  But I still have the 386 entries in menu.list.   Can I:
1.  Remove the entries in menu.list without any issues?
2.  Delete all of the extra kernel in the /boot directory?[/QUOTE]

You can remove the i386 kernel or keep it as a backup.  The important thing is to use apt-get/synaptic to add or remove packages.  Don't go in a terminal and start using rm to delete files.  If you remove a kernel with apt-get, all of the little details like updating the grub menu will be done automatically.

Some deb packages don't actually contain files to install, they just depend on other packages to make upgrades easier.  These special packages are called meta-packages.  linux-386 is actually a meta-package.  Its job is to force other packages to automatically be installed when you do apt-get install linux-386.

If you want to remove a kernel, start Synaptic (System->Administration->Synaptic Package Manager) and do a search for "linux".  Then sort the "Installed Version" column by clicking on it twice so you see the installed packages at the top of the list.  Some of the linux packages that you see installed are just meta-packages (they force other packages to be installed).  linux-386 requires linux-image-386 and linux-restricted-modules-386.  those are both meta-packages too.  On my computer linux-image-386 requires linux-image-2.6.10-5-386 which contains the the actual kernel.  This file will change as updates are released so it may be different on your system.  This is the file that you need to remove to uninstall the 386 kernel.  Just right click on the package and select "mark for complete removal".  Synaptic may ask you if you want to remove linux-restricted-modules-2.6.10-5-386.  It is fine to remove it because this package is only needed for the 386 kernel your are removing. Be sure you are removing the correct kernel!  Then click "Apply" and a confirmation window will appear listing the changes that are about to be made.  You should only see things on the list with 386 in their name--nothing with 686 if that is the kernel you are keeping.  Then click apply in the confirmation window and Synaptic will do everything else.

I hope this helps and that I have not confused you.

---

