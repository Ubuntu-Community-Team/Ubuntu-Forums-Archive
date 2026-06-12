---
title: "HDD Transplant"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by GuitarHero on 2006-06-28
Ok right now I have twp computers:
Crappy old compaq with ubuntu on it
Freakin Sweet home built computer with a windows hdd and a storage hdd.

I want to remove the storage hdd from the good computer and put it in an exeternal enclosure.  Then i want to take th ubuntu HDD and put it in the good computer.  How will I set it up to boot correctly?  I need grub to recognize both OS's and let me choose when i turn the computer on.  Will simply putting in the hdd do it?  Also in the good computer I have an ATI Radeon X1900XT video card.  How will i install the drivers when i know ill get an Xserver error from startup?  Should I install the ati drivers on the ubuntu HDD while still in the compaq?


Also if anyone knows anything about external hard drives, do i just put the jumper on master and install it into the enclosure?


Lots of questions i know.

---

### Post by glotz on 2006-06-28
You will need to edit /boot/grub/menu.lst accordingly to your setup. (The hd(x,y) locations specifically.) I think you don't need to add the correct ATI driver beforehand. See here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by GuitarHero on 2006-06-28
so i should edit the grub file, shut down, then remove the hard drive correct?

---

### Post by confused57 on 2006-06-28
I have my system set up this way:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you have Windows on your built computer, you could set it as the slave and
Ubuntu as the master drive...then add the Windows grub entry.

---

### Post by glotz on 2006-06-29
Yeah, that's the racket.

---

### Post by GuitarHero on 2006-06-29
Alright hopefully all goes well, but something always goes wrong when i try to do anything it seems so we'll see.

---

### Post by GuitarHero on 2006-06-29
Ah well ive made the switch and ubuntu booted up fine and the ati drivers work first try! I was surprised.  Now to figure out how to add windows to grub and ill be good.

---

### Post by glotz on 2006-06-29
Welcome to Ubuntu! :)

---

### Post by GuitarHero on 2006-06-29
Ah its nice to have ubuntu on a good computer.  I still need windows for games and recording, so i need grub working.  I got this code from another thread that the one you linked to linked to.:
```

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```
will this make my slave windows drive appear on the grub list?

---

### Post by confused57 on 2006-06-29
That entry should do it...see the thread I gave you for how to edit your
/boot/grub/menu.lst.

If it doesn't, post back, it shouldn't be a problem to get your system booting Windows from grub.

---

### Post by GuitarHero on 2006-06-29
Well I tried editing that file but it wont let me due to permissions.  It never asks me for a password.  I tried using natuilus to just go there and edit it plus gedit /boot/grub/menu.lst

How do I get it to allow me

---

### Post by confused57 on 2006-06-29
Open a terminal:  Applications--->Accessories--->Terminal

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
I should have mentioned, copy & paste the above one line at a time & press enter each time...the last command actually opens up your menu.lst file.

Copy & paste the following lines above;
###BEGIN AUTOMAGIC KERNEL LIST
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
The above code, you'll copy & paste the entire entry at one time to your /boot/grub/menu.lst. 

Find the line "Hidden" and place a # in front.e.g.  "#Hidden"
You might want to change the timeout from 3 seconds to 10 seconds.
You might want to read over this link again:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Hope this helps, post back if you have any questions...it should work.

---

### Post by GuitarHero on 2006-06-29
I added that code.  THen i didnt have to do anything to hidden because it already ahd two #'s.  Now ubuntu stops loading on checking all filesystems.  WIndows is on the grub menu but it cant find it when i click on it.  How do I fix it????

---

### Post by confused57 on 2006-06-29
[QUOTE=GuitarHero]I added that code.  THen i didnt have to do anything to hidden because it already ahd two #'s.  Now ubuntu stops loading on checking all filesystems.  WIndows is on the grub menu but it cant find it when i click on it.  How do I fix it????[/QUOTE]
The changes shouldn't have affected how Ubuntu loads...when the grub menu loads, what happens when you press "down" arrow to highlight Ubuntu, then press enter?

You might want to go into bios when your computer is booting up to make sure that the slave drive is detected...if not, set to "enable" or "auto".    Edit:  Just read your first post again, shouldn't be an issue since you used the slave drive as a storage hd.

If your slave drive is detected, when the grub menu appears at bootup and the windows entry is highlighted, press "e" to edit the boot options for Windows.  Try changing the root (hd1,0) to (hd1,1) & boot with that changed... if this doesn't work you might also want to try changing root to rootnoverify (hd1,0).
This change won't be permanent, but if it works, it can be made permanent in your menu.lst.

If none of this works, bootup with a Live CD, open a terminal and post the output of:

```
fdisk -l
```
The -l is a lowercase "L".

This will tell you what your partition tables are on both hard drives.

---

### Post by GuitarHero on 2006-06-29
rootnoverify and 1,1 made windows boot, now to see if ubuntu will boot

---

### Post by GuitarHero on 2006-06-29
No, ubuntu doesnt boot because i cant save the changes.  I boot into windows, then shut down and the settings revert.  would the windows problem be affecting my ubuntu boot?  i wouldnt think so, but i cant think of anything else..... what to do now?

---

### Post by GuitarHero on 2006-06-29
fdisk -l gives me this:

hda1 1 2377
hda2 2378 2482

extended
hda5 2378 2482


should there be two partitions there?  both hda2 and the extended hda5 start and end at the same place.

---

### Post by confused57 on 2006-06-29
[QUOTE=GuitarHero]fdisk -l gives me this:

hda1 1 2377
hda2 2378 2482

extended
hda5 2378 2482


should there be two partitions there?  both hda2 and the extended hda5 start and end at the same place.[/QUOTE]
hda5 is probably your swap partition(probably a logical partition), I don't understand the hda2 extended partition and the hda5 swap partition occupying the same "sectors?".

You could highlight the Grub Ubuntu entry when your computer is booting up and press "e" (same as you did for Windows)...see if the root is (hd0,0).  I really don't understand how the changes you made could have affected booting Ubuntu, I've set up 2 different computers using this method and have had no problems...I'm still learning Ubuntu myself.

If this doesn't work, maybe you could try disconnecting your Windows slave drive and see if your master drive with Ubuntu will boot(making sure to select or highlight Ubuntu in grub).  If you still can't boot Ubuntu, you could try restoring grub(while you have your Windows drive disconnected):
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub)

---

### Post by GuitarHero on 2006-06-30
I tried restoring grub.  But the second step, root (hard drive, number) wouldnt work.  i tried hda1,0    hd0,0    hd0,1  hdd0,1

None worked it gave me some number proccessing error or something..  what two values do i use.

---

### Post by glotz on 2006-06-30
The first number is the number of the physical disk and the second is the partition. Both count from 0 up. Use system > admin > disks to figure out your numbers.

---

### Post by confused57 on 2006-06-30
[QUOTE=GuitarHero]I tried restoring grub.  But the second step, root (hard drive, number) wouldnt work.  i tried hda1,0    hd0,0    hd0,1  hdd0,1

None worked it gave me some number proccessing error or something..  what two values do i use.[/QUOTE]

Does your computer boot normally to Windows if the drive is connected as the master drive?  If it does, then your Windows drive mbr hasn't been altered.

If you've established that, then you could try just connecting your Ubuntu drive as master(Windows drive disconnected), and try to restore grub this way:
[quote=remmelt]
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.[/quote]

For #4 above, your root should be "root (hd0,0).  I haven't tried this, but it may work for you.  The only other alternative I can offer is reinstalling Ubuntu, disconnect your Windows drive if you don't want grub to be installed to the Windows mbr.

If you don't mind grub being installed to the mbr(be sure to backup any data on the Windows drive you don't want to lose), you can check out these 2 links:
[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by GuitarHero on 2006-06-30
Windows boots as master so its mbr is in tact.  root (hd0,0) gives me a device not found error, and root (hda,0) gives me an error pasring number error.

---

### Post by confused57 on 2006-06-30
[QUOTE=GuitarHero]Windows boots as master so its mbr is in tact.  root (hd0,0) gives me a device not found error, and root (hda,0) gives me an error pasring number error.[/QUOTE]
Great that your Windows drive hasn't been affected.  Grub uses different designations for hd's and partitions than fstab or "device manager?":

For example, hda1 in your device manager would be designated hd0,0 in grub.
(hda2 = hd0,1), (hda3 = hd0,2);  (hdb1 = hd1,0),  (hdb2 = hd1,1) for your slave drive.

When you're installing Ubuntu, the master drive would be designated hda and the slave drive would be hdb; if you installed Ubuntu with both drives connected.  Therefore, if you know that Ubuntu is connected as the slave drive, you would select hdb to install Ubuntu on...Windows would be hda on the master drive.  As I mentioned before, installing Ubuntu this way would place grub onto the mbr of Windows on hda...and there is always the possiblity that problems could occur that you would need to fix the mbr on Windows using the Windows install disk.
That's why I prefer to dualboot Windows & Ubuntu using 2 hard drives using the method I outlined for you and gave a link for, this way doesn't install grub to the Windows mbr.

You could try checking out the link on the other thread of yours concerning grub at the bottom of the page:
[http://www.ubuntuforums.org/showthread.php?t=206375&page=2&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=206375&page=2&highlight=grub)

Use the LiveCD as mentioned, and mount hda1 as described...if you backed up the menu.lst, you could type the command:
```
cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

It might just be easier in the long run to try reinstalling Ubuntu(with Windows drive disconnected, if you don't want grub on the mbr)...

I was a beginner once, so I know how confusing it is at first...I'm still learning, long way to go.   At least you're learning in the process, in spite of the frustrations...Try to give a little more detail on what you're doing, error messages, etc, that'll help immensely for someone trying to help you find a possible solution.

---

### Post by GuitarHero on 2006-06-30
Yes this is very frustrating but i dont want to reinstall ubuntu because i put a lot of programs on it.  I installed ubuntu onto the harddrive in a separate computer, and then moved it over.  But it was the master in the other computer so it should still be hda i guess.  I will try to mount hda.

---

### Post by confused57 on 2006-06-30
[QUOTE=GuitarHero]Yes this is very frustrating but i dont want to reinstall ubuntu because i put a lot of programs on it.  I installed ubuntu onto the harddrive in a separate computer, and then moved it over.  But it was the master in the other computer so it should still be hda i guess.  I will try to mount hda.[/QUOTE]
Just a thought, but have you tried booting Ubuntu up in recovery mode...when the grub menu is displayed, arrow "down" to Ubuntu recovery mode & press enter, if it works it'll bootup to a command prompt.  If it does(worth trying),
you can:
```
cd /boot/grub
sudo cp menu.lst_backup menu.lst
```

this would restore your original menu.lst...

Good luck...

---

### Post by GuitarHero on 2006-06-30
Ive tried it to the same result.

Well after a day of trying everything i could think of i gave up and reinstalled ubuntu. And the problem persists.  It still hangs on checking all file systems or whatever and thats after a reinstall with no windows hard drive in the equation.  Somtimes after a long time, it will go to a black screen with the white text of the check list and checking file systems says ok, but then checking network devices or whatever doesnt work and eventually the screen goes black or grey and thats it.  I cant believe a reinstall didnt format it.  That means it has to be a problem with bios or something doesnt it?  I can still get to windows, i just unplug the ubuntu drive and plug in the windows drive.  So its probably not a hardware problem.  BIOS maybe?  I didnt change anything though.... what do i do?

Oh and when i reinstalled with the live cd i restarted and it booted into ubuntu.  I couldnt get my wireless network card to work.  i configured it and checked it with iwconfig, it appeared to be detected, configured, and connected.  But i still could get to the internet.  So I rebooted, and i discovered the problem was still going on.  Why would it have booted after the install but not after using it for a short bit?  I had my network card working with ubuntu before i tried to add the windows drive....

---

### Post by confused57 on 2006-06-30
[QUOTE=GuitarHero]Ive tried it to the same result.

Well after a day of trying everything i could think of i gave up and reinstalled ubuntu. And the problem persists.  It still hangs on checking all file systems or whatever and thats after a reinstall with no windows hard drive in the equation.  Somtimes after a long time, it will go to a black screen with the white text of the check list and checking file systems says ok, but then checking network devices or whatever doesnt work and eventually the screen goes black or grey and thats it.  I cant believe a reinstall didnt format it.  That means it has to be a problem with bios or something doesnt it?  I can still get to windows, i just unplug the ubuntu drive and plug in the windows drive.  So its probably not a hardware problem.  BIOS maybe?  I didnt change anything though.... what do i do?

Oh and when i reinstalled with the live cd i restarted and it booted into ubuntu.  I couldnt get my wireless network card to work.  i configured it and checked it with iwconfig, it appeared to be detected, configured, and connected.  But i still could get to the internet.  So I rebooted, and i discovered the problem was still going on.  Why would it have booted after the install but not after using it for a short bit?  I had my network card working with ubuntu before i tried to add the windows drive....[/QUOTE]

It could be a problem with your ATI video card, see if there's anything in this thread that may help:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

You could press "Ctrl+C" when Ubuntu is checking network devices, to bypass this step during startup to see if Ubuntu will continue booting up.

---

### Post by GuitarHero on 2006-06-30
Yes that could be it.  But im not getting any xserver errors.  Plus theres no place where i get a command line to do a dpkg reconfigure.  Ill try the ctrl+c deal.

---

### Post by GuitarHero on 2006-06-30
I did ctrl c and it continues to boot to the login screen(the screen glitches right before it goes to login but it does get there).  I log in and then it just goes to the brown screen with a pointer.  The little splash screen where nautilus/gnome ect load never comes up.  I even tried reinstalling ubuntu again.  I installed it, did the reboot out of the live cd and it goes to ubuntu.  At that point i entered my essid and DHCP for my wireless card an enabled it.  It didnt work so rebooted and i got the holdup on boot again.  COnfiguring network devices is right after checkinf file systems so i now believe it has something to do with my network card or something.  I cant understand how that would ruin my booting though.  Im completely annoyed with ubuntu right now but i still seek an answer.  Las time when i had it working, i installed it on another machine with a different network card so i dont know if it used different drivers or something but now i have no idea what to do.

---

### Post by confused57 on 2006-06-30
[QUOTE=GuitarHero]I did ctrl c and it continues to boot to the login screen(the screen glitches right before it goes to login but it does get there).  I log in and then it just goes to the brown screen with a pointer.  The little splash screen where nautilus/gnome ect load never comes up.  I even tried reinstalling ubuntu again.  I installed it, did the reboot out of the live cd and it goes to ubuntu.  At that point i entered my essid and DHCP for my wireless card an enabled it.  It didnt work so rebooted and i got the holdup on boot again.  COnfiguring network devices is right after checkinf file systems so i now believe it has something to do with my network card or something.  I cant understand how that would ruin my booting though.  Im completely annoyed with ubuntu right now but i still seek an answer.  Las time when i had it working, i installed it on another machine with a different network card so i dont know if it used different drivers or something but now i have no idea what to do.[/QUOTE]
At the login screen, press Ctrl+Alt+F1, this should get you to a console, where you can login and enter:

sudo dpkg-reconfigure xserver-xorg

after you get your xorg configured, at the prompt, enter:

startx

that should get you into a GUI.

I don't know anything about wireless network cards, but maybe you can do a search for enabling or if you can't find anything, start a new thread(be sure to mention what kind of network card you have & how you connect to the internet, etc.

---

### Post by GuitarHero on 2006-06-30
Ive done some more testing and its definatly the network card.  I reinstalled ubuntu without the network card in and rebooted, it worked.  I Turned it off, put the network card in, and booted, it worked.  I enabled and configured the network card and rebooted, and then the problem came out again.  I guess this isnt an intsallation problem anymore so il post in the networking forum, feel free to post in it if you can help. 

Thank you so much for the help you've given me so far.  Im not giving up.

---

### Post by confused57 on 2006-06-30
[QUOTE=GuitarHero]Ive done some more testing and its definatly the network card.  I reinstalled ubuntu without the network card in and rebooted, it worked.  I Turned it off, put the network card in, and booted, it worked.  I enabled and configured the network card and rebooted, and then the problem came out again.  I guess this isnt an intsallation problem anymore so il post in the networking forum, feel free to post in it if you can help. 

Thank you so much for the help you've given me so far.  Im not giving up.[/QUOTE]

Glad you're not giving up, hang in there...it'll be worth it, I'm sure other people have had the same problems with configuring a network card and will be able to share their solutions.
Best of luck...

---

