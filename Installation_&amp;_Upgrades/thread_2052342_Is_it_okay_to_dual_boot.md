---
title: "Is it okay to dual boot?"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by AlfredAraza on 2012-09-03
Hey there,

I'm dual booting on my laptop ( Windows 7 & Ubuntu 12.04 LTS ), And I pretty much like it
& I'm planning to get a desktop next week, And I want to dual boot (Windows 7, Ubuntu 12.04 LTS, Ubuntu Studio) And I might consider adding BackTrack or Linux Mint, So my questions are :-

1- Is it bad to dual boot in the long term?

2- Is it gonna harm the hardware in any way?

3- Is it gonna make one of the OS slow....etc?

4- Is there anything i should check before dual booting more than 2 OS?

PS : I use the PC ALOT ( record music, edit music, encode videos, upload things on my website, manage my schedules, watch the house cameras, 3D designing ), so sometimes the CPU usage gonna be @ 100% for days, And i have a good cooling system of course :lolflag:

Thanks in advance :)

---

### Post by MG&amp;TL on 2012-09-03
> **AlfredAraza said:**
> Hey there,

I'm dual booting on my laptop ( Windows 7 & Ubuntu 12.04 LTS ), And I pretty much like it
& I'm planning to get a desktop next week, And I want to dual boot (Windows 7, Ubuntu 12.04 LTS, Ubuntu Studio) And I might consider adding BackTrack or Linux Mint, So my questions are :-

1- Is it bad to dual boot in the long term?

2- Is it gonna harm the hardware in any way?

3- Is it gonna make one of the OS slow....etc?

4- Is there anything i should check before dual booting more than 2 OS?

PS : I use the PC ALOT ( record music, edit music, encode videos, upload things on my website, manage my schedules, watch the house cameras, 3D designing ), so sometimes the CPU usage gonna be @ 100% for days, And i have a good cooling system of course :lolflag:

Thanks in advance :)

1) No, it's not. Feel free to go as long-term as you wish.

2) Nope. 

3) Also nope, but I do find that dual-booting **slightly **increases boot time.

4) Install Windows first. Windows does not like being installed after linux. Other than that, just be careful when playing with partitions, things tend to break rather easily.

---

### Post by lordievader on 2012-09-03
The only downside of dual-booting I can think of is that you use more disk space, since you have 2 OS'es instead of one. Another thing is that Windows can not read the Linux partitions, so Windows can not access any files stored on the Linux side of the mirror.

Furthermore I have never experienced any of your first 3 points.

---

### Post by mastablasta on 2012-09-03
> **AlfredAraza said:**
>  Ubuntu 12.04 LTS, Ubuntu Studio) And I might consider adding BackTrack or Linux Mint, 
 
what is the purpose of having so many Ubuntu derivatives? i mean they are more or less the same thing appart from some minor tweaks and tools (which can easilly be installe don the other  one). i understand if someone plans to multi boot Ubuntu and red hat/centos & maybe slackware or arch since they are kind of different all the way to the core. but the ones you mentioned are more or less the same thing. 
would it be easier to just go with one and install all necessary tools to it and then tweak it to your liking?
 
for example take the studio (since you need osme audio specific stuff), add cinamon desktop (this will basically give you mint) you can also add mint software manager, backup tool. then when you need ming, just log out and loging with cinnamon. similary you add gnome and unity and then log out and login on unity it will give you Ubuntu (or you can just install ubunntu-desktop package).
 
then add the "hacking tools" air crack, orphcrack etc. and if you need it, add the hardened kernel. this will sort of give you backtrack.

---

### Post by opensshd on 2012-09-03
I have Win7/Precise/OpenBSD5.1 multiboot setup.

Things to consider.

What bootloader will you use?

You can only have four primary partitions on a disk; though you can run some OS's on logical partitions. Planning a good partition layout beforehand is helpful. I personally, would boot a liveOS from usb/disk and use gparted to set all my partitions up all at once; perhaps the installer of the first OS you are loading. It makes it easier to get through the installers of the particular OS's if you get that work out of the way.

To protect against any harm, make sure all sensors are detected correctly and all fans are running in each OS environment. In Linux I use:

```

sudo apt-get install lm-sensors && sudo sensors-detect

```

sensors-detect will offer to put the appropriate lines for your particular sensors in the appropriate conf file, go ahead and add those lines.

Other than any one of your operating systems not running the internals of the machine correctly, I don't see that there can be any harm. dmesg is a good place to start after an install.

Gl!

Also: [http://www.linuxquestions.org/questions/general-10/partitions-logical-vs-primary-528766/](http://www.linuxquestions.org/questions/general-10/partitions-logical-vs-primary-528766/)

A good read on partitions. :)

---

### Post by Mark Phelps on 2012-09-03
Since, by your own admission, you currently use your PC a LOT, the last thing you want is to have to boot into Win7 -- and suddenly have it not boot anymore!  This can easily happen if you mess around with files inside the Win7 OS partition while running any Linux distro.

So, for quick recovery, it would be a good idea to do several things...

First, once you get Win7 configured and running the way you want, use the Disk Management utility (NOT Linux apps) to shrink the OS partition down to make room.  Then, reboot a couple of times to let the filesystem make adjustments.

Second, use the Backup feature to create and burn a Win7 Repair CD.  If the bootloader gets corrupted, you can use this CD to make repairs.

Third, download and install the free version of Macrium Reflect.  Use the option to create and burn a Linux Boot CD.

Fourth, use MR to create a full-partition backup of Win7, including the separate boot partition (if you have one). Save this backup to an external drive.

NOW, you have the tools to (1) repair any Win7 boot problems, and (2) restore your Win7 to the state it was in when you made the backup.

---

### Post by Old_Grey_Wolf on 2012-09-03
You have gotten good answers to your four questions. 

If you are getting a new computer you may want to get one that has a processor with support for VT extensions. Then consider using one of the Virtual Machine hypervisors; such as, KVM, ESXi, Xen, VirtualBox. If I run more that 3 operating systems then I use Virtual Machines. Depending on the number of cores/threads and the RAM, you can have more than one OS running at the same time.

---

### Post by Bashing-om on 2012-09-03
In addition to all the other great advise. Do not forget about operating overhead space. All operating systems will require at least 20% more disk space than installed on (windows perhaps even more (fragmenting & house cleaning). /There we go again: Prior Prudent Planning Preventing P--- Poor Performance ==>Partitioning!

[INDENT]just my little bit <==BDQ
[/INDENT]

---

