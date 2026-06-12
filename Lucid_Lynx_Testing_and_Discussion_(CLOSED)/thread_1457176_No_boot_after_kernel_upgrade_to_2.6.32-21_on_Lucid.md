---
title: "No boot after kernel upgrade to 2.6.32-21 on Lucid Beta2"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Macchi on 2010-04-18
Kernel upgrade of Lucid Beta-2 to 2.6.32-21-generic breaks completely one of my test systems a Sony Vaio laptop VGN-B1XP! The system had a clean install of Beta 2, but now cannot run with the upgraded kernel.

I could not yet identify the exact problem in order to make a decent bug report on launchpad, but believe that it can be related to screen and graphics. It is difficult to tell because I get no signs of intelligible activities. Thus will have to start to dig into system logs.

Any suggestion of solutions for related 2.6.32-21 bugs?

Could you suggest good diagnosis tools?


PS: A TEMPORARY WORKARAOUND IS TO REMOVE THE PACKAGE linux-image-2.6.32-21 IN SYNAPTIC.
With this method the system will boot by default the previously working kernel. Observe that the packages linux-image and linux-image-generic are stuck at the faulty version and will be removed as well. Thus a WARNING: After this change I am not sure if later upgrades to linux-image will be added automatically to the system (Most probably no upgrades!). 
After the bugfix we probably will have to reinstall linux-image in order to automatically get forthcoming kernel upgrades.

---

### Post by grupotux on 2010-04-18
I have exactly the same problem on an HP-2200 laptop, my only available machine at present. Fortunately, I have copy of Knoppix 6 which is a live distribution, so I'm here thanks to Knoppix 6. 

Not so fortunately, the change to the grub 2 bootloader leaves me in a void. With the older grub (now legacy) it was a simple matter to change the default kernel to an earlier one. I have no idea how to do this safely  under the new scheme of things, but I will look into it right away.

Meanwhile, I'm sure that Macchi and I are not the only souls in this predicament. My boot sequence reaches only to the point where a file system check should begin but it never gets under way. The furthest it has gone is to the legend announcing the check, then the dots under the Ubuntu label progress for left to right by turning red, then the screen goes blank and everything stops, including disk activity.

Can anyone else help?

Cheers,

grupotux

---

### Post by grandtoubab on 2010-04-18
> **grupotux said:**
> I have exactly the same problem on an HP-2200 laptop, my only available machine at present. Fortunately, I have copy of Knoppix 6 which is a live distribution, so I'm here thanks to Knoppix 6. 

Not so fortunately, the change to the grub 2 bootloader leaves me in a void. With the older grub (now legacy) it was a simple matter to change the default kernel to an earlier one. I have no idea how to do this safely  under the new scheme of things, but I will look into it right away.

Meanwhile, I'm sure that Macchi and I are not the only souls in this predicament. My boot sequence reaches only to the point where a file system check should begin but it never gets under way. The furthest it has gone is to the legend announcing the check, then the dots under the Ubuntu label progress for left to right by turning red, then the screen goes blank and everything stops, including disk activity.

Can anyone else help?

Cheers,

grupotux
Read this maybe help
[http://ubuntuforums.org/showthread.php?t=1444879](http://ubuntuforums.org/showthread.php?t=1444879)

---

### Post by grupotux on 2010-04-18
Here's a temporary solution: Reboot your machine and promptly press the left-hand shift key when the BIOS screen appears. This will force the splash screen to appear, listing all installed kernels (if you machine has only one OS, the splash screen is not shown by default).

Then choose (arrow down to) the first line for kernel 2.6.32-20 and hit Enter. For now, do this every time upon booting or rebooting the system.

A few upgrades have just appeared on the repositories. I'll be back in a while.

Cheers.

---

### Post by jarocooke on 2010-04-18
Yep, I'm having the exact same problem on my parent's laptop.  Upgraded to latest kernel and now it won't boot!  Until there's another update that works, I am thinking of just using the "start up" program to set my default kernel to the old one.  Which I hope still works!

Right time to try it...

---

### Post by Macchi on 2010-04-18
Of course I can avoid the faulty kernel by manually choosing the previous working version upon every boot. As a temporary workaround I simply removed the 2.6.32-21 kernel on Synaptic. The packages linux-image and linux-image-generic were stuck at the faulty version and got removed as well. I could not find a way to force them back into the previous version.

---

### Post by purdurnr on 2010-04-18
Your post was clear and to the point.
You helped me stop pulling my hair out to get to GRUB menu!!!
Damn if every other post had 5 ways to NOT get it.

I was quickly able to back up to a prior release of the 10.04 LTS.
There is a graphics? issue that is stopping lots of people :(

Thanks Again!

---

### Post by Bobhuber on 2010-04-18
> **Macchi said:**
> Kernel upgrade of Lucid Beta-2 to 2.6.32-21-generic breaks completely one of my test systems a Sony Vaio laptop VGN-B1XP! The system had a clean install of Beta 2, but now cannot run with the upgraded kernel.

I could not yet identify the exact problem in order to make a decent bug report on launchpad, but believe that it can be related to screen and graphics. It is difficult to tell because I get no signs of intelligible activities. Thus will have to start to dig into system logs.

Any suggestion of solutions for related 2.6.32-21 bugs?

Could you suggest good diagnosis tools?
Make sure it actually loaded the kernel. I did an upgrade from 9.10  and it showed on the grub menu but had not been loaded. I had to install it thru synaptic.

---

### Post by slooksterpsv on 2010-04-18
Phew I was just about run sudo apt-get upgrade to get all the packages that are out there 327, but figured, everythings working great (I just installed Kubuntu on its own partition (10.04 Beta 2)) so I won't. Glad I found this post.

---

### Post by dpb on 2010-04-18
I'm also getting a boot hang on 2.6.32-21-generic.  This is on amd64 on an HP XW8400.  Something odd is going on.  Even if I boot up in single user mode (recovery mode), I get nothing to interact with.  I get past the point in the startup where my filesystems get mounted, and then, no more output.

I can hit ctrl-alt-del and the system reboots cleanly, so I know the kernel isn't truly "hung", also I can switch to other VTs, but everything besides 1 is blank.  I have waited about 10 minutes at the same state with no visible forward progress on the boot.

---

### Post by EddieInGeeksClothing on 2010-04-19
I'm getting the exact same problem on my test Laptop (a IBM X40 ThinkPad) after doing a load of updates the other day. I gave up after 3 re-installations of Lucid, as I didn't know how to get to GRUB when the splash is hidden!

Thanks for the work around! Is anyone going to update this post when the problem is fixed?

Before the issues I was loving 10.04, top effort by the developers!

~~~ EDIT ~~~

I was able to boot using the old Kernel, and everything is working fine. Does anyone know what the problem is with the Kernel that was in the updates (Release 21 I believe)?

---

