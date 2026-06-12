---
title: "How to Install FiestyFawn 7.04 on USB drive."
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Timboleo on 2007-12-30
This is a howto on installing Feisty Fawn 7.04 on a external USB hard drive with no support for USB in the BIOS

First of all I am a newbie to Linux. Second you can do this too with a little trying on your part. Third there is all kinds of info out there if you search for it. There is one problem though. All the info I saw assumed that you had Linux to work with. Well DUH!! You wouldn’t be trying to install it if you had it already. So we are going to work with the assumption that you have Windoze,  are fed up with all the crap, and want to try something new.

Step 1) Fire up your favorite browser (Firefox or Opera) and download Ubuntu Feisty Fawn 7.04 Live CD ISO. Next download the Ubuntu text base install ISO.  You will need both for this method of install. Yes it’s a lot to download, but how much do you want to install it? Burn the ISOs to a CD. Connect your USB drive to make sure your system can see it. (This always helps as a first step.) Everything working? Good, lets get started. My system has 2 SATA 80GB drives, and 1 USB 80GB external drive. Yours may differ if you have a ATA drive and the USB drive. My system also has no support for booting to a USB device even though the options are there in the BIOS. Ok set your BIOS to boot from the CD first then the Hard drive second. Now save the changes and exit the BIOS.

Step 2) Put the text base install CD in the drive and reboot. You will be greeted with the Ubuntu start-up menu that has a few options on it. Enter on the Install option. The install routine will analyze your hardware first then ask for your user name and password along with a administrator password. (Writing them down now would be a good idea.) It will also ask you to set up your DHCP to connect to the internet so have a computer name ready for your system. Next up is where you are going to install to. It will also ask where to put GRUB. This can be tricky to pick the correct drive to install to if your system has SATA drives on them like I do. See Linux sees the SATA drives as SCSI drives and assigns the drive names as SDA, SDB, SDC. Throw in a few partitions like I have and you have SDA, SDA1, SDB, SDB1 get the picture it gets confusing. So it is best to know what is in your USB drive. I have a Maxtor. My other 2 drives are Seagate. The partitioner GParted will list the drive as a Max 80 and the others as SB76xxxxxx. Now if you have an ATA drive they will show up as HDA, HDB. With the partitions as HDA(0,0), HDA(0,1), and the USB as SDA. Select the correct drive for you. As far as GRUB goes we want to install it to the drive that the system is being loaded to as you don’t have USB support and it won’t boot up anyway.  It will then ask how to partition the drive. The best method is to let it do it automatically. In my case I didn’t have any other options it just took the whole drive and split it up the way it wanted to with a ROOT, an EXT3, and a SWAP partition. And that was just fine as now I have plenty of room for Pics and Music. Click next and let it do its thing. When its done it will start to load files on the drive just sit back pop a cold one and relax. After the files have loaded it will want to reboot. Here’s the catch you can’t!!! You don’t have USB support so it can’t see the drive and will boot right into windoze. Not only that but now in windoze you can’t see the USB drive any more because it’s EXT3 file system isn’t supported! Great can’t see the drive and can’t boot to it. Or can we?!? We now need 2 things. 1)Ubuntu Live CD. 2) A little program for windoze called EXT2IFS by Stephan Schreiber. Time to fire up that browser again and Google for it. Download and install it with the USB drive turned on. When installed it will give your USB drive permanent drive letters. Why this program? Well it lets you see what’s on the drive as far as files, and it also lets you write to them. You’ll need this later.

Step 3) Ok you got your EXT2IFS on look at the USB drive. Are the files there? Good! The install worked. Now pull out the Live CD put it in the drive and reboot the pc. Choose the install from the menu and it will load the live version into memory and nothing on the hard drive. Welcome to Ubuntu! You can now access all the files on the drive. Um! Well sort of. Your running off the cd and not actually in the system. Oh Poopy! So to get your system to boot we need to create a boot CD. No we can’t do a boot floppy as it can’t hold enough info. To start the process to make the boot cd we need to edit a few files so the system can find the USB drive. It’s best to look around at the files on your system to get to know where some of them are. Look for the “Home” folder. It should have a folder in it with your name for login in it. We’ll be working in here. Look for etc/initramfs-tool/modules file. We’ll have to edit this file. Also etc/initramfs-tools/initramfs.conf file. Need to edit this also. Alright lets get started editing files.

Open a terminal (under Accessories – Terminal) type in the line;

gksudo gedit /mountpoint  for your harddrive/etcinitramfs-tools/modules   press enter

(Note; mountpoint  on my system is /media/disk this is because Linux sees the USB drive as a CD drive now.) 
This will open the text editor with that file. We will need to add these lines to the end of the file:

### This is a reminder that these modules have been added to allow a CD to boot a USB drive
usbcore
sd_mod
ehci_hcd
uhci_hcd
ohci_hcd
usb-storage
scsi_mod

(It is a good idea to put comments in so you know that you know what was changed) Now save the file and exit gedit.

There is one small problem we need to address before we go on. USB drives take a few seconds before they are set up by Linux, so it won’t boot if the drive is not there to be seen. To fix this we need to tell initrd file to wait for the USB drive to become available.
Open a terminal again and type in:

gksudo gedit /mountpoint for your harddrive/etc/initramfs-tools/initramfs.conf   Press enter.

Now insert  this to the very top line:

###This makes the bootup wait until USB drive is ready
WAIT=15

Then save file and exit editor.
Now that we have corrected the initrd’s setup we must use this setup to rebuild the initrd using the new guidelines. One thing we can’t do from the Live CD is the rebuild we don’t have permission to rebuild the files just see them. Time to reboot (you’ll be doing this a lot be prepared.) On shutdown Ubuntu will ask you to take the CD out of the drive do so and put in the text install CD but don’t close the door yet. When it’s all the way down it should close the door for you and restart. At the menu pick the rescue option (This is not on the Live CD.) it will read your system ask a couple of questions about your keyboard setup, install DHCP you can use default here. Then it will ask you where to boot to and show you the drives available with all the partitions. If you pick the wrong one it won’t boot. Just go back and pick the right one. On install my system said it was SDA but for some reason in here it was SDC go figure. It will ask you if you want to open a shell select YES. We are now ready to start editing. 
Type in command:

sudo chroot /mountpoint     (mount point is now sdb or sdc not /media/disk as before)
 
mount -a 

You should be in the root system now and can rebuild your initrd from here with the command:

dpkg-reconfigure linux-image-<kernel version>   ( mine was 2.6.20-15-generic)

You can get your version from looking at the files while its rebooting or from looking at the files on the system.
If the reconfigure command worked you should see some lines about rebuilding initrd, and updating GRUB. Now you can find your new initrd and matching kernel in /boot of your system and they are called initrd.img-<kernelversion> and vmlinuz-<kernelversion>.
You now need to boot back into windoze. Give a good 3 finger salute (CTRL-ALT-DELETE)  Linux will shutdown pull out CD and reboot.

When windoze reboots go to the USB drive in explorer and you should see your new files. All there? Great!!  We now need to copy these files along with the configuration file for the bootloader GRUB to the “HOME “ folder. This is where EXT2IFS comes in handy the Live CD won’t let you create a new folder you don’t have permission. Well we don’t need no stinkin permission in windoze.  Go to the “HOME” folder open and create a folder called “bootcd” open that folder and create one called “grub”. Remember Linux is case sensitive GRUB and grub are 2 different folders take care to write down what you call folders because 1 wrong letter and it won’t open up the folder.  Now copy the files vmlinuz and initrd.img to  the “bootcd” folder and rename them without the <version> on it. Also copy the from /usr/lib/grub/i386-pc the file “stage2_eltorito” to the grub folder. Also from /boot/grub folder “menu.lst”  ( that’s ellst not onest) to the grub folder. See how easy that was now.  The renaming comes in handy later when there are updates as you don’t have to rename the files then.

Step 4) Ok time to reboot again using the Live CD.  We now need to edit the menu.lst  with the text editor. Look at the bottom of the file where the actual OS entries are. Delete what is there and make two new entries (replace /dev/sda 1 with your root partition if this is not correct.):

title	Ubuntu

root	(cd)

kernel 	  /boot/vmlinuz root=/dev/sda 1 ro quiet splash

initrd	/boot/initrd.img

boot


title	Ubuntu Recovery Mode

root	(cd)

kernel	 /boot/vmlinuz root=/dev/sda 1 ro single

initrd	/boot/initrd.img

boot


Now save the file. By default the top entry will be booted. That is the entire contents of  your bootable CD, so now we have to build it. 

Reboot time. Use the text base install cd  again and boot into the recovery mode again sane as before we need to open a shell again. Type in:

genisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o UbuntuBootCDForUSB.iso /home/bootcd 


You should now have a CD image that is called UbuntuBootCDForUSB.iso
Reboot time, it’s back to windoze for you. Now look in the /home /bootcd folder this is where the .iso file should be. All that needs to be done is to burn it to a CD. May I suggest a rewriteable as it took about 5 tries before it worked properly.  The file is about 11 megs so you can see why floppies are out of the question. If all worked correctly it’s time to reboot one more time. This time using your shiny new BOOT CD. On boot you should be welcomed by the ever bland Grub bootloader with the choices of :

Boot to

Ubuntu

Ubuntu Recovery Mode

Windows your crappy version.



One note if you update the kernel version say to 7.10 Gusty Gibbon you will have to redo the boot cd again. Minor updates to 7.04 will still bootup. Now get going and enjoy the speed that you’ve been missing!!!

---

