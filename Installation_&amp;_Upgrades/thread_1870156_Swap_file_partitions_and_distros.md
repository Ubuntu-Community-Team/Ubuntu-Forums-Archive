---
title: "Swap file partitions and distros"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by rmcellig on 2011-10-26
I am planning on creating about 10 partitions on my test laptop so that I can try out various distros. Does each partition have to have it's own swap file or can I just create one swap file? I'm a bit confused. Because I want to learn more about Linux and try the different distros out there, is this the right way to go about it? Let's just say that I want to continue to educate myself with whats out there. I want to run the distros natively and not from Virtualbox.

---

### Post by zvacet on 2011-10-27
One swap partition is enough,because you will always run just one distro at the time. :D I don't konw how smart it is to install several distros  right now.Try with one and when you get familiar with it go to another if you want to explore linux distros.But tha,t is just my opinion.In short you can make 10 partitions if they are part of extended partition,because if you use primary you can not get more then 4 partitions.

---

### Post by rmcellig on 2011-10-27
I have all eight of my partitions set up. So far I installed Linux Mint 11 snd Zorin 5.1. Any suggestions for other distros I could take a look at that you have used? I already have Ubuntu 11.10. I am more after distros that are easy to install/maintain and that work well.

Keep in mind that this is my test laptop so I am trying to learn as much as I can about Linux by just doing. Lot's of fun! Hardly on my iMac anymore.

---

### Post by Lars Noodén on 2011-10-27
You should look at Fedora and Slackware, too.

---

### Post by rmcellig on 2011-10-27
I have Fedora 15 on CD. I have never tried Slackware. Will give it a try as well. Thanks!! I might even install Linux Puppy again although I know it is mainly for a usb stick or CD boot situation.

---

### Post by Lars Noodén on 2011-10-27
> **rmcellig said:**
> I might even install Linux Puppy again although I know it is mainly for a usb stick or CD boot situation.

Puppy's useful for very old or underpowered systems.

---

### Post by satanselbow on 2011-10-27
I did try that one time (having loadsa distros installed to check out on individual partitions) but quickly found that some distros only get about 30 seconds of my time (thinking openSuse here) before I dump then and vow never to return... made setting up all the partitions a bit of a wasted effort.

Likewise any test distro I found interesting got a fair chunk more of my time - which leaves X other distros sitting there rapidly going out of date and requiring mission critical updates when I do eventually have a look - which occasionally ended in breakage :(

Fedora should defo be on the list and if you are feeling a tad braver Arch Linux is excellent all round... never played with Gentoo so do let me know :D

The proliferation of liveCDs makes superhuman partitioning schemes pretty redundant anyway - IMHO.

---

### Post by rmcellig on 2011-10-27
Thanks for the comments! This is so much fun using both of my laptops for testing purposes. I just created my first 2GB USB bootable stick using Puppy Linux. Really cool stuff. I am learning more every day and one thing I am definitely learning is that you can do way more with Linux than you can with Macs or Windows. I use my iMac about 20% of the time now.

---

### Post by satanselbow on 2011-10-27
> **rmcellig said:**
> I use my iMac about 20% of the time now.

Well it must be about 80% ready for an Ubuntu installation on it then :popcorn:

---

### Post by cbowman57 on 2011-10-27
Just wanted to second the vote for Arch, if you want to learn linux it is a good way to start.

I've been trying out linux for about 15 years from time-to-time but once I started using it full time my progression was basically as follows (with other distros tested along the way):

Linux Mint
Ubuntu
LMDE (Linux Mint Debian)
Debian
Arch

Fedora & OpenSuse were easy to setup & run but they didn't keep my interest. Slackware is a beast that really isn't made to cooperate with Gnome but it wll also force you to learn linux.

---

### Post by oldfred on 2011-10-27
You need to keep track of which system is the "master" or the one with the boot loader in the MBR. Ubuntu is one of the worst as it does not offer the option not to install grub2's boot loader, but is the best as its os-prober finds just about every other system.

If you have a system with grub legacy just install it to its / (root) partition. You can add chainload entries from 40_custom to boot then. 
I understand Fedora defaults to a separte /boot which it needs as its main install becomes a LVM. But you can force it just to install to a partition which some have suggested.

Add labels to every partition so you know what is where. And learn about boot info script. I run it before and after every install so I know what is installed where and how it is booting. Helps document system in case of major issues you have full partition layout.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by ratcheer on 2011-10-27
> **cbowman57 said:**
> Just wanted to second the vote for Arch, if you want to learn linux it is a good way to start.
.

I will "third" that. As a second distro, I have stuck with Arch longer than just about anything else I have tried. It really helps you get down into Linux and it is pretty "cutting edge". Arch is a really nice distro.

Tim

---

### Post by rmcellig on 2011-10-27
Speaking of Slackware, how the heck do you install it? I downloaded the iso file (S13.37d2) and burned it to a CD. I don't think it is a live CD though. Is there a live CD of Slackware I can boot from to install it? Maybe there is a video on youtube. I'll check. Right now I am trying out Zorin 5.1 and really like it.

---

### Post by zvacet on 2011-10-27
You can try Sabayon also.It is Gentoo based distro.

---

### Post by cbowman57 on 2011-10-27
A **warning** about Sabayon (possibly Gentoo)

The last time I tried to install Sabayon on a disk with multiple partitions (8-9) it corrupted my entire hard drive.  Quite possible it as an error on my part but it's the only time it's happened to me in over a decade.  Just wanted to inform you of the possibility of that if you decide to try it on a drive formatted as you described.

---

### Post by zvacet on 2011-10-28
If you feel like it try PCLOS.See [http://www.pclinuxos.com/](http://www.pclinuxos.com/)

---

### Post by rmcellig on 2011-10-28
I installed pclinuxos full Monty. It has everything but the kitchen sink and takes a long time to boot into. Does anybody know what bootloader it uses? It looks so clean and well organized.

---

### Post by andrew.46 on 2011-10-28
> **rmcellig said:**
> Speaking of Slackware, how the heck do you install it? 

The installation details are here:

[http://slackware.osuosl.org/slackware-13.37/Slackware-HOWTO](http://slackware.osuosl.org/slackware-13.37/Slackware-HOWTO)

and I would personally recommend that you download the dvd version rather than cds, this way you get the source + slackbuilds as well as the packages.

---

### Post by rmcellig on 2011-10-28
Thanks andrew.46. I will give it  try.

---

### Post by satanselbow on 2011-10-28
I'm getting that tingly "must try more distros" feeling again... bad monkey! bad bad monkey!

!# (crunchbang) is pretty cool for a lightweight debian/xfce experience ;)

---

### Post by critin on 2011-10-28
> **rmcellig said:**
>  Any suggestions for other distros I could take a look at that you have used? I already have Ubuntu 11.10. I am more after distros that are easy to install/maintain and that work well.

Keep in mind that this is my test laptop so I am trying to learn as much as I can about Linux by just doing. Lot's of fun! Hardly on my iMac anymore.

Take a look at AriOS.  Easy and works well for me.

---

### Post by zvacet on 2011-10-28
You can give a try to [Pardus.]("http://www.pardus.org.tr/en")

---

