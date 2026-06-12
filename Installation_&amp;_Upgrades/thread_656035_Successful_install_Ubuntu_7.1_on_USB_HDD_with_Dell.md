---
title: "Successful install Ubuntu 7.1 on USB HDD with Dell Inspiron B130 laptop"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by alexandroid on 2008-01-02
Hi all,

Today I finally managed to install Ubuntu 7.10 and would like to describe my experience. I have some questions and notes open which I list at the end and refer to through the text.

First, I would like to thank to the authors of posts which helped me -- [DaBruGo's post]("http://ubuntuforums.org/showthread.php?t=80811"),  [Ubuntu Switch blog]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/") and [post explaining boot process details]("http://www.nabble.com/Grub-td12216387.html#a12218543").

DaBruGo described installation of Fiesty Fawn, while I did Gutsy Gibbon, so everything went simpler and more close to described by Ubuntu Switch. Another difference was that I used Live DVD for installation and not Live / Alternate CDs. This caused an open question [1].

Why I used Live DVD is simple: 1) I wanted to have the most full package, just in case, since it was not clear what CDs does not have comparing to DVD. 2) I do not have CD-R blanks to burn CD ISOs on =).

My goal was to install Ubuntu 7.10 on external USB HDD (WD Passport 160 Gb) without affecting Windows XP on the laptop (have MBR intact too). The laptop is Dell Inspiron B130 (Pentium M 1.7 Gz, 1 Gb RAM, 80 Gb internal HDD.

In the end, the main problem turns out to be with laptop/BIOS which mislead me from the beginning. I've reinstalled Ubuntu around 4-5 times till I actually got what is happening. =\

Ok, the final process, as I remember is simple and straightforward:
0. Setup proper boot order in BIOS: CD, then USB devices, then internal HDD. Connect USB HDD.
1. Reboot with Live DVD inserted, Boot into live Ubuntu 7.10 on it.
2. Connect to WiFi network (enter password for it [2]), make sure it works by launching Firefox and trying to load web pages.
3. Run terminal and execute 'sudo fdisk -l' to see what device name USB HDD got assigned --> /dev/sdb in my case. (Internal HDD was /dev/sda and it was clear which device is what  by size -- 80 Gb vs 160 Gb).
4. Run install. Optionally, unmount USB HDD and optionally uncheck [preferences to mount it]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/"). However I think install script or partition editor unmounts it automatically anyway.
5. On partitioning step, select "Guided - use entire disk" for USB HDD (sdb in my case, the size again was indistinguishable). In advanced options change path to install boot loader from (hd0) to /dev/sdb.
5.1 Frankly, I am not sure if it worked this way last time, cause during some attepts I got errors later during install that Grub cannot be installed because device name is wrong or smth. I tried installing Grub manually once, but I *think* on last clear attempt it worked all automatically and successfully with /dev/sdb. [3]
6. Do not reboot, open "Places - Computer" browser, mount USB HDD back (do not remember -- double click on it to browse or right-mouse-click and select "mount"). Enter it, note the path on the top (press on arrow to show it all). Normally it is smth like /media/disk.
7. Open terminal, 'sudo chroot /media/disk', 'sudo vim /boot/grub/menu.lst'. See [DaBruGo's post]("http://ubuntuforums.org/showthread.php?t=80811") for link to vim cheatsheet.
7.1 Add another '#' in fron of line '#hiddenmenu' to comment it out. [4]
7.2* Change (hd0,0) to (hd1,0) in #groot line.
7.3* Change (hd0,x) to (hd1,x) in boot menu options at the end of the file (where x is some digit like 0 or 1 or 2 etc, leave it unchanged) and vice versa (i.e. replace hd1 by hd0) in boot menu options. In my case there were 3 options for Ubuntu (generic, rescue and memtest86+) and 3 other options for internal HDD -- Dell Utility partition, Windows XP Home edition and "Windows NT/2000/XP" (not sure what it is, probably Windows installation files used by Windows rescue), [6]
7.4 Save changes by exiting vim via ':x'.
8**. Now reboot (and take out DVD or leave the tray open, glad my laptop cannot close it back).

* In my case I did not do these steps initially and tried booting (see booting dance below). This resulted in "Grub error 17: cannot mound selected partition" (if I remember the wording correctly), so doing 7.2-7.3 was clearly the thing to do at this point. 

** Note I did not do usb-ehcd / initramfs trick described by DuBraGo at all, the only changes were to comment #hiddenmenu and swap hd0 and hd1 in /boot/grub/menu.lst. I did not do grub-update or anything like that either [5].

Rebooting and booting on my laptop turned out to be a real tricky thing. Imagine my frustration when I got everything as described, was rebooting and seeing only blank screen with blinking cursor in top left corner. No keys working, HDD is not seems to be read, no Grub menu -- nothing.

At some point I even thought that maybe BIOS not really supports booting from USB, even though it provides USB in a list of devices to boot from (actually some guy on #ubuntu IRC channel asked me if I am sure about that, sorry do not remember his nick). So I booted back to XP, took my USB 256 Mb flash stick and [made it Win98 bootable in 10 minutes]("http://www.bay-wolf.com/usbmemstick.htm").

Rebooting from it was a breeze. =) After wiping out tears of nostalgia from working in Win98's DOS, its simplicity and predictability, I switched back to problem of booting my Ubuntu... There were other attempts to install... from console installer, more reading DaBruGo's post, adding magic usb lines, trying to execute 'mkinitramfs' described, reading internet about "blank screen" problem, reinstalling, updating grub, editing devices.map, adding nosplash to defoptions in menu.lst etc etc etc...

During one of the attempts I saw Grub menu! I could not understand what happened, since I did not change anything recently. However, when I tried selecting "Ubuntu" to boot, I very quickly got kernel panic after which laptop froze completely (powering off and was required). Rebooting once again brought me to blank screen again. Grub menu was gone.

Soon after that I did 'clean' reinstall of Ubuntu and started to dance with the booting from the start, since it was clear that Grub is there and I just do not see it consistently.

The final tambourine trick (thank you Dell (?) / WD (?) for my time):
1. Disconnect USB drive.
2. Reboot and press pause continuously to stop it as soon as possible.
3. Connect USB drive. Give it 5-10 seconds to spin up and be recognized by BIOS.
4. Unpause.

It looks like during reboot USB drive gets turned off and on and somehow does not initialize properly or completely to let BIOS boot from it. BIOS does see it and tries to boot from it, but somehow it does not work this way (using F12 instead of pausing and waiting in BIOS's menu of boot-from devices, then explicitly selecting USB does not work either, resulting in blank screen again).

When I figured the last dance (and swapped hd1<->hd0, in my case I did it later by booting in Live DVD once more, again question [1]), Ubuntu finally booted. No errors.

And then I found out that I forgot my password and cannot login. Oh boy! =))))

Ok, after some break I recalled the password. It seems that during installation I was asked about the password for my account with using some wording similar to "key ring" thing (I am sure there was 'ring' word somewhere), so I got confused about [2] again and entered another password than I wanted to use for my login initially. The fact that I was not asked for other passwords just slipped out of my head and since I booted way later after install, this detail did not come up to my mind either.

The good thing: hardware works ok. Graphics works. Sound is here, no MP3 support in default player -- bummer, so I turned on internet radio so far. And while I was writing this post, Rhythmbox player crashed twice with "internall data flow error", so I had to restart it. Mouse and touchpad are ok, WiFi card works ok, however I could not set up static IP yet and gave up with "roaming mode" (fancy name for DHCP? ;-)). Maybe another day.

Another striking thing was that Ubuntu asked to download and install around 139 updates right after the boot. That was ok and expectable, The biggest surprise was that it asked to reboot after installing them. OMG! Linux, asking to reboot after updating some packages?!! That was very unpleasant one. I thought that these *ugly* Windows habits never happen here, since everything can be achieved by restarting X, Gnome, daemons -- whatever... unless the kernel is not updated. This is my final open question actually -- why Ubuntu asked (askes?) to reboot after installing updates?


Next in my list:
1. Setting up static IP + port forwarding.
2. Check out if it is possible to copy Firefox settings from Windows to Ubuntu.
3. Shrink ext3 partition and make some space for FAT32 to be able to use it from Windows, since I do not need it all for Ubuntu anyway.
4. Find & install some stuff: mp3 player, torrent client, Apache+mod_perl+Mason+MySql (another dreams come true)+maybe update perl to 5.10,
5. Do something with screen space, I feel like because of those bars on top and bottom I have less screen space than on Windows... =\

PS: Happy new year! =) (while I typed this post, Jan 2 started, but anyway ;-)) 

-------
Open questions and comments:

1. Where is the rescue mode on Live DVD? Boot menu does not have any notions about it. If enter command mode (by pressing ESC in LiveCD menu) typing 'rescue' does not work. Typing 'install rescue' brings up installer without any notions of rescue mode either. I've found posts with this question around, but no one was actually answered.

2. When I entered password for WiFi network I was also asked for another password to store "key ring". What exactly is that and why Ubuntu asked for it?

3. Boy, why on earth default option is to install Grub to hd0 MBR? Installer is still very geeky at this point. I think using external HDD is pretty common case and installer should be smart enough to at least ask the user about this option specifically and not hide it in "advanced". Actually partition editor displayed even mode notes for USB HDD, there was even some string like "WD passport 160Gb". I think installer could be smart enough to offer simple options "internal HDD", "external USB hdd" in addition of scary device codes. I guess 90% of people have Windows + have it installed on internal HDD. "Dell utility partition" is not a rocket science also, so installer could take it into account too.

4. This was also pretty unfair for installer to hide Grub menu. Especially considering the fact that I may want to boot in Windows too. I expected to see Grub menu by default and spent tons of time figuring out why nothing happens at all (Grub was not booting, but that is another story. Many Ubuntu installation instructions over internet specify that Grub menu should be visible).

5. Grub is terribly desperately totally badly documented. I understand some options in menu.lst are linux-kernel-specific, but could not find any explicit documentation about, for example, when running update-grub is needed or not (I saw notions in forum that it is needed after editing menu.lst and/or device.map), what mean these 'splash', 'nosplash' magic words (or what difference it will make if I remove defoptions completely), what is the priorities of defoptions and options specified for kernel in boot menu down below in menu.lst... I failed to find any clear manual or wiki describing these moments.

6. I saw installer offering me to support settings / accounts from other operating systems, but the list was empty in my case. I guess the fact that my Windows XP is installed not in the first partition (occupied by "Dell Utility") did not allow installer to find it. If this is the case, then too bad for the installer -- it seems so obvious and common case that it is surprising it was so silly at this point.

---

### Post by logos34 on 2008-01-02
> **alexandroid said:**
> 3. Boy, why on earth default option is to install Grub to hd0 MBR? Installer is still very geeky at this point. I think using external HDD is pretty common case and installer should be smart enough to at least ask the user about this option specifically and not hide it in "advanced". Actually partition editor displayed even mode notes for USB HDD, there was even some string like "WD passport 160Gb". I think installer could be smart enough to offer simple options "internal HDD", "external USB hdd" in addition of scary device codes. I guess 90% of people have Windows + have it installed on internal HDD. "Dell utility partition" is not a rocket science also, so installer could take it into account too.

The text-mode Alternate install CD gives you a choice for grub install locations.  For the live install cd the K.I.S.S. (keep-it-simple-stupid) principle prevails--I guess the devs figure adding grub options would confuse more noobs than it would help.  Most people have only one hard drive, and even for those who have a second internal drive or external usb grub can be counterintuitive.   But I agree with you--the option shouldn't be hidden away in 'Advanced' button...maybe a popup dialog box with a simpler version of what is on the alternate cd.
> 
5. Grub is terribly desperately totally badly documented.... I failed to find any clear manual or wiki describing these moments.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

