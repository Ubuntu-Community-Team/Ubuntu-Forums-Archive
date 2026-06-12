---
title: "USB stick"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by meatmaker on 2010-09-26
I am new to ubuntu and computer programming for that matter so I may have been too bold in trying to do this without a wizards help, but...
I am in the process of installing ubuntu on to my Mac OS X using the USB stick method and a question has arose, can I revert my flash drive back to its orginal state now that I have changed it?

---

### Post by meatmaker on 2010-09-26
I have this strange feeling that you can't change it back

---

### Post by lbrty on 2010-09-27
What do you specifically mean? Revert back to original file system or data of the USB flash device?

---

### Post by meatmaker on 2010-09-27
Sorry do not know all the correct speak. I meant to the original file system, but I figured out how to do it. I have a new problem now though because when I follow these instructions (which are from the ubuntu [download page]("http://www.ubuntu.com/desktop/get-ubuntu/download")):

 
1. Download the desired file

2. Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)

3. Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format    UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
Note: OS X tends to put the .dmg ending on the output file automatically.

4. Run diskutil list to get the current list of devices

5. Insert your flash media

6. Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)

7. Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)

8. Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).

9. Using /dev/rdisk instead of /dev/disk may be faster.
If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.

10. Run diskutil eject/dev/diskN and remove your flash media when the command completes

11. Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick

I do not see the USB-Stick as an option. Almost positive I have followed the instructions to the dot, but still do not get the expected results. Any suggestions? Or should I just drop the $ for some CD/DVD's to create a Live CD?

---

### Post by lbrty on 2010-09-28
Please clarify what you actually trying to do with what system setup and configuration. Once you clearly state what type of problem you're having, the community can better assist you in finding a solution. =)

---

