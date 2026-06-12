---
title: "desespearely need help!"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by karistouf on 2005-04-30
hi !

i m still trying to find a solution to install ubuntu warty on my old laptop:
-no net connection
-cdrom on usb plug
-no usb booting from bios

can someone tell me where to find an image for floppy or how to boot if i copy the iso  of the cd on my dev hda5 ?

it will be great to have some help!

thanks
christoph

---

### Post by az on 2005-04-30
In the install directory of your cd there is a floppy image of smart boot manager.  Rawrite it to a flooppy and boot from it.  You should be able to find your usb cdrom with that and boot....


Lemme know if it works..

---

### Post by karistouf on 2005-05-02
thanks for reply !
I m sorry but smb doesn t recognize my cd rom on usb port. 
Also on debian.org the image for hcdrom-usb do not work with ubuntu. All images from ubuntu doesn t fit my case ....

any further idea ? :neutral:

---

### Post by Gandalf on 2005-05-02
take a look also to [this](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by karistouf on 2005-05-02
thanks gandalf for your answer I will try to do this, but its very difficult, I m not really newbie but it s quite a shame that nobody tried to make an universal floppy boot for this... Perhaps a new project to launch ? I mean one that is activating in ramdisk a little linux  2.4 or 2.6 and putting it out when cd is founded ?

Oh, by the way, be aware of the Ballrog...

christoph

---

### Post by Gandalf on 2005-05-02
[QUOTE=karistouf]thanks gandalf for your answer I will try to do this, but its very difficult, I m not really newbie but it s quite a shame that nobody tried to make an universal floppy boot for this... Perhaps a new project to launch ? I mean one that is activating in ramdisk a little linux  2.4 or 2.6 and putting it out when cd is founded ?
[/QUOTE]
well i know it's hard, but since it's rare that we face people without a CD, you know, so the developpers look for better things to develop!

[QUOTE=karistouf]
Oh, by the way, be aware of the Ballrog...

christoph[/QUOTE] :lol: heheheh yeah you're right ;) :-P

---

### Post by karistouf on 2005-05-02
you know about old machines it s on this point I m arriving to put out all the windows in my Company... because of old laptop I convinced them to use knoppix installation.

So its a point where you can get some people where there is no money to buy new computers. 

For example if i want to buy a new CD player for my thinkpad T21 it cost me with local IBM agents 178 euros...

So, about developping, its interrestin  to pass times to develop certains things like this.

Main problem is that floppy boot actually with the 2.6 kernel are too huge.

Ok, I will try your solution tonight. Keep in touch about eating one day some Hurukaî...

christoph

---

### Post by Gandalf on 2005-05-02
well, just wishing you good luck, anyway if i'm not around here, there are many generous guys around ;)

---

### Post by ed_agamemnon on 2005-05-02
[http://ubuntuforums.org/showthread.php?postid=145618#poststop](http://ubuntuforums.org/showthread.php?postid=145618#poststop)
[http://ubuntuforums.org/showthread.php?postid=146746#poststop](http://ubuntuforums.org/showthread.php?postid=146746#poststop)

this those two :)

-ed.

---

### Post by karistouf on 2005-05-02
thanks Agamenon ! ( something to see with Atreides Old Greek House ? )

I will test the boot disk way, because I don t have net at home. It will be great like this!

NB: be aware of Eurydice !

---

### Post by karistouf on 2005-05-03
again and again....

dear everybody from mythology ( ancient and more recent); all links are conducting to a net installation !

I resume once again the situation of this laptop:
no internet connection
no cd rom but a cd rom on USB port
no boot from usb port
ethernet card not recognized

HOW CAN I INSTALL UBUNTU ?

Debian images are all for internet installations
Floppies are also for internet installations

bouououuou [-X

---

### Post by Gandalf on 2005-05-03
[QUOTE=karistouf]again and again....

dear everybody from mythology ( ancient and more recent); all links are conducting to a net installation !

I resume once again the situation of this laptop:
no internet connection
no cd rom but a cd rom on USB port
no boot from usb port
ethernet card not recognized

HOW CAN I INSTALL UBUNTU ?

Debian images are all for internet installations
Floppies are also for internet installations

bouououuou [-X[/QUOTE]
 your situation is weird man, i don't know if you can install it, because even after installation when you need something you need internet!

---

### Post by karistouf on 2005-05-03
thanks but it is not weird it is a poor case and I m not the only one...

once upon a time , when we were on kernel 2.4 you had usb image fort cd rom distributed ( example with mandrake 9.2). Now that kernel is bigger and that there is a need to make a complex floppy boot with 2 disk, nobody do it.... I had a few days ago two floppy to make boot knoppix 3.6 but installation was creating lot of crashes due to to the presence in ramdisk of 2 linux kernel... ( boot disk and then ramdisk knoppix)
I have tried also feather linux that is a knoppix remastirized, helas, not enough stable ....

I m usually proceeding from usb key to grab elements and dependencies missing. Quite painfull but my needs are limited to certains apps.

I beginning to be disespeared...

should I suicide  far away from Ubuntu Pingouins ?

 :roll:

---

### Post by az on 2005-05-03
Install woody using the woody boot floppy.

Dist-upgrade from woody to Hoary.

---

### Post by karistouf on 2005-05-03
??? you mean by that way that woody floppy boot handles a cd rom on usb port ?

 \\:D/ 

i will try, thanks

---

### Post by karistouf on 2005-05-03
dear azz, I have made a little google to find boot floppy for woody.

Results gave me this two files: debian-7248-boot.img and debian-7248-ramdisk.img

Of course after a rawrite under windows ( and certain tries to be sure about the quality of the floppies) nothing cames, no syslinux no debian installer, etc... In fact no system is founded....

Perhaps those are my sources.
Have you got a precise address for getting woody floppy boot ?

Or perhaps it is not the good way about the dist-update?
Are you sure it will help me in this frustating state not to install Ubuntu ?

A certain length of answer from you will make me enjoy to read you and help not to waste to much time on not sure solutions, or bad impulsions about the way to handle this problem.

Oh by the way SMB is only there to help you to make a boot on the bios recognized partitions on a system. It s like a "routage" of your acces to hard drive or bios-detected possibilities. ](*,) 


Sincerely yours, christoph

---

### Post by az on 2005-05-03
[http://www.debian.org/releases/stable/i386/install](http://www.debian.org/releases/stable/i386/install)

[http://www.debian.org/releases/stable/i386/ch-install-methods.en.html#s-downloading-files](http://www.debian.org/releases/stable/i386/ch-install-methods.en.html#s-downloading-files)


[http://http.us.debian.org/debian/dists/woody/main/disks-i386/current/images-1.44/bf2.4/rescue.bin](http://http.us.debian.org/debian/dists/woody/main/disks-i386/current/images-1.44/bf2.4/rescue.bin)
[http://http.us.debian.org/debian/dists/woody/main/disks-i386/current/images-1.44/bf2.4/root.bin](http://http.us.debian.org/debian/dists/woody/main/disks-i386/current/images-1.44/bf2.4/root.bin)
[http://www.debian.org/releases/stable/i386/ch-appendix.en.html#s-driver-images](http://www.debian.org/releases/stable/i386/ch-appendix.en.html#s-driver-images) (you may need the 5 floppies which are kernel modules (usb-disk?)

You should not need the base system floppies (20) since the plan is for you to access your usb drive from the installer.  You should download the woody iso image and use that as your base system repository.

Obviously, use the bf2.4 kernel.

Once you have a base system, 
apt-cdrom add
and add your hoary iso image

apt-get dist-upgrade
apt-get insall ubuntu-desktop

Good luck.

---

### Post by karistouf on 2005-05-03
thanks azz for helping me clear my mind...

file:


.../current/images-1.44/bf2.4/driver-5.bin

no more exist. I will still try without it, and hope to arrive to it. If yes it should be a new message that explains the manipulations.

ok ... go to work am I, and pleased very pleased from your help  \\:D/

---

### Post by karistouf on 2005-05-03
dear azz,

its a samourai sword i have actually in my stomach....

if i follow well :

-boot with rescue
-insert root floppy

and there images of root floppy doesn t work nor is recognized as it should

I made several tryes with rawrite and a set of new floppies ( i thing i m actually influencing in France consommation of such little accessoires)

so actually using this special kernel for hardware detection especially usb ones as described, nothing arrives...

have you got any idea ( i have damn small linux actually installed on hda 5) HOW i can clearly boot from hd in a simple manner ( ouppsss wrong word in my case)
I have lilo as boot loader on mbr and on my windows i put a grub loader under C;

but until now its nightmare...

and finally i m thinking going to a museum to be exposed as the poor guy of the year...

oh god !!! it s hurting this sword in my stomach
( do you meet developpers of the project from time to time ? perhaps they will laugh a lot but it would be great to hear about their opinion of a universal boot floppy .... for all dev)


see u.... arghhhhh

---

### Post by karistouf on 2005-05-03
ok azz, shame on me...

I had the bad luck to have a bad stock of floppy disk ( 40% not good)
so the images and procedures seems right, i m just tonight bloqued by the fact i need to download iso and burn it on CD of woody because its asking to put the base ( version of base at the adress are 11 flopies or 22, choices choices ...).

so the solution to install it thuth this kernell fb2.44 seems very good.

I keep you in touch about it when i will have some time to download somewhere woody image ( that should be basic woody iso ? am i right ? or should i download a special woody iso ?)

thanks again

keep in touch

( what a nightmare, but hopefully wath a luck so many active people in community !)

---

### Post by karistouf on 2005-05-04
azz, (and others), sorry for this monologue in 3 parts, the night has come along for me trying to install ubuntu.

Its a big lesson to know that you have to sya "my floppy vendor is rich"...

I m near of it BUT still in troubles.... Seems no more being a problem about accessing cd rom on USB port. Just problems of upgrading (I hope)


finally i downloaded late by night the base debs package (27M) at friends home.

 * I ran the installation thruth the floppies (4 floppy of drivers, the 5th is not existing in fact ) , adding to the kernel the following modules drivers:

-ethernet card ( succeed)
-pNp  plug&play  ( succeed)
-USB mass storage ( succeed)
-mouse on USB ( succeed)

 * then I put the CD where I write the debs package and it was automaticaly included as apt-get cd rom for install.

The installation succeed. I open linux under console mode ( normal, being in base)

 * I made the apt-get dist upgrade

I have updated woody to warty ( that the only CD of ubuntu I have actually)

No errors reported

 * Then I made the install of ubuntu desktop ( 1 hour of installation) being very long ( it going back on certains packages etc...)
I have seen it has installed also module of Nvidia and my graphic card is a S3...
And when finally the moon was rising and wolfes where shouting at it, I launched Linux.... :roll: 

 * Ubuntu begins well until X. Screening overlayed and delayed and carshing in all senses and not good.

IE errors are caused by the modules Synaptics ( for laptop) that I did not choose, the mouse ( that was not plugged it was a convenience for me):
X server at 0:0 crashes.* 

 * So actually system is on the machine, but only in console mode.

 * Should I begin again an all installation from Woody, and unselect the modules that causes the crashes from the module advanced of fb2.4 ?

 * or is there an other way to do it ? I mean by launching a script to configure X86 ?
Xsetup.sh doesn t exist. 

Thanks for all, I think the biggest troubles are pasted, thruth your help. Now it will be only little adjustements, am I right ?

 ;-)  courage courage courage. * . * ..

---

### Post by karistouf on 2005-05-05
Azz, thanks for your help, I m still in troubles; Is there any script like xsetup in Warty?

---

### Post by bored2k on 2005-05-05
[QUOTE=karistouf]Azz, thanks for your help, I m still in troubles; Is there any script like xsetup in Warty?[/QUOTE]
 You want to configure xfree86 ? Try
 sudo dpkg-reconfigure xserver-xfree86
 sudo dpkg-reconfigure xserver-xorg [on hoary]

And btw, you're posting in the hoary subforum

---

### Post by karistouf on 2005-05-05
hi, its lunching the service i want but still do not work. perhaps it is due to the experimental kernell fb2.4 i used. i will try tonight a boot floppy from woody classical, perhaps it will work. and i was confused first time i posted so it was posted there and discusssion continued with azz wich was great... ;-)

---

