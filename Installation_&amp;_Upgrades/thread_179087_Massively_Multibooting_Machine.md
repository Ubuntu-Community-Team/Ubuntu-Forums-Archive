---
title: "Massively Multibooting Machine"
date: 2006-05-19
forum: Installation &amp; Upgrades
---

### Post by Basu on 2006-05-19
Hello all! I'm getting a computer all to myself from tomorrow and what I really want to do it turn it into a an experimentation system. That means that i would like to have several partitions from where I can boot several OSes, all of different types. I would like to boot
Ubuntu
PClinuxOS
Arch Linux
FreeBSD
Minix3
And keep a spare partition or two for whatever else I might decide on,plus one partition for all my documents and music. I know that I can make upto 63 logical partitions. I have an 80GB HDD and so I'm planning to make about 8-10 logical partitions. What I really would like to know is how can I make sure that only ubuntu's GRUB is used and how can I tell that GRUB about the other OSes. I know that I could if I install Ubuntu at the end it'll auto detect all the others, but that's not really an option as I'll be swapping OSes every month or so. It would be great if someone could tell me how I can manage GRUB and prevent the other OSes from overwriting.
Thanks all,

PS Is there a way that I can find out what kernel modules my hardware is actually using? I need the module names to configure Arch. Thanks again. Feel free to visit my blog where I'll be posting about my progress.

---

### Post by Herman on 2006-05-19
You might install Ubuntu first and install Ubuntu's Grub to MBR, then after that, do not install anything new to MBR, just install the other operating system's bootloaders to their own operating system partition. Well, you won't really need a boot loader for the subsequent Linux installs anyway, grub can boot them as long as they at least have a kernel and probably an initrd.img. Grub does not require any other boot loaders except for Windows. It does no harm to install Lilo to an operating system partition if you can't avoid installing a bootloader somewhere, or install GRUB to a floppy disk to make the new operating system installer happy without installing any more bootloaders to MBR.
    To re-boot during the install of each of these operating systems you can use [Grub's command line]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and [make grub do the research for you]("http://www.troubleshooters.com/linux/grub/grub.htm#_Having_Grub_Do_Your_Research_For_You"). You should practice this a little first. When you know how to use Grub from the command line you'll be able to get grub to search for each new operating system's kernel and boot them as you add them. Write down the commands used to boot with and then make an entry with the same commands to your menu.lst file manually.  Or press 'e' from the Grub Menu to edit the commands before booting if you prefer that way. 

I'm sorry but I don't know enough to help you with the kernel modules question.

I'll be interested in checking your blog, thanks for sharing! :D Regards, Herman

---

### Post by Basu on 2006-05-20
Ive been reading through the GRUB manual and it seems that the best thing would be to install all the OS's bootloaders to their root partitions and then edit the Ubuntu GRUB menu.lst to link to their bootloaders via chainloading. I think that should work. Has anyone installed a BSD or minix3 beside Ubuntu? If yes, please help!

---

### Post by Herman on 2006-05-20
Agreed, although Grub is perfectly capable of booting any ("supported") operating system's kernel directly, it does use chainloading for unsupported "proprietry" operating systems like Windows. There is nothing to prevent you using Grub to chainload other bootloaders (Lilo or subsequent instances of Grub), it will just take a second or two of extra time for each boot-up.

 There is an easier way to do what you want, you might find it faster and simpler to use [GAG Boot Manager]("http://gag.sourceforge.net/") instead, which will be less of a headache for someone who  wants a lot of fast changes and doesn't necessarily need to finish as a grub expert.>  I'll be swapping OSes every month or so GAG Boot Manager is better suited for that kind of use. Here's a link to my web-page about [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") in case you are interested.
> Has anyone installed a BSD or minix3 beside Ubuntu? If yes, please help! GAG might help you there too, I don't know those two operating systems at all, I know GAG has an icon for BSD, so I think it will boot it easily.  Although I love Grub, there may be times when GAG Boot Manager might be more appropriate (depending on what it is you want to do, that is).

 I just wanted to make sure you have all the information, I don't mind which booting plan you decide on.
Personally, I use Grub as my main bootloader, installed to MBR. I also have Lilo installed on each Linux partition. Lilo doesn't erase Grub, and it enables chainloading in case I do some silly experiment with Grub that fails and locks me out of my system. I can always Boot with Lilo via GAG to regain access to my system and then fix the problem. GAG Boot Manager and Lilo are good combined with Grub.
Keep up the good work, Basu! Regards, Herman :D

---

### Post by Basu on 2006-05-20
Thanks for recommending GAG, it seems to be just what I was looking for. I'm also getting the gparted LiveCD so that I can partition before I actually install. Thanks a lot !

---

