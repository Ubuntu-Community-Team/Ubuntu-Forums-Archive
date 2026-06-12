---
title: "2 harddrives, 2 operating systems, how and clarification?"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by Griffin Bain on 2008-10-29
hmmm, I have ubuntu 8.04 as my primary operating system (actually my only). Yesterday I was given a second internal hardrive. I want to keep the second one unmounted in ubuntu and have that hardrive run my copy of XP that I had before I had ubuntu. Assuming I don;t boot them at the same time can I decide to run my machine in XP sometimes and Ubuntu others depoending on my needs?

I only ask because I believe when I first statred this linux adventure i kept reading stuff about windows installs disabling the ubuntu installs and I didn;t pay attention because I thought I was never going back to windows. My circumstances have changed and I want ( . . . and need) them both but I do not want to have to reinstall my 8.04 just because I installed XP.

fprgive my ignorance my mates, educate me if I am missing something.:-k

---

### Post by icanfly0307 on 2008-10-29
yes you can. that's the whole point of grub. btw, is xp already installed on the second hard drive or do you have to install it right now? 

in order to get xp working, all you have to do is configure grub to recognize your second hdd and whalla! that's it! 

let me know when you're ready to install the second hdd. i'll give a more detailed explanation then. :)

---

### Post by Griffin Bain on 2008-10-29
the harddrive was put into the computer last night by my dad. nothing else happened, but I did notice an icon for it in the file manager but did not do anything with it other than see the mounting notice it brought up which I just clicked out of.

there is nothing on the second harddrive and my dad doesn;t know the ins and outs of linux so I know he didn;t log in and do anything. I have the xp cds that came with the computer though so I should be ready to try this. However, I don't know what grub is other than just hearing about it before.

---

### Post by icanfly0307 on 2008-10-29
hi. i hate to say this and i'm not 100% sure but..........

if ubuntu is installed on your primary hdd, the windows xp cds will definitely delete ubuntu in the installation process. there is no way to make them install to the second hdd from the recovery cds. it's my personal experience. 

your only options are is to make a backup of all your data, install xp (overwriting ubuntu) and then install ubuntu from scratch on the second hdd. i know this is a big pain and maybe someone else has a better solution.

good luck!

PS. grub is the bootloader for linux. it's what tells the computer where to look for the operating system ie. xp, ubuntu, or whatever you have...

---

### Post by maniac_X on 2008-10-29
You can still do this in a round about way. I don't understand Grub enough to help on that end but this method will let you boot either your Ubuntu drive or your XP drive.

You said Ubuntu is installed currently on your main harddrive.

1. open up the panel on your computer and disconnect the drive with Ubuntu on it.

2. you should now have only the clean drive attached. set this drive to Master via the jumpers.

3. install XP on the drive.

4. set the jumper back to Slave or what it was before step 2.

5. connect your Ubuntu drive again. you should now have both drives attached.

6a. at this step is probably where you would want to configure your current Grub to add the option for the fresh XP drive. Someone here will need to give you those details...

.....or

6b. you can just reinstall Ubuntu on the original drive(backup any files you want/need first). During the reinstall, it should recognize and make entry in Grub for selecting XP during the bootup.

This will keep the XP install completely seperate allowing you to remove either drive at will. If you remove the XP drive, your Ubuntu drive is still intact. The only thing you might have to do is remove or comment out the XP entry from the Grub file. Likewise, if you remove your Ubuntu drive, just change the jumper on the XP drive to Master and you will be ready to go.

Note: if you have Sata drives, you probably don't have any jumpers to worry about. I'm still using old ATA drives ;)

.

---

### Post by uidb4056 on 2008-10-29
In this link [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) you can found examples how to handle it

---

### Post by bulldog on 2008-10-29
Just connect both hdd's and boot from the ubuntu hdd.
Add some lines at the menu.lst and it's done.
```
gksu gedit /boot/grub/menu.lst
``` to open the menu.lst with a text editor.
Add the entry for windows at the end of the menu.lst like this,```
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

