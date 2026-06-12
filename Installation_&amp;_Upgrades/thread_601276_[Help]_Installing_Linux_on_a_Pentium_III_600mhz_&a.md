---
title: "[Help] Installing Linux on a Pentium III 600mhz &amp; 64mb Ram"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Kasa.Ramone on 2007-11-03
Dears users of this forum:
first excuse me if my english isn't the best, after all i'm argentinian, but maybe you can help me.
I've been trying to install diferent Distributions of linux and I'll had to say i got at least one problem with each one.
First of all I tried to install Fluxbuntu RC 7.10, but when installing the "base system" in the 6% it gets an error of corrupted file , but the md5 is Ok and the integrity of the cd too, well " I'll install Xubuntu , and if it works then if it goes slow i'll buy a Ram module for it". But same results.
I Tried With Debian Etch (XFCE & NetInstall)and also with Zenwalk and the same thing happened.
"Well, let's give it a try to Slackware.." I said, so i download Slackware 11, but it didn't boot, tried with Kwort 2.2 and the same thing (Feather linux gaves me the same result too).
I tried KateOS but it didn't boot correctly, Sam hungs up because of lack of ram (well that's what i want to suppose), Can't Install LunarLinux properly, I can run Vectorlinux 3.2 but it's a very old version and i can't support new VL because of the Requeriments, same for Slax.
I can't get in to the Installation menu of Fedora or Ubuntu to install the base system and then install fluxbox because it hungs up.(it gets some rare errors).
I really don't like Meta-distributions Like DSL or PuppyLinux.
I couldn't get AntiX boot properly, and neither Knoppix or Rule RH9 (based on Redhat9).
Just a few minutes ago I tried Wolvix cub but guess what, in loggin screen I type "root" & "toor" and it gets an error..
I'm running out of ideas(and distributions too), what do you recommend for this pc?.
There's any XFCE 4.4 or Enlightement distro that actually can Work on this pc?.
I'm just getting the idea that Tux hates me..

Yours Faithfully.

Kasa.ramone

Edit:
I leave you some info of my pc
HDD: 15.3Gb UDMA
Video: Sis620 Onboard
Processor: Pentium III 600mhz Katmai FSB 100
Mem Ram: 64mb DIMM pc100
Motherboard: Xcel2000 (M748LMRT)

---

### Post by digifan on 2007-11-03
> **Kasa.Ramone said:**
> 
I really don't like Meta-distributions Like DSL or PuppyLinux.
I couldn't get AntiX boot properly, and neither Knoppix or Rule RH9 (based on Redhat9).
Just a few minutes ago I tried Wolvix cub but guess what, in loggin screen I type "root" & "toor" and it gets an error..

I'm just getting the idea that Tux hates me..

Yours Faithfully.

Kasa.ramone

Edit:
I leave you some info of my pc
HDD: 15.3Gb UDMA
Video: Sis620 Onboard
Processor: Pentium III 600mhz Katmai FSB 100
Mem Ram: 64mb DIMM pc100
Motherboard: Xcel2000 (M748LMRT)

Hello Kasa.Ramone, Tux isn't hating you, your main problem is that the base memory is too low, for installing and using linux as a desktop environment with Ubuntu , Red Hat, Mandriva or SuSE you need at least 128Mb of internal memory which you have only half of.
You say you don't like to install DSL and the likes, but probably that's your best bet with your present configuration. DSL is very low on recources and will most likely run on your specs. Also graphics memory plays a big role, here 8Mb is as low as it get better is 16Mb on your machine.

My advice is install DSL just too see if it runs, if it does than try to find another 64Mb module of PC100 memory and try installing your favorite distro.

---

### Post by zvacet on 2007-11-03
You can install Xubuntu with alternate CD.

[http://www.xubuntu.org/get#gutsy]("http://www.xubuntu.org/get#gutsy")

---

### Post by digifan on 2007-11-03
> **zvacet said:**
> You can install Xubuntu with alternate CD.

[http://www.xubuntu.org/get#gutsy]("http://www.xubuntu.org/get#gutsy")

True zvacet, it's possible to install with alternate CD, but it will not run very well (and that's an understatement) .
Xubuntu recommend the following:

[quote=[URL="http://www.xubuntu.org/get#gutsy"]
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install.
The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu CAN run with 64 MB RAM, but it is strongly recommended to have at least 128 MB RAM.
[/quote]

---

### Post by Kasa.Ramone on 2007-11-03
I didn't try with the LiveCD , I get the error installing from the alternate CD (in low memory mode). Anyway I'll download DSL and see if it works, if you say that a memory module will fix my problems then i'll buy it.
If you have Debian 2.0 or 3.0 on your attic, and you want to hung it up on internet, then i will appreciate that.
What Distribution you recommend with Enlightement with 128mnb ram ?
If you know about a distribution with XFCE 4.4.1 that i haven't test with then please tell me.

---

### Post by zvacet on 2007-11-03
@ **digifan**

I know that,but he ask to install ubuntu with 64MB of RAM and I give him solution.

@ **Kasa.Ramone**

> if you say that a memory module will fix my problems then i'll buy it

Do that and install Xubuntu with alternate CD.

---

### Post by Herman on 2007-11-04
Hello everyone,
I am typing to you right now from my PC Chips 'Book PC', with a 400 mhz celeron CPU and 128 mb of PC100 RAM.

I only had 64 mb of RAM when I installed with the 'Alternate CD', in low memory mode, and I added another 64 mb later.

I actually performed this installation as a minimal install, just to demonstrate how to to that with the 'Alternate CD'. Actually, it would be easier to do as zvacet says and just install Xubuntu with the 'Alternate CD', you can always add the other desktops later.

The reason I did it the hard way was just to show people how that can be done. My new web-page about that is here: 
[Windows98SE+Ubuntu Gutsy Gibbon]("http://users.bigpond.net.au/hermanzone/p2.htm")  This example is based on the excellent Ubuntu Community Doc's How-to about [Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") - Install Ubuntu on older computers with low memory. It is claimed in that second link, that the 'Alternate CD' can be used to install in a computer with as little as 32 mb of memory! :)

I did find that Xubuntu was pretty slow at 64 mb of RAM, but it will run okay. Fluxbox or IceWM work much better when the computer only has 64 mb of RAM. 

128 mb of RAM is a lot better, I can run Xubuntu fairly well now and even Gnome desktop will run, but very slowly. Right now I'm logged into my IceWm desktop, I couldn't decide whether to log into Xubuntu or IceWM. IceWM is nice, I like it.
With a little more RAM I can run Gnome (Ubuntu) fairly well. I used to have more RAM than this but I gave some away to someone else who needed it.

It is really worth adding more RAM if you can get it. It's not as expensive now as it used to be back when some of these older computers were made. More RAM probably will make installing a lot easier and definitely everything after the installation is done will work a lot better.
Really, this computer I have is capable of handling 512 mb of RAM, and I'm hoping a freind of mine will bring me two 128 mb ram modules back from a trip to the city tomorrow. Then I'll be able to really make this little computer shake, rattle and roll! :)


I have one other tip for you too, Kasa.Ramone. 
When I have had a lot of trouble installing operating systems like you described, it turned out to have been caused by a dirty CD/DVD drive lens.
If you are able to, try to clean the lens in your optical drive with a Qtip (cotton bud), and some denatured alcohol (methylated spirits). Some CD drives have the lens that slides out with the CD drawer so it's easy to reach. Others have it built in and you have to take the machine apart to clean it. If you have the right tools and skills, it might be worthwhile to try that. I did and it worked for me. For most people it would be easier to buy a new CD/DVD drive, they are not too expensive these days and easy to change, depending on what kind of computer case you have.

Regards, Herman :)

---

### Post by Kasa.Ramone on 2007-11-04
I cleaned the lens of the CD-ROM Device but it's the same (well at least now it's clean), I got the same error:
In Xubuntu and Fluxbuntu i get error in "Loading additional Components; 23%"
In Debian,Zenwalk & MiniGuadalinex i get error in "Installing Base System; 6%"
And other distros have multiple problems (kwort and slack don't want to boot for example), i tried DSL but it Crashes on the screen after boot parameters ( it says DSL use it at your own risk and thats it, nothing else hapens.) in 4.0 & previous versions.
Otherwise I'm really considering to sell this pc and try to buy something better, because (in my country) for a new CD Device and get old ram it's the same in price that sell it and buy something , not "woow", but something newer that can get more compatibility & perfomance.
I Like that old pc, but i think there's no choice left.

Thanks to all, and if you know a way to get it working please tell me.

---

### Post by kagashe on 2007-11-06
I have a Desktop with only 32 MB RAM (not extendable) and I have Ubuntu 6.06 server+JWM on it. In addition I have DSL (frugal install) with Opera browser on it which works faster then on Ubuntu. I also use this desktop with Puppy Linux Live CD for playing audio CDs since Puppy could set up its Yamaha Sound Card. My thread on Ubuntu forums regarding this installation is [here.]("http://ubuntuforums.org/showthread.php?t=465029")

My first advice is don't try any Ubuntu after Dapper and go for server install (I hope you can setup the network with command line) and add the desktop (Fluxbox or JWM later). You can also try Fluxbuntu (based on Dapper) Live CD but after you have swap partition.

For any Live CD (except DSL) to work on your machine you need to have a SWAP of atleast 128 MB RAM. I could do this while Ubuntu Dapper server was installed. You can also try this, otherwise, use Gparted Live CD.

After you have SWAP, I recommend you go for Puppy Linux or Fluxbuntu 6.06.

Now coming to DSL Live CD:
Press F2 (then) F3 at boot prompt and have a look at various boot options. You can try the following:
dsl vga=normal (or dsl vga=769)
Note: I don't know whether they mean the same or not, but vga=769 is the least option.

I hope your system should boot into the DSL desktop (if not you can try lowram option as well).

After booting into the desktop, the first thing you should do is to setup a DOS swap file (I hope the files sytem must be fat32).

When swap is set up and being used you can setup the network (if it was dhcp DSL would have set it up automatically), click on Firefox and browse.

---

