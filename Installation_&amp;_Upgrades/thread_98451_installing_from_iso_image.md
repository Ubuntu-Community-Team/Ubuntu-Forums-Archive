---
title: "installing from iso image"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by vampire_janus on 2005-12-03
how is this done? please help.. thanks! :D

---

### Post by atoponce on 2005-12-03
Download the .iso, burn it to a CD, place the CD in your CDROM, and reboot.  Follow the onscreen prompts to install the system, remove the CD, and reboot again.  Your new Ubuntu distro will be up and running, in that you didn't have any problems with the install or hardware.

---

### Post by vampire_janus on 2005-12-03
[QUOTE=atoponce]Download the .iso, burn it to a CD, place the CD in your CDROM, and reboot.  Follow the onscreen prompts to install the system, remove the CD, and reboot again.  Your new Ubuntu distro will be up and running, in that you didn't have any problems with the install or hardware.[/QUOTE]
of course i don't want to burn it into a cd ie i don't have a cd writer

---

### Post by mlomker on 2005-12-03
[QUOTE=vampire_janus]of course i don't want to burn it into a cd ie i don't have a cd writer[/QUOTE]

That isn't an option if you want to do a normal installation.  If you don't have access to a CD burner then you should [order a disc]("http://shipit.ubuntu.com/").

---

### Post by taurus on 2005-12-03
If you don't have a cd burner, then

1.  Buy one since it's dirty cheap now...
2.  Find a friend who does...
3.  Go to local library to see if they have one available...
4.  Order it for free from Ubuntu's or some other Linux onlines for minimal fee...

---

### Post by vampire_janus on 2005-12-03
don't you have any better advice than getting a cdrom? i want to install it using the iso image. either you tell me how it is done or just do not comment at all.

---

### Post by aysiu on 2005-12-03
I don't know if this HowTo is still valid (it was written in April), but...

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by Ptero-4 on 2005-12-03
Vamp. You can't install off an iso b/c to do that you would need to make the BIOS spin up the HD, then point to the iso, mount it and then boot off it. Of course that's pretty hard and cumbersome to implement and even if it got implemented doing it would mean that the HD needs to be mounted which would make it imposible to repartition (you can't re-partition a HD if one or more of its partitions are mounted). The reason for burning it to a CD is that being in a CD makes it bootable without having to relay in the HD.

---

### Post by mlomker on 2005-12-03
[QUOTE=aysiu]I don't know if this HowTo is still valid (it was written in April), but...
[/QUOTE]

That's interesting.  It's a netboot installation, though, because it doesn't use the ISO file. 

[quote=vampire_janus]either you tell me how it is done or just do not comment at all.[/quote]

The code of conduct here doesn't allow being disrespectful.  If someone is providing you with a work-around solution then that's valid advice.

---

### Post by aysiu on 2005-12-03
[QUOTE=mlomker]That's interesting.  It's a netboot installation, though, because it doesn't use the ISO file.[/QUOTE] Good point. It was the closest I could find in a search, though.

---

### Post by xe1ufo on 2005-12-04
And I have the same, I beleve, valid question.  I know that in some of the other distros out there you CAN install from an ISO image on your hard drive (SuSE, for example, which unfortunately is too much for my 64-Megs RAM.). They offer a floppy disk boot image that lets you point the installerto the specific ISO image on your drive and takes it from there.

I am using an old Sony Vaio PCG-505FX. I have NO CD ROM drive, so can I download it to a dirctory and then use a program like IsoBuster to take apart the CD image and then install from there? Taking the Hard Drive out of this machine is VERY hard to do. 

By the way, what are the minimum system requirements for Ubuntu?
--266 Mhz.
--40-Gig drive
--64-Megs

Thanks in advance!

Dr. Steve, central old Mexico

---

### Post by aysiu on 2005-12-04
Your best bet I already linked to in post #7 of this thread.

---

### Post by Topsiho on 2005-12-04
I remember that somewhere in (it almost must be) this forum was a description how to use an .iso image on the hard disk to install from. The author said that never again he would burn an .iso image on a CD. I leave it to you to search fot this description yourself :D. 

So according to this author it really is possible.

About partitioning the hard disk: I guess you must do this first before the installing, but then: read the description first.

Topsiho

Edit: I should have read and followed up Aysiu's post #7, as it points exactly to what I was referring to. If this post did not help you then I can tell you no more :(

---

### Post by linbetwin on 2005-12-04
[quote=xe1ufo]And I have the same, I beleve, valid question.  I know that in some of the other distros out there you CAN install from an ISO image on your hard drive (SuSE, for example, which unfortunately is too much for my 64-Megs RAM.). They offer a floppy disk boot image that lets you point the installer from to the specific ISO image on your drive and takes it from there.

I am using an old Sony Vaio PCG-505FX. I have NO CD ROM drive, so can I download it to a dirctory and then use a program like IsoBuster to take apart the CD image and then install from there? Taking the Hard Drive out of this machine is VERY hard to do. 

By the way, what are the minimum system requirements for Ubuntu?
--266 Mhz.
--40-Gig drive
--64-Megs

Thanks in advance!

Dr. Steve, central old Mexico[/quote]

I'm afraid 64 MB of RAM is too little for GNOME. Maybe xfce would be better suited.

---

### Post by bwog on 2005-12-04
@vampire janus: install with iso; [http://ubuntuforums.org/showthread.php?t=28948&highlight=booting+iso+hd](http://ubuntuforums.org/showthread.php?t=28948&highlight=booting+iso+hd)

There is additional info here: [http://ubuntuforums.org/showthread.php?t=94168](http://ubuntuforums.org/showthread.php?t=94168)

I also think that buying a CDROM player is good advice, but perhaps the links above can help you. Tell us if it worked. Good luck.

---

### Post by vampire_janus on 2005-12-04
i know now how to :D



you need to download the files in here 

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current//images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current//images/hd-media/)

and place it in a convenient directory, say /hdinstall 



if you have grub, you can temporarily add an entry like this

title Install Ubuntu 5.10 (Breezy) from IDE ISO

kernel   (hd0,7)/hdinstall/vmlinuz root=/dev/ram0
initrd   (hd0,7)/hdinstall/initrd.gz



of course, you have to change (hd0,7) to the appropriate partition you added the folder hdinstall into. then boot into it.

if you have windows 9X, you can also use loadlin. restart in msdos mode. cd into hdinstall then run
loadlin vmlinuz initrd=initrd.gz root=/dev/ram0

i just wonder why ubuntu doesn't have a sort of askmethod in its default install?

i forgot to mention that the ubuntu installer would be automatically looking for the isos. so you have to place it in a searchable location.

---

### Post by vampire_janus on 2005-12-04
and also, the installation hung up in the end when it was about to restart (maybe just my hardware? or maybe because i use loadlin). but the first stage of the installation is finished so i just have to reset and everything is ok.

---

### Post by bwog on 2005-12-04
@vampire janus: 

"i just wonder why ubuntu doesn't have a sort of askmethod in its default install? "

The makers of ubuntu try very hard to keep installation simple.

When you make lists of questions for users that even includes installing from iso, you will have a long list of questions.

---

### Post by vampire_janus on 2005-12-04
[QUOTE=bwog]@vampire janus: 

"i just wonder why ubuntu doesn't have a sort of askmethod in its default install? "

The makers of ubuntu try very hard to keep installation simple.

When you make lists of questions for users that even includes installing from iso, you will have a long list of questions.[/QUOTE]

other distros have this way too long ago. and the install page shouldn't show unless explicitly called for at the beginning ie fedora has this if you will be giving the 'askmethod' parameter at the start. so simplicity should be preserved.

and on a technical viewpoint, it shouldn't be hard to implement i think. as the source of install should be transparent to the installation program.

---

### Post by bwog on 2005-12-04
All distros make choices on principle, but as this is not a question on installation, the topic is better suited for the development section or the chat section.

---

### Post by jonnnny on 2007-01-25
> **vampire_janus said:**
> i know now how to :D



you need to download the files in here 

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current//images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current//images/hd-media/)

and place it in a convenient directory, say /hdinstall 



if you have grub, you can temporarily add an entry like this

title Install Ubuntu 5.10 (Breezy) from IDE ISO

kernel   (hd0,7)/hdinstall/vmlinuz root=/dev/ram0
initrd   (hd0,7)/hdinstall/initrd.gz



of course, you have to change (hd0,7) to the appropriate partition you added the folder hdinstall into. then boot into it.

if you have windows 9X, you can also use loadlin. restart in msdos mode. cd into hdinstall then run
loadlin vmlinuz initrd=initrd.gz root=/dev/ram0

i just wonder why ubuntu doesn't have a sort of askmethod in its default install?

i forgot to mention that the ubuntu installer would be automatically looking for the isos. so you have to place it in a searchable location.

Thanks for this!!

For edgy, I think you need different files from this location instead:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/)

---

### Post by mjrclark on 2007-02-18
Thank you for that.
I can confirm that location works for edgy, and for fiesty too. This process is remarkably simple, perhaps more people would use it if it was documented somewhere. A large application would be perfectly clean dist-upgrades, or installing the server edition, or installing alongside a different Linux distro.

---

