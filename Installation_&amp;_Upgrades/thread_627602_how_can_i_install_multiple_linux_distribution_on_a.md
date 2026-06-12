---
title: "how can i install multiple linux distribution on a laptop"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by nicolasdiogo on 2007-11-30
hi folks,

i would like to find out how to install multiple Linux distributions on the same laptop, side by side and without virtualisation.

i tried installing suse after ubuntu and it has overwritten my boot partition and deleted my ubuntu kernel, eve though i did ask for reformat the partition.

so suse has deleted all grub entries for booting ubuntu, but create perfect entries for windows!

thus i would really appreciate some guidance or a pointer to some documentation.


thanks

Nicolas

business intelligence for small business
[www.brainpowered.net](www.brainpowered.net)

---

### Post by projectblu on 2007-11-30
you need to make a seperate partion for each distro you cant put multiple distros on one partition. im not sure if you need to have a seperate swap partition.

---

### Post by Pumalite on 2007-11-30
One /swap will do.
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by nicolasdiogo on 2007-12-04
thanks,

but how about grub and the /boot partition?

can i have a shared /boot partition?
where do i install grub? in the mbr?

sorry for asking so many question.

Nicolas

---

### Post by sethvath on 2007-12-04
Suse does not play with other linux distros. So in a way I would install suse first then ubuntu. The ubuntu installer will detect other OSes on your system and create a grub entry for it.

---

### Post by perixx on 2007-12-04
Hello guys,

speaking of multi-booting: Am I mistaken by thinking that installing Grub once (into the MBR or a superblock) is sufficient for all other Linux-distros when I set them up correctly in the menu.lst? 

If so, how can I tell the Ubuntu-installer on the Live-CD to set up without installing Grub again (for I'll then have to superfluosly chose it's own superblock)? 


perixx

---

### Post by Pumalite on 2007-12-04
You just have to edit your menu.lst

---

### Post by perixx on 2007-12-04
Have a look at this site, nicholasdiogo:

[http://wiki.ubuntuusers.de/menu.lst]("http://wiki.ubuntuusers.de/menu.lst")

and here:

[http://www.icpug.org.uk/national/linnwin/contents.htm]("http://www.icpug.org.uk/national/linnwin/contents.htm")


perixx

---

### Post by nicolasdiogo on 2007-12-05
thanks for your responses,

so i am getting the following installation procedure from this discussion:

partition the this, for example (HD= 160G);

HD(160G)
 |-- /home = 80G
 |-- / for Ubuntu = 12G
 |-- / for Suse = 12G
 |-- / for Slack = 12G
 L-- SWAP = 4G

install the grub in the HD mbr
install EACH /boot folder into its distribution own / root partition
amend grub menu.lst file to add entries for each distribution

so whenever i boot into any distribution, the same /home and SWAP partition will be used for all of them.

have i understood this properly folks :?:

---

### Post by Pumalite on 2007-12-05
I would make /swap 1 GB unless this is a laptop and it has more than 1 GB of RAM

---

### Post by perixx on 2007-12-05
Hi nicolas,

looks good so far! Just remember to install Grub into your MBR (hd0,0) as well, from which you then can chainload the separate distro's Grub-loaders in their /hdaX superblocks.

Also I think that you'll have to create a separate /hda1/homeXY folder for each distribution, which you'll then have to mount by editing your /hdaX/etc/fstab-files respectively. Otherwise you'll mess up your installations while all OS's are writing to the same /home folder on /hda1 - perhaps using different usernames on each installation would also suffice, but I'd recommend the first method.

For moving your /home folders to /hda1/homeXY after installation, refer to the following links:
> [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
[http://ubuntuforums.org/showthread.php?t=592913&page=2]("http://ubuntuforums.org/showthread.php?t=592913&page=2") 

regards,


perixx

---

### Post by perixx on 2007-12-06
Hi again!

Nicolas, please stick to the Howto at Psychocats for now!
That means, better create a** separate** /home partition for each distro, despite what I said before!

I've just been experimenting with using subdirs (instead of /) for multiple /home folders and things went utterly bad since then!

I suppose that I've somehow messed up my filesystems in the first place, which might be the reason for the problems. But it could also be that Ubuntun can't handle '/home partitions' mounted to subdir-folders... I'll have to investigate this further.

It's also a problem that I've got an older /ath partition hanging around at the end of the HDD, which was trouble in my installations ever since I've set it up, so I'm gonna wipe all that crap to finally have reproducable results.

Additionally, I've come to the conclusion that it's not so good an idea to mess around with partitions while working on a mounted system. Although it's possible to change things that come AFTER the mounted system-partition, I'm not sure anymore wheter the filesystem gets affected or not! 
So, please use a Live-CD for your partitioning for your own good :) 

regards,

perixx

---

### Post by Pumalite on 2007-12-06
A Gparted Live CD.

---

### Post by perixx on 2007-12-06
Right, Pumalite!

But Ubuntu Live-CD's should contain Gparted, no?

---

### Post by Pumalite on 2007-12-06
But it works with a mounted partition (not good), it's an older version, less flexible and less powerful.

---

### Post by uidb4056 on 2007-12-06
I would suggest you consider to create a small partition to install there the GRUB, in this way you dont have the risk that if you delete the last distro you have installed bieng unable to boot because MBR is pointing to a non existing partition. I would suggest you to read carefully [http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

Hope it could help

---

### Post by perixx on 2007-12-07
Well, some way to solve the problem. But you'll have to always and in the first place make sure to install Grub into /hda2 resp. (hd0,1) if using it along with Windows - and then chainload the Grub in hda2 from the nt-bootloader. This way you'll prevent messing up your XP-partition. 

But you'll also waste a whole primary partition entry - and there's only 4 of them - won't you? Or could you install the Grub into /hda5 (extended) while making hda2 the 'extended'-container for all other (Linux)-partitions?  


**EDIT:** Since I've encountered trouble myself when installing Grub into the MBR along with an existing XP installation (hda1) and as there are many posts reporting similar problems, I was convinced that doing so ALWAYS overwrites the nt-bootloader!
Now I've heard that using the auto-setup method of Ubuntu should install Grub without trouble - overwriting the nt-bootloader and booting XP directly from Grub... so, does that mean that the trouble usually only starts when removing Grub again (leaving the MBR without any bootloader for XP) and that I MUST use the auto-setup (not manual to hd0) installation of Ubuntu to avoid problems with Windows? 

perixx

---

