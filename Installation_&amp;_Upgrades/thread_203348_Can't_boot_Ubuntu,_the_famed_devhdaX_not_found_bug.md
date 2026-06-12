---
title: "Can't boot Ubuntu, the famed /dev/hdaX not found bug"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by MDesigner on 2006-06-25
Ubuntu was hanging at the "Waiting for root filesystem" or something like that.. on the back end, it was sitting there for a few minutes, and wound up telling me something along the lines of "/dev/hda3 not found" then it kicks me to BusyBox shell.

Well, I did some reading on the forums about this.. one suggestion was to boot the live CD, and figure out the real device name for the partition that Ubuntu sits on.  Well.. I went to System->Disk Info and sure enough.. it really is /dev/hda3.  So I don't really know what to do here.

Anyone know how to get Ubuntu 6.06 working?  Or do we have to wait for the next release?

---

### Post by Herman on 2006-06-25
Hello, MDesigner, I'm not sure I understand your exact problem, but if it's just a booting problem, for example, GRUB has been misconfigured, that can easily be solved using GRUB's command line interface. [*click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to see how to use it. 
If your system is bootable, you should be able to boot it with GRUB.

If you need specific help, you'll need to at least post the results of ```
sudo fdisk -lu
``` You can do sudo fdisk -lu from a Live CD.

Or is this an install problem where you didn't get a system fully installed and it won't boot (nothing can boot it), or some other problem to do with your hard disk and partitions?
More info will help others to help you. 
Regards, Herman

---

### Post by MDesigner on 2006-06-25
Nope, can't boot.. it's not a GRUB misconfig.  Same issue as all these people:

[http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)

And it looks like nobody got a solution.  The closest solution was that somehow GRUB had the wrong HD paths in them and you have to boot the live CD to figure out the root partition, then edit the boot command line to fix it.  But I tried that.. /dev/sda3 is indeed the root partition.  I don't know what else to do here.  I'll try again & come back with the exact error message...

---

### Post by MDesigner on 2006-06-25
OK, the message is something like:

ALERT!  /dev/sda3 does not exist! Dropping to a shell.

Then I get the BusyBox shell.  But like I said.. if I boot on the live CD, /dev/sda3 is there, no problems.  Could it be that when Ubuntu made the install on the HD, it didn't modprobe the correct drivers to support my SATA controller?

---

### Post by MetalMusicAddict on 2006-06-25
[QUOTE=MDesigner]OK, the message is something like:

ALERT!  /dev/sda3 does not exist! Dropping to a shell.

Then I get the BusyBox shell.  But like I said.. if I boot on the live CD, /dev/sda3 is there, no problems.  Could it be that when Ubuntu made the install on the HD, it didn't modprobe the correct drivers to support my SATA controller?[/QUOTE]
How many drives do you have? Are you sure that sda3 is still your filesystem drive?

---

### Post by MDesigner on 2006-06-25
[QUOTE=MetalMusicAddict]How many drives do you have? Are you sure that sda3 is still your filesystem drive?[/QUOTE]

Two HDs on SATA ports, and one DVD burner on PATA IDE.  Actually I can't verify that sda3 is my system drive.. I can't do much in the BusyBox shell.  If I boot on the live CD, then yes.. "/" is /dev/sda3 and it's 15GB just as I set it up.  Actually, on the live CD, I think it's /target, not /.  Anyway.. interestingly enough, in the BusyBox shell, if I look at the /dev directory, sda3 doesn't exist at all.  None of the sda or sdb devs do.

---

### Post by MDesigner on 2006-06-25
OK I'm in the live CD now.. I was wrong, there is no /target.  So I mounted /dev/sda3 onto /tmp/pug.  Any idea where the startup script is that runs all the modprobe calls to load up drivers?  I have a feeling it's not loading up the right SATA drivers...

---

### Post by MetalMusicAddict on 2006-06-25
You should really only need to change 2 files. Your menu.lst (grub) and fstab.

When you boot the live cd and then go to Administration->"Disks" should give you how the disks are mounted. If what should be your filesystem drive is different than sda3 you need to change it in the menu.lst (grub) and fstab into whatever it is. Maybe sdc3?

---

### Post by MDesigner on 2006-06-25
Yeah I tried that.. booted the live CD, it says /dev/sda3 is perfectly valid.  I even mounted it & saw the files there.

---

### Post by MDesigner on 2006-06-25
Sorry , double post..and I couldn't figure out how to delete it

---

### Post by mobgame on 2006-06-27
I have the same problems as you posed. Does anyone find the solution to solve that?
Thanks!
My PC:
Amd 64 3000+
120G HDD 
160G HDD

---

### Post by MDesigner on 2006-06-27
UBUNTU!!!!!!!!!!!!!!!!!!!!!!!

](*,) 

Sorry, there was no point to that.. it was just a bit of mild frustration.  Very mild. ;)

---

### Post by mobgame on 2006-06-27
thx!

So, what did u do now? should I give up ubuntu and change to FC5 or SuSE?:confused: :confused:

---

### Post by MDesigner on 2006-06-27
I am actually not giving up on Ubuntu just yet.  My desktop PC is having some major issues with the IDE/SATA onboard controller, so that may be at fault.  I have to replace the motherboard soon, so after that's done, I'll give Ubuntu another shot.

---

