---
title: "I messed up my computer"
date: 2014-11-22
forum: Installation &amp; Upgrades
---

### Post by eikichiinji on 2014-11-22
Hello everybody!
I just messed up my computer and I don-t know how to solve it.
now i-m on internet using lubuntu on live pendrive but layout of keyboard wrong so cannot type everythng properly> sorry.

Before I have ubuntu 10.04. now no more supported. so i started to look around.butstill I-d like to keep it as backup. i downloaded some iso and put on pendrive.
after I created some space to keep dual OS, one for old ubuntu and a new one for lubuntu, so 3 partitions plus swap things
dev sda1 ubuntu with 14 gb called ubuntu 10.04
dev sda2 files data with 120gb called files
dev sda3 swapthings
dev sda4 new empty partition about 13gb, called lubuntu 14.10
one hour ago i use unebootin to write the iso of lubuntu on sda4>big mistake! *dont ask me why but i thought it could have been easier that way!(
after that i restarted my computer and BOOM>black screen with written things that I don-t understand *but i don-t know how to copy here, things about cable not connected....
try to do something> nothing solved. needed to stop the computer> only unplugging and taking the battery away worked.
tryed to use f2 to change ordeer of booting but nothing change
then I use my pendrive wehre i wrote the same iso and start the computer in mode try but not installing lubuntu *i-m afraid if install now maybe I loose some data or the other partitions(
open gparted> but cannot delete that partition sda4, and cannot unmount it it says>
umount: /cdrom: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
I think if i can delete that partition where there is the iso written with unebootin, the computer will work as before, but cannot do anything to that partition, cannot unmount it, cannot create a partition table becasue of that mounted, but if i check on hte folders it doesnt show up...in gparted under the voice Mount Point it says cdrom!!!
so what I-m gonna do_ please help me

---

### Post by eikichiinji on 2014-11-23
I don-t know why but i cannot see the partition in the file manager, but i can see the usb live, and i can see both on gparted. but cannot unmount the sda4. beyond this I also have another problem> I cannot save the file from the home partition, I mean I tryed to copy to an external hard disk, but some folders cannot be copied, I really don-t know why...and also I cannot open those folders and this shows up:
Error opening directory '/media/lubuntu/files/rudy/Desktop/wo......': Permission denied
this is just an example, but actually many folders I cannot open, see, save...I noticed mostly are audio files, but some aren-t. someare just docs or videos or pictures....What can I do?
beyond that I cannot save anything if I don-t use an exteranl hardisk

---

### Post by eikichiinji on 2014-11-23
another thing I noticed when I try t ohave a look with the installer of lubuntu, because it has something for partitioning inside:if select the last option, it shows me ths message:your installation medium is in /dev/sda4. you will not be able to create, or resize partitions on this disk, but maybe you will be able to install to existing partitions there....so I start to think I_m using the installer on sda4, but without the pendrive it doesn-t start at all...so I-m just more confused: I_m actually using the installer on the pendrive or the pne that I have installed on the partition sda4? jus tfor fun I unmount the pendrive after the computer is on, and it still work....but without it it doens-t start!!!! I-m getting crazy!!! plz help me...

---

### Post by carl4926 on 2014-11-23
You can choose the 'something else option' to manage partitions manually
That will let you set the target partition for your new install
Also at this point be sure grub is set to install to your HDD not the USB, sometimes it gets mixed up. Where the USB is seen as sda and the HDD as sdb
Just ignore the other partitions for now, focus on where you want 14.10 to go
Set the mount point as /
Use ext4 for format

---

### Post by eikichiinji on 2014-11-23
thank you for answering me...
before i mistype: all the partitions are sdb not sda...
I don-t understand what do you mean writing about grub, what is grub?
if i do follow that else option, how exactly should i do?
i mean> i guess i select dev/sdb4 
button change
select Ext4 journaling file system
format the partiiton with the tick
but which one i select? 
options are: / /boot /home /tmp /usr /srv /var /opt /usr/local
and then? i go and everything will be ok, or installed, or just changed in that partition?

---

### Post by carl4926 on 2014-11-23
Let us see a picture of it all in Gparted

---

### Post by nerdtron on 2014-11-23
> **eikichiinji said:**
> thank you for answering me...
before i mistype: all the partitions are sdb not sda...
I don-t understand what do you mean writing about grub, what is grub?
if i do follow that else option, how exactly should i do?
i mean> i guess i select dev/sdb4 
button change
select Ext4 journaling file system
format the partiiton with the tick
but which one i select? 
options are: / /boot /home /tmp /usr /srv /var /opt /usr/local
and then? i go and everything will be ok, or installed, or just changed in that partition?

And provide the screenshot on that part of the installation. Post it here so we can see and advise if needed before you click proceed.

---

### Post by eikichiinji on 2014-11-23
screenshots of the installer
i don-t know why but after that i could use gparted to format that partition, anyway after that i tried to start the computer withot the pendrive but still didn-t work....
the last picture is from gparted

---

### Post by eikichiinji on 2014-11-23
this is a picture of my computer f i start it without the pendrive (with the installer on it)

---

### Post by nerdtron on 2014-11-23
Third screenshot looks fine to me. Is that successful after you reboot? How far did you go after the reboot?

---

### Post by nerdtron on 2014-11-23
Are you sure you have set the hard drive as the first boot device?

---

### Post by eikichiinji on 2014-11-23
I havent istall it yet, afraid of losing data, because I couldnt start the computer without the pendrive (even if virtually I formatted that partition), so I guess the problem still persist.
I think even if I install it, problably I will have just 2 Os but with the same initial screenshot (the 5th picture i posted)....
so do you think I can install it now? or I will not solve nothing?

---

### Post by eikichiinji on 2014-11-23
about the boot: you mean the thing at the beginning with f2, right?
usually i let the usb for first one, and then other things, but usually no difference anyway i will post a picture.



(I didn-t notice that there was already a second page of answers)

---

### Post by eikichiinji on 2014-11-23
thank you very much...
now it's basically working, (just had a fast look and it look like working, I mean both working without the pendrive)
just for reference, if someone will get the same problem: at the beginning unmount the troublesome partition (that still I don't understnd why once I could do it), and then install there the OS, with the specifications as in the previous screenshots...
One more thing If I can ask: I'd like to optimize my partitions, keeping ubuntu 10 as backup (I love it and if something doesn't work I can still use it), but I want to move to lubuntu 14 that I've just installed as said above (thank you again)...do i need ot reside some partitions? like the swap, or the 3gb one (there is lubuntu) or do ineed to move them?
the pictures are to know better how to optimize... keep in mind that probably i'll tend to reinstall most of the programs of ubu in lubu, but keeping away the ones i didn't use 

again thank you very much :D :D :D :D :D :D

---

