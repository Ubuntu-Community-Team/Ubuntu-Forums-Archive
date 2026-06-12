---
title: "how can i prevent sony vaio rescue(custom) from deleting ubuntu"
date: 2013-10-12
forum: Installation &amp; Upgrades
---

### Post by btrix2 on 2013-10-12
[SIZE=2][B]hi,

as the title says "how can i prevent sony vaio rescue(custom) from deleting ubuntu"

i hv been using ubuntu along with windows 8 but in windows 8 i couldnt find driver and it didnt detect my dsl internet connection. so i used win8 without internet. i used ubuntu more than win and internet worked in ubuntu but not in win.

but now i want net in my win 7
 
i deleted win 8 now i hv win 7 but it says drivers are not compatible even if i downloaded it from vaio website for win 7 home basic 64 bits. it didnt work
 
still no internet in win.

so i called vaio care they told me that any other source windows will not do they create costimized windows with drivers so i had recovery cd. but when i boot with it and go to advanced recovery it says it will create 4 partition
1. recovery
2.
3. c drive
4. d drive

my current hdd status[/B][/SIZE]
[IMG]http://www.imageurlhost.com/images/01fzpghfpzgpsn2ttga9.jpeg[/IMG]

[SIZE=2][B]i would like to install windows 7 home basic from vaio rescue cd

plz help me

[COLOR=#ffa500]my main problem is no net in windows 7 home basic 64 bits my laptop is vpceb44en
[/COLOR]
thnx in advance[/B][/SIZE]

---

### Post by maestrobwh1 on 2013-10-12
This is tricky but not impossible.  

1)The "easiest" thing to do is download a copy of "Clonezilla" live and clone that ext4 partition (and any other you want to keep) to an image file onto an external disk.  Then, after the recovery process, create an new ext4 partition of equal or larger size in the same place (sda2) (i.e. use GParted live or a Gparted on a Ubuntu CD/USB stick), then boot back with clonezilla and restore the partition.  You can actually clone the entire disk and just restore the partitions you want but you'd have to create those again before restoring.  Clonezilla can't create partitions unless you restore the whole disk image and obviously you just want to restore Ubuntu and possibly some data partitions.  Also, you'd have to make sure that your disk geometry is similar when you recreate the partitions.

2)There are other means.  You could use Gparted live  or a Ubuntu Live and directly copy the partition(s) to an external device, then make a new empty space that in the restored drive to an equal or greater value to the one you want to copy back. You'd have to reinstall grub.  This gets oddly tricky if you have EFI booting.  Do you?

3)I personally, if you can boot into Ubuntu, would make a Linux partition on an external device slightly larger than your data size, and install dump.  Then, while running Ubuntu, you could use the dump command onto the new mounted partition.  You'd then still need a bootable linux and it is slightly more involved, but it is faster to do this and you can put the restored partition where ever you want.  Then next steps involve booting from a Ubuntu live cd/usb, recreating whatever partition(s) you'd want, then use cp -a /path2mounted_external /path2mounted_new_internal; then edit /etc/fstab on the internal drive, and reinstall grub.  This is an ADVANCED user option.  If you want specific steps on this option, post back.  Again, EFI is oddly tricky to reinstall boot to Ubuntu but notimpossible.

 THE VERY FIRST METHOD IS GENERALLY THE EASIEST OPTION THOUGH if you shrink down the restored (Windows I assume). to less than it is now and recreate any new partitions (and make sure they are EXACTLY equal in size or (slightly) larger.  Clonezilla can restore to a smaller partition under advanced options but I WOULD NOT TRY THAT.

Sorry for the capitals, but I just want to make you aware of some things.  Actually option 2 or 3 will set you up to fairly easily boot that ubuntu from an external device (again, you'd have to reinstall grub)  Using option 2, you would not be able to boot it if you copied it back because option 2 keeps the original uuid whereas option 3 does not (hence needing to edit fstab)

Or just reinstall Ubuntu completely... actually that in some ways is easiest if you are not horribly attached to your current install.

---

### Post by btrix2 on 2013-10-13
what is EFI. i googled it but understood just little. how should i check if it EFI or not. 

well in any case i think i need a external drive to accommodate ubuntu and my data which would be around 250 gb. as i dont hv an external drive is there any method to hide those partition from vaio rescue to fool it to think that hdd is of just 150 gb or so. 

i dont want vaio rescue to touch my ubuntu install and my data. i can go other way round but that would be time consuming. ie let vaio delete ubuntu and data than use recovery tool to get deleted data back will it work. even if it works it will take lots of time.

so can i fool vaio rescue to thing my hdd is of 150 gb can i hide my ubuntu and data partition from vaio rescue so that it doesnt have any acess to it and will not delete those patition.

thnx in advance

---

### Post by maestrobwh1 on 2013-10-13
I think you'd know.  There is no BIOS on newer computers and even Win 8 machines are booting like a MAC does.

I don't think you can do what you  are asking.  Even if you used say Gparted to "hide" a partition, the restore is just going to wipe the entire disk anyway.  Run 7 in a virtual machine?  Probably not an option but just a thought.

---

