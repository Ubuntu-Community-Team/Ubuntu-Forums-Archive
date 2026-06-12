---
title: "Can't install on Compaq Presario 1245 Laptop"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by Nathyn on 2005-07-20
Someone else had my same, identical problem in this thread:
[http://ubuntuforums.org/archive/index.php/t-29223.html](http://ubuntuforums.org/archive/index.php/t-29223.html)

The CD was burned properly (I checked it), my processor is an AMD K-6 3D (which I'm pretty sure is a 32-bit processor, not 64-bit).

I have 32 MB of RAM, so it runs in low-memory mode. If I try the default install, it goes through.. It installs the CD rom drive... Then, when it starts installing additional components for the Ubuntu installer, and it gets to the file 'nic-extra-modules-2.6.10-5-386-di' it does a crash loop. In other words, the screen goes black, it tries to load the file, then the screen goes black again, and it tries to load the file, repeating the crash loop forever.

If I try to do the expert setup, when it gets to that file, it goes back to the expert menu again. No matter how many times I try it again, or other parts of the install, it won't install the additional components.

EDIT: I played around with expert mode and found that it wasn't installing some important  modules properly. I THINK that's the problem, but I don't know what to do.

The modules it wouldn't load are:
ide-mod (Linux IDE driver)
ide-probe-mod (Linux IDE probe driver)
ide-detect (Linux IDE detection)
ide-floppy (Linux IDE floppy)

That's the problem, I think. It can't detect the CD rom or HD... While I was playing with it, I was wondering if it was unpacking to the memory, because I noticed in expert mode that if I added all of the optional components, it crashed BEFORE it got to nic-extra-modules-2.6.10-5-386-di.

Also, more information: I already DID format my HD, in case you're wondering. So, there's plenty of space for Ubuntu.

I'll try the AMD version of Hoary Hedgehog, as well as Warty Warthog tomorrow.

---

### Post by Nathyn on 2005-07-21
Anyone?? :-?

EDIT: I didn't realize Compaq was owned by HP. But I just checked and my laptop was made in 1999, before Compaq merged with HP. So, the HP version of Ubuntu probably wouldn't work, would it?

Basically, I think that the problem is that it can't install the IDE drivers, then tries to unpack the installer into the memory. With only 32 MB of RAM, that runs out really quick and causes a crash loop. I have some memory chips laying around the house, so I can upgrade the RAM to at least 128 MB, but that still won't solve the problem.

I need the Linux drivers for the laptop's integrated HD and CD rom drive. Anyone know where I can find that?

HP only has Windows drivers on their website.

---

### Post by uniko on 2005-07-21
I think it might help you a lot adding more memory. Installer basically at that point AFAIK doesn't write anything to disk as it isn't partitioned yet nor have created any filesystems. I think it uses RAMDISK (as using RAM) for anything until it gets to point of actually installing packages to disk. You shouldn't need hd or cd-rom drivers for your laptop and I don't think there is any available. Try adding more memory if you can and report back.

---

### Post by Nathyn on 2005-07-21
[QUOTE=uniko]I think it might help you a lot adding more memory. Installer basically at that point AFAIK doesn't write anything to disk as it isn't partitioned yet nor have created any filesystems. I think it uses RAMDISK (as using RAM) for anything until it gets to point of actually installing packages to disk. You shouldn't need hd or cd-rom drivers for your laptop and I don't think there is any available. Try adding more memory if you can and report back.[/QUOTE]
Actually, I just looked.. I didn't realize that laptop RAM chips were smaller than PC RAM. I've got several RAM chips, but none of 'em are for a laptop. :|

Do you think it's possible to do a server install of Ubuntu (just the Linux base, no fancy GUI), then setup a swap area, and load the GUI and all that other stuff into Ubuntu's server install?

---

### Post by Nathyn on 2005-07-21
Yeah, I talked to a friend of mine whose a Linux user and he told me to just re-burn the CD. I did, but I had the same problem. So, he had screw Ubuntu and to just switch to Damnsmalllinux.

By the way, Ubuntu's tech support totally sucks ass. On the IRC channel for a few hours yesterday, no one could help me. People often didn't answer.. I said one guy's name a couple times, and he reprimanded me for "bothering specific people."

After they couldn't help me, he said something about me adding myself to the users' list.. I didn't know WTF he was talking about, so I came here, and THIS. I have to bump my thread to get a single response.

And even then, it's just somebody telling me to upgrade my RAM. Jesus. Frickin' horrible.

---

### Post by geekdreams on 2005-08-12
[QUOTE=Nathyn]Yeah, I talked to a friend of mine whose a Linux user and he told me to just re-burn the CD. I did, but I had the same problem. So, he had screw Ubuntu and to just switch to Damnsmalllinux.

By the way, Ubuntu's tech support totally sucks ass. On the IRC channel for a few hours yesterday, no one could help me. People often didn't answer.. I said one guy's name a couple times, and he reprimanded me for "bothering specific people."

After they couldn't help me, he said something about me adding myself to the users' list.. I didn't know WTF he was talking about, so I came here, and THIS. I have to bump my thread to get a single response.

And even then, it's just somebody telling me to upgrade my RAM. Jesus. Frickin' horrible.[/QUOTE]
 I have the same system and I'm pretty disappointed that I can't get even a minimal install (server) of Ubuntu on it. :-/

---

### Post by Blackie_Chan on 2005-10-12
I had the same problem, and them after googling I found: [http://ubuntuforums.org/archive/index.php/t-1022.html](http://ubuntuforums.org/archive/index.php/t-1022.html)

By the way, the specs of the machine I'm installing it on is AMD 300MHz, 32 MB Ram, 2MB VRam and 4 GB of space.

Here's a how I got around the problem:

**1. Create a swap partition**
I got the computer with windows 98 on it, so I installed Partition Magic 7 on it. Using Partition Magic, I resized the partition, and created 2 new partitions (1 Linux ext partition and another Linux swap partition).

At this point, I put hal91 on a floppy (as suggested on a post in a link above), booted off the floppy and the ran ```
fdisk -l
``` which told me that my linux swap partition was on /dev/hda5

I exited, removed the floppy, and booted from the Ubuntu linux CD. 

**2. Use the swap partition in installation**
I followed step 1 in [http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)  then after I got to some screen where it loaded drivers for my CD Rom, I pressed ALT + F2 to get to the ash shell, then I ran the following:
```
mkswap /dev/hda5
swapon /dev/hda5
```

I exited, then I pressed ALT + F1, to get back to the installation wizard.

**3. Continue Installing....**

At this point, installation continued with no problems.

---

### Post by kalel on 2006-01-14
I' use the same machine but i have 160mb ram :)

---

