---
title: "how to make a usb flash boot for trying jaunty"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jesse c on 2009-03-21
two questions:I just spent a couple of hours downloading a jaunty beta just to try it out.I went to system/admin/create usb boot but i didnt know how to get the file i just downloaded into the mix and another problem might be that i tried using an old flash drive that had a file already on it .Since i couldnt figure out the usb boot application i tried to just drag and drop the jaunty files from the desktop and now it reads that both old and new files are on the flash drive.Questions:Does the drag and drop method give the same result as the 'create boot file' since im using the same downloaded file if i had used a fresh flash drive,and now how can i clean out my flash drive now that theres junk on it ,i dont need to save anything thats on it now

---

### Post by Rallg on 2009-03-21
Cleaning out the flash pendrive:

This will also remove any boot sector that may be present on the pendrive. In your particular case, you probably want to do it this way.

Insert the pendrive, and when it mounts, right-click its icon. Find Properties > Volume > Mount Point. It is probably something such as

/media/YOURUSB

where "YOURUSB" is the pendrive's own label.

Again right-click the icon, and unmount the pendrive.

In Terminal:

sudo dd if=/dev/zero of=/media/YOURUSB bs=512

after it gets your password, it will write zeroes to all of the pendrive, including its boot sector (if the pendrive had a boot sector).

Now, you should be ready to use "Make USB startup disk." I don't know about drag and drop. To locate the *.iso file that you want, click "other" and navigate to the file. Also ensure that the USB device is correctly identified. I should mention that the best way to avoid problems is to ensure that no other removable device (such as an external hard drive or other USB, or iPod) is connected.

Keep in mind that when you create the USB startup disk, it is a "live" Linux that reads from a compressed file system. It will be slower than an unpacked installation, and it will not have the same ability to add and remove files.

---

### Post by jesse c on 2009-03-21
Rallg thanks for reply but how do i 'navigate'to the file after i hit other?
edit:I Just tried to clean up my flash using your method and no luck.when i right clicked my icon and checked mount point it read   /media/disk so i put that in your terminal line where you have  YOURUSB and when i clicked enter command it told me i changed directory but did nothing inside flash disk cause when i plug it back in it still finds old files

---

### Post by Yashiro on 2009-03-21
Or just use [http://sourceforge.net/projects/unetbootin/](http://sourceforge.net/projects/unetbootin/)

---

### Post by Rallg on 2009-03-21
If the pendrive is being mounted to /media/disk, that is unexpected. However, you can also locate it by device number, which might be something like /dev/sdb (but don't guess, since if you guess wrong you have BIG problems). Rather than describe what to do here, as Yashiro noted, "Unetbootin" might be your best bet. It is a Windows program that can do what you need to do (if you also have Windows). Although it has a selection of known ISO files built into its menu, in your case you will want to pick the ISO from the (Windows) desktop.

---

### Post by jesse c on 2009-03-21
Thanks for sticking with me Rallg but i checked out unetbootin but they dont have a Jaunty iso,just 8.10 which i already use.I was hopeing to learn to use the file system a little and i went out today and bought two new flash drives(2g and 4g)but i still dont know how to get the jaunty file i downloaded from ClubUbuntu.com into that 'other' section of the Intrepid 'create a usb start up disk'application but im afraid to plug in a new usb and get stuck at the same situation

---

### Post by Yashiro on 2009-03-22
Download .iso.
Download Unetbootin.
Run Unetbootin.
Select the 'iso' box.
Browse to iso file in Unetbootin (button on the right).
Write the files.
Reboot.

---

### Post by Rallg on 2009-03-24
One other possibility, easy to fix if true in your case:

Sometimes, when you install Ubuntu from a USB drive (instead of from a CDROM), the installed system thinks that the USB is a CDROM, and makes note of that. To straighten it out, use Terminal:

gksudo gedit /etc/fstab

After you give the password, a text file opens. Look through it, and see if there is a line showing /dev/sdb mounted to /media/cdrom (your details may differ, but this is the most likely scenario). If so, comment out the line by putting a hash # in front. Then save the file and re-boot. You will then be able to properly mount a USB.

This problem is fixed in recent builds, but is not retroactively fixed in prior installations, even if you update.

---

