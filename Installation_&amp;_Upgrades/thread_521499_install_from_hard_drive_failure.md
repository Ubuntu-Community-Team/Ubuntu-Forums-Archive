---
title: "install from hard drive failure"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by deepinlife on 2007-08-09
Hardware spec:
hardrive :17 mega
4 drives.
196 ram
bus 66

guys i wanted to install ubunutu from teh hard disk..i made a drive , copied all teh contents of the iso file to that drive.Then edited grub to bot through it..
and i succeeded to boot..but then it just stops 

the iso i use is ubuntu-7.04-desktop-i386.iso

teh message it stops at :
squashfs:version3.2-r2(2007/01/15)Phillip lougher

---

### Post by forestpixie on 2007-08-09
why did you want to install from the hardrive?

---

### Post by dabl on 2007-08-09
> **deepinlife said:**
> 

 copied all teh contents of the iso file to that drive



Huh -- where did you get the idea to do that?  You're supposed to burn the ISO image to a CD ROM, and then boot the Live CD.  The Live CD has the installation option and routine on it.  There is no "copying to disk" that you need to do.

---

### Post by forestpixie on 2007-08-09
I think he/she's likely to have a problem with 196Mb Ram as well.

---

### Post by dabl on 2007-08-09
> **deepinlife said:**
> 

hardrive :17 mega
4 drives.
196 ram
bus 66



Whoa -- you don't seriously mean "17MB"???  I think maybe that's enough to set up DOS 5.0!

;-)

And forest is correct, 196M of RAM is below the minimum recommendation of 256M. :)

---

### Post by deepinlife on 2007-08-09
i m sorry 17 giga not mega..

about installation from hard , i always use this method with all linux distributions..why install from cd when u can install from hard disk ?
installing from hard is more cheaper and more reliable .
my cdrom writer is not working.

i have seen article on the ubuntu site ,describing how to install from hard drive.
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

i have made all what is written but still in vain???

---

### Post by logos34 on 2007-08-09
Not sure about the error message you're getting but you're wasting your time trying to install using the live cd (whether from cd or hard disk)--as stated above you need **at least 256MB ram**.

with your system specs I'd try the [Xubuntu]("http://www.xubuntu.org/get#feisty") live cd.

If you still get the error message, and you're not stuck on a slow internet connection, try a netboot install from hard disk using the **mini.iso**.  Can't promise you it will work in your case, though.  Use the same "Installation/FromLinux" howto but change a couple of things.

First, get the [.iso here]("http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso").

Just change the paths slightly (no '/boot' dir on mini.iso):

..........................

"Step 3. Edit your grub configuration file (typically /etc/grub.conf or /boot/grub/menu.lst) to boot from the new partition by adding the lines

> title installer
        root (hd0,0)
        kernel /vmlinuz  root=/dev/ram ramdisk_size=1048576 rw
        initrd /initrd.gz

....................................

I *think* that's the menu.lst entry to use (it's been a while since I last tried it). 

Note: the ideal solution would be to use the text-mode alternate install from the full .iso, but for some reason it will not work--the installer fails trying to locate the CD.  The mini.iso is the only ttext-mode cd that seems to work with an install form hard disk frm linux.

If and when you get the installer going, you will be given a choice of desktop environments--choose "Xunbuntu"

---

### Post by deepinlife on 2007-08-10
i have tried xubuntu before ubuntu and i have failed completely..with another error message.

but tel me am i trying to install the live cd?
how do u knew that?
i m sorry for the strange question , it is just the first time for me with ubuntu..
i m using ubuntu-7.04-desktop-i386.iso ..

if this was the live cd then what is the name of the install cd ?

---

### Post by logos34 on 2007-08-10
> **deepinlife said:**
> i have tried xubuntu before ubuntu and i have failed completely..with another error message.

but tel me am i trying to install the live cd?
how do u knew that?
i m sorry for the strange question , it is just the first time for me with ubuntu..
i m using ubuntu-7.04-desktop-i386.iso ..

if this was the live cd then what is the name of the install cd ?

ubuntu-7.04-desktop-i386.iso = live cd + install

ubuntu-7.04-alternate-i386.iso = text-mode install cd only

If xubuntu failed too, then it's time to try a network install using the mini.iso.

---

### Post by Mark Phelps on 2007-08-10
With that little memory and that small a drive, you really only have two useful options:
1) text mode installation of Ubuntu -- download the Alternate CD image, burn it to CD, install from that.  It will give you a quasi-graphic mode (text with borders) that takes less memory to load and run.  However, after you're done, don't be surprised if Ubuntu is really slow with the default Gnome desktop.  Running it in less thatn 256MB of memory is asking for trouble.
2) install Xubuntu instead.  You said you got error messages -- what were they?  I tried installing Xubuntu on a 256MB old PIII laptop and initially, got the dreaded 'busybox' error messages. But reading this forum, I found some threads that said if you have a blank diskette in the drive during the initial installation, it works.  So, I tried that -- and it did work!  Just make sure you change your boot sequence in the BIOS so it doesn't boot first from the diskette.

---

### Post by logos34 on 2007-08-10
> **Mark Phelps said:**
> ... download the Alternate CD image, burn it to CD, install from that.

he can't install from cd -- his cd drive isn't working (post#6). 
> 
got the dreaded 'busybox' error messages. But reading this forum, I found some threads that said if you have a blank diskette in the drive during the initial installation, it works. So, I tried that -- and it did work! Just make sure you change your boot sequence in the BIOS so it doesn't boot first from the diskette.

Interesting, I got that message for the first time a couple of days ago when I tried to run a factory-pressed feisty cd, but I would swear I fixed it by doing the opposite--taking out the floppy that was in the drive.  I'll have to try it again.

---

### Post by deepinlife on 2007-08-13
here what is happening.
first i tried alternate cd , and it worked successfully..but unfortantaly it is configured to install from cdrom..so it insist on searching for files from cd rom..i think there is a component which is called isoscan , which search for iso files on the hard to install from it , but this component is not there in the alternate cd..so i just gave it up..

i tried teh ubuntu iso again , after removing my spoiled cdrom..it worked..but alot of error message then suddenly i found teh gnome manger , i thought it will give me installation menu , but simply it logged at once to the gnome manger and it is asking about the user name and password ?!!!!i don't know how it is asking about that ?

i will try to download the mini iso and check it up but if any ideas for the above, it will help

---

### Post by logos34 on 2007-08-13
> **deepinlife said:**
> here what is happening.
first i tried alternate cd , and it worked successfully..but unfortantaly it is configured to install from cdrom..so it insist on searching for files from cd rom..i think there is a component which is called isoscan , which search for iso files on the hard to install from it , but this component is not there in the alternate cd..so i just gave it up..

That's why I said this in post #7 above:
> Note: the ideal solution would be to use the text-mode alternate install from the full .iso, **but for some reason it will not work--the installer fails trying to locate the CD.** The mini.iso is the only ttext-mode cd that seems to work with an install form hard disk frm linux.

If it won't take the mini.iso, try [COLOR="Red"][UNetbootin]("http://lubi.sourceforge.net/index.html")[/COLOR] (Lubi).  If you're on Mandriva, get the [unetbootin-ubuntu704rev21.sh]("http://downloads.sourceforge.net/lubi/unetbootin-ubuntu704rev21.sh?modtime=1186550117&big_mirror=0")
version installer.

---

### Post by deepinlife on 2007-08-13
Guys
Congratulations..
i m sending now from xubuntu .
i installed it using mini.iso
thanks everyone for being that friendly ,helping me in that problem..
i finally made my first step in the Ubuntu world , and it was nice..
the forum is good and friendly..

i have found some problems when i installed the xubuntu itself , but that is another story..now i will just celebrate the ubuntu..

but soon i will begin using the forum soon , facing these problems :) ..

thanks agin everybody.
see u soon

---

### Post by logos34 on 2007-08-13
> **deepinlife said:**
> Guys
Congratulations..
i m sending now from xubuntu .
i installed it using mini.iso
thanks everyone for being that friendly ,helping me in that problem..
i finally made my first step in the Ubuntu world , and it was nice..
the forum is good and friendly..

i have found some problems when i installed the xubuntu itself , but that is another story..now i will just celebrate the ubuntu..

but soon i will begin using the forum soon , facing these problems :) ..

thanks agin everybody.
see u soon

Glad the mini.iso worked out for you--I thought it would but wasn't 100% sure because as I say it's been a few months since I last did a netboot installation from linux (I know I installed the 64-bit version but was wondering if my maybe I confused it with an installation from the windows side using the Xubuntu alternate cd).

At any rate, welcome to (X)ubuntu!  It's a great distro, have a lot of fun.

You might also want to keep an eye out for the 7.10 Gutsy release of [Fluxbuntu]("http://fluxbuntu.org/"), another lightweight desktop (fluxbox).

---

### Post by deepinlife on 2007-08-14
for sure i m in great need for such light ubuntus on my pc..
i will open eye wide on them
thanks

---

