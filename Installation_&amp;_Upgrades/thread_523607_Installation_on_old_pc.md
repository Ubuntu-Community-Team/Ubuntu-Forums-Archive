---
title: "Installation on old pc"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by questy_bin on 2007-08-12
Hi there,

I want to install ubuntu on my old system which already has WinXP working well.

My system has the following configuration
.
Pentium III-733MHz(Socket 370-Coppermine)
ASUS CUV4X mainboard with VIA chipset
192MB PC133 RAM
80GB Samsung HDD
ASUS RIVA TNT2 32MB Graphics Card.

I have only Ubuntu 7.04 live cd with me, and the system hangs(waits for more than 30mins) on booting from the cd directly before the desktop can load.

I tried with the following kernel options by putting them at the end of the existing options.

noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

My mouse works now, but still the desktop doesnt load up fully.

Are there any other things I shoudl try out ? Is it possible to do a complete text-based install using this Live CD.

Please help.

Thanks
Questy

---

### Post by Herman on 2007-08-12
Hello questy_bin,
You should be able to install Ubuntu okay in a computer like that. I have one here with a 400 Mhz Celeron CPU and 190 Mb of RAM, it's running Feisty Fawn just fine.
It used to have only 127 MB of RAM.for most of its life and it ran all the earlier editions of Ubuntu like that.
A lot depends on other design factors in the computer though, like how well matched everything is. Some computers with double the specs 'on paper' struggle to do as well in reality because they have a 'bottleneck' in their design somewhere, such as a lack of CPU cache capacity maybe. 

In any case, the trick to use the LiveCD for installing with (or for doing pretty much anything with, for that matter), is to have a Linux swap area made on the hard disk somewhere (like a page file), for the LiveCD to use in addition to all the RAM it can get. A 1.0 GB Linux swap area will be fine. You can make one of those with a [GParted -- LiveCD]("http://gparted.sourceforge.net/") first, as that is a liveCD with only a small operating system and a light desktop, so it doesn't need as much RAM as the Ubuntu LiveCD.
Any good Linux ('Parted based partitioner will do if you have something else on a CD already, like GParted or QTParted, etc. 
Avoid using partitioners made for Windows, they seem to cause a lot of problems.
I really think [GParted -- LiveCD]("http://gparted.sourceforge.net/") is the best. After you have a 1.0 GB swap area made, your LiveCD will work much better.

If you don't want to do that, another way is to use the 'Alternate' CD, see my first signature link for all the details you would ever want about that.

Either of those solutions should work, just do whichever seems easier for you. Probably for most people, the LiveCD would be a little simpler. It also has the migration assistant. I used it yesterday to install Ubuntu for a freind. It copied things like bookmarks and files into Ubuntu automatically. I was very impressed with that, I think it's great! :)

Regards, Herman :)

---

### Post by Jakob22 on 2007-08-12
I have also had the same problem, but not even on an "old" PC.  I can only use 6.06 on an 800Mhz computer; every other installation disc beyond that "hangs" even on the the newer 3.1 Ghz computer upon installation.

I've just burned 7.04 and it still hangs on each computer.

To predict responses, yes I've burned it on several different drives and several different discs.  The problem is not with my hardware.  I'm quite confused about why the installation hangs after a bit, never to be installed.

---

### Post by Pumalite on 2007-08-12
Post your specs. Let's see if we can help you.

---

### Post by Jakob22 on 2007-08-12
Both of my computers are "home built."  The one of immediate concern has these specs:

ECS k7VTA3 MB, 800Mhz AMD Duron, 256 MB RAM, 3Dfx VooDoo 3000 (yes it's old), HP 9100 CD reader.

It works fine with Ubuntu / XUbuntu 6.06; anything beyond that hangs the system upon installation of any newer version.

---

### Post by Pumalite on 2007-08-12
If you want a system that installs well and runs fast in your computer; then I would go with Xubuntu Alternate CD. For two reasons at this point: 256 MB RAM and possible graphical and hardware problems. Lets sort them at a time. First get the iso: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Do md5sum, burn at 4x, check CD for corruption before install and start installing, then report back with findings or questions.

---

### Post by questy_bin on 2007-08-13
Hi everyone,

I got my installation done. Thank You Herman for pointing out the swap fix.

I created and formatted a swap partition of 1GB using partition magic from WinXP and
passed that in as a boot paramter at the install and presto everything started working
well.

Here are the boot params I finally used.

noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 swap=/dev/hda6

I think it is time we looked into the boot process of the ubuntu Live CD. I am not sure
how to ping the ubuntu devs on this one. I subscribed to ubuntu-desktop, not much
activity there.

We need to primarily determine the total memory to start the live system and if that
much is not present we need to give the option to the user to resize and create a
swap before proceeding. I wouldnt think that is too difficult. I can help too, if some
dev can do a little hand holding.

Considering the fact that Fedora boots well on this system without any extra boot
params, we also need to spend a little time to research on how that can be fixed.

This is the same system that I had RHL6.1 installed and working well back in mid-2000.
and was my main PC till around 2003 with the latest RHL/Fedora distros.

Ubuntu being a new distro has its disadvantage, which needs to and can be fixed.

Thanks for all the help guys.

Regards
Questy.

---

### Post by A$h X on 2007-08-13
[FONT="Tahoma"]Hi questy, i'm suffering pretty much the same problems as you installing feisty fawn on a similar spec machine. I'd like to know how you setup the swap file in partition magic and the EXACT arguments you used in the ubuntu install menu. (I'm assuming you hit F6 then added the arguments). [/FONT]

---

### Post by questy_bin on 2007-08-14
create a partition of around 1GB and format with the type "Linux Swap". Find out what the drive hdX value is. If you dont know, take a screenshot of your disk structure on Partition Magic and upload it some place and attach the link, I could help you. In my case it was hda6.

The boot params I used are in my previous post.

---

### Post by stoodleysnow on 2007-08-14
Hello
I'm having problems installing Ubuntu 7.04 on an ancient Jetway 531CF, Super Socket 7 motherboard with AMD K6 550MHz and 256MB RAM, with inbuilt SIS Graphics (BIOS set to 8MB shared RAM) and a 20GB HDD.
It loads Windows 98 from the HDD without trouble, but booting from CD (I've tried a couple of drives ~ 48x) is excruciatingly slow. It takes 5 minutes just to get off 'Isolinux (C) 2005 (whoever that guy is - I forgot)'. Then I have to wait another 3 or 4 minutes for the boot options to appear. On selecting a boot option, it hangs. What gives?:confused:
PS The board had bad caps, so I recapped the board with equal rated caps. This shouldn't affect the CD without affecting the HDD, right? I mean, it POSTs OK, boots from HDD OK, just not CD.
??????????????????????????????????????????????????????????????????????????????
EDIT: Same problem with all Linux distros I have including Ubuntu 5.10, Kubuntu 6.06, Freespire, D-Small.

---

### Post by questy_bin on 2007-08-14
Read my earlier posts on how I installed Ubuntu 7.04 on my old PC, that should work in
most cases.

Or if these dont work, try Fedora (and Debian), seems to have better support on older systems.

I am sure that Red Hat 9 will work very well on that machine. But it is unfortunate
that RH recently announced that they no longer support it. And besides it is an ancient OS
so try it as only the last resort.

---

### Post by stoodleysnow on 2007-08-16
It's not just Ubuntu in particular. All my distros are getting stuck. I think it's to do with booting from CD, since RAM and swap size issues only usually surface after most of the Cd boot is complete. But on this machine it takes yonks just to get to the boot options selection screen. May be NTSP - not the same problem.
:(:confused:

---

### Post by stoodleysnow on 2007-10-26
bump...:confused:

---

### Post by Pumalite on 2007-10-26
Clean the lens in your burner, change your burner or try the CD's in a different computer.

---

### Post by stoodleysnow on 2007-10-29
"They work fine in my other computers", he replied with a sagely nod. "That was the first thing I did"
:)

---

