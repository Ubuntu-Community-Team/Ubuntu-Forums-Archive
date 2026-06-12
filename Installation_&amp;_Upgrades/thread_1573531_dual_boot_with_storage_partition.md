---
title: "dual boot with storage partition"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by dirtyburger on 2010-09-12
hi everyone! im exited to get into ubuntu, i wanna intall it for real after using wubi!
 
i have only one question
 
i am right now burning ubuntu to a dvd with imgburn
 
i know how to install it
 
i right now am on windows 7, and i wish to duel boot ubuntu and 7
 
i have shrunk windows 7, and now have 20 gigs unalloated space i want to install ubuntu on.
 
i also have a 250 gig storage partion that i made ages ago for windows, to make formatting easier.
 
it is ntfs, as is 7 obviously.
 
my question is, if i intall ubuntu into my unalloated, can i make it a ext filesystem, or will it have to be a ntfs one to access the ntfs storage drive??
 
 
i dont know about the comapiablity between file systems, it sure would be nice to use ext for ubuntu, but ntfs for storage and windows.
 
 
i guess my question is, will intalling ubuntu mess up my sotrage partion, and will i be able to drag and drop filse from the storage partiion into ubuntu, and vice versa?
 
thanks! for any help!!!! i know you guys proboly get asked this 80 times a day!

---

### Post by zpletan on 2010-09-12
You can read/write NTFS partitions from Ubuntu, no matter what partition type Ubuntu is installed on.

(By the way, if you have 20GB unallocated space, why would you want to install with Wubi?)

---

### Post by dirtyburger on 2010-09-12
> **zpletan said:**
> You can read/write NTFS partitions from Ubuntu, no matter what partition type Ubuntu is installed on.
 
(By the way, if you have 20GB unallocated space, why would you want to install with Wubi?)
 
thanks for the reply
 
im not using wubi anymore, i wanted to see what ubuntu was like so i downloaded it
 
now im ready to really intall ubuntu so i burned it to a disk, and made 20 gigs to allocate for ubuntu
 
so basiccly i jut tell the unbut intaller to install into my 20 gig free space?
 
where do i point grub?

---

### Post by zpletan on 2010-09-12
Yeah - just tell the installer to put it in the 20GB unallocated space.

GRUB should be set up automatically; you shouldn't have to do anything with it.

---

### Post by presence1960 on 2010-09-12
> **dirtyburger said:**
> thanks for the reply
 
im not using wubi anymore, i wanted to see what ubuntu was like so i downloaded it
 
now im ready to really intall ubuntu so i burned it to a disk, and made 20 gigs to allocate for ubuntu
 
so basiccly i jut tell the unbut intaller to install into my 20 gig free space?
 
where do i point grub?

If you only have one disk put GRUB on MBR of sda. If you have multiple disks we need way more info to insure you set ubuntu up properly on the first try. If you have multiple hard disks (not partitions) do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by dirtyburger on 2010-09-12
> **presence1960 said:**
> If you only have one disk put GRUB on MBR of sda. If you have multiple disks we need way more info to insure you set ubuntu up properly on the first try. If you have multiple hard disks (not partitions) do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

hi thanks for replying, i only have 1 harddrive

so i will point it to my 20 gigs allocated space to make a ubuntu partian

i have to delte my dell 60 mb partition first though or theres 5 primary partions lol **** dell

---

### Post by presence1960 on 2010-09-12
> **dirtyburger said:**
> hi thanks for replying, i only have 1 harddrive

so i will point it to my 20 gigs allocated space to make a ubuntu partian

i have to delte my dell 60 mb partition first though or theres 5 primary partions lol **** dell

Then the install should be very straightforward.

Hopefully when you remove that Dell Utility partition it removes that software that some Dell & HP computers have that keeps writing to the area of the hard disk that GRUB occupies. That software continually corrupts GRUB until either the software is removed or it is shut down in Control Panel under Services. Hopefully this will not be the case with you.

With wubi you are immune from that because you use the windows bootloader to choose Ubuntu, which then passes to GRUB which is not in the MBR on wubi installs.

---

### Post by dirtyburger on 2010-09-12
> **presence1960 said:**
> Then the install should be very straightforward.

Hopefully when you remove that Dell Utility partition it removes that software that some Dell & HP computers have that keeps writing to the area of the hard disk that GRUB occupies. That software continually corrupts GRUB until either the software is removed or it is shut down in Control Panel under Services. Hopefully this will not be the case with you.

With wubi you are immune from that because you use the windows bootloader to choose Ubuntu, which then passes to GRUB which is not in the MBR on wubi installs.

wow very informative thx

just one problem though, this little partition is at the front of my harddrive! the very first partition sda1

if i delete it in gparted, theres no sda1

and windows is sda2

will windows 7 still boot????? how do i make windows sd1 and just merge that empty dell 60 mb later down the harddrive, maybe sda3 or something??? thx

im on the live cd right now trying to figure this out

i dont wanna have to reformat

---

### Post by presence1960 on 2010-09-12
> **dirtyburger said:**
> wow very informative thx

just one problem though, this little partition is at the front of my harddrive! the very first partition sda1

if i delete it in gparted, theres no sda1

and windows is sda2

will windows 7 still boot????? how do i make windows sd1 and just merge that empty dell 60 mb later down the harddrive, maybe sda3 or something??? thx

im on the live cd right now trying to figure this out

i dont wanna have to reformat

Windows will still boot because it's bootloader is on the MBR not sda1. At only 60 MB I would not worry too much about that lost space, it is totally insignificant. **_BUT_** I would like to be sure that is a Dell utility partition and not a system reserved windows 7 boot partition. because if it is the latter your windows will not boot. If you don't know how to determine which that 60 MB partition actually is then run the boot info script from my previous post.

---

### Post by dirtyburger on 2010-09-12
> **presence1960 said:**
> Windows will still boot because it's bootloader is on the MBR not sda1. At only 60 MB I would not worry too much about that lost space, it is totally insignificant. **_BUT_** I would like to be sure that is a Dell utility partition and not a system reserved windows 7 boot partition. because if it is the latter your windows will not boot. If you don't know how to determine which that 60 MB partition actually is then run the boot info script from my previous post.

nah its defintly dell

gparted says its dellultity

but i also have a 100 mb windows 7 partition that im obviously leaving alone

thanks

ill delete this prtitation and see how it goes :)

---

### Post by presence1960 on 2010-09-12
> **dirtyburger said:**
> nah its defintly dell

gparted says its dellultity

but i also have a 100 mb windows 7 partition that im obviously leaving alone

thanks

ill delete this prtitation and see how it goes :)

GREAT!! Get rid of the Dell Utility but keep the 100 MB Windows 7 partition as that contains the files needed to boot windows 7. Which ever bootloader you use GRUB (with a dual boot) or Windows the way it is now points to that partition to boot windows.

---

### Post by dirtyburger on 2010-09-14
> **presence1960 said:**
> GREAT!! Get rid of the Dell Utility but keep the 100 MB Windows 7 partition as that contains the files needed to boot windows 7. Which ever bootloader you use GRUB (with a dual boot) or Windows the way it is now points to that partition to boot windows.

what a ordeal lol

i ended up just formatted windows 7, and ubuntu leaving only my storage partition, i then reinstalld windows 7 set it up, and reinstalled ubuntu onto the free space

now my drives all all organized, starting with w7 system reserved first > then windows 7 > then ubuntu > then ubuntu swap > then storage drive

no unallocated free space, even though it was only 55 mb it feels better having everything avialiabe to me

i dont miss windows at all, i love how fast ubuntu is, i dont game or nothing just listen to music and use facebook and youtube so this is awsome! thanks for the help, i gotta keep w7 though for microsot office 2010 (.docx), and my printer which is a lexmark x1100 which doesnt work on ubuntu

other then that, im sold on ubuntu!

---

