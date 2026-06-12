---
title: "Help! Ubuntu Works fine, but Vista doesn't"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by mustang_jt on 2007-06-23
I have tried linux disto's before and given up because they were difficult, but at the advice of my brother decided to give Ubuntu a try.  I have a Dell, Lattitude 9400 with the dreaded ATI X1400.  Anyway, it was not so easy to install because of the ATI Card, and the way Dell had the partitions set up, and I ended up using the latest GParted live CD to move my Vista partition to the front of the drive and install Ubuntu behind it.  Well, Ubuntu works great, I even got Beryl working, but Vista will not boot.  I have searched the forums and found plenty on that subject but nothing has worked to fix it.  Vista will sort of boot, but it boots to a blank blue screen with a cursor.  I am able to CTL-ALT-Delete and start Task Manager and then use that to start explorer.  Once Explorer is started it says that my user profile wasn't loaded properly, and pretty much everything doesn't work.  I can't even run Setup.exe off of the Vista disk, it says that the file is not found.  All of the information appears to still be there it just won't boot up. After searching the forums I have tried repairing the Vista installation with the Vista disk and also by running chkdsk off of a XP disk.  According to what I have found, that has fixed it for everyone else, but it did not work for me.  I really don't want to re-install Vista if I don't have to and re-load all of my programs.  Please help.

thanks

---

### Post by Pumalite on 2007-06-23
The bad news are that Vista requires that you partition FROM Vista to work. Somebody else might have better advice, especially if a Vista user.

---

### Post by digital_exhaust on 2007-06-23
You don't have to partition from within Vista in order for it to work.. as long as it's on a NTFS partition, it doesn't really matter... but it sounds like something went wrong when whatever bootloader your using (grub, I assume) was installed and it borked your Vista install somehow...

I don't mean to sound harsh, but if you are going to be dinking around with OS partitions that you care about, an image of that install is something you should have in place before you begin.. that way re-installs are no big deal.. 

I know this isn't exactly helpful, but the only advice I can offer is to start over..

---

