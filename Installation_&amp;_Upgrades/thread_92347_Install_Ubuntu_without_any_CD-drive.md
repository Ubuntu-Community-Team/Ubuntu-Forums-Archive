---
title: "Install Ubuntu without any CD-drive?"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by Gonte on 2005-11-19
What is the esiest way to install Ubuntu if you can't use a boot cd?

(I could use a floppy boot disk but don't know how to create one)...

*The main problem is that my CD-drive is broken, and i haven't actually been needing it for 6 months so it feels a little bit unnessesery to buy a new just to install ubuntu...*

---

### Post by Dr. Nick on 2005-11-19
Do you have an os on their now? If you have windows you can try this link
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

Their may be another way to do this, Im not sure.

---

### Post by Gonte on 2005-11-24
well, this seems like a possible way, but i don't know how to do the first step "Resizing the partition", so if someone could tell me how it would really be helpfull...

---

### Post by Dr. Nick on 2005-11-26
It depends on yor setup now.

If you have windows and want to go to Ubuntu solely, then dont worry about partitioning, just set up grub for windows and get it to boot into the installer then erase all partitions(erasing all data)

If you have windows and want to keep it and just dual boot with Ubuntu then what is your partition layout right now? If its one big partition you need a 3rd party app to resize it. Ive never done that but the forums may have instructions. If you have multiple partitions you can move the files on one to another then just erase one of your partions in the linux installer for use.

If you can post your situation I may be able to help more with specifics.

---

### Post by andrew.sroka on 2005-11-26
Hello I got almost the same problem. I have laptop without CD rom.There is instaled Linux Suse 10.0. (it was simple to install suse through net).
But now I would like to install ubuntu and have no idea  how to do this. 
On the othere computer in network is Windows XP, there is working CD ;-)

Anybody can help

Regards:  Andrew  Sroka

---

### Post by Dr. Nick on 2005-11-26
You should be able to follow the above instructions somewhat, Download the required files for breezy, watch out that you dont get hoary as the links are old, just navigate to breezy versions. When they say edit menu.list subsiute "sudo gedit /boot/grub/menu.lst" The files you download need to be put in the /boot directory. Then you can use your suse entry in the menu.lst as a template of sorts. Just copy and paste one of the entries and edit the paths.

If you hit problems just post your menu.lst and the names and locations of the files you download, you may rename them to something distinguisihng them as ubuntu as to not overwrite suse files incase somethng goes bad. Just realize that if you do the install this way you only get 1 chance to get it all right in the install. If you partition and format then close the install you cant get back to the install or suse. 

>>> Yes I have done the last part myself , its very annoying :)

---

### Post by andrew.sroka on 2005-11-26
THX.

What to do if I lost partition with suse ? And computer will boot only from floopy ? Is there any solution ?

Regards: Andrew Sroka

---

### Post by Dr. Nick on 2005-11-26
If you install it this way you will lose the suse partition, but hopefully ubuntu will work correctly. If the install fails and you are stuck with a floppy boot only you would have to reinstall linux using a floppy as before and try again. Very timeconsuming and sorta waste bandwitch. Hopefully it wont fail. Do you have any external storage like a usb hard drive? You may be able to backup and restore. If it werent a laptop I would just suggest adding another hard drive but that may be impossible for your laptop.

---

### Post by andrew.sroka on 2005-11-26
unfortunatly it is laptop and I have no any memory storage (memory stick is only 128 Mb and I dont know where execly it is :-) ok I'll try you solution with floppy and another system... 
thanks for your help
regards: Andrew Sroka

---

### Post by Doughsay on 2005-11-27
The ubuntu install process can resize paritions for you, you dont need any 3rd party app.  When your presented with the paritioning part of the install process, select the partition you want to rezise and just change the "size" value.  I did this and it worked great on my NTFS partition.

---

### Post by Gonte on 2005-11-27
[QUOTE=Dr. Nick]It depends on yor setup now.

If you have windows and want to go to Ubuntu solely, then dont worry about partitioning, just set up grub for windows and get it to boot into the installer then erase all partitions(erasing all data)

If you have windows and want to keep it and just dual boot with Ubuntu then what is your partition layout right now? If its one big partition you need a 3rd party app to resize it. Ive never done that but the forums may have instructions. If you have multiple partitions you can move the files on one to another then just erase one of your partions in the linux installer for use.

If you can post your situation I may be able to help more with specifics.[/QUOTE]

Now i got Windows 2000, and i would rather keep it if possible, but i only got  one big partion (at least i think it's only one)...

---

### Post by UbuWu on 2005-11-27
[QUOTE=Gonte]What is the esiest way to install Ubuntu if you can't use a boot cd?
[/QUOTE]

See advanced installation methods on this page:

[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

---

### Post by xelink on 2005-11-27
I suggest buying a 10$ CD drive, or borrowing one from an old coputer... really fi you can't do/afford that you shouldn't be installing an OS.

[http://www.newegg.com/Product/Product.asp?Item=N82E16827101205](http://www.newegg.com/Product/Product.asp?Item=N82E16827101205)

or if you want something a bit more multi-valent...
[http://www.newegg.com/Product/Product.asp?Item=N82E16827106988](http://www.newegg.com/Product/Product.asp?Item=N82E16827106988)

installing is simple. opene case, screw it into place. plug in power cord and IDE ribbon, close case, done

---

### Post by bwog on 2005-11-27
This info could be superfluous by now, but perhaps this helps

HOWTO: Install Ubuntu Linux without burning a cd - 04-22-2005

[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

or the guide it refers to. Havent tried it myself.

Buying a drive (like xelink said) is not a bad idea either, it simplifies things, but perhaps it is not an option for this poster.

---

### Post by andrew.sroka on 2005-11-27
Hello again :-)

I trying to install ubuntu using netboot. I got dhcp serwer on other computer with windows (Tftpd32) and there is full image of ubuntu.  I've tried to use (Installation / Server Netboot Wiki - [https://wiki.ubuntu.com/Installation/WindowsServerNetboot](https://wiki.ubuntu.com/Installation/WindowsServerNetboot))

Everythig starts ok. Ubuntu is trying to boot from "windows" but I stuck  when I have to input mirror... When I choose one from the list I get :

[B]Bad archive mirror
The specified Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror.[/B]

what to do to force the installer to get the image  form the other computer ?


Regards: Andrew Sroka

---

### Post by Dr. Nick on 2005-11-27
[QUOTE=Gonte]Now i got Windows 2000, and i would rather keep it if possible, but i only got  one big partion (at least i think it's only one)...[/QUOTE]

If you want to keep it then you will have to resize the current partition, The post just above yours says the ubuntu installer can do that for you, I have never done so myself therefore I am not sure how risky or how easy it is to do.

---

### Post by yesplease on 2005-11-27
The installer can resize. However, it is easy and safe with gparted on the live CD. 

Edit: Oh, this was the 'I have no cd' item :)

---

### Post by Doughsay on 2005-11-28
> The installer can resize. However, it is easy and safe with gparted on the live CD. 

The Ubuntu installer and gparted both use the ntfsresize utility, so they should both have the same reliability.

> Everythig starts ok. Ubuntu is trying to boot from "windows" but I stuck when I have to input mirror... When I choose one from the list I get :

Bad archive mirror
The specified Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror.

what to do to force the installer to get the image form the other computer ?

I just did all this myself.  The problem is that you're not resolving names from a DNS server.  In your tftpd32 program, you need to specify a DNS server address in the DHCP tab.  I found my DNS server addresses by going to a command console in windows and typing "ipconfig -all".  If you can't find it that way, I could suggest maybe typing "ping <ubuntu-archive-mirrir>"  This will give you it's IP address, then manually fill in the IP address into the Ubuntu installer.  I don't if that will completely work though...

Good Luck!

---

### Post by Gonte on 2005-12-05
hmm... now i erased windows and installed ubuntu as the only operating system, but after installing i'm a little bit cunfused...

on the live cd (wich i tested on an other computer) u come straight to the desktop after logon, but with the new install i end up with getting told to enter username and password, and after that it just tells me:
```
Ubuntu 5.10 "Breezy Badger" Gonte tty1

Gonte login: gonte
Password:
Last login: Mon Dec 5 16:00:06 on tty1
Linux Gonte 2.6.12-9-686 #1 Mon oct 10 13:25:32 BST 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with absolutely no warraanty, the extent permitted by applicable law.
gonte@Gonte:~$
```

Could there be something wrong with the installation or am I just supposed to write a command now? (and in that case: What command should i write?)

---

### Post by bwog on 2005-12-05
You could try this: [http://ubuntuforums.org/showthread.p...t=vesa+console](http://ubuntuforums.org/showthread.p...t=vesa+console)

write

sudo dpkg-reconfigure xserver-xorg 

(press ctrl-alt-f1 to get into console if you need to) you are already in a console if I understand this question well.

and chose vesa driver

If this works, search the howtos in 'customization tips' to install your video cards driver(probably Nvidia or ATI). If it is possible for your video card, choose one that is available via synaptic.

---

### Post by Gonte on 2005-12-06
Well, i guess it's something wrong with the installation, cause i just get the answer:

Package 'xserver-xorg' is not installed and no info is available.


Think it's time to get a cd-drive and make a new install from a cd cause this is just to much trouble...

---

### Post by Kelpie on 2005-12-06
[QUOTE=xelink]really fi you can't do/afford that you shouldn't be installing an OS.
[/QUOTE]

not true at all because some laptops do not come with a CD-rom drive or even a floppy drive and even though this can be troublesome theres no real way to fix THIS problem unless youre great with modifying laptops

oh and i never thought about looking in the advanced install thing, guess i should of thanks you guys :D hope it works out

---

### Post by tuxcantfly on 2007-04-29
If you're using windows and want to install Ubuntu without a CD, see here: [http://ubuntuforums.org/showthread.php?t=427793](http://ubuntuforums.org/showthread.php?t=427793)

---

