---
title: "It shouldn't be this difficult"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by bradlees on 2011-07-30
I have two hard drives on my pc. One is operating with xp. The other I formatted and am attempting to install Ubuntu on. I have also tried other distributions troubleshoot. I am attempting to boot from a live cd. I have switched media, dvd/cd drives, versions of ubuntu. At first I got the 'ubuntu' logo and the 5 dots underneath and the pc seemed to freeze from there. Now I am getting a host of different messages when I attempt to install ubuntu, mint, or xbuntu. The latter two give me a "NTLDR is missing, ctlaltdelete to restart message." Ubuntu now gives a message:
 (initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
can not mount /dev/loop 0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

What do I need to do to get ubuntu up and running on this hd, which I would like to dedicate fully to ubuntu.
 
Some pc info: emachines pentium 4 2.9ghz, 512mb RAM, 80g hd, withunanother 150gb with xp on it. I have had linux functioning on these components in the past.

Help! Please, man! help me!

---

### Post by fdrake on 2011-07-30
why don't you try to install wubi.exe ubuntu. it's like an application but basically it's the full ubuntu os. and if there is a problem you go back to windows and you uninstall it. it has the same properties of ubuntu so you are not loosing anything

---

### Post by garvinrick4 on 2011-07-30
bradlees you can boot into Windows drive? And is Windows on main drive and you want to install Ubuntu on USB drive? You have 512 meg of Ram and older processor. I would give
Lubuntu a go, it runs super on 512 meg of Ram and is nice.
[http://people.ubuntu.com/~gilir/]("http://people.ubuntu.com/%7Egilir/")
Use Lubuntu 11.04.iso it is 680 meg can download and [COLOR=RoyalBlue]burn[/COLOR] to a CD. Boot off of and check
it out then can install. If is your second drive will be [COLOR=Red]sdb not sda[/COLOR] drive to put grub in (boot loader) Then set your Bios to boot off of USB drive first in order and then update grub;
```
sudo update-grub
```Will put windows as a menu entry to boot along side of Lubuntu. 
When you boot off of Windows only drive(sda) can only boot Windows, its grub (boot loader) does not put Ubuntu as a menu entry.

## By the way Lubuntu uses LXDE and OPENBOX if you want to do research. I like them, quick simple and fast. Running at a full gallop uses about 350 meg of RAM.
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by bradlees on 2011-07-30
I can boot into the windows drive. I am trying to load the ubuntu onto an second hard drive and compo80gb drive i recently formatted. I know my hardware is older, but I had ubuntu and fedora successfully running on these components before. I'll give lubuntu a whirl.

Thanks, and I'll keep you informed of my progress!

---

### Post by bradlees on 2011-07-30
I tried the wubi to no avail. The first time i tried to install the wubi to the e: drive, the blank, formatted 80gb. It went almost all the way through and then gave me a message about access or permissions. I tried again and it installed it to the empty drive but it just loops and resets to my bios, emachines, screen if that hd is given boot priority. I'd like to put ubuntu on its own drive, not side-by-side with windows. 
I'll try the wubi again though, maybe I'll get a different message.

Thanks

---

### Post by garvinrick4 on 2011-07-30
> I can boot  into the windows drive. I am trying to load the ubuntu onto an second  hard drive and compo80gb drive i recently formatted. I know my hardware  is older, but I had ubuntu and fedora successfully running on these  components before. I'll give lubuntu a whirl.First just use Try Ubuntu or lubuntu to make sure the Cd boots and then you can install in sdb drive.
Should not be this hard, something is amiss. Here is a illustrated site:
 Ubuntus show me how site: This is a nice site:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by garvinrick4 on 2011-07-31
> **bradlees said:**
> I tried the wubi to no avail. The first time i tried to install the wubi to the e: drive, the blank, formatted 80gb. It went almost all the way through and then gave me a message about access or permissions. I tried again and it installed it to the empty drive but it just loops and resets to my bios, emachines, screen if that hd is given boot priority. I'd like to put ubuntu on its own drive, not side-by-side with windows. 
I'll try the wubi again though, maybe I'll get a different message.

Thanks Wubi is installed in a Folder in C: drive, you just put the Ubuntu CD in the tray open it and click on Wubi asks you for size you want your user name and password and 
then click install. (do not have to boot off of Ubuntu CD.) It will install in the folder and attach
"wubildr" inside of Windows boot manager so as to give you an option to boot into windows or Ubuntu. Folder will be right next to Users called Ubuntu in C: drive. You can uninstall in that folder or in ADD and Remove programs in Windows.

---

