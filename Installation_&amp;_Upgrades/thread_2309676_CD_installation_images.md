---
title: "CD installation images"
date: 2016-01-12
forum: Installation &amp; Upgrades
---

### Post by daryl9 on 2016-01-12
I am working on a project where I received several older systems. I am installing edubuntu on these systems. The issue that I'm am running into is that some of these systems only have CD drives, but the installation media is DVD.  I've looked at the download options for edubuntu, and they are all DVD images.  Is there somewhere that I can get CD images?  

Thank you.

Daryl

---

### Post by Bucky Ball on 2016-01-12
Not really. Guess Edubuntu doesn't fit on a CD anymore. A few of options, though.

1/ [Install a lighter flavour]("http://xubuntu.org/") and add the Edubuntu packages you want. You can add 'modules' separately for young ones, primary, seconday, tertiary or a combination; you probably don't need all of them on the one machine. See ['Installtion on an existing Ubuntu system', second heading here]("https://edubuntu.org/Download"). There is also Xubuntu-core and Lubuntu-core available in 15.10.
2/ Do a [minimal install ]("https://help.ubuntu.com/community/Installation/MinimalCD")and add just the packages you want. Very light and speedy on old machines.
3/ [Install with a USB]("www.unetbootin.sourceforge.net"). That way CD size is not an issue.

---

### Post by daryl9 on 2016-01-12
> **Bucky Ball said:**
> Not really. Guess Edubuntu doesn't fit on a CD anymore. A few of options, though.

1/ [Install a lighter flavour]("http://xubuntu.org/") and add the Edubuntu packages you want. You can add 'modules' separately for young ones, primary, seconday, tertiary or a combination; you probably don't need all of them on the one machine. See ['Installtion on an existing Ubuntu system', second heading here]("https://edubuntu.org/Download"). There is also Xubuntu-core and Lubuntu-core available in 15.10.
2/ Do a [minimal install ]("https://help.ubuntu.com/community/Installation/MinimalCD")and add just the packages you want. Very light and speedy on old machines.
3/ [Install with a USB]("http://www.unetbootin.sourceforge.net"). That way CD size is not an issue.


Bucky,

Thanks for the suggestions.

When I first started evaluating to see if Ubuntu would fill my needs, I installed regular Ubuntu, and installed individual educational programs.  However, I wasn't sure which programs were for elementary, primary or tertiary.  I was just "picking and choosing".  However, when I learned of Edubuntu, and learned that I could tailor the install for the educational level that I am building the system for, I then realized that Edubuntu is the direction that I want to go.

I'll take a look at the USB install.  That might work for me.

Thanks

Daryl

---

### Post by Bucky Ball on 2016-01-12
If you have a look on the Edubuntu page at the link I provided under 'Installing in existing Ubuntu System' you will see that the groups of programs are clearly delineated for installing. Pre-school, primary, secondary, tertiary. Take your pick.

To be honest, I've been at uni (for years!) and have never used Edubuntu tertiary. It just doesn't have the majority of apps I need. Unless you're maths/science based, not much of interest there. I find the included apps a little skimpy. Prefer to go the mini install route and create a hybrid that suits my study needs perfectly. Just throwing that in. 

Good luck. :)

---

### Post by daryl9 on 2016-01-13
> **Bucky Ball said:**
> If you have a look on the Edubuntu page at the link I provided under 'Installing in existing Ubuntu System' you will see that the groups of programs are clearly delineated for installing. Pre-school, primary, secondary, tertiary. Take your pick.

To be honest, I've been at uni (for years!) and have never used Edubuntu tertiary. It just doesn't have the majority of apps I need. Unless you're maths/science based, not much of interest there. I find the included apps a little skimpy. Prefer to go the mini install route and create a hybrid that suits my study needs perfectly. Just throwing that in. 

Good luck. :)

The apps that get installed are not really for me to decide.   I need input from the educational environment that I'm building these systems for.  Right now the best option that I have is the pre-configured bundles.  I actually don't know if these will work for the schools that I am building these for, but we'll give it a try.  I'm actually thinking of building a single system send it to the school that I am building these for and see if I can get some feedback.  

As for installing.  I think that the solution that I am going to end up with is network install.  I can share out an ISO image from my NAS with FTP access.  I see on Ubuntu's website there is a network install option, but it is not in an ISO image format (which I would prefer).  when I drill down the version that I want, 14.04 LTS i386, I just get a directory listing:

[TABLE="class: grid, width: 500"]
[TR]
[TD][TABLE="width: 115"]
[TR]
[TD="width: 115"]Name[/TD]
[/TR]
[/TABLE]
[/TD]
[TD]Last modified[/TD]
[TD]Size[/TD]
[/TR]
[TR]
[TD]Parent Directory[/TD]
[TD][/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]boot.img.gz[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]25M[/TD]
[/TR]
[TR]
[TD]mini.iso[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]33M[/TD]
[/TR]
[TR]
[TD]netboot.tar.gz[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]25M[/TD]
[/TR]
[TR]
[TD]pxelinux.0[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]26K[/TD]
[/TR]
[TR]
[TD]pxelinux.cfg/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]ubuntu-installer/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]xen/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[/TABLE]

I'm trying to figure out what I actually need to build an network installation CD.

I downloaded netboot.tar.gz and boot.img.gz, and extracted the files.  ubuntu-installer/ is what is in netboot.tar.gz. I drill down into the directory, and get:

[TABLE="class: grid, width: 500"]
[TR]
[TD]Name[/TD]
[TD]Last modified[/TD]
[TD]Size[/TD]
[/TR]
[TR]
[TD]Parent Directory[/TD]
[TD][/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]boot-screens/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]initrd.gz[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]20M[/TD]
[/TR]
[TR]
[TD]linux[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]5.6M[/TD]
[/TR]
[TR]
[TD]pxelinux.0[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]26K[/TD]
[/TR]
[TR]
[TD]pxelinux.cfg/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[/TABLE]


I'm assuming that I need all of the above in the root of the CD, correct?  How about:  pxelinux.0, pxelinux.cfg and version.info?  They were also extracted from netboot.tar.gz, but are at the top of the archive, not down in the ubuntu-installer directory.   Do I need those three files in the root of the CD?

Any advice that you can give me on building the network installer CD, I would appreciate it.

Thank you.

Daryl

---

### Post by grahammechanical on 2016-01-13
The Ubuntu minimum CD image is not an ISO image but it is an image file. A raw CD image file. It can be burnt to a CD just like the usual DVD size ISO image. It is only 40MB in size. I have used the File Manager with a right click on the image file and select the Write to disk option to burn a Ubuntu minimum CD image to a CD R/W disk.

It will load like an ISO image burned to DVD but it will have a text based interface and not the Graphical User Interface. All selection has to be done from menus. We have to set up an internet connection.

You will first get a screen with 4 options

Install
Command-line install
Advanced options>
Help

treat "boot:" as if it is a command-line prompt.

My suggestion would to be write down the steps that you take and create an installation guide so that installing Ubuntu on these machines becomes a matter of following a list of instructions.

If these machines have similar hardware and disk drives of equal size then it would be possible to set up one machine, create an image of the hard drive and restore that image to the drives of the other machines. That might simplify installation of an OS for many machines.

Regards.

---

### Post by daryl9 on 2016-01-13
> **grahammechanical said:**
> The Ubuntu minimum CD image is not an ISO image but it is an image file. A raw CD image file. It can be burnt to a CD just like the usual DVD size ISO image. It is only 40MB in size. I have used the File Manager with a right click on the image file and select the Write to disk option to burn a Ubuntu minimum CD image to a CD R/W disk.

It will load like an ISO image burned to DVD but it will have a text based interface and not the Graphical User Interface. All selection has to be done from menus. We have to set up an internet connection.

Regards.

The only image file that I see is boot.img.gz.  Is this all I need to create a network installation CD?  What with everything else in the directory?  None of it is needed?

> **grahammechanical said:**
>  [COLOR=#000000]If these machines have similar hardware and disk drives of equal size then it would be possible to set up one machine, create an image of the hard drive and restore that image to the drives of the other machines. That might simplify installation of an OS for many machines. [/COLOR]

No, not all systems are identical. I have 20 different systems, about half are similar, the rest are all different.  I would love to create a single machine, image it, and then build all of the other machines based on that image.  It would make my life a lot easier, but unfortunately, I can't do it that way.

Thanks

Daryl

---

### Post by Bucky Ball on 2016-01-13
> **daryl9 said:**
> I would love to create a single machine, image it, and then build all of the other machines based on that image.  It would make my life a lot easier, but unfortunately, I can't do it that way.

Why not? Install a system, tweak it, [create an ISO of the system]("https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/") with Clonezilla or using another method. You could clone the install and restore it using each machine's hard drive as the target. You may need to screw about with grub on each, though. Boot Repair might make it streamlined.

Have a [look here]("https://duckduckgo.com/?q=create+custom+iso+ubuntu"). Once you have your custom install you could create an image and somehow install on all machines at once using a net install on your local network. ;)

(Thinking out loud, well, in black and white, here.)

---

### Post by daryl9 on 2016-01-13
> **Bucky Ball said:**
> Why not? Install a system, tweak it, [create an ISO of the system]("https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/") with Clonezilla or using another method. You could clone the install and restore it using each machine's hard drive as the target. You may need to screw about with grub on each, though. Boot Repair might make it streamlined.

Have a [look here]("https://duckduckgo.com/?q=create+custom+iso+ubuntu"). Once you have your custom install you could create an image and somehow install on all machines at once using a net install on your local network. ;)

(Thinking out loud, well, in black and white, here.)

Clonezilla works fine if the hard drives are all the same size, but if there not, its a more of an headache than what I want to deal with.  I've used it before.

Daryl

---

### Post by Bucky Ball on 2016-01-13
If you do the whole drive. But if you clone a partition ... the taget partition needs to be the same size or larger. Whether this idea is helpful would depend on the size of the partitions existing on each machine already. The size of your finished customised install will probably not amount to much more than 10-15Gb, depending on how wild you're intending to go. ;)

---

### Post by daryl9 on 2016-01-13
> **Bucky Ball said:**
> If you do the whole drive. But if you clone a partition ... the taget partition needs to be the same size or larger. Whether this idea is helpful would depend on the size of the partitions existing on each machine already. The size of your finished customised install will probably not amount to much more than 10-15Gb, depending on how wild you're intending to go. ;)

That is an option.  I'll look at clonezilla again.  I do have a machine that I just recently built that has only an 80G hard drive. I'll look at cloning that machine, and then see what happens when I put it onto a system that has a much larger drive.   I know going from a larger drive to smaller one will not work, but I don't remember if I've ever gone from a smaller to a larger drive.  Its been a while since I've used clonezilla.

What I was thinking, if I can get an answer on the network installation, and how to create the network boot CD, that I setup a kickstart server (I don't remember what Ubuntu calls their build server).  I found documentation, but have not read through it yet.  I'm thinking that I should be able to specify a percentage in hard drive allocation.  Not set a hard limit, but say to use a percentage on the boot partition, a percentage on the swap, and then the rest on the OS.  That way it doesn't matter how large or how small the drive is.  But like I said, this is just a thought at the moment, and I haven't looked into any further it yet.

Any thoughts on the network boot issue?

Thanks

Daryl

---

### Post by Bucky Ball on 2016-01-13
When you say drive, do you mean partition? You are going to need a target partition on the drive of machine B to clone the source partition from machine A to. 

Cloning to larger is fine.

---

### Post by daryl9 on 2016-01-13
BTW, I think that I finally found an answer to my original question, how to split up the installation DVD into multiple installation CD images.  I was speaking to a co-worker, and I was pointed to [Power ISO]("http://www.poweriso.com/").  This program will allow me to take the installation DVD ISO, save it in a format that will allow the program to create CD sized ISO images.  If all else fails, I'll get a copy of that and give it a try.

Thank you.

Daryl

---

### Post by Bucky Ball on 2016-01-13
Compressing an ISO image? I think I'd be going the USB route. 

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

But good luck. See how it goes.

---

### Post by daryl9 on 2016-01-13
> **Bucky Ball said:**
> When you say drive, do you mean partition? You are going to need a target partition on the drive of machine B to clone the source partition from machine A to. 

Cloning to larger is fine.

When I said drive, I meant drive. The default installation of Ubuntu, or Edubuntu, partitions out the entire drive, unless I manually partition it.  If memory service me correctly, it creates swap and OS partitions. I would imagine that it creates a boot partition as well, but I have never looked that close to see if it does nor not.  

I don't remember the amount of spaced used on the machine that has an 80G drive.  maybe its only 10 - 15G as you originally said.  But I know that the entire drive was partitioned when I built the machine. 

Thanks

Daryl

> **Bucky Ball said:**
> Compressing an ISO image? I think I'd be going the USB route. 

UNetbootin:
[www.unetbootin.sourceforge.net]("http://www.unetbootin.sourceforge.net")

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

But good luck. See how it goes.

No, not compressing an ISO image, splitting it up into multiple CD sized installation disks.  Also, the USB is not an option.  These machines will not boot USB.

Any thoughts on the network boot option?

Thank you.

Daryl

---

### Post by daryl9 on 2016-01-13
No one answered this question in my original posting, so I thought that I would start a new thread just for this question.

I want to create a Network Installer CD. If you go to the  [Alternative downloads]("http://www.ubuntu.com/download/alternative-downloads") you find a section for Network installer.  Clicking the link for "[Download the network installer for 14.04 LTS]("http://cdimage.ubuntu.com/netboot/14.04/?_ga=1.93293917.1986304819.1452635812")" takes me to another page where I'm prompted to "Select an architecture to install".   I choose my appropriate architecture, in this case its i386. Instead of finding an installation image I find the following directory and files:


[TABLE="class: grid, width: 500"]
[TR]
[TD]Parent Directory[/TD]
[TD][/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]boot.img.gz[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD][TABLE="width: 64"]
[TR]
  [TD="width: 64"]25M[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD]mini.iso[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD][TABLE="width: 64"]
[TR]
  [TD="width: 64"]33M[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD]netboot.tar.gz[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD][TABLE="width: 64"]
[TR]
  [TD="width: 64"]25M[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD]pxelinux.0[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD][TABLE="width: 64"]
[TR]
  [TD="width: 64"]26K[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD]pxelinux.cfg/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]ubuntu-installer/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[TR]
[TD]xen/[/TD]
[TD]1/8/2016  5:17:00 PM[/TD]
[TD]-[/TD]
[/TR]
[/TABLE]


There are no images in this directory, other that the boot.img, which is needed to make the CD that I intend to create bootable, and mini.iso.

I downloaded netboot.tar.gz, unziped it and dropped the contents onto a blank CD, extracted boot.img and pointed my CD burning software to it, to make a bootable CD.  But this does not work. I just get boot errors.

I did try the "mini.iso".  I created a CD from it, and I was able to boot, configure networking and see my networked shared ISO image.   I was able to download some "additional components", but there was no option to do an actual install.  The last option in the list is to abort the install.  There is no option to perform the install.

Can someone provide directions on what I need to do to get a working bootable network installation CD?

Thank you.

Daryl

---

### Post by howefield on 2016-01-13
Threads merged.

---

