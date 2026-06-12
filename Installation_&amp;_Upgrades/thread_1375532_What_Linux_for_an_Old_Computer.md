---
title: "What Linux for an Old Computer???"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by SchizmWolf on 2010-01-08
Hey all. My buddy's got a really, really old computer that he asked me to put Linux on. He has had some limited experience with Kubuntu on another machine, and wants something with the intuitiveness of Ubuntu that will actually run. I don't know much about the machine because the Windows on it is completely borked and won't let me execute any commands. All i know is that it has roughly a .5 ghz processor, 512 kb cache, and it's got a pentium three processor on a BIOS dated at 1999. I'm trying to put Xubuntu Hardy 8.1 on it, but so far it's been less than successful. We've tried PuppyLinux on it and it was fantastic, except he complained that it was too difficult to interact with, and he didn't like the idea of having to boot from disk/USB every time. So, what I'm looking for is:
1)A small distro that uses very, very little RAM
2)Something that has a new-user-friendly interface
3)Something a Windows user could use without much experience.
4) Something you can install without needing a bootdisk/cd.
Is there any distro out there that will suit those needs, and where could I get them????

---

### Post by Bartender on 2010-01-08
Puppy can be installed to the HDD.

That doesn't solve the problem of course, but facts is facts.  Kubuntu's and Ubuntu's "user-friendliness" comes from having a full-featured desktop environment.  The lighter you try to go, the less point-and-clicky it's going to be.

So you're being pulled in two different directions, and it's hard to say where the balance point might be.  Maybe Ubuntu, but using the Xfce or LXDE desktop?  Xfce is Xubuntu.  I believe there are people working on a "Lubuntu" offering, which would be LXDE, but for now I think it's a roll-yer-own type of deal...

---

### Post by SecretCode on 2010-01-08
It would help to know the amount of RAM. If he can boot Puppy, entering
```
free
```
in a terminal window should reveal the truth.

Puppy is the most click-friendly of the very small distros I've played with, DSL somewhat less so, and Tiny Core pretty much unfriendly!

However, the DE on the PartedMagic recovery CD is smooth. It uses the OpenBox window manager. I'm not sure if there's a similar general-purpose distro.

---

### Post by cgroza on 2010-01-08
well, if your friend has 128 mb of ram MEPISLite should run acceptable on this pc with a few megs of swap.

---

### Post by SchizmWolf on 2010-01-09
> **SecretCode said:**
> It would help to know the amount of RAM. If he can boot Puppy, entering
```
free
```in a terminal window should reveal the truth.

Puppy is the most click-friendly of the very small distros I've played with, DSL somewhat less so, and Tiny Core pretty much unfriendly!

However, the DE on the PartedMagic recovery CD is smooth. It uses the OpenBox window manager. I'm not sure if there's a similar general-purpose distro.

I did that. I don't know which numbers I should use, but I *think* it's in bad shape. I'll try my best to transcribe what's on his computer into this:
```

#free
                 total            used               free           shared      buffers
 Mem:                189612        185244            4368               0        33020
Swap:             0                  0                  0                 
 Total:        189612        185244            4368

```Is it seriously telling me i've only got appx. 190 kB of RAM to work with, or am I being stupid?

In any case, I would still like a link to further instructions on how to install puppy to the HDD. It might just be the fact that I've slept for perhaps 6 hours over the last 3 days trying to get three operating systems up and running, but it seems like every time I google for a howto article it always brings me back to "How NOT to intstall Puppy Linux."

---

### Post by vinnywright on 2010-01-09
I think that's aprox.190Mb I'm riting this from a old presario 2100 and I get same

> guest@guest-laptop:~/Desktop$ free
             total       used       free     shared    buffers     cached
Mem:        184988     179484       5504          0       4088      53952
-/+ buffers/cache:     121444      63544
Swap:      1172736      76920    1095816
guest@guest-laptop:~/Desktop$ 


with abought a 600MHz CPU and it runs Xubuntu fine in fact I just let it upgrade it's self to 9.10 today and it's runing even better. :)

you say you were unsecsesfull ?? what was the prob?

VINNY

---

### Post by SchizmWolf on 2010-01-09
> **vinnywright said:**
> I think that's aprox.190Mb I'm riting this from a old presario 2100 and I get same



with abought a 600MHz CPU and it runs Xubuntu fine in fact I just let it upgrade it's self to 9.10 today and it's runing even better. :)

you say you were unsecsesfull ?? what was the prob?

VINNY
 
Well, i have tried both the Normal install and the Safe Graphics install, using two disks burnt seperately. First, they're super slow, but they work. When the get to "detecting hardware" after step 7 of configuration (15%) it hangs forever. Well, with one. The other one hangs at 53% forever.

---

### Post by arvevans on 2010-01-09
I tried several stripped-down Linux distributions for a similar situation (700 MHz Celeron, 128 MB RAM, 4 GB HD).  All came up lacking, including a very stripped version of Ubuntu.  Finally I tried a basic Debian install. 

[INDENT] [http://www.debian.org/releases/stable/i386/ch02s05.html.en](http://www.debian.org/releases/stable/i386/ch02s05.html.en)[/INDENT]

This link claims you only need 40 MB or RAM and 500 MB of HD.  In actuality it is a bit more, but still within reason for older machines.

Running Debian on older machines will require that you live with a slow boot time (up to 10 minutes), but once booted and a window manager running, it is reasonably fast.  Of course larger applications (Firefox, etc.) may use up most of your available RAM and spill over into swap.  So, be generous with the swap assignment.  Try to use the lightweight equivalents of browsers, word processors, etc; where possible.  
There are smaller and faster window managers than traditional Xorg.  You might want to look into what they offer, and see if they might be adequate.

This could probably be a wake-up call for future Ubuntu (and other distro) developers.  The basic Debian OS runs fast, where others seem to have overloaded features that use a lot of processing power and a lot of memory.  Rather than require us to purchase bigger and faster computers every new OS release, there could possibly be some effort to make kernal module loading _and unloading_ a more dynamic process, and during installation only load those modules that are really required for what the user wants his/her computer to do (IMHO).  Alternatively, it might work to make a simple GUI for helping the user build and compile and install a custom kernal that is more in line with his/her actual needs.

---

### Post by vinnywright on 2010-01-09
you may want to prepartition the drive and have some swap space avalable to use .
when I did this old puppy I first partitiond the drive it's onley a 20Gig so I just cut out about 1 Gig for swap and the rest ext3 for/
Then fired up the cd live and made shure the swap was in use and then did the install.

it was slow as heck runing live but it did install.

VINNY

---

### Post by SchizmWolf on 2010-01-09
> **vinnywright said:**
> you may want to prepartition the drive and have some swap space avalable to use .
when I did this old puppy I first partitiond the drive it's onley a 20Gig so I just cut out about 1 Gig for swap and the rest ext3 for/
Then fired up the cd live and made shure the swap was in use and then did the install.

it was slow as heck runing live but it did install.

VINNY

mkay.i've never manually partitioned a harddrive before. this computer does'nt have internet access and it's current OS is too corrupted to fix. How would I go about doing this? I'm pretty noobish with a lot of things still, i've only just started using linux within the last month or so. I have no idea how to set up swap space xD but this thing has 80gB HDD in it.

---

### Post by vinnywright on 2010-01-09
well 80Gig nice.......first get a gparted livecd for the partitioning 

I assume sence you sead you tryed the xubuntu8.1 cd you have a way to get them.

use Gparted to first blank the drive by removing/deleting eney partitions
now make 1 1-2Gig partition for swap then a 6-10Gig partition for/ and the rest for /home formating root/ and /home ext3.

then fire up the xubuntu cd and start it live......check to see that swap is mounted (it should be) if not do 

> sudo swapon -a

then start the installer at the partitioning part chose manual and point it to the partition's you made and set the mountpoints acordingley.

VINNY

---

### Post by lostinxlation on 2010-01-09
> **SchizmWolf said:**
> I did that. I don't know which numbers I should use, but I *think* it's in bad shape. I'll try my best to transcribe what's on his computer into this:
```

#free
                 total            used               free           shared      buffers
 Mem:                189612        185244            4368               0        33020
Swap:             0                  0                  0                 
 Total:        189612        185244            4368

```Is it seriously telling me i've only got appx. 190 kB of RAM to work with, or am I being stupid?
 
In any case, I would still like a link to further instructions on how to install puppy to the HDD. It might just be the fact that I've slept for perhaps 6 hours over the last 3 days trying to get three operating systems up and running, but it seems like every time I google for a howto article it always brings me back to "How NOT to intstall Puppy Linux."
 
I have a puppy on my 300MHz+128MB machine and it takes only 50MB when idling.
Xubuntu would be too heavy for 500MHz/180MB machine(I have a machine with similar spec that I installed Xubuntu and I know it's quite slow). 
Go with Puppy.
 
Installing puppy is quite simple. You click on "install" icon, select "Full installation" and specify the partition to install the OS to. Try it once to see how it goes.
 
Your challenge is more on partitioning/formatting. Try LiveCD to run Gparted to partition/format the HDD. If it doesn't work due to CPU power or memory space, there are other ways to try too.
 
IF you don't know how to partition/format with Gparted, go to Youtube and search Gparted. YOu can find tutorials.
 
 
By the way, there are some reports that say the latest kernel of Puppy isn't friendly to old machines and it is recommended to get the retro kernel. I'm using Puppy 4.3.1 K2.6.21.7(retro kernel) for my 10 year old laptop.
[ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/special-puppies/](ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/special-puppies/)
[]("ftp://ibiblio.org/pub/linux/distributions/puppylinux/puppy-4.3.1/special-puppies/pup-431-k2.6.21.7-scsi-intel_modems.iso")

---

### Post by rahilm on 2010-01-09
puppy should (and will) work in my opinion..
other than that there is lubuntu

---

### Post by the8thstar on 2010-01-09
Try CrunchBang Linux (Ubuntu + Openbox) [http://crunchbanglinux.org/]("http://crunchbanglinux.org/") or Elive (Debian + Enlightenment 17) [http://www.elivecd.org/]("http://www.elivecd.org/").

Both can run on a small specs computer and provide nice GUIs.

---

### Post by Darce on 2010-01-09
+1 for Puppy.

Tried K/L/Ubuntu on an old 600Mhz PIII 196Mb Laptop. Ubuntu & Kubuntu were useless. Completely unable to perform any tasks one the OS had ( finally ) loaded. Lubuntu was OK 'till you tried to do anything.

Puppy on the other hand runs well and makes the previous Win98 install feel SOOOO slow.
Great OS for older PC's and plenty of install options for the PC's without boot from CD/USB.

Cheers,

Tim

---

### Post by greenfrog on 2010-01-09
Look at wattOS, it is designed for older computers.

---

### Post by mkvnmtr on 2010-01-09
In a virtual box i have  a Ubuntu minimal install of 9.10 with the fluxbox window manager. I started with 300 Mb or ram but quickly saw that I could reduce it to 200 Mb. It runs fine and normally runs the package manager with less that 60 MB. With Firefox it gets to about 100 Mb. A basic install like that should work on your machine if you do not mind the command line install.

---

### Post by wandalalakers on 2010-01-09
Another +1 for puppy!
Especially for a PC with 128mb.

---

### Post by SchizmWolf on 2010-01-09
Thanks for all the help, guys! After reading your comments and dinking around a bit, I think I've come to a decision. I will manuall partition the drive with the gparted liveCD, try Xubuntu one last time (sorry, it's what I started on, I'm most familiar with it x3) and if that doesn't work, I'm going to put Puppy on it and tell my friend he's going to have to learn the command line. I will too, obviously, but that might be a task for another time.

Also, I think I am going to take a look at other small OS like MEPISLite and wattOS. I'd never heard of them, but I like the experience I'm getting with all these different flavors.

---

### Post by raymondh on 2010-01-09
My new favorite for low-spec/older machines is MASONUX ... developed by forum-member EARTHPIGG.

---

### Post by SchizmWolf on 2010-01-09
Just as a sidenote, what do you guys think of trying to put the new Lubuntu Lucid beta on there? from what I've read Lubuntu is much smaller, faster, and capable than Xubuntu on low-spec systems.

---

### Post by jkinney23 on 2010-02-04
i have been putting vector linux light on pentium 3's with processors from 400MHz to 600MHz and 256 MB Ram - it runs great and everything works right away.  xubuntu, besides running like a pig, did not pickup ISA sound automatically for instance.  i haven't tried, but vector light should run with 64 MB ram.

---

### Post by pkm4o93 on 2010-02-04
I too found puppylinux extremely fast. I tryed XFCE but found LXDE much faster. For awhile I gave up and used terminal and gnu-screen.  I use 9.04 with LXDE on my 555mhz VIA 4watt mini itx(old wyse thin client)

---

