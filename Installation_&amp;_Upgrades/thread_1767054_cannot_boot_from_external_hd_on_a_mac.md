---
title: "cannot boot from external hd on a mac"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by dr_chad on 2011-05-25
Hello,

I have been trying for many days now to get ubuntu installed on western digital passport 1 TB USB external hd attached to my MacBook Pro (with intel Duo Core processor).  I have installed the latest ubuntu 11.0.4 64-bit (needs to be 64-bit for work) on the external USB hd, and when I reboot rEFIt shows a new penguin icon.  So, I selected that, and I see a screen with a penguin in the middle for a while, but then the screen turns black and just has a text error message that says "No bootable device -- insert boot disk and press any key".  BTW, I checked that my Duo Core is definitely 64-bit.  Also, ubuntu does run off the install CD.  Even the wireless works and I can use firefox.

I have been reading lots of forums trying to find a solution.  A couple that I have tried:
1) reboot and when in rEFIt, choose the sync option and resync the drives.  I did that and now the penguin icon just launches a black screen with a different message about "no valid operating system" or something like that.  
2) Another site said the key was to change where boot loader got installed, so during the installation, at some point near the end, there would be an "Advanced" button to click on, and in there I could set grub to install onto sdb, the location/name of my external USB hd.  However, in the present version 11.0.4, there is no "Advanced" button on any of the install screens.  

Any suggestions would be appreciated.  I really wish Mac just used a BIOS instead of this frustrating EFI.  Do I need to edit or alter something somewhere?  If so, exactly what?

  
Thanks,

Chad

---

### Post by drunkfish on 2011-05-25
I run Ubuntu11.04-x86_64 from a external USB harddisk which machine is installed Win7. I do not know MAC, just tell you my experience. When I install Ubuntu, I disconnected the internal HD, just connect the USB HD. Boot the machine form the install CD, and set the BIOS boot sequence CD-USB-HD. After that I re-connect the internal HD; boot from external disk, it seems Ubuntu could recognize the Win7 and list it in the boot menu. Everything work properly.

When I install my second Ubuntu, I find I need not disconnect actually, from the install menu, select manual allocate the partition, and select the boot loader install on your external disk, it will get the same result as above.

If you are not family define the partition in Ubuntu, you could try the first way. 

Sorry for my poor English.

---

### Post by dr_chad on 2011-05-25
Thanks for the info about your experiences installing on a usb hard disk.  Your english is fine.  I have installed linux on many standard pc clones, with or without existing windows installations.  But, this is my first attempt to install any linux on a Mac.  The problem seems to be that there is no BIOS on a Mac.  Instead, they have to be different, and use an EFI.  Fortunately, someone wrote rEFIt, which gives a boot menu to select different operating systems.  The only problem is that they did not think of it to support booting linux from an external USB drive.  I have twice installed Ubuntu to the external drive, but rEFIt will not boot it afterwards.  I just a screen with a penguin briefly, then a blank screen, with a text error message as I previously described.  I have 8 or 9 days on this now and cannot find any forums, wikis or anyone with a solution that actually solves this problem.  Whoever wrote rEFIt needs to improve it to support booting to external usb drives.  If anyone has any other ideas to circumvent this problem, please let me know.


Thanks,

Chad

---

