---
title: "Installed kubuntu 11,04 instad of ubuntu"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by LMH1 on 2011-05-07
Hi i tryed to installed ubuntu 11.04 but that dont work with grub bootloader.

So i tryed kubuntu 11.04 instad, that work.

Used :Sudo apt-get install ubuntu-desktop

 But i dont get this menus:

[IMG]http://www.neowin.net/images/uploaded/Ubuntu_10.10_Maverick_Meerkat_Netbook_Live_USB.png[/IMG][IMG]http://www.muylinux.com/wp-content/uploads/2010/10/Unity.png[/IMG]

I just get this wallpaper (Without menus?)

Is it some "[*[I]Requirement*[/I]]("http://en.wikipedia.org/wiki/Requirement")" that i need? E.g display-drives/OpenGL or someting?
If not will this menu`s be disabled?

I just got some like: (Ubuntu classic)
[IMG]http://compixels.com/wp-content/uploads/2010/09/Ubuntu-10.10-desktop-System.png[/IMG]
[IMG]http://img3.imagebanana.com/img/x34gp6re/wartyfinalubuntu.jpg[/IMG]
As default desktop (Ubuntu)

KDE desktop work great also.

---

### Post by Dutch70 on 2011-05-07
I doubt if very many people have tried installing Kubuntu 11.04 & then adding ubuntu-desktop, so you're chances of finding someone that knows about that aren't very good. That doesn't mean that you won't though. It's up to you if you want to wait & see.

Have you tried other options on the log-in screen?

What do you mean Ubuntu 11.04 won't work with grub boot loader? 
It sounds like maybe you had a bad download or a bad burn to the cd/usb with Ubuntu 11.04.

Check the md5sum of the Ubuntu 11.04 download & check the cd for defects when you boot it up. Instead of selecting install.

---

### Post by pbpersson on 2011-05-07
I had a terrible time getting the 64-bit live CD ISO image for 11.04.  I received two corrupted copies that I verified with the md5sum.

Finally I received a good version through BitTorrent, having given up on the standard download.

---

### Post by LMH1 on 2011-05-07
> **Dutch70 said:**
> 
Have you tried other options on the log-in screen?

Yes, that i trying with, KDE/Gnome old works but not (Unify desktop?)

> **Dutch70 said:**
> 
What do you mean Ubuntu 11.04 won't work with grub boot loader? 

I get (Grub command) instead of boot command menu.
[IMG]http://i41.tinypic.com/s49oi8.png[/IMG]

> **Dutch70 said:**
> 
Check the md5sum of the Ubuntu 11.04 download & check the cd for defects when you boot it up. Instead of selecting install.

I have check MD5 sum and SHA1.

---

### Post by MAFoElffen on 2011-05-07
> **Dutch70 said:**
> I doubt if very many people have tried installing Kubuntu 11.04 & then adding ubuntu-desktop, so you're chances of finding someone that knows about that aren't very good. That doesn't mean that you won't though. It's up to you if you want to wait & see.

Have you tried other options on the log-in screen?

What do you mean Ubuntu 11.04 won't work with grub boot loader? 
It sounds like maybe you had a bad download or a bad burn to the cd/usb with Ubuntu 11.04.

Check the md5sum of the Ubuntu 11.04 download & check the cd for defects when you boot it up. Instead of selecting install.
I've got some experience there with this "on" 11.04-- installing  ubuntu-desktop, xubuntu-desktop and kubuntu-desktop on the desktop and server  bases. 

No, you are not going to get the option of what desktop to boot from the Grub menu.  Your choice comes later...

Before I say where... ubuntu-desktop and xubuntu-desktop use gdm and differences are nominal.  Kubuntu's kubuntu-desktop starts via kdm.  Whatever you install last, is going to be the  a mix of the splash and some other things inherited... As you'll notice in the install process of the desktop. the last thing it does before running grub-update  is that it updates the kernel image.  I am assuming with some pointer to the Xorg loader, as that it seemed that "that" default changed somewhere in that process.   Even on a server base, where the "default" is tty, once you install a desktop and the image is updated, the default is then "changed", and from then on- you would "have" to tell the kernel to boot a text console session if you wanted it...

When you install both a gdm and kdm, the first time you try to boot it, it pops up a dialog box (at least it "should" do this) and asks you what want you want to use as you default Xsession loader, gdm or kdm.

Too much info?

Okay now:

If you load multiple desktops. When you are booting and get to the logon screeen, select your username. >

The password box will appear..
.
At the same time, there will be startup options that appear in the bar   at the bottom of the screen, halfway across will be a pull-down box that   will allow you to select Ubuntu, Ubuntu "Classic." Ubuntu Classic   without affects... etc.  
[IMG]http://img59.imageshack.us/img59/8084/loginoptions.png[/IMG]
In that dropdown window, besides the options in the image above, "you" will see both Ubuntu and Kubuntu... Select what desktop you want. > type in your password and go on.  It will remember and stay at whatever you selected last as the option.

I was testing "what" it actually ended up with... With my 3 desktops that I tested... all the applications did end to to setup in all 3 desktops... and had to be careful as some applications for Ubuntu and Xubuntu all ran in Kubuntu-- but, understandably, not all app's from KDE would run in Ubuntu and Xubuntu. (rare instances, but still happened).

Edit-  And wasn't the screen shot you posted a KDE unity desktop, so it looked like unity was working, right??

---

### Post by LMH1 on 2011-05-07
> **MAFoElffen said:**
> 
.
At the same time, there will be startup options that appear in the bar   at the bottom of the screen, halfway across will be a pull-down box that   will allow you to select Ubuntu, Ubuntu "Classic." Ubuntu Classic   without affects... etc.  
[IMG]http://img59.imageshack.us/img59/8084/loginoptions.png[/IMG]


I tryed that but get:

[IMG]http://img3.imagebanana.com/img/x34gp6re/wartyfinalubuntu.jpg[/IMG]

Instad of (Desktop with menu`s).

And just "apps icon" the menus is disabled.

---

### Post by orangep on 2011-05-07
Installed the wrong thing?
I really did that a few days ago.

I picked up an AMD 64-bit Kubuntu disk when I meant to use a 32-bit disk,
and installed it on a laptop with an Intel Core2 Duo CPU.
And the darned thing ran. I didn't notice the error until I wanted to
install more packages and the system was demanding that I put the 64-bit disk in the drive...

How is that even possible? A 32-bit CPU runs 64-bit code???

---

