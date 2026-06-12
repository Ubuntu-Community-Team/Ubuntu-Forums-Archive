---
title: "Backing up my computer before I dual boot ubuntu"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by Sidster67 on 2010-07-20
So im trying to backup my computer, and I understand the easiest and maybe best way is just through an external hard drive.  Mine is 1 terabyte.  Ive organized my folders by just putting everything into my documents.  But when I hook up my external hard drive, and I try to drag and drop, even through explorer, or copy and paste the folder, it just creates a shortcut.  Then, if I bring it to another computer and open that file it just goes to the my documents of that computer, so it's obviously useless.  I know this is extremely basic but I know I should do it prior to dual boot just in case.

---

### Post by cj.surrusco on 2010-07-20
Sorry, but this is a Windows problem and probably shouldn't be in the Ubuntu Forums.

---

### Post by varunendra on 2010-07-21
> **Sidster67 said:**
> when I hook up my external hard drive, and I try to drag and drop, even through explorer, or copy and paste the folder, it just creates a shortcut.

If you only want to secure your data, try press and holding 'Ctrl' key while dragging (the folder icon should show a small 'plus' sign with it while dragging). If you want to backup your installation too, try some partition imaging tool (ghost, partimage or clonezilla, etc.)

If normal copy-paste isn't working, it'd be better to put your question in a relevant Windows forum, it should provide you better support for your win version.

---

### Post by Sidster67 on 2010-07-22
sorry about having it in the wrong forum.  but about the backing up installation...do you mean the files in the hidden partition on my hard disk.  Because i didnt think i could access them.  When i open disk management.  I dont even have the option to assign a letter to the partition.  and is this neccessary?  because a guy at a computer shop told me that as long as i dont delete the hidden partition,  I can mess around with my OS as much as I want and still restore it to its factory condition.

---

### Post by varunendra on 2010-07-22
No, I don't mean only files, I mean image of your 'installation partition' (the one where the windows boots from). It is like a photographic image (compressed- if you wish) of the partition you are imaging, and can be used to restore the partition exactly to its current state (including everything on it- visible or hidden).

For an example, follow this link:
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

For a LiveCD including such tools, you should consider [SystemRescueCD]("http://www.sysresccd.org/Download")


For the restore (hidden) partition part, what you've been told is not entirely true. The provided restore function works only upto the point when the MBR (Master Boot Record) and partition structure/state is not changed.
The conditions for the success of this kind of 'auto-restoration' may vary between different models, but **the bottom-line is that it is not 100% guaranteed!**

This should be specially concerned if you are planning to resize existing partitions & create a new one for Ubuntu (the default partition plan in Ubuntu setup).


**End Note for you:** Don't get it wrong, you are always welcome here as long as you ask for a generic or linux related help. We only politely advised you to put your question in a windows forum since it was windows-specific :).

---

### Post by Sidster67 on 2010-07-22
ok so i went to that link on dedoimedo, and that seems awesome to be able to image anything...but i am a bit unclear on the whole livecd thing.  Most linux related programs seem to incorporate it.  Clonezilla is the one im thinking im going to use, but it says it needs to boot from a cd... first of all, im on a netbook and dont have a cd drive, just usb, so could i use my flash drive? (512MB) ; second, it actually boots from the cd like its an operating system in a dual boot?  so it runs like a virtual machine without touching my hard drive.  This seems confusing but i want to know how it works...

Also thank you so much for the help, ive browsed many forums in my life but ive never actually posted.  I dont know why i guess i was thinking of it as youtube; being really hard to get noticed.  but ive gotten almost instant responses that are really helpful.  so it's just awesome

---

### Post by varunendra on 2010-07-22
> **Sidster67 said:**
> could i use my flash drive? (512MB); second, it actually boots from the cd like its an operating system in a dual boot?  so it runs like a virtual machine without touching my hard drive.  This seems confusing but i want to know how it works...

Yes you can, and yes it (or any 'Live OS' for that matter) does boot into a real OS just like one installed on a separate hard disk.
[But unlike a virtual machine, a live OS often has the capability to 'touch' your hard drive, however, it doesn't do so without your permission]

At the time of booting (from live cd/usb) the cd or usb drive behaves like a separate physical disk where the (live) OS is pre-installed. Once booted, the (live) OS, depending upon its capabilities (or 'intentionally' imposed restrictions), can access the other drives and partitions just like a regular OS would do.


Now to download Clonezilla for USB flash drive [see here]("http://clonezilla.org/download/sourceforge/alternative/iso-zip-files.php"). (Download the ".zip" file, .iso is meant for burning on CD)
For a 'How To' guide, [see here]("http://clonezilla.org/clonezilla-live/liveusb.php").


However, I'm not sure if clonezilla live can provide you as friendly a GUI as SystemRescueCD can (I haven't tried clonezilla yet!). Besides, SystemRescueCD contains many other useful tools also. But 512MB is minimum requirement (unless customized) for its installation on a USB flash drive ([see here]("http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick"), follow instructions under "**B) Recommended USB installation method from Windows**") whereas for clonezilla live, it is 128MB only. So with a 512MB USB flash drive, I'd suggest you to try both of them and select what seems better to you before 'actually' making any change to your hard drive.


And yeah! This one is really a great forum with a great community!! :)

---

### Post by Sidster67 on 2010-07-22
yeah now that i have read some more i think im going with the diskrestorecd with partedit rather than clonezilla...

but okay, this is what im thinking of doing, although im a bit unclear on some of the steps:

1. Back up my My Documents files onto an external drive.(already donn)
2. Put the live cd onto a flash drive.
3. Boot the live cd in a virtual machine, and then use partedit to create an image of the hard drive, and store that on an external hard drive.
4. Use Gparted to create a partition for Windows, a partition for Ubuntu, a swap space for Ubuntu, and all my data that windows and ubuntu can both use.
5. Then eventually perhaps delete the windows partition.

does this sound right?

---

### Post by corrytonapple on 2010-07-22
If you have Windows 7 try this: [sevenfourms.com]("http://ubuntuforums.org/sevenfourms.com")

---

### Post by varunendra on 2010-07-22
> **Sidster67 said:**
> 1. Back up my My Documents files onto an external drive.(already donn)
2. Put the live cd onto a flash drive.
3. Boot the live cd in a virtual machine, and then use partedit to create an image of the hard drive, and store that on an external hard drive.
4. Use Gparted to create a partition for Windows, a partition for Ubuntu, a swap space for Ubuntu, and all my data that windows and ubuntu can both use.
5. Then eventually perhaps delete the windows partition.


[LIST=1]
[*]Not needed as the image would contain everything on the partition. But okay if already done.
[*]Correct! (I assume you know by now how to do it)
[*]Ummm.... well.... as I said earlier, as soon as you put the cd contents on a USB flash drive and make it bootable, it itself becomes a Live USB disk- not to be referred as 'virtual machine'. So you'd be booting your 'actual' machine from that flash drive. But apart from the terminology, you are going right! (booting off USB, running partedit to create image, store image on external drive)
[*]A slight improvement can be made: Use GParted to shrink (resize) an existing partition to create space for Ubuntu. Then create a new ext3 or ext4 partition in that space (typically 5GB or above) for Ubuntu. Creating a swap partition (typically 200MB-2GB, depending upon available RAM) is not necessary, but definitely improves performance.
[*]Not required at all!! Just simply install Ubuntu on the newly created ext3/4 partition, and it will automatically detect the existing Windows installation. After the installation is finished, you'll be presented the Grub menu to choose between Ubuntu and Windows (intact as it is!) everytime you boot.
[/LIST]

Now it's 1:09 am in my timezone and I'd go to bed. See you tomorrow):P

---

### Post by Sidster67 on 2010-07-22
Good night!

---

