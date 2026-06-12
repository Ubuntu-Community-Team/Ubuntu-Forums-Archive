---
title: "Old PC p weird cd problem"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by croquagei on 2008-02-08
Hey guys

Decided to revive my parents old computer to put xubuntu onto.Specs:
600mhz celeron
128MB RAM
20GB hard drive

Basically it's a pile of junk with windows on it.

I'm ready to install xubuntu except i have one weird problem i can't seem to figure out.
My cd-rom drive isn't being recognised by my motherboards bios but is if i let it continue to load into windows.

This creates a real hassle as i can't install xubuntu if i can't get the cd-rom drive to work.

I've never heard of bios not seeing an IDE device but windows does.  Any suggestions so i can get this junker back running again?

---

### Post by overdrank on 2008-02-08
> **croquagei said:**
> Hey guys

Decided to revive my parents old computer to put xubuntu onto.Specs:
600mhz celeron
128MB RAM
20GB hard drive

Basically it's a pile of junk with windows on it.

I'm ready to install xubuntu except i have one weird problem i can't seem to figure out.
My cd-rom drive isn't being recognised by my motherboards bios but is if i let it continue to load into windows.

This creates a real hassle as i can't install xubuntu if i can't get the cd-rom drive to work.

I've never heard of bios not seeing an IDE device but windows does.  Any suggestions so i can get this junker back running again?

HI and do you mean that when you are in your bios that no cd drive is detected or are you meaning that it just doesn't boot to the cd and I assume that with that low memory you are using the alternate cd?

---

### Post by croquagei on 2008-02-08
Correct that it doens't boot to the cd.  But i believe the reason why is that when i go into cmos and it displays my IDE devices the cd-rom drive isn't there.

---

### Post by overdrank on 2008-02-08
> **croquagei said:**
> Correct that it doens't boot to the cd.  But i believe the reason why is that when i go into cmos and it displays my IDE devices the cd-rom drive isn't there.

Ok is the cd drive slave to the hard drive or is it on a separate ide channel? On most older motherboards there are two ide channels and sometimes they are setup with the cd drive as a slave to the hard drive. I have not seen this issue that the bios did not recognize the cd drive yet access it in the OS.

---

### Post by slipperhead on 2008-02-08
would unetbootin be any use to you?

 [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411&release_id=573013](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411&release_id=573013) 
download the exe file version since you already have windows.

i installed ubuntu on an old compaq deskpro that didnt have a cdrom, using this.
you could install ubuntu first, then remove ubuntu desktop and install xubuntu desktop in its place.

i know it doesnt solve your cd problem. but it gets ubuntu installed if you have a net connection.


you could also remove the hard drive and put it in another pc to install xubuntu. 
i originally installed ubuntu this way before i found unetbootin and had no problems as ubuntu hardware detection is very good.

---

