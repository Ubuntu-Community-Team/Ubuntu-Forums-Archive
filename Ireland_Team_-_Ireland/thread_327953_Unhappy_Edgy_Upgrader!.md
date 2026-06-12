---
title: "Unhappy Edgy Upgrader!"
date: 2006-12-30
forum: Ireland Team - Ireland
---

### Post by derby007 on 2006-12-30
Well, i'm back after my Seasonal lashings of Guinness, cream&pudding sandwiches, turkey for breakfast, lunch & dinner......ho ho belch ho.

Q for ye: i've recently updated to Edgy, i'm having loads of problems....1st my Usplash went, Nautilus wont autodetect my USB's or CD/DVD's, i had to reload a few programs like Gedit, games, etc. It might have to do with a mix up after my install of XFCE (before Edgy). Just wondering if ye are seeing problems aswell.
Note: i now have to run 'Thunar' (>XFCE program) to see my USB / CD/DVD's....

---

### Post by bikeboy on 2006-12-30
You are saying this was an upgrade rather than a fresh install right?

---

### Post by derby007 on 2006-12-30
Yeah, an upgrade. NOTE: i dont have the Internet ! 
I had Ubuntu Dapper originally, then i got the Kubuntu Dapper Alt CD and did 'apt-get install kubuntu-desktop', this all went swimmingly well. Then i upgraded my Mythtv to 0.20 from the Edgy repos by downloading the .deb files and installing them. Then i installed Xubuntu (Edgy i think, this may be the cause of my problems !). Then i got the Ubuntu Edgy Alt CD and did an upgrade to that. Maybe i've done too much..... I was thinking if Deleting the whole 'shebang' and starting a fresh install, but i dont want to loose all my tweaking, mp3's, mythtv, settings, etc. I'll try and get these few things sorted & be happy :)

---

### Post by bikeboy on 2006-12-30
Yeah I completely understand you not wanting to lose what you've done. You should definitely think about how you can backup the important things should a fresh install be your only option.

If you try a 'sudo apt-get update && sudo apt-get update' does it give you any errors? When I did an upgrade some things were held back due to new dependencies that were needed, a simple 'sudo apt-get install ###' for each was all I needed. Also, double check your /etc/apt/sources.list to make sure it's all correct.

/me slaps head! Hmm, no internet, well you should still be able to check for missing dependencies with and apt-get upgrade, then if there are any you can download them from packages.ubuntu.com and transfer to your Ubuntu machine for installation.

---

### Post by derby007 on 2006-12-30
Yeah i did both: apt-get & aptitude 'update', & aptitude gives a more realistic error, it gives a 'kubuntu-desktop- error, ie. rem it was installed via Dapper CD, maybe i need to upgrade it to Edgy, i just dont know! Any ideas on Nautilus seeing my CD/DVD's & USB !
I got this info from a manual:
/etc/fstab
Lists the filesystems mounted automatically at startup by the mount &#8722;a command (in /etc/rc or equivalent startup file). Under Linux, also contains information about swap areas used automatically by swapon &#8722;a . See Section 5.10.7 and the mount manual page for more information. Also fstab usually has its own manual page in section 5.
So: maybe i'll look for the 'mount' command in the /etc/rc or similar.....:???:

---

### Post by bikeboy on 2006-12-30
Hmm this getting well beyond the scope of my knowldege, but I do feel that having some Edgy components mixed with some Dapper could well be causing problems due to shared libraries and more fundamental changes that happened for Edgy.

---

### Post by OpenSourcer on 2006-12-31
Have a look at the steps I took to upgrade my machines from Dapper to Edgy. It might help:

[LIST=1]
[*]Edit /etc/apt/sources.lst: Remove lines referring to the old CD's/DVD's and replace references to "dapper" with "edgy".
[*]"apt-cdrom add" the new CD's/DVD's.
[*]"apt-get dist-upgrade"
[*]"apt-get install ubuntu-desktop", because X.org was broken.
[*]Reboot to the new kernel.
[*]Run aptitude to remove obsolete packages first, **then** upgrade some packages kept to old versions...
[/LIST]

One machine needed some more attention. I had to:

[LIST=1]
[*]Edit the system menu and add "gksu" in front of some of the commands.
[*]Add myself to the groups which have access to removable media, floppy disk drives etc.
[/LIST]

I believe the last one is your main problem too...

---

### Post by derby007 on 2007-01-04
Cheers 'OpenSourcer', i've tried some of what u mention in your reply. It seems like i have a very uptight/tenuous (on the Edge) system. Everytime i change my Sources.list and then do an 'update/upgrade', something else goes missing, etc. (grrrrr I hate dependencies !!! ](*,) ).  
You could be right with the last part, editing the System menu: ie. look at my /Media dir:
:/media\> l -a
total 56
lrwxrwxrwx  1 root   root        6 2006-06-20 22:28 cdrom -> cdrom0
drwxr-xr-x  2 root   root     4096 2006-06-20 22:28 cdrom0
drwxrwx---  3 root   plugdev 16384 1970-01-01 01:00 hda1
dr-xr-x---  1 root   plugdev  8192 2006-12-19 17:31 hda2
drwxrwx--- 10 root   plugdev  4096 1970-01-01 01:00 hda3
drwxrwx--- 15 root   plugdev  4096 1970-01-01 01:00 hda5
drwxr-xr-x  2 root   root     4096 2006-09-09 21:45 sda1
drwxr-xr-x  2 root   root     4096 2006-09-09 21:50 sda5
drwx------ 12 derby derby  12288 1970-01-01 01:00 usbdisk

I notice if i open Thunar (from XFCE) it sees my USB & then after so does my Desktop & Nautilus, OR if I click on the My Computer icon in Nautilus I can see the USB, then when i double-click this USB icon it shows up in Tree view & on my Desktop......wierd.

It is now giving me an error that it wants a certain type of Ubuntu Edgy: ie. >

Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)

compared to:

Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)             :-k

---

