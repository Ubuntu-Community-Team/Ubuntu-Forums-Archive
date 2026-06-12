---
title: "Does Ubuntu install grub to MBR by &quot;Default&quot;?"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2006-09-13
Hey folks!

I am currently arguing the statment that, "ubuntu installs grub to the MBR by default".

My experience is that it, in fact does NOT! The Desktop CD gives the user the option to install grub to the MBR, or NOT, correct?

---

### Post by aysiu on 2006-09-13
The Desktop CD does, in fact install Grub to the MBR by default--and not only by default, by necessity. It gives you no other option.

The Alternate CD, however, gives you a lot of choice about where to install Grub.

---

### Post by randell6564 on 2006-09-13
> **aysiu said:**
> The Desktop CD does, in fact install Grub to the MBR by default--and not only by default, by necessity. It gives you no other option.

The Alternate CD, however, gives you a lot of choice about where to install Grub.

then how come, when I am installing ubuntu, towards the end of the installation, I am notified that ubuntu sees another OS on my drive, and say's "if you are sure that this is the only OS on your drive, then it should be safe to install grub to the MBR"?

THAT is an OPTION! I was told that there IS NO option.

---

### Post by aysiu on 2006-09-13
Can you post a screenshot of this dialogue and what choices you are offered?

---

### Post by randell6564 on 2006-09-13
> **aysiu said:**
> Can you post a screenshot of this dialogue and what choices you are offered?
[http://www.linuxforums.org/forum/ubuntu-help/70403-need-able-select-ubuntu-windows.html](http://www.linuxforums.org/forum/ubuntu-help/70403-need-able-select-ubuntu-windows.html)

---

### Post by aysiu on 2006-09-13
Where was the screenshot?

---

### Post by randell6564 on 2006-09-13
> **aysiu said:**
> Where was the screenshot?
Not sure aysiu! I was just arguing with someone in another forum.

I have the official ubuntu desktop CD, and I in fact DO have an option as to wether grub gets installed to my MBR, or NOT.

---

### Post by aysiu on 2006-09-13
Well, all I know is that the Ubuntu Desktop CD I downloaded in June did not ask where you want Grub installed. I'm not sure if the official CDs are different from the original June 1 release.

---

### Post by randell6564 on 2006-09-13
> **aysiu said:**
> Well, all I know is that the Ubuntu Desktop CD I downloaded in June did not ask where you want Grub installed. I'm not sure if the official CDs are different from the original June 1 release.

It does not ask "WHERE you want grub installed". It asks wether you want to install grub to MBR, or NOT.

---

### Post by aysiu on 2006-09-13
So if you choose not to install Grub to the MBR, it won't install Grub at all...?

---

### Post by randell6564 on 2006-09-13
> **aysiu said:**
> So if you choose not to install Grub to the MBR, it won't install Grub at all...?

HA.,! I dont KNOW, I never chose any other way but to install to the MBR!

---

### Post by toasted on 2006-09-16
I would like to know this too, I am about to wipe my spare install of Ubuntu and reinstall it. I don't want it to install grub at all since its installed already and pointing to my regular Ubuntu install on another drive.... follow me? I really want no grub installed at all during this install of Ubuntu and I will add this fresh install to the menu for my primary.

So, do I need the alternate CD to do this? Will the alternate allow this? I would rather not take a chance with the Live CD if there is a chance to screw this up.

---

### Post by confused57 on 2006-09-16
> **toasted said:**
> I would like to know this too, I am about to wipe my spare install of Ubuntu and reinstall it. I don't want it to install grub at all since its installed already and pointing to my regular Ubuntu install on another drive.... follow me? I really want no grub installed at all during this install of Ubuntu and I will add this fresh install to the menu for my primary.

So, do I need the alternate CD to do this? Will the alternate allow this? I would rather not take a chance with the Live CD if there is a chance to screw this up.
The desktop cd doesn't give you any control of where to install grub.  You can choose where to install grub with the alternate cd, even to floppy:
[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

I'm not sure about not installing grub at all, here's an excellent link explaining grub:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There are links throughout the above site with some excellent installation information and configuring your system.

---

### Post by toasted on 2006-09-16
> **confused57 said:**
> The desktop cd doesn't give you any control of where to install grub.  You can choose where to install grub with the alternate cd, even to floppy:
[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

I'm not sure about not installing grub at all, here's an excellent link explaining grub:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There are links throughout this site with some excellent installation information and configuring your system.
Thanks, I never found that one!
So answer me this if you know....

If I choose to install grub to floppy, will this in anyway modify my existing MBR to point to the floppy? I hope that I would have to make sure boot order in bios was floppy first for this to work. If it does not modify MBR then I can simply add the new install to primary dapper install and forget about the floppy....   see what I mean?

---

### Post by confused57 on 2006-09-16
I've installed multiple Linux OS, by installing grub to the root partition of the Linux OS I'm installing...then add an entry to my main grub menu to boot to the root partition:

title    Dapper
rootnoverify (hd0,4)
chainloader +1

You'd need to designate whatever your root partition is...what happens is that you'll boot to the root partition of the OS from your main grub into the grub menu on the root partition.

I don't believe installing grub to floppy will affect your mbr, maybe someone else can clarify this.

---

### Post by samssf on 2006-09-16
This is news to me. I am very confused. I downloaded Ubuntu 6.06 a couple days ago and am plagued and not able to get it running.

When I install using the more advanced options (editing the partion tables myself.. and yes I know exactly how to set up the partition tables) The install never says ANYTHING about mbr or grub. When I finish the install, my system boots right back into windows.

I've installed like 5 times and have never seen anything about MBR

---

### Post by toasted on 2006-09-16
> **confused57 said:**
> I've installed multiple Linux OS, by installing grub to the root partition of the Linux OS I'm installing...then add an entry to my main grub menu to boot to the root partition:

title    Dapper
rootnoverify (hd0,4)
chainloader +1

You'd need to designate whatever your root partition is...what happens is that you'll boot to the root partition of the OS from your main grub into the grub menu on the root partition.

I don't believe installing grub to floppy will affect your mbr, maybe someone else can clarify this.

So then you keep hopping from grub to grub till it finds one that does not have a a'Forwarding Address' if you will. Then it boots...  I see what you are saying but I dont think I want to do that though... but thanks for the interesting idea!

---

### Post by randell6564 on 2006-09-16
> **samssf said:**
> This is news to me. I am very confused. I downloaded Ubuntu 6.06 a couple days ago and am plagued and not able to get it running.

When I install using the more advanced options (editing the partion tables myself.. and yes I know exactly how to set up the partition tables) The install never says ANYTHING about mbr or grub. When I finish the install, my system boots right back into windows.

I've installed like 5 times and have never seen anything about MBR

What kind of HD setup do you have?  I WAS wrong. I had it backwards in my OP. The Desktop Live CD does NOT offer any GRUB options, but the Alternate CD DOES!

The reason that I asked about HD setup is that if you are running an IDE along with a S-ATA device, and Windows is on your S-ATA then Ubuntu most likley put GRUB on the IDE because she might not recognize the [S-ATA]("http://linuxmafia.com/faq/Hardware/sata.html"), so Windows is still in charge of your MBR.

Otherwise, I see no reason that Ubuntu failed to write GRUB to MBR ,giving you a dual-boot option sinse it is done by default when there is an existing OS, correct?

---

### Post by samssf on 2006-09-16
Thank you for the reply.

My HDD setup is as follows:

2 120GB SATA HDD on RAID mirror array.

1 74GB Sata


When I install, the two 120s are listed as SDA and SDB.
My 74 gig is the SDC.

I have windows on the 74gig (SDC part #1)... and I want to dual boot to ubuntu (on SDC part 2)

I cant get this to work for the life of me. I get no dual boot option. Sometimes when I installed I just go straight into windows. The last time I installed, using the default options and letting ubuntu use free space on my 74 gig, I got "Operating System could not be found"

I think it is because when I first boot up my machine, the 74GB SATA is not my 3rd hdd.. its the first one. But linux sees it as #3...

any suggestions?

---

### Post by confused57 on 2006-09-16
> **toasted said:**
> So then you keep hopping from grub to grub till it finds one that does not have a a'Forwarding Address' if you will. Then it boots...  I see what you are saying but I dont think I want to do that though... but thanks for the interesting idea!

Maybe you could set up your new install the way I mentioned, once you boot into it, go into your /boot/grub/menu.lst(of the new install)...write down the exact entry to boot the root partition, then add the entry to your main grub menu, which should boot directly into the kernel(of the new install)...if it works, you could delete the chainloader method or keep it as  a backup.  I don't know, it should work...haven't tried it myself.
Thought I'd throw out this option, since no one else has responded.

---

### Post by toasted on 2006-09-16
I have a windows part in the mix too. 
The way I see it now (maybe im wrong)

When boot hits MBR it is directed to Grub on primary Ubuntu install. Boot occurs. 

Now if I install another Ubuntu then MBR will be changed and directed to the wrong grub (the new install) and in this case the MBR itself would have to be modified to point to the correct grub... the original primary install. Or I could install the path to the original install in the new grub menu.lst but I would rather keep it on the main install. 

Now, its also an option to back up my MBR and restore it after the new Ubuntu install but I would rather not go through all that. Not that its that big a deal.

I think the easiest way is to choose to install to floppy. That would give me the option of booting from floppy if needed, or if I just do not use the floppy then the MBR would still be pointed to the original grub... if thats the way it works. Somebody will know   :)

Thanks for the input regardless!!

---

