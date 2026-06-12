---
title: "Several installation troubles.  Need advice please"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by partsmutt on 2007-07-30
I'm really trying to get this to work.

I'll number these to make it easier for you helpful folks to reply.

1) First of all a curiosity.  I have a single hard drive (no dual boot, this is a pure Linux box, windows is never an option in my house).  The drive is IDE, the motherboard does *not* have a scsi controller either.  Yet Ubuntu sees my drive as a scsi drive.  Is this normal for Ubuntu or is this an error that will bite me later?

2) The Fiesty install didn't work as hyped.  I did get it installed, eventually, using the "live cd" image, but not with everything I wanted..... I guess I should interject here, this is an Edubuntu install.  For those unfamiliar Edubuntu is Ubuntu with a more kid friendly desktop appearance (still gnome) and a ton of educational software.  Just what I wanted since this machine is for my young son.

I finally got it installed, but not the full install with the educational software.  However, all that software is available on an additional software iso image.  I downloaded that.  But I can't get the software to install.  I tried the "add/remove programs" menu item, but it wouldn't work because I have no network connection (more on that later).  I tried Synaptek (sp?), and that wanted a network connection also.  There is an option in there to Add the CD-Rom as a repository so it could load from there, but it won't work.  It says the cd-rom isn't mounted.  However it surely is mounted, because I get a CD icon on the desktop and can peruse the contents of the cd through that.  Incidentally, the cd is full of .exe and .dll files.  Why is there a bunch of windows stuff on the linux disk?  (I don't own a windows box to look at this).

So question 2 is:  How do I load this software off the cd?

3) The network.  This is a can of worms.  Using the lsusb command, I can see the usb network adapter, but it isn't recognized as such by the computer.  The computer just tells me something is there, and there is no driver loaded for it.  BTW, I have a Linksys WUSB54G version 2.  Using the iwconfig command, the computer sees nothing.  Now I understand I likely need to use the ndiswrapper and a windows driver for the Linksys to work, but how do I get it recognized in the first place?  Since loading simple apps at this point isn't possible, I'm sure that I'll be back asking how to load the driver later, but for now I'd be happy having the hardware seen.
Question 3, how do I get the usb net adapt recognized?

That's it for now.  I figure if I can get these 3 issues working in the next day, I'll press on with Ubuntu.  Otherwise I'm going to give openSuse a try later this week just to see if it's a little more user and hardware friendly.

Thanks everyone,
Dave

---

### Post by funpop on 2007-07-30
1) i have no idea why your ide is seen as scsi, sorry.. so your drive is shown as sda ?
2) Linksys: [http://ubuntuforums.org/showthread.php?t=478558&highlight=Linksys+WUSB54G](http://ubuntuforums.org/showthread.php?t=478558&highlight=Linksys+WUSB54G)
3) how to use the add-on cd:
[http://doc.ubuntu.com/edubuntu/handbook/C/ch02s03.html](http://doc.ubuntu.com/edubuntu/handbook/C/ch02s03.html)

note: i never used wireless or edubuntu, so these are just some search results..

---

### Post by partsmutt on 2007-07-30
Thanks funpop.

Yup, my drive is sda1.  Weird huh?

The link for the wireless is version 4, which is evidently very different from the version 2 that I have.

As far as the add-on cd.  That link would be great if it really worked that way.  It says that upon insertion it will recognize the disk as an add on volume and ask if I want to install packages.  Unfortunately it doesn't do that.  It just puts the icon on the desktop and refuses to look at it with the application / package managers.  So that's my problem, it won't do what the documents say it does.

Thanks anyway.
Dave

---

### Post by funpop on 2007-07-30
maybe you should visit 

#edubuntu
on irc.freenode.net
"This is our main channel where day to day conversations and support relating to Edubuntu take place."

good luck

---

### Post by bobjo on 2007-07-30
I installed Edubuntu as you did and encountered the same problems, I was fortunate that my internet connection went OK and after implementing auto updating/upgrading the, one of the upgrades opened up the capability to install all of the educational applications.
I can not advise you on how to fix your internet, but I would make that my first objective because it will make everything a lot easier.
The educational apps. are well worth the effort, I do not know any other linux that offers a childrens version.
I installed it for my grandchildren and they reckon it is great.:popcorn:

---

### Post by bobjo on 2007-07-30
I should have mentioned that, Edubuntu is the same as Ubuntu, but with a interface for children.
So all info relating to Ubuntu applies equally to Edubuntu.:KS

---

### Post by partsmutt on 2007-07-30
Thanks for the words of encouragment bobjo.  If I can get an answer to my wireless questions in the other forum I'll be good.  I think I'm on the right track to getting it working, just bogged down in a couple details.

Thanks again!
Dave

---

