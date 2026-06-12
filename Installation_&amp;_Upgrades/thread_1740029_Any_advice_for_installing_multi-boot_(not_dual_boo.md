---
title: "Any advice for installing multi-boot (not dual boot)"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by leon_chame on 2011-04-26
Hello All,

This is not essentially an ubuntu question but figured I would try here as I imagine someone here has done similar and because of the great advice I always get here...

I have a laptop I want to install many OSs on.  Does anyone know of a link or two where I can go for help on partitioning my hard drive?

Ideally I want to put:

Windows7
XUbuntu
Ubuntu
Fedora
CentOS
Slackware

all on the same laptop (it has lots of space)...and boot into one or the other.  Believe me pls in advance I have my reasons for this and not going the VM route.  I have done dual boot many times, but never more than that...Ive even read some that only 3 OSs can exist but others have claimed to 5 on their boot....but Ive only found basic help so far via google and no real advice on how to partition this drive and any gotchas (for example with grub updates, shared /home etc....)  

Anyone have any info to pass to help me please?

Thanks!

---

### Post by scottykal12 on 2011-04-26
Download Gparted live ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) and partition you're hard drive. I don't know much about have more than 2 OS on a system since I only have 2 on mine, but i assume you just need to install one at a time (choosing a partition for each system) and I assume that would work. 

From what i have learned windows should be installed first to make it easier.

Hope this helps 
-Scott

P.S. Don't know if you need it but here is how to use Gparted live [http://www.youtube.com/watch?v=-sq3PBzplYg](http://www.youtube.com/watch?v=-sq3PBzplYg)

---

### Post by Dutch70 on 2011-04-26
Install windows into a primary partition first. You can only have 4 primary partitions. Then create an extended partition for your linux OS's. You can have just about as many logical partitions in an extended prtn as you want, but the extended counts as 1 of your 4 primary's. 

There are a too many issues that arise with a shared /home prtn for each Linux OS. I'ts best to keep /home in the same prtn as / and have a data prtn, create folders inside it & symlink them to your home folder. Too many options for me to give them all to you. 

You only need one prtn for swap...equal to or slightly larger than your physical RAM.

Here is a pic of one of my hdd's for a visual reference.

---

### Post by leon_chame on 2011-04-26
Thanks Dutch...right along lines for what I was looking for in terms of advice...

three other questions?

1. I am assuming from your screenshot you have all the OS set to use a shared swap..correct?
2. I didnt see a grub partition..am I missing something...did you have to edit your grub manually or do each time via updates with the multi OS?
3. Did you ever find a good resource (url/website) with info that talks about this?

---

### Post by Dutch70 on 2011-04-26
1. yes that is correct, 1 swap prtn they will pick it up on their own during install. How sweet is that!!! 

2. That's right, there is no grub or /boot partition. That just overcomplicates things. Grub will be in whichever system you install last. If you want to move it, it's only 2 commands.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

If you want to tweak grub..install Grub Customizer form the repo's.


3. links, for what exactly? if you mean for multi booting, I found a bunch, none that I can think of that made an impact.

---

### Post by oldfred on 2011-04-26
The main issue is keeping track of which boot loader is in charge. Most installs give you a choice of where to install the bootloader. Ubuntu does not offer the choice of none. If the install uses old grub legacy install it to the PBR - partition boot sector that you install the system. It adds chainload as another way to boot. Grub2 does like like to install to the PBR, just MBR. Install Ubuntu last, or have Ubuntu liveCD handy to reinstall grub2's boot loader.

Since converting to grub2 this does not apply but does show the partition planning required. I do not recommend grub legacy any more.
chainboot 145 systems - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

You just do this over & over for every install.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by leon_chame on 2011-04-29
Thanks all!!!!

Got my systems up and going!

Thanks again!!!

---

### Post by Dutch70 on 2011-04-30
Well it took ya long enough :wink: lol j/k

Glad to hear you got it going. 

So, just curious... what systems did you end up installing?

---

### Post by walt.smith1960 on 2011-04-30
Here is one option for booting as many operating systems as you like.  I use the older program(BootItNG), haven't tried the new one. It's paid shareware but bypasses the 4 partition limit and works pretty well for partitioning disks as well. As oldfred mentions, you have to be careful where each OS puts its boot loader.  The boot loader has to be placed in the partition, not the MBR or it will overwrite the Extended MBR that BootIT uses to keep track of partitions.

[http://www.terabyteunlimited.com/bootit-bare-metal.htm](http://www.terabyteunlimited.com/bootit-bare-metal.htm)

---

