---
title: "Kernel Errors during installation"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by Jack Ryan on 2004-12-16
I just recently built a new computer (Athlon64 3500+, 1024 MB RAM K8T800pro mobo) and installed winxp, I downloaded the x86_64 version of Ubuntu and while the installer was installing the base system I get an error message saying "Unable to load Kernel" I did an MD5sum and it came back bad (No surprise there) but when I downloaded it again I got the same problem I even tried the i386 version and it didn't work. Is it my CD burner? my media? I am relatively new to this and I don't know what to do. (and I'm not crazy about downloading the entire thing again.) why do I keep getting corrupt files?

-thanks

---

### Post by p!=f on 2004-12-17
I don't want to sound scary but I had similar problems with MD5 sums and apt-get, when installing and updating package info. After some research I ran memtest86+ (that plus is important :)) to find out my new 512 RAM is bad.
You may also want to check BIOS and try to load default values.

---

### Post by Jack Ryan on 2004-12-18
I used Memtest86+ and everything looked fine, I uninstalled WinRAR I doubt it will help any but I guess I'll have to do another download. I might try another distro to see if its the servers, but I guess I'll have to use another computer to burn the install CD. anyway thanks.
              -John

---

### Post by Rancoras on 2004-12-18
[QUOTE=Jack Ryan]I uninstalled WinRAR I doubt it will help[/QUOTE]

Just out of curiosity, what does WinRAR have to do with anything?  You should download the iso and then burn the image to disc.  Don't try to extract the iso and make sure you don't just end up with the iso file on the disc.  

Example: If you use Nero to burn, then select Recorder | Burn image then browse to the iso file.

Make sure the iso passes an MD5 check before you try to burn it.

---

### Post by Jack Ryan on 2004-12-18
I tried burning the install disc on a Thinkpad R42 using Burn4free (the same computer and app that burned the live disc) and I got the same problem. I just don't get it. I've wasted about 4 or 5 CD-Rs trying to get this thing up and running. Burn4free may have something to do with it so i'm gonna try Nero (My ISPs gonna hate me by the time I get this done) I'm not sure what WinRAR has to do with it Rancoras but It was like auto-extracting or something I burned the regular ISOs but I'm can't be sure. I'm gonna try Gentoo or Yoper and see what happens. I'm also gonna download and burn Ubuntu for one last time just to be sure... by the way has anyone else had this problem?

---

### Post by gkhewitt on 2004-12-19
Just for clarification, here's the process you should be going through.

-Download ISO from Ubuntu servers.

-Check MD5 of the ISO from your current OS (eg. Windows) BEFORE burning a CD

-Use Nero or similar disc burning package to burn the ISO to a CD. Do not unpack using WinRAR or whatever. If Nero or similar is installed, then just double clicking the ISO file you downloaded should open the appropriate part of the program since the *.iso will be associated with that program. 

-Try burning the CD at a much lower speed to get an accurate burn. Sometimes burning at very high speeds can cause problems.

-Reboot your machine and install using CD.

If you're still having trouble, check the discussion a few threads down started by me about Install Dependency errors, you may be having the same problem. If you check tty3 when the error occurs (Shift + F3) you may see some more helpful errors.

HTH

---

### Post by Rancoras on 2004-12-19
[QUOTE=gkhewitt]If Nero or similar is installed, then just double clicking the ISO file you downloaded should open the appropriate part of the program since the *.iso will be associated with that program.[/QUOTE]

Nah, that may be where WinRAR was coming in.  .iso files are associated with WinRAR by default if that program is installed.  Just open Nero and click Recorder | Burn image then browse to the iso file.

---

### Post by Jack Ryan on 2004-12-19
OK, I downloaded Ubuntu again (via bittorrent) and got and MD5sum, it came back good and I thought everything was going great. I booted from the install disk and checked the integrity of the CD-ROM. once again everything was going great, but when I was installing the base system I got the kernel error. I installed the i386 kernel (cause the torrent had more seeds). At this point I don't know what to do. if its true that in Linux "what does not kill my harddisk makes me smarter" I'm getting there. 
             -John

---

### Post by Rhodan on 2004-12-19
[QUOTE=Jack Ryan]OK, I downloaded Ubuntu again (via bittorrent) and got and MD5sum, it came back good and I thought everything was going great. I booted from the install disk and checked the integrity of the CD-ROM. once again everything was going great, but when I was installing the base system I got the kernel error. I installed the i386 kernel (cause the torrent had more seeds). At this point I don't know what to do. if its true that in Linux "what does not kill my harddisk makes me smarter" I'm getting there. 
             -John[/QUOTE]
 Do you have a SATA hard drive ?

---

### Post by Jack Ryan on 2004-12-19
No, its a regular old 200gig IDE

---

### Post by gkhewitt on 2004-12-19
[QUOTE=Jack Ryan]No, its a regular old 200gig IDE[/QUOTE]
 Could you post the exact error messages? It could be that it is similar to the bug that I get, about dependency errors. As above, you can view error messages by cycling through the different consoles (ctrl + f3 etc..)

---

### Post by Jack Ryan on 2004-12-19
I get these errors:

        [!!]Install the base system
    Unable to install the selected kernel
an error was returned while trying to install the selected kernel into the target system.

Kernel package: 'linux-386'

check /var/log/messages for details or virtual console 3

(thats what I get in the main screen, if I alt+F3 I get this)

The following packages have unmet dependancies:
        Linux-386 Depends: Linux-image-386 but it is not installed
                        Depends: linux-restricted-modules-386 but it is not going to be installed

I hope that helps, I'm sure I didn't get everything or everything exactly right but its a step closer. anyway
-John

---

### Post by Jack Ryan on 2004-12-19
gkhewitt, I'm sorry I didn't see any of the other threads. I got the live disc to work as well. I'm sure there is a resolution to this problem. Has anyone tried the Hoary installer? sarge? Is there any other way I could install the ubuntu live disc to the hard drive?
Cheers,
John

---

### Post by Rhodan on 2004-12-19
[QUOTE=Jack Ryan]gkhewitt, I'm sorry I didn't see any of the other threads. I got the live disc to work as well. I'm sure there is a resolution to this problem. Has anyone tried the Hoary installer? sarge? Is there any other way I could install the ubuntu live disc to the hard drive?
Cheers,
John[/QUOTE]
 Jack Ryan see my post over here, [http://www.ubuntuforums.org/showthread.php?t=8380](http://www.ubuntuforums.org/showthread.php?t=8380) , it seems to be a problem with the kernel supplied with the warty release, so I'm guessing a current build of Hoary with the 2.6.9 kernel would fix it, I'm busy downloading it now to give it a test. Maybe you shoud give it a go as well ?

---

### Post by Jack Ryan on 2004-12-19
I might install Hoary Rhodan, But I think i might try to install warty via knoppix first. I could just copy the live disc to my reiser partition but I don't know. I'll get back to everyone pretty soon. 

p.s. tell me if you find a hoary torrent

---

### Post by Rhodan on 2004-12-21
Jack Ryan did you manage to get it to work ? I got my Ubuntu install to work by using the expert option, and then selecting only the IDE drivers specific to my pc, when it got to the kernel stage I was able to select from 4/5 different kernels which worked fine. 

So it seems its possibly a problem with Ubuntu not being able to load the correct driver for the cdrom/ide devices.

---

