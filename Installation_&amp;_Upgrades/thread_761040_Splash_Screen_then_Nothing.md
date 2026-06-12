---
title: "Splash Screen then Nothing"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by bondboy8 on 2008-04-20
I am having so many troubles with linux i cant get it to boot.  I have it all installed and ready to go but after the splash screen with the loading bar the screen goes black, there is no sound, and my disk stop.  I tried reinstalling but no luck.  I am attempting to run 7.1 and I am using both PCI video and sound cards not the ones on my mother board if that is a problem

---

### Post by martrn on 2008-04-20
Do you get an error message if you boot ubuntu without a splash screen ?

[http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/]("http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/")

Further how far in the boot process do you get.

You boot grub,  do you get get a message saying "Staring......" (ie does the kernel boot ???)

Does ubuntu mount the file system correctly ? 

What is the last message (without the spash) you get before you it goes for a hang ?

---

### Post by bondboy8 on 2008-04-22
i tried what u said i got it to boot, it seemed to mount the file system i dont really know, and the word went by pretty fast but i think i made out the words "perioic command" in the last line before the screen when black

---

### Post by martrn on 2008-04-22
I don't have anacron installed in my system, so I do not know what is next in boot up sequence.  If you can boot into a terminal using (boot recorvery mode) then at a terminal you could type :-

> ls -l /etc/rc2.d

and get a list what is selected to boot up at the start like following :-

> lrwxrwxrwx 1 root root  17 2008-02-07 23:59 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-02-07 08:02 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  25 2008-02-07 08:06 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root  34 2008-01-27 23:13 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  14 2008-01-27 23:59 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  13 2008-01-27 23:59 S12hal -> ../init.d/hal
lrwxrwxrwx 1 root root  13 2008-03-25 22:45 S13kdm -> ../init.d/kdm
lrwxrwxrwx 1 root root  15 2008-01-27 22:58 S15bind9 -> ../init.d/bind9
lrwxrwxrwx 1 root root  13 2008-01-27 22:59 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  23 2008-01-27 21:05 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx 1 root root  22 2008-02-07 08:03 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  19 2008-01-27 21:05 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx 1 root root  16 2008-01-27 22:58 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  15 2008-01-27 21:05 S19mysql -> ../init.d/mysql
lrwxrwxrwx 1 root root  17 2008-01-28 01:04 S20dirmngr -> ../init.d/dirmngr
lrwxrwxrwx 1 root root  22 2008-02-15 23:56 S20kde-guidance -> ../init.d/kde-guidance
lrwxrwxrwx 1 root root  17 2008-01-27 20:56 S20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root  21 2008-04-16 07:47 S20moblock-nfq -> ../init.d/moblock-nfq
lrwxrwxrwx 1 root root  23 2008-01-28 05:23 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  19 2008-02-07 08:06 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-01-27 21:05 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  15 2008-02-08 04:50 S20rwhod -> ../init.d/rwhod
lrwxrwxrwx 1 root root  15 2008-01-27 21:06 S20samba -> ../init.d/samba
lrwxrwxrwx 1 root root  16 2008-01-28 20:40 S20vsftpd -> ../init.d/vsftpd
lrwxrwxrwx 1 root root  17 2008-01-27 21:06 S20winbind -> ../init.d/winbind
lrwxrwxrwx 1 root root  26 2008-02-17 04:29 S20xpilot-ng-server -> ../init.d/xpilot-ng-server
lrwxrwxrwx 1 root root  18 2008-01-30 22:58 S21sendmail -> ../init.d/sendmail
lrwxrwxrwx 1 root root  20 2008-02-07 08:04 S22consolekit -> ../init.d/consolekit
lrwxrwxrwx 1 root root  13 2008-01-28 07:03 S23ntp -> ../init.d/ntp
lrwxrwxrwx 1 root root  16 2008-02-07 08:04 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  17 2008-04-17 16:52 S24dovecot -> ../init.d/dovecot
lrwxrwxrwx 1 root root  18 2008-03-18 18:54 S29ubiquity -> ../init.d/ubiquity
lrwxrwxrwx 1 root root  20 2008-03-05 05:06 S50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx 1 root root  16 2008-01-31 17:01 S50hdparm -> ../init.d/hdparm
lrwxrwxrwx 1 root root  20 2008-03-05 05:07 S50x11-common -> ../init.d/x11-common
lrwxrwxrwx 1 root root  14 2008-01-27 21:05 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  24 2008-03-01 08:36 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root  17 2008-01-27 21:05 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  17 2008-02-07 08:10 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-02-07 23:59 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  19 2008-03-01 12:49 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx 1 root root  21 2008-02-07 08:02 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2008-01-27 20:56 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-01-27 20:56 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  24 2008-04-17 20:01 S99stop-bootchart -> ../init.d/stop-bootchart
lrwxrwxrwx 1 root root  24 2008-02-07 08:06 S99stop-readahead -> ../init.d/stop-readahead
lrwxrwxrwx 1 root root  13 2008-04-17 18:42 S99xdm -> ../init.d/xdm


The next entry listed after anacron I would have thought would be the problem....
 Eg.  Where S19 is processed before S20

So if S19 was anacron the problem will be with one of your S20's ..... Everying in linux is a file, so these are all symoblic links to files.  If you think one of your S20's for example is causing a problem you could rename it to say _S20 (with an underscore at the front) and it wouldn't execute at boot up.  Your can rename a file by :-

> mv    S20samba   _S20samba
// to rename S20samaba to _S20samba

If any X11 system or X11 drivers follow your succsessfull anacron load then try :-
> sudo dpkg-reconfigure xserver-xorg

Aother notorias boot problems are Bluetooth / PPP modem drivers, wireless network card drivers.

Looking through your /etc/rc2.d  should give you some hints.  Sorry I couldn't be more help but I do not have anacron installed in my system so do not know what is next in the list.
:(

---

### Post by bondboy8 on 2008-04-22
I'll try this I really dont no wut alot of it means I am new to Linux so if there are anymore details or steps u could include for clarity it would be helpful

---

### Post by martrn on 2008-04-23
> I'll try this I really dont no wut alot of it means I am new to Linux so if there are anymore details or steps u could include for clarity it would be helpful

You have said you have installed a version of ubuntu 7.10 (gusty).

When you boot, you are able to boot from the bois into grub.  Grub is able to boot the kernel, and then move onto its boot sequence.  Your boot sequence is processed right upto the point where anacron (the periodic commend scheduler) is loaded and shortly after that it hangs, I think because you state you have seen the command "Starting Periodic Command Scheduler" while the operating system has booted up.

I do not know if you are using a mobile computer or desktop or server based system and what processor you are using, and guess you are using and booting via the correct kernel.

You should be able to boot into a terminal by searching through the grub menus and finding an entry with (recovery mode) .  From here you will see a terminal with a prompt simular to $  or root $  or login :
This is just a command line interface for diagnostic purposes, and many linux users are very comfartable at the command prompt.

Linux was devised from UNIX roots and is a UNIX-like system so you can type any UNIX command at the command line prompt.  Note DOS commands like dir won't work because we are not using a full blown linux or UNIX-like system.  Commands like ls  (list)  or mv (move) will work.  Google linux unix commands to get a list of commands that you can type at a terminal.
[google unix linux commands]("http://www.google.co.uk/search?hl=en&as_q=unix+linux+commands&as_epq=&as_oq=&as_eq=&num=100&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images")

Typeing :-
```
ls -l /etc/rc2.d
```
at a terminal will list the directory of your /etc/rc2.d   directory and list your standard sequence, where linux will process.  Ubuntus (or any debians) boot sequence will boot 
all scripts in this directory begging with an S  and start from S01 and move upto S98, and I thing S99 secequences have a special meaning.

So typeing the above line at a command prompt will give you a list of your boot sequence.  Underneath anacron will be a process that has most likely caused a hang in your system.  If I new your boot sequence and a list of your S  - files I would guess that it would be anacron or something that shortly follows it that causes your boot sequence to hang.

Posting  your /etc/rc2.d/ directory would give more clues.

The linux X11 windows system including XORG and drivers are know to cause some computer systems to fail.  Although ubuntu has a fail-safe X11 system it doesn't always work you could try typeing
```
sudo dpkg-reconfigure xserver-xorg
```
at a terminal prompt.  This will re-configure you windowing system, ensure you enter the correct monitor resolutions, the X11 windowing system will fail again.  This is by no means gareteed to work, or fix your system, but X11 is a very common place which causes hangs.

Other than than moving (renaming) files using :
```
sudo mv S20samba _S20samba
```
to the offending peice of boot process that causes your system to hang then I do not have an idear.  Do not type this (sudo mv S20samba _S20samba) you would need to modify to your /etc/rc2.d  entries and your /etc/rc2.d  directory will have diffrent S20's [..S...??] and some of these processers are essential.

---

### Post by bondboy8 on 2008-04-23
Ok that makes sense thanks alot it sounds like the best thing i could do here is post my /etc/rc2.d my question is how is there anyway to like save it or do i have to write it down

is there like a program i can run that will save it

---

### Post by bondboy8 on 2008-04-26
i reconfigered my XORG and rebooted and got this after the splash screen

*Star anc(h)ronistic cron anacron 			        [OK]
*Starting deferred excution scheduler atd			[OK]
*Starting periodic command scheduler crond 			[OK]
*Checking battery state...					[OK]
*Running local boot scripts (/etc/rc. local)			[OK]
_

What now

---

### Post by bondboy8 on 2008-04-26
I reconfigured my XORG and rebooted.  After the splash screen was this

*Star anc(h)ronistic cron anacron 				[OK]
*Starting deferred excution scheduler atd			[OK]
*Starting periodic command scheduler crond 			[OK]
*Checking battery state...					[OK]
*Running local boot scripts (/etc/rc. local)			[OK]
_

What now?

---

### Post by martrn on 2008-04-26
Things you could do :

At this stage you could -

Press <Ctrl>+<Alt>+F2 to start a terminal session
or you should be able to boot into a terminal by searching through the grub menus and finding an entry with (recovery mode) or via your rescue disk. From here you will see a terminal with a prompt simular to $ or root $ or login :

Make sure you are using the correct kernel type :

sudo apt-get install linux-generic
sudo apt-get install linux-386

Type uname -r at a terminal to find out what kernel you are using.  You would neeed linux-generic for athalon and above and pentiumII's and above and you would need linux-386 for upto AMD K6 / upto pentiums. (I do not know full how the ubuntu kernels are compiled. although the kernels contain basic system drivers also, and plugin kernel modules to load the drivers).

Type 
```
sudo apt-get update
sudo apt-get install sysv-rc-conf

sudo sysv-rc-cong
```
To install a way of edititing files that boot up eg at the "..Running local boot scripts (/etc/rc. local).." stage.

Deselect everything that is non essential.  Look at [http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491") and remove everything marked in red.

I do not know your system specs.  Do you have two graphics cards installed, and have you ensured one is removed from the motherboard.  You should be able to boot, into two screens, and can run multiple monitors on all video cards or run headerless, but I do not know how to configure X11 for two graphics cards.  Ensure you have enough memory to run kde and/or gnome at least 192+ MB and check the specs at ubuntu.

try either one of the following
```
startx
./etc/init.d/gdm 
./etc/init.d/kdm
```

to start x  - post any error message you might get here.

what specs do you have on your system memory wise / graphics wise.. ?

---

