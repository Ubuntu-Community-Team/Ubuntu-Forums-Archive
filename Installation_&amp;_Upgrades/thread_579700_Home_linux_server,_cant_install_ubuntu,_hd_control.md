---
title: "Home linux server, cant install ubuntu, hd controller issue?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Snowmirage on 2007-10-18
I have worked in computer support for many years and am currently back in school working from my CCNA and a degree in general network administration.

I have been intruduced to the many possibilities of the linux world by friends and proffessors and wanted to experiment and get a feel for it by setting up a server at home to provide a lot of various features (eventually, file / print sharing, possibly routing , firewall, ect ect) not beacuse i need to but i want to know how it works and learn.

I initialy was going to install debian simply beacuse there seemed to be a lot of very very detailed guides over at aboutdebian.com explaining even the details that most linux users assume everyone knows.

I also tried ubuntu when that didnt work and have issues there too.


I'll try to be as detailed as I can but I have reinstalled and formated the drive 20 times over in the last 3 weeks or so.

PC setup

Abit BP6 motherboard dual 366 celeron CPUS
768 MB RAM
board has 2 ide channels + a IDE raid controller

I have no intention of using this onboard raid controller, long ago when I was using the PC for a windows server, I recall installing a bios revision that did not use the raid controller, I was under the impresion this would disable the raid controller

I would like to use my SATA PCI raid controller to eventually add in 2-4 sata drives to use the PC as a file server.

First I installed Debian

I did this via a net install CD, its only about 180MB or so, and it downloads the rest of the basic install and any needed packages via ftp, which works fine.  During this first install all that is in the PC, is 1 PCI NIC, 1 PCI video card, 1 8GB maxtor HD master on the primary IDE channel,  and a DVD drive slaved off that drive its the slave of the primary IDE channel.

Install goes fine only thing I was doing was disabling the install from getting an IP via DHCP with the command

linux netcfg/disable_dhcp=true    

the install seems to go just fine prompts for me to take out the CD then it restarts..   Then it booted i could log in install telnet all is well.

I power down the PC and back on ... and was getting an error to the effect of

Waiting for something(root? boot?) partition....

WARNING! /dev/hda1 does not exist dropping to shell

after searching for a week or so on google, and reading about I saw a lot of posts about people referances to hda change to sda or hde ect.

I was able to edit the grub loader ("e") on boot and edit one line references (i assume) where the OS is and changed it from hda1 to hde1

and the PC booted!

but again restart the PC and i get the same error but... "WARNING! /dev/hde1 doesnt exist"

I then tried ubuntu and that worked even less... after the install which went fine (again from a net install CD) i remove the CD and reboot, the the PC would freeze at verifying DMI pool.... well acctually it was after "booting from cd ..... failure" but if i disabled boot from CD, then it failed at verfying DMI pool...

tried writing ZERO's to the drive a few times and reinstalling and still I get the same thing.


I really cant for the life of me figure out whats going on...

I went back to Debian had the same issue with sometimes it would boot with hda1 and sometimes hde1..

I think I did see during a few of the boot ups it reference something about HTP386 or something to that effect that was the name of the On board IDE raid controller.  

So the only think I can think of is that sometimes linux is seeing that on board IDE controller, and sometimes its not.

If it boots and didnt see it then the primay master on the (my hard drive) would be assigned to hda1 

if it detected the raid card first i think that it would assign my hd to hde1..

Now after trying to install debian again after a few more tries with ubuntu I am now getting the freeze at verifying DMI pool even with debian now and then

Last night i was getting an error to the effect of 

Initializing ACPI, and something else (sorry i'll write this down and post when I get home cant remember it now it was a new error)

then after that hangs for a few min it again drops to a basic shell


I have seen posts asking for people to get grubs menu.lst? or some such file as well as a few others fstab? from thier PC's as a way to help trouble shoot.  Which they must get booting a live linux CD such as knoppix or what have you..

I have tried to do this and would have posted them but I cant even seem to be able to mount my drive after this issues occur when booting a live CD, but maybe im just missing something.

Sorry that I cant be much more detailed, but again im trying to start experimenting with linux for the first time.

Any help/advise you can provide would be most helpful

Thank you

Brandon

---

