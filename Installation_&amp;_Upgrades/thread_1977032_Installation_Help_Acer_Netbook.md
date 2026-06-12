---
title: "Installation Help Acer Netbook"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by Del64 on 2012-05-09
Hello,

I recently wanted to try out the windows installation of Linux though windows on my new netbook. The PC is an 64bit Acer Aspire One 722. I decided to try Kubuntu since I like KDE bit better.

I am still fairly new to Linux so I am unsure what the problem may be here: The software installed fine on Windows end however when I attempt to boot into Kubuntu the screen boots normally, the mouse appears and then freezes. This does this upon every boot option. 

I attached the following screenshots below: One in verbose the other in a normal boot. 

I uninstalled and re-installed this with no luck of success. 

Is there anything I can do to fix this?

---

### Post by cortman on 2012-05-09
I had the same problem on my Acer Aspire One 722 as well. Thankfully there's a very simple, albeit puzzling fix: On bootup press F2 to go into BIOS, and change the boot order to **network boot FIRST**. Save and reboot.
I wrote up some stuff about Linux on the 722 [here]("http://cortman.wordpress.com/2012/04/13/linux-on-acer-aspire-one-722-0369/"), you may or may not find it interesting. Good luck!
EDIT: I think it's F2. It may be some other F key, it'll say at the Acer splash screen.

---

### Post by Del64 on 2012-05-09
That did not work, I even plugged it into the router with the same results.

---

### Post by cortman on 2012-05-09
AFAIK this is a well known problem, and this fix has never failed that I've seen. I'm not sure what your level of proficiency is; but are you sure you're changing the dedicated boot order, and not just choosing to boot from a different device (which is a one-time action)?

---

### Post by Del64 on 2012-05-09
Yes.  I have changed the order in the BIOS to boot from the network, some Atheros driver, first. All it does is say wired connection failed and exiting this boot which leads to the windows boot manager where I select either Windows or Kubuntu.

edit: Demo mode works now though. Everything else isnt

---

### Post by jadtech on 2012-05-09
did you try the boot modification  ??? try pressing f6 trring nomodeset soft spash there are several others

---

### Post by Last Mohican on 2012-05-09
Were you trying to install a netbook version of Kubuntu or did you just do the desktop version?  I have a netbook and I want to do the same thing, but if you tried the netbook version maybe I should wait.

Why did you choose the "Windows installation"?  My approach is to put it on USB first.

---

### Post by jadtech on 2012-05-09
im not sure why they tried a windows install though its not mine to question , each machine is differnet the way to get a feel to kn ow if it will work well on yours is to get an ISO  burn a dvd or bootable USB and  see if if will boot and run in test mode .. 

some take a bit of tweaking most of the solutions are built in to the live CD  a few are not ...

---

### Post by Del64 on 2012-05-10
What about pressing f6? I did not quiet understand the rest of that sentence lol. 

I installed it through Windows using the wubi executable. I did not want to partition my hard drive, which is why I took this direction. 

As I said earlier, demo mode of Kubuntu works, backtrack linux as a live cd works; what does not work is finishing the installation in default boot, verbose, and acpi workarounds mode. Verbose mode has gone past the previous steps where it stopped in my first post. I will post another screenshot soon.

I set the PC to network boot first, is there anything else I can do?

---

### Post by cortman on 2012-05-10
If you can actually boot to the desktop, blacklisting the acer_wmi module in the kernel seems to help. If you can't and it was a partitioned installation, I'd say chroot in with a live CD, but I'm not sure how all that would work with Wubi.

---

### Post by Del64 on 2012-05-12
I can use the demo mode and any other live CD to do that , I am just not sure how. How would I black list the that item?

---

### Post by jadtech on 2012-05-12
look if you are trying to install wubi   no partition rather then  trying to boot from the cd boot to windows then  put the cd in the drive and it will pop up and ask if you want to start the wubi installer .. 


nhow ever since you cant get it to boot  from the CD I cant say  the wubi install will work  it will most likly need  tweaking  ..

keep in mind wubi is a windows program there is no ned to boot from that CD if your not going to parttition  how every running live cd and wubi are  basically the same Idea with one difference you can down load and install update wubi ..

---

### Post by Del64 on 2012-05-13
I understand that, I am asking how would I would I tweak it aka blacklist this feature by Acer.

---

### Post by jadtech on 2012-05-13
wubi install gives you no options of that nature there isn't much in the way of that flexibilty with wubi and I beleive black listing something after its already installed  is ponitless  since well its already there :)

the help was advice to get the live CD to boot for you , if you dont want to partition   you dont need to boot that CD at all , after  its all installed  if ubuntu has trouble booting  you can  come back  with details and see  what needs to be ajusted ..

---

### Post by cortman on 2012-05-13
> **jadtech said:**
> wubi install gives you no options of that nature there isn't much in the way of that flexibilty with wubi and I beleive black listing something after its already installed  is ponitless  since well its already there :)

the help was advice to get the live CD to boot for you , if you dont want to partition   you dont need to boot that CD at all , after  its all installed  if ubuntu has trouble booting  you can  come back  with details and see  what needs to be ajusted ..

This is misleading and incorrect. Blacklisting kernel modules is a process executed within the Linux system and is unaffected by wubi/virtualization.

> **Del64 said:**
> I understand that, I am asking how would I would I tweak it aka blacklist this feature by Acer.

You can blacklist it by running the following in a terminal:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

Add the line

```
blacklist acer_wmi
```

to the file, save, and reboot.

---

### Post by jadtech on 2012-05-13
there is no terminal though :) he is in windows with a wubi installer !?!?! which comes as part of the ISO ..

all you get to do is click in stall it asked for  a user name and password and install then   in the end   tell you to remove disk and reboot ..

---

### Post by jadtech on 2012-05-13
i do understand what you are attempting to show him   to get the live CD to boot  how ever not much need to boot  from that disk if they want to install wubi just boot to window  put the CD in the drive  ciick install when the installer comes up .. 

I do understand they could have the same issue after the install maybe not..

---

