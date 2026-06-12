---
title: "error 17"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by vanja1610 on 2007-12-10
hi!
i have instaled ubuntu v7.10 (64 bit) in a dual boot with vista. I made 15 gb free space with vista disc manager and then preceeded booting ubuntu cd and instaling..I have only 1 hard drive with 3  ntsf partitions and those witch ubuntu made by defolt on that 15 gb free space
when my computer boots up i get (think its grub) telling me should i boot ubuntu or windows. Windosw works just fine but when i want to boot ubuntu it says error 17:cannot mount selected partition..!!
help please!=?

---

### Post by confused57 on 2007-12-10
> **vanja1610 said:**
> hi!
i have instaled ubuntu v7.10 (64 bit) in a dual boot with vista. I made 15 gb free space with vista disc manager and then preceeded booting ubuntu cd and instaling..I have only 1 hard drive with 3  ntsf partitions and those witch ubuntu made by defolt on that 15 gb free space
when my computer boots up i get (think its grub) telling me should i boot ubuntu or windows. Windosw works just fine but when i want to boot ubuntu it says error 17:cannot mount selected partition..!!
help please!=?
Boot into the Ubuntu desktop live cd, open a terminal and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Here's a description of grub error 17:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

The output of "fdisk -l" will show your partitions, here's what the root designation should be:
/dev/sda1...root (hd0,0)
/dev/sda2...root (hd0,1)
/dev/sda3...root (hd0,2)
/dev/sda4...root (hd0,3)
etc, etc

Once you determine which is your root partition, try booting your computer, highlight the Ubuntu entry in your grub boot menu, press "e" to edit, then highlight the line with root, press "e" again, change your root, press "enter", then "b" to boot.  This is temporary, if it works, but you can make it permanent.

---

### Post by vanja1610 on 2007-12-10
ok here's the terminal copy!
I'v tried to change the root from (0,0) to all combinations (0,1 to 9) and 1 of them worked but ubuntu won't start..(it just starts to boot but its like frozen)...
any further sugestions?
thank's!

---

### Post by vanja1610 on 2007-12-11
Hey people, i'm still on the same problem here. I was able to boot into recovry mode (if that can say anything to anybody...), but still when i try boot into ubuntu loading frezzez at system startup!
What should I do?

---

### Post by confused57 on 2007-12-11
> **vanja1610 said:**
> Hey people, i'm still on the same problem here. I was able to boot into recovry mode (if that can say anything to anybody...), but still when i try boot into ubuntu loading frezzez at system startup!
What should I do?
From the output of "sudo fdisk -l", I would assume root (hd0,6) was correct.  If you're able to boot into recovery mode & not the desktop, it's possibly a video card issue(what graphics card are you using?).
   The generic "vesa" driver may be able to get you to a GUI...boot into recovery mode, enter:
```
cd /etc/X11
cp xorg.conf xorg.conf_backup
nano xorg.conf
```
Page down to the video device section & change the video card driver to "vesa", with quotes...then save by "ctrl+x, y, enter"...then enter "reboot", without quotes.

You could try to see if there's any error messages booting, by pressing "e" with the Ubuntu entry highlighted in your grub boot menu, then remove the quiet and splash options in the kernel line, then press "b".  It "might" show an error that could give a clue, unless it freezes completely.

---

### Post by vanja1610 on 2007-12-11
i have ati x 1950 pro, pci
1. I can't write X or x in recovery mode-help on that please? (I get like a dot instead of x)
2. When I remove splash and quiet and try to boot it say's error 19: linux kernel must be loaded before initrd
I don't know if this matters but while having same problems I deleted linux partitions in vista manager and installed it again (in case of some old grub trapped in the system)

---

### Post by confused57 on 2007-12-11
> **vanja1610 said:**
> i have ati x 1950 pro, pci
1. I can't write X or x in recovery mode-help on that please? (I get like a dot instead of x)
2. When I remove splash and quiet and try to boot it say's error 19: linux kernel must be loaded before initrd
I don't know if this matters but while having same problems I deleted linux partitions in vista manager and installed it again (in case of some old grub trapped in the system)
Here's a little info on grub error 19:
[http://users.bigpond.net.au/hermanzone/p15.htm#19](http://users.bigpond.net.au/hermanzone/p15.htm#19)

You might try mounting your root partition, using the desktop live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Once you've mounted your root partition, you may want to post the boot entries in your /boot/grub/menu.lst.

---

### Post by vanja1610 on 2007-12-12
Thank's for the help and tips but still nothing! Here's what I get when I try to mount root partition...Em I doing somethin wrong there?
](*,)

---

### Post by confused57 on 2007-12-12
I think it might be the spacing in your commands:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda7 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
```

Try copy & pasting one line at a time in a terminal, press "enter" after each line.  I believe that's the problem...if it works, post your menu.lst boot entries.

---

### Post by vanja1610 on 2007-12-13
menu1 boot etries are or is empty..but when I press open in text editor i can find one menu1 ..Here's everything in screenshots and files.(This menu1 is the one i can simply open in text editor).

---

### Post by psusi on 2007-12-13
What are you talking about?  Paste the contents of that file.

---

### Post by vanja1610 on 2007-12-13
I'm saying when i wrote the code in terminal, boot meni1 just poped up in text editor like shown in screenshot2 and it was empty-no text!!

---

### Post by psusi on 2007-12-13
It's menu.lst ( that's an L not a 1 ) and your screen shot shows the contents of the file.  Just copy and paste it here.

---

### Post by vanja1610 on 2007-12-13
Sorry, I was that sure it says 1 not L i didn' check it out?
So here it is, i hope.

---

### Post by psusi on 2007-12-13
Just copy and paste the results rather than save them to a text file and attach.  I can't read that txt file properly on windows here at work.

You said before that you managed to manually find the correct (hd0,n) to boot?  Edit menu.lst and make sure that it has the same value for the root command.

---

### Post by confused57 on 2007-12-13
You might try booting up the Ubuntu live cd & opening Gnome Partition Editor(System--Administration--Gnome Partition Editor)...then try removing the boot flag on /dev/sda7.
I don't know if this may be causing your problem, but I think you can have only one partition with the boot flag on a single hard drive.  Anyway, Ubuntu doesn't need the boot flag active.

Once you made this change, then try booting into Ubuntu, using root (hd0,6), by pressing "e" at the grub boot menu, etc.

psusi, here's his Ubuntu entry:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

The Vista entry also has root (hd0,0), which is correct.

---

### Post by psusi on 2007-12-13
You should only have one partition with the bootable flag set, but only DOS/windows pays attention to that.

---

### Post by confused57 on 2007-12-13
I just noticed, your kernel line needs to have root=/dev/hda7, which should probably be /dev/sda7:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Gutsy 7.10 uses UUID's for root in the kernel line, e.g. root=UUID=string of letters/numbers...if you /etc/fstab is using UUID to mount your root partition, you may have a problem with /dev/hda7 in the kernel line.

Use the Ubuntu live cd, mount your root partition & post your /etc/fstab:
```
gedit /media/ubuntu/etc/fstab
```

Your best course of action would probably be to reinstall Ubuntu, select "Manual" partitioning and reinstall over your current Ubuntu partitions.

---

### Post by vanja1610 on 2007-12-14
So I'v instaled it manually and still have to edit the root to mount and then it again frezzez at boot time. The instalation removed the boot flag from linux partition so there is only 1 now. And here is the fstab!

---

