---
title: "Installing Edgy on USB"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by b.treu on 2006-11-04
Thankfully this process works the same as with Breezy and Dapper. You can do the install SIMPLY and completely through the GUI. You just need to disable the automatic mounting of drives. I found the following exactly as you see it on the [Ubuntu Switch]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/") website. You only need to do the following:

To install Ubuntu on the external USB hard drive, I simply ran the install from the live CD just as if I were going to install normally. Before running the install, I plugged the USB hard drive in and Ubuntu detected it. Not only did Ubuntu detect it, but in mounted the drive. ](*,) This became a problem later when trying to partition the drive and create a file system because the drive was mounted.

To fix the problem System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

I then proceeded to install Ubuntu on the USB Hard Drive by clicking through the defaults in the installer. I chose to wipe my external hard drive and do a fresh install. If you have data on the disk you want to keep, choose to partition the disk appropriately. Be sure you are dealing with the right disk. The installer lists your main internal hard drive as /hda1/ more than likely and your external hard drive will be listed as /sda1/ or something similar.

Thank you to shakyone for pointing out the following to me.
MAKE SURE YOU DO THIS! OTHERWISE YOU WILL NEED TO PLUG IN YOUR USB DRIVE EVERY TIME YOU WANT TO BOOT YOUR COMPUTER. Don't ask how I know. ](*,)

"b.treu you are exactly correct, this is the easiest method. One change though, at the last step before it executes the installation procedure, it gives a summary. In there is a button for install GRUB to (hd0). Press this button and replace the text with

/dev/sda

and it works like a charm."

The last step after actually installing Ubuntu on the external USB Hard Drive was to get my laptop to boot from the USB. This was nothing more than pressing F2 at a normal boot to change the boot order to load my USB before my internal hard drive.
OR, just hit (in my case) F12 and it will provide you with a one time boot list. Choose USB, and voila! \\:D/ 

Best to all!

---

