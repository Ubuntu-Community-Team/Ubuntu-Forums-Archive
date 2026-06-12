---
title: "Ubuntu 32 bit X86 on vista as virtual PC"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by John_Q on 2008-10-31
I am trying to run the ISO of ubuntu 32 bit on a virtual PC maintained on a vista platform. i am allotting 512 mgs of ram and 16 gigs of hard drive space to the virtual system. however when i select "run with out changes" or "install ubuntu" i get a long list of error messages ending in 

[   0.232014]  ===========================
[   0.232014] ---[ end trace 4eaa2a86a8e2da22 ]---

im wondering if i am doing something wrong of if possibly i cannot run this version of linux on virtual PC. Any help would be appreciated. 

Oh, in advance. i am doing this not so much out of need, but because i want to have the ability to use ubuntu and vista at the same time without having to restart the PC and switch to a different boot sector.

--edit--

i suppose it would help to note the version of ubuntu. im currently using ubuntu-8.10-desktop-i386 on a toshiba laptop with dedicated video, vista ultimate 32 and 4 gigs of ram. currently i am able to run any windows based OS in virtual PC such as XP, which i use for various software Microsoft neglected to create backwards support for. i am unsure if virtual PC and run a linux OS. i don't see why it cant. but i don't know for sure that i can.

---

### Post by markharding557 on 2008-10-31
what vm software are you using?

---

### Post by John_Q on 2008-11-01
MS Virtual PC 6.0.192.0

its the newest version i know of.

---

### Post by andrewtechhelp on 2008-11-01
I'm having the same problem too and also a problem just installing normally on a Dell 6400 Laptop

---

### Post by John_Q on 2008-11-01
Well its good to know that im not the only one trying to do things the hard way :-D.

---

### Post by rb126 on 2008-11-03
I'm trying Ubuntu on Microsoft Virtual PC 2007 on an 8-core (dual quad core) Dell desktop with 4GB RAM and Vista Business SP1, and I get errors.

With 8.04 I get to choose the language and then "Try without changing anything".  A brief progress bar opens up saying it is starting the kernel, and I then get an "Invalid processor instruction" popup messagebox, that offers to reset the virtual machine.  This then repeats.

With 8.10 I get to choose the language (English) and then choose to try without changing anything, and I then immediately get a stack trace dumped that ends "unknown bootoption" and "end trace".

I'm downloading 8.04.1 now, although I'm not holding out much hope of it working...

Anyone got any idea how to make this work?

---

### Post by iamdigitalman on 2008-11-12
I am having this problem as well on my machine. I am running this on an Asus EEE PC 1000H, 1.60ghz intel atom, 1gb RAM, 160gb HD, and Windows Vista Service Pack 1.

I also ran this when I had XP Service Pack 3 on here, and it did the exact same thing. I think this is a application problem, and not a machine issue. One thing to note is I put VPC 2007 Service Pack 1 on here, and it still failed.

I followed [this](http://arcanecode.wordpress.com/2008/11/10/installing-ubuntu-810-under-microsoft-virtual-pc-2007/) guide. I was thinking of trying an older version of ubuutu, and doing an upgrade to 8.10, assuming the older version can be installed.

---

### Post by Aireas on 2008-11-12
I don't believe that this is a software issue with the VM. I have been trying to do a normal installation of Ubuntu 8.10 and 8.04 (32 and 64 bit) on my Compaq Presario Notebook and I get the same errors as you guys. This seems to be a problem with computers built for Vista. I will also try to install an older version of Ubuntu. I will be sure to let you all know how it works out.

---

### Post by iamdigitalman on 2008-11-12
> **Aireas said:**
> I don't believe that this is a software issue with the VM. I have been trying to do a normal installation of Ubuntu 8.10 and 8.04 (32 and 64 bit) on my Compaq Presario Notebook and I get the same errors as you guys. This seems to be a problem with computers built for Vista. I will also try to install an older version of Ubuntu. I will be sure to let you all know how it works out.

Actually, mine was not built for Vista. It has a Designed For Windows XP case sticker. However, the chipset and graphics card both meet the requirements for Vista's aero interface, which works flawlessly on this machine.

By the way, both the regular live/install and the alternate install CDs fail, both in the same place, in the same way. I tried it.

---

### Post by iamdigitalman on 2008-11-14
Just an update, I tried downloading and installing the server flavor of ubuntu, and it failed in the exact same way, no matter what settings I tried.

I guess those of us who want to run ubuntu inside virtual pc are screwed, unless they fix this in 9.04.

---

### Post by Steveway on 2008-11-14
MS Virtual PC is not designed to run any other Operating System other than Microsofts own ones and Suse Linux. Get a real Virtual Machine like Virtualbox.

---

### Post by iamdigitalman on 2008-11-14
I have ran ubuntu in MS virtual PC 2004 on the mac, and it ran flawlessly. And right now I have ReactOS and Freedos running in it. But I will try another x86 virtualizer.

---

### Post by AndrewNi on 2008-11-16
Any progress on this? Versions before 8.x were fine.

---

### Post by Danpritchard18 on 2009-02-27
Helloooo

I got Ubuntu to work on Virtual PC in the end by changing some of the boot options...

Firstly put in the disk and what not, and let it load, Select english and all that, and then you get to the main menu for the boot up.

When highlighting "Try Ubuntu without any change to your computer"  press F4 and select “Safe graphics mode“.

Then press F6.

Modify the following boot line:

“Boot Options seed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash –” 

Delete the part that says “quiet splash  -” and replace it with “vga=791 noreplace-paravirt”

Then press return for it to boot with these options. 

Then install as normal ... 

Once its installed and you go to reset the virtual Pc, you may face the same problem again.

IF this does happen, just press escape when it tells you to, to enter the menu and then go to boot options. 

Edit the boot option again, and just change 
 “quiet splash  -” 
to 
"noreplace-paravirt"

This will then lead to it booting up, and a lot of code will come up, and a green Bar. It may seem like something has gone wrong, but just leave it, and you will be on the main start up screen after about 5  minutes. 

Hope this helps :D

---

