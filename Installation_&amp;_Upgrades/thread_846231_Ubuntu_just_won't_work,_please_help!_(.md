---
title: "Ubuntu just won't work, please help! :("
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by st3vo on 2008-07-01
Hi all,

After reading some stuff about ubuntu I have decided to give it a try but I'm just about to give up now, so I thought I'd try here first.

I have a Toshiba Equium Laptop with Vista premium installed.
I downloaded the ISO and burned it to CD.
First I tried to run the DEMO from CD and it didn't work,
so I tried the next option "Install under Windows".
So, I've installed it without a problem.
Next I restarted the laptop and selected "ubuntu" to boot from.

It says, press ESC to go to menu and the first 10 times I tried without but always got either asked to ENTER a command at the command prompt or I get the following:

udevd=event[1550]:run_program: '/sbin/modprobe' abnormal exit.

Then it just goes for ever and finally I get a Black screen with nothing on...I wait 10 minutes after that and restarted the pc.

I also, tried going to the menu and the Safe mode option and all the others, except the Live CD, which I don't know what that option's for as I already burned a CD, so I haven't tried that one.

I am really desparate to check out ubuntu as I always wanted to get rid of windows and move to Linux but I need to try it out for a bit first!

Hope someone can help!

Thanks

ST3VO

---

### Post by L337_K3y5 on 2008-07-01
You said that the live CD didn't work....did you check the md5sum AFTER it was downloaded?  If not that may be the cause for the first problem, and I would recommend that you burn another, check the md5sum, and start again.  As for the other with the GRUB, I have no idea, I'm new to this, but I'm gaining experience. -EDIT- Oh, looks like, I may be wrong though, that the kernel is messed up, probably resulting from the bad burn of the iso, and or the downloaded iso messed up in mid-transit.

---

### Post by st3vo on 2008-07-01
OK, downloaded another ISO did the checksum. All fine.
I then burned the ISO (at slow speed), installed ubuntu (2nd installation option) and it installed fine.
It asked me to restart and I restarted, then selected boot from ubuntu, splash screen came out and after it came:

udevd=event[1550]:run_program: '/sbin/modprobe' abnormal exit.

Does anyone else get this or is it only me? :(

Help Please!!!

---

### Post by Midwest-Linux on 2008-07-01
I have a Vista laptop. I was able to play the Live CD (insert the CD, shut off the computer, and then it boot from the disc) that part went normally and I was able to use the Live CD like that.

 I used the WUBI program to install Ubuntu and while Wubi worked and installed Ubuntu. Restarted the computer, there was the bootloader clicked Ubuntu and then it went to busy box and didn't go any further.

 So I shrunk the Vista partition (using the built in Vista shrink partitioner)and shrunk the partition down and ended up with about 12 GB free space. On that freed space I installed Ubuntu (and used the alternate text installer CD) and everything went well.

 I have found wubi and Vista didn't get along on my machine.

---

### Post by st3vo on 2008-07-01
Hi Midwest-Linux,

I have installed ubuntu as an application (2nd option) and have 28.4GB of space and 1GB RAM on my laptop, so shouldn't it run properly?

BTW: I installed ubuntu in my E partition just in case it's an issue.

I really hope I can get it running!

---

### Post by avtolle on 2008-07-01
[https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623) Take a look at this.

---

### Post by st3vo on 2008-07-01
Hi avtolle,

I followed the link and did an instructed step-by-step.

rebooted and the error:

udevd=event[1550]:run_program: '/sbin/modprobe' abnormal exit, still came out followed by a prompt asking me to type a command or H for help.

I really don't know what commands it's waiting for or what to do after that.

Is it supposed to wait for commands? 

Any advice on what to do now pls?

---

### Post by st3vo on 2008-07-01
I have also noticed that there are no files in my:

E:\ubuntu\disks\boot\grub directory.

Could this be because it hasn't run properly yet?

---

### Post by avtolle on 2008-07-01
At this point, my knowledge is at its limit. Regarding your last post, I surmise that to be the case. 

The only thing I can come up with is to uninstall Ubuntu and do a reinstall. I've a very strong feeling that the issue is somehow connected to your problems in trying to run the Live CD. There have been some threads on the forum concerning problems with Toshibas, you might want to take a look around and see if anything in those might help you. 

I wish I had better suggestions. I've taken a look around the Wubi Forum, and cannot find anyone with precisely your problem. If you decide to try to reinstall through Wubi again, take a look at the Wubi Guide (the link I previously gave you only scroll up and down the page) for instructions on how to safely uninstall and then install again. Good luck.

---

### Post by st3vo on 2008-07-01
Thanks avtolle but I've already re-installed it 3 times :(

I'll take a look around for Toshiba issues.

Thanks for your time!!!

---

### Post by st3vo on 2008-07-01
Hi all,

OK, I admit! I NEED UBUNTU BADLY :(  If someone can help me please help!!!

---

### Post by st3vo on 2008-07-02
Anyone please???

---

### Post by rotron on 2008-07-02
We have the same problem except that mine is

udevd-event [1505]: run_program: 'sbin/modprobe' abnormal exit

I'm using a new model Toshiba Satellite L300-N502 that doesn't come with any operating system.

I've tried installing Ubuntu on a high-end Toshiba Satellite A300-P531 and it worked fine.

I'll check out other forums for this problem.

---

### Post by st3vo on 2008-07-02
Great thanks :)

Hope we can both get it sorted and thanks for your reply!

Please let me know if you find the issue / fix please!!!

---

### Post by st3vo on 2008-07-02
Any updates please?

---

