---
title: "Installation missing 1 of the settings?"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by chris20pl on 2012-02-18
I wanted to install Ubuntu(64) 11.10 with Windows 7. I ran the disk and it's missing one of the options to "Install Ubuntu alongside Windows 7" I don't want to use the other options because I do not want to partition manually.( rather use the slide thing) Although, It does say the laptop has multiple operating systems? Yesterday I used VMware to try out Mac snow leopard, but I uninstalled Vmware today. Not sure what to do to get the other option back?
[IMG]http://img85.imageshack.us/img85/8334/img0539ea.jpg[/IMG]

---

### Post by darkod on 2012-02-18
First: Don't rather use the slider, instead boot win7 and resize any partitions you need to resize with windows Disk Management. Restart win7 few times in case it wants to do some disk checks after the resize.

Second: It is not offering the option "along side" because it's not seeing win7 is there. Did you maybe use this disk in raid before? It might have meta data left on it.

You can do one check, select the Something Else option and see if it shows the disk partitions correctly in the list, or there will be no partitions, blank list. Then just cancel the process, it will not change anything on the hdd if you don't continue.

Not showing the partitions is usually because of meta data remains, or some error in the partition table.

---

### Post by chris20pl on 2012-02-18
Alright, so i partitioned the drive in windows,first time doing this but it looks correct? I made it 49GB for Ubuntu
[IMG]http://img259.imageshack.us/img259/4508/picwb.png[/IMG]
Now this part is confusing, I had no idea what to do next, I couldn't find the drive I just made.
[IMG]http://img4.imageshack.us/img4/8343/img0542uz.jpg[/IMG]
 There is also another device that didn't fit in the picture
"/dev/sda4 ntfs 72256mb 16625mb" I guess ubuntu is not for me haha

---

### Post by ottosykora on 2012-02-19
You should have mentioned that you have a HP computer, then people would warn you before you do modifications to your partitions.
Now your partitions are dynamic (in opposite to basic) and you can not install any linux into it like this.

---

### Post by ottosykora on 2012-02-19
there are some tools claiming they do the conversion simple, I would try to make some kind of image backup of each partition or the whole disk in case something goes wrong.

[http://www.dynamic-disk.com/convert-dynamic-disk-to-basic.html](http://www.dynamic-disk.com/convert-dynamic-disk-to-basic.html)

[http://www.partitionwizard.com/](http://www.partitionwizard.com/)


so remove the new made ubuntu partition completely, and try to make the remaining 4 partitions to basic type first.

Only then people here can give you some more hints as how to install linux from there.

---

### Post by darkod on 2012-02-19
Yeah, forcing it to create a 5th partition converted the disk in dynamic without asking you (thank MS for that). Dynamic disks are a MS format and linux doesn't install on them.

Another error, was creating ntfs partition for ubuntu. Linux doesn't install on ntfs, it needs to install on its separate filesystem. When preparing your disk for linux you need to leave the space as unpartitioned (unallocated), and you will create the linux partition during the linux install.

---

### Post by ottosykora on 2012-02-19
I hope someone will make at least on the install disk some kind of check if there are 4 partitions already or not and stop people doing mistakes then.

Somehow then at least issuing a warning and some short advise not to create next primary partition by hand.

---

### Post by chris20pl on 2012-02-19
Guys, thanks for all the great support. Here is what I did;

I changed my drives from dynamic to basic, made the Unbuntu drive back to unallocated space(49.80GB)
[IMG]http://img818.imageshack.us/img818/7416/captureezn.png[/IMG]
Here is what it looks like now on Unbuntu
[IMG]http://img856.imageshack.us/img856/2488/img0545if.jpg[/IMG]
I noticed it now states there's free space, but also shows it's unusable. Can I do anything from there?

---

### Post by darkod on 2012-02-19
It's much better now, but still you have one (easy) problem left.

Your computer came with 4 primary partitions which is the limit of the HDD. You need to delete one, either the Recovery or HP Tools (don't delete the small System partition because windows boot files are there).

In most cases, I would recommend you boot windows, open the Recovery Software and create recovery DVDs from your recovery partition. Then you can delete it, and if at any moment you want to restore to factory state, you can use the DVDs. Deleting this partition will also help you use those 17GB that it takes.
Another option is deleting the HP Tools, you can live without them too.

After that ubuntu will be able to install into the unallocated space. If you install manually, create the ubuntu partitions as logical. You can create as many as you want, they will form one single extended partition.

The hdd can work with max 4 primary partitions, or 3 primary + 1 extended which can have many logical inside.

---

### Post by chris20pl on 2012-02-19
Sorry guys back again, I stumbled on another type of situation. I am not sure what to pick for the new drive.
[IMG]http://img809.imageshack.us/img809/9726/img0548pd.jpg[/IMG]
[IMG]http://img24.imageshack.us/img24/4600/img0550vt.jpg[/IMG]
I was looking around the forums and I believe it's "\" for the mount.
If I don't set anything, i get the following error "No root file system is defined"

---

### Post by ottosykora on 2012-02-19
> **chris20pl said:**
> Thank you Darkod and Ottosykora. The information you guys offered was spot on. I will be putting the Recovery D drive on dvd's and then delete that drive. Once again, thanks guys, loving the support on Ubuntu forums!

just small intermediate question:

which tool or method did you use to change the partitions back to basic?

---

### Post by ottosykora on 2012-02-19
what I did with the last HP computer was following:

1.use partition image software , something like clonzilla or other similar sotware to make backup of the partitions recovery and hp-tools

2.delete those two partitions, but not down how big they were abt

3. create an extended partition in the now empty space
you can use gparted for that, it should be on the installation CD, otherwise separate CD can be downloaded or boot cd called partedmagic (google for)

4.in the extended partition create first ntfs partition just same size or slightly bigger then the recovery was 

5.create after that the small fat32 partition to hold the hp-tools

6. restore now the contents of recovery and hp-tools to those partitions

7. check if windows still boots and all works and the recovery and tools partitions are ok, otherwise run scandisk/checkdisk on them

you have now full operational original system, including the recovery partition, it is in same position and will be found by the recovery manager


8. in the empty space inside the extended partition you can now create the root partition, swap partition in about the size of your ram and recomended also home partition for your data and settings.

Now you are ready for installation, using the CD, selecting not automatic, but something else option.


so your partitons may look like

1. windows boot
2. actual windows 
inside the extended
3. recovery
4. hp tools
5. ubuntu (root)
6. swap
7. home


all can be very much different, there are many ways of doing all correct, this is just a suggestion, I tried to do it recently just to see if I can preserve the full functionality of the restore and tools partition, and yes it seems to really work.

---

### Post by chris20pl on 2012-02-19
> **ottosykora said:**
> just small intermediate question:

which tool or method did you use to change the partitions back to basic?

I used "MiniTool Partition Wizard" to convert my Dynamic drives back to basic.

---

### Post by ottosykora on 2012-02-19
the sign / is for the root partition, this is where the actual ubuntu operating system will go in.
This is the one which is absolutely essential, otherwise the operating system can not work.

The /home is recomended to have separate partition, this is where your data and your personal settings will go

then we have the /swap , well this is just for the operating system to work more efficiently under heavy data load or hibernation proces etc.

---

### Post by ottosykora on 2012-02-19
> **chris20pl said:**
> I used "MiniTool Partition Wizard" to convert my Dynamic drives back to basic.

OK so far, seems you managed well with the tool, so I will make a link to that program for future reference.
There are different tools on the net, but some do not what they promise so a real experience is nice reference.

---

### Post by chris20pl on 2012-02-19
> **ottosykora said:**
> the sign / is for the root partition, this is where the actual ubuntu operating system will go in.
This is the one which is absolutely essential, otherwise the operating system can not work.

The /home is recomended to have separate partition, this is where your data and your personal settings will go

then we have the /swap , well this is just for the operating system to work more efficiently under heavy data load or hibernation proces etc.

How about the "/boot" also? I have been reading a guide and plan to actually install Ubuntu tomorrow and make sure everything is set up correct.

---

### Post by ottosykora on 2012-02-19
> **chris20pl said:**
> How about the "/boot" also? I have been reading a guide and plan to actually install Ubuntu tomorrow and make sure everything is set up correct.

well the /boot is not used today too much any more. It was essential with some older hardware where the boot files had to be only on first hard drive and within first certain number of sectors or in some cases bellow certain amount of Gb etc.

In your case , rather new HP machine, it has no importance and the /boot directory will be found later in the main / (root) partition.

If you manage to make separate partition for /home, this is one of the most useful things as it will allow you later to make clean install with some new version without loosing your data and settings.

Depends on how much space you have, for the ubuntu alone it could be 10-20Gb well enough, rest could be left for the /home as you can store then anything in it.

On my computers I also have some kind of partition to exchange data with windows. For that I use one smaller partition formated to fat32.


BTW: you did fine job , considering what mess have you been in with all those 'ugly yellow partitions' (dynamic) . Do all slowly, write down what you want install where, and try to make backup of all your valuable data for the case something should go wrong.

---

### Post by chris20pl on 2012-02-20
I have successfully installed a duel boot Ubuntu! All that's left is about 330+ updates for Ubuntu. Do you guys recommend "EasyBCD"  the windows boot looks a bit cleaner than Ubuntu's

[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/2/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/2/")

---

### Post by darkod on 2012-02-20
Personally, no, I don't recommend easyBCD.

What is bothering you in the boot menu? You can turn off the memtest entries if you want. All that will be left is the normal and recovery entry, plus another line for the previous kernels (when more than one exists).

It is also easy to move windows on top so you don't care how long is the list below.

---

