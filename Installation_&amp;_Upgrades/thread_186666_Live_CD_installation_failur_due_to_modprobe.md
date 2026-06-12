---
title: "Live CD installation failur due to modprobe"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by abs on 2006-06-02
hello,

when i tried to install my CD with the newly burnt CD i get this error when the installer get to the detecting hardware.

the error msg i get is  "Error while running 'modprobe -v amd76xrom'"

](*,) 

anyideas, should i re download the CD and burna fresh copy.

abs

--

---

### Post by amadeus2003 on 2006-06-02
i am having exactly the same problem.

If anyone has a solution please let me know.

Specs

Dual AthlonMP 2800+
512mb Ram
GeforceFX 5900 256mb

Live CD seems to work great.

Perhaps there is a way to disable that module from running in the first place?

Here is a more detailed report of what it claims the error is

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code None; see /var/log/installer/syslog and /var/log/syslog


Thanks in advance.

P.S. - I dont know if this will help at all, but when i run the command in the terminal i get this message

insmod /lib/modules/2.6.15-23-386/kernel/drivers/mtd/maps/amd76xrom.ko
FATAL: Error inserting amd76xrom (/lib/modules/2.6.15-23-386/kernel/drivers/mtd/maps/amd76xrom.ko): No such device

---

### Post by amadeus2003 on 2006-06-03
nobody know's how to fix this? or can offer any ideas? :(

---

### Post by abs on 2006-06-03
hello.

I have a dual athlon MP1800

and a sata controler, what i dont understand is that i never
got this problem with the beta 2 release.

how could i debug this and show the information here

---

### Post by amadeus2003 on 2006-06-03
Well I found a work-around!

If you go to

[http://mirrors.cat.pdx.edu/ubuntu-iso/dapper/](http://mirrors.cat.pdx.edu/ubuntu-iso/dapper/)

and download the following file:

ubuntu-6.06-alternate-i386.iso

(The key part is the ALTERNATE) Anyways, thats the OEM disc which basically you load up, its got the old CLI based installer, but still fairly easy to run, then after it installs and boots into Ubuntu, you will have to login as oem, which it will instruct you to do during installation.

Once you have logged in as OEM open up the terminal and type

sudo oem-config-prepare

Then restart the computer, it will prompt you for some stuff for the computer and you answer the questions and boom, you are good to go!

P.S. - My motherboard does support RAID but i have it disabled, im wondering if it has to do with the mobo chipset? or perhaps the athlonmp's? I have an ECS mobo

---

### Post by abs on 2006-06-04
WTF,.... i cant even install ubuntu now.

---

### Post by gaggle on 2006-06-10
I'm having this exact problem.

Coincidentally (or is it) I'm also running a Dual AthlonMP, it seems like a common trait between the three of us so far. The motherboard is an ASUS A7M266-D. Beyond that the machine has a Promise IDE RAID controller, a GeForce2 MX and 1 GiB of ECC RAM.

For what its worth the Server edition installs without a hitch, so for now I'll be running with the LAMP installation and see how far I can use that. If that totally fails I'll give the Alternate iso a try.



- gaggle

---

### Post by gaggle on 2006-06-11
For the record the Alternate installation went without a hitch. ASCII installer "for teh win" as they say nowadays.

---

### Post by RavenndudE on 2006-09-15
I'm also getting this error ... 

Error while running 'modprobr -v amd76xrom'

I'm running AMD MP 2200+s

Is there any kind of work around besides having to download the 700mb iso? I normally wouldn't mind doing it, but here at school, my bandwith limit is 1gig per day, and I'm getting kinda close.

---

