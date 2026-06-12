---
title: "pc wont boot live cd"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by tednugent on 2007-02-04
Just purchased a dell latitude c400 laptop with the intention of loading dapper drake.
I have ran the live cd on my desktop (gateway 505gr)and it works great. however when I try to run it on my laptop it will not work it either skips and goes into win xp (I have set the bios to boot from cd))or if I format the hardrive (no os installed) it says non system disk . I have tried the livecd,the alternate install,as well as knopix,and mepis.Mepis is the only one it will try to boot with. If anyone could help me with this problem it would be greatly apreciated. I have also downloaded  a new copy and tried it as well same result works fine on my other pc but not the dell c400.

---

### Post by Stephen Howard on 2007-02-04
On the basis of [these reports of other successful installations on a C400]("http://www.linux-on-laptops.com/dell.html"), I'm thinking that you might have a hardware problem with the laptop's cd-rom drive.  Alternatively, if you used the same cd-burner for all your tries, maybe that drive is the problem.

---

### Post by tednugent on 2007-02-04
I had thought maybe that could be the case however it reinstalled windows from cd (several times) and I used another pc for the ubuntu downloads also all other cds seem to work its been quite a puzzle. I picked this laptop because it seemed to be one that worked with ubuntu fairly well.:confused:

---

### Post by Stephen Howard on 2007-02-04
does it try to boot at all (ie any text on the screen)?  Or does the drive just click a few times while it tries to read?

---

### Post by tednugent on 2007-02-04
will not try at all,either jumps ahead to xp or when i dont have xp installed it tells me non system disk push f1 to retry or f2 for boot menu f1 repeats the process . It does seem to try to read the disk ,spins ,light blinks etc etc etc

---

### Post by tednugent on 2007-02-04
Just ran an old 2004 simply mepis live disk and it worked.Well at least as well as it ever did it was an old unstable version I still had lying around

---

### Post by tednugent on 2007-02-04
hoping someone out there can help me still having the same problem

---

### Post by Stephen Howard on 2007-02-05
It really does have the feel of an alignment problem on the cdrom.  Given the age of the laptop that's not surprising.

Assuming the cdrom is out of action, then the only way is to bootstrap the laptop using floppy disks and/or netboot.  Both can be a bit of an adventure, but basically they create a very basic setup on the laptop which you can use to install a full system using repositories on the internet or another PC.  I think I'd opt for a network based install using PXE - that is assuming the laptop has an option to boot from LAN.

Another option is to replace the cdrom - even temporarily swapping one out of another laptop just for the duration of the installation.

---

### Post by Stephen Howard on 2007-02-05
Here's a [link]("http://www.howtoforge.com/ubuntu_pxe_install_server") to a guy who has some clear instructions on setting up a pxe installation.  As I said, a bit of an adventure!  

If you succeed, let us all know.  Take lots of notes for an article!

---

### Post by tednugent on 2007-02-05
I,ll see if I can get a new cd drive but Why does every other cd work except ubuntu and knopixx. xp install loads, all music cds work, grub by itself works,I have loaded the newest mepis ,an old mepis,etc etc etc the only cd I have problems with is ubuntu it wont even recognise the disk in windows mode. it did load the disk screen 1 time could it be too slow?it is only a 24 x very puzzling I am downloading suse now to see if it will work. kind of a bummer I have been contimplating linux for a few years now and ubuntu seems to be the one I like oh well Ill try suse for now as Im not to fond of mepis,not sure why I dont like it just prefer ubuntu. Thanks so much for everyones help.

---

### Post by tednugent on 2007-02-05
just loaded suse linux live cd also I guess ubuntu wasnt meant to be.

---

### Post by tednugent on 2007-02-14
just letting anyone else who may have this problem know I burned a dvd install (not cd) and it worked great. all functions seem to work wireless card hibernate etc etc etc

---

