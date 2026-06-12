---
title: "Ubuntu will not start from SSD on Acer travel mate 8481"
date: 2015-07-27
forum: Installation &amp; Upgrades
---

### Post by paulravin on 2015-07-27
[COLOR=#000000][FONT=Calibri, sans-serif][SIZE=2]I am trying to install ubuntu on an acer travelmate 8481. The machine has 2 hard drives, a 500mb HDD and a 64GB SSD. I can install ubuntu 12.04 on the HDD and it runs fine but I can not install it on the SSD which is what I am trying to acheave. [/SIZE][/FONT][/COLOR]

 
 [COLOR=#000000][FONT=Calibri, sans-serif][SIZE=2]I install ubuntu from a live cd and that seems to go fine but when I start it up it shows the acer start up screen followed by a black screen with a cursor in the top left corner and that's it nothing else happens. I cant type, it just sits there like that.
[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Calibri, sans-serif][SIZE=2]So I know the machine will work with Ubuntu but it will not run the operating system from the SSD. Any help much appreciated![/SIZE][/FONT][/COLOR]

---

### Post by oldfred on 2015-07-27
Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Is system UEFI or BIOS?
With UEFI on Acer you have to add a UEFI password (never lose that), and enable trust on the Ubuntu boot files.

---

### Post by kerry_s on 2015-07-27
please provide specs.

if it was me i would go with xubuntu at least version 14.04 cause it's a newish laptop & a newer kernel will support it better.
i would select something else when choosing where to install. i would put /boot on the 500mb hd & / on the 64gb ssd.
some laptops with 2 hd's are designed to work that way.

---

### Post by paulravin on 2015-07-27
Here is the boot info:

[ http://paste.ubuntu.com/11951206/]("http://paste.ubuntu.com/11951206/")

Looks complicated! What does it all mean?

---

### Post by paulravin on 2015-07-27
> **kerry_s said:**
> please provide specs.

  i would put /boot on the 500mb hd & / on the 64gb ssd. some laptops with 2 hd's are designed to work that way.

What do you mean by this? I want to use the SSD for speed etc, that's the point of it. I am installing 12.04 as that is what I have, I am constrained by download limits and have already wasted lots of download data when I first installed 12.04 and got it to update as it installed. I can download ubuntu 15 if needed just don't have data to burn.

Specs: Acer travelmate 8481-2464G38ikk   made 11/2011
i5 1.6GHz   64gb ssd + 500gb HDD

---

### Post by kerry_s on 2015-07-27
just to clarify.

you have no problems running live from the cd ? 
it's only after you've installed it doesn't fully boot ?

try this:
when you get to the part where you select where to install, chose the last option, "something else" i think it says.
there make sure you select the ssd drive, format it as ext4, mount it as / 
in between that & the continue button, there is a drop down where you select where to install grub, make sure you select the ssd drive.

---

### Post by oldfred on 2015-07-27
If you boot can you use entry that says sdb1? It is nearer the bottom of the grub menu?

You show two full BIOS based installs with MBR partitioning, one on sda1 and one on sda2.

Do not run Boot-Repair's autofix. 
That just installs one grub to the MBR of both drives. You want your install in sda to have its boot loader in sda, which you have. But then you want to add grub to the MBR of sdb from the install in sdb.
If you can boot into install in sdb, run this:
       sudo grub-install /dev/sdb

Grub does not use boot flag, but a few BIOS want to see a boot flag. I might use gparted, Disks or terminal to add a boot flag to sdb1.
In gparted click on sdb1 and right click to add boot flag.

---

### Post by paulravin on 2015-07-29
Thanks for the replies, Kerry_s your fix worked. I tried installing about 6 times, partitions etc making it more complicated but it is all working. Thanks Oldfred for your help, your post was way too complicated for me to follow, sooo many acronyms that I do not understand..

---

