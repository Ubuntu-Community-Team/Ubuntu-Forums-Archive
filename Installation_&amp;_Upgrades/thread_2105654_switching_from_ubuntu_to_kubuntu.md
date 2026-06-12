---
title: "switching from ubuntu to kubuntu"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by MasterJimmy on 2013-01-16
ok the situation is a little convoluted so read the whole thing first before you have the "dumbass" reaction. ok, im running a 64 bit ubuntu 12.10 and want to go to a kubuntu 12.04. i know i can just install and wipe ubuntu completely and i know i can do a dual boot. my issue is not enough backup media for all my files like music, videos etc. is there a way to run a dual boot then use a usb drive to transfer the files from the ubuntu os to the kubuntu os then get rid of ubuntu and expand the kubuntu install?

---

### Post by mad2-814 on 2013-01-16
If you install Kubuntu as well, you can access all of the Ubuntu partition as they are the same filesystem.  All you need to do is open nautilus on the Kubuntu install and copy all the desired files from the Ubuntu partition to the Kubuntu partition.

---

### Post by MasterJimmy on 2013-01-16
ok and how do i get rid of the ubuntu install completely and etc?

---

### Post by mad2-814 on 2013-01-16
After you have all the files and are booted into the Kubuntu install, install gparted
```
sudo apt-get install gparted
```

Run grub install just incase
```
sudo grub-install /dev/sda
```
with (/dev/sda) being the name of your disk you want grub on

and delete the Ubuntu partitions in gparted

---

### Post by MasterJimmy on 2013-01-16
> **mad2-814 said:**
> After you have all the files and are booted into the Kubuntu install, install gparted
```
sudo apt-get install gparted
```

Run grub install just incase
```
sudo grub-install /dev/sda
```
with (/dev/sda) being the name of your disk you want grub on

and delete the Ubuntu partitions in gparted
then expand the kubuntu partition?

---

### Post by mad2-814 on 2013-01-16
Im not sure if you can expand to a previously used partition, but you can reformat it and use it to hold files and such.  If anything look for an expand option in gparted.  I'm currently on a windows machine so I can't look.

---

### Post by MasterJimmy on 2013-01-16
im a little leery about doing any additional partitions for mostly not wanting to have to deal with it and i prefer to have one partition when i have one os. im just going to have to bite the bullet and back up everything somehow and just redownload whatever i cant and do a fresh install because the kubuntu installer is a little out of my range so to be safe im just going to start from scratch. im used to the ubuntu installer and kubuntu's isnt familiar enough for me to risk it. thanks for the info though.

---

### Post by oldos2er on 2013-01-16
Other than the desktop environment, the Kubuntu installer is the same as Ubuntu's.

Having your media files in a separate partition, whether it's /home/user/ or something else, would make this much simpler.

---

### Post by MasterJimmy on 2013-01-17
> **oldos2er said:**
> Other than the desktop environment, the Kubuntu installer is the same as Ubuntu's.

Having your media files in a separate partition, whether it's /home/user/ or something else, would make this much simpler.
I like the alice reference btw. Ok this is the situation in a nutshell. I created the live usb using startup creator, then clicked test disk. Tried to run the install from that but appaarently it didn't display correctly but did when I ran it normally. I interrupted the instal during resize and went back to it after I handled what I stopped to handle. Now I only can use the whole disk or manual resize. Not a tragedy as I can still access everything I'm concerned with. I tried to install kde on my ub12.10 and get rid of unity but had a thermal shutdown during it so when I boot norml it says can't. Detect video settings and gives me a choice of run low res or fix manually but won't letme select either option. When I plug in the usb I cqan use kubuntu with no prob. Any leads on how to have it where you have to have the usb or micro sd card insterted to boot up? I like how it is now other than I'm not sure if I would be able to install software or keep it updated this way. I just want it so you have to hve my specific usb or microsd card inserted. Mostly my james bond super spy phase from when I was a kid talking, but I like the idea of it. Btw I like the Alice referrence on your tagline

---

### Post by MasterJimmy on 2013-01-20
well i got internet back so here goes. i dont know what happenned during the whole affair before but i did lose some of my files. no big tragedy for the most part as i can recover everything that is actually important from my old desktop anyway. not sure exactly what all i did lose but im pretty sure it was all stuff i didnt care about anyway. the loss of my business plans would have annoyed me if they werent all on the desktop hard drive though. i have to say that other than a few things like how to get to various menu items and such kubuntu is pretty good so far. im not thrilled about how hard it is to do a two window drag and drop for moving files like i would do on ubuntu but after a few minutes of working with dolphin and figuring it out i can deal with it. most of the questions i had about kubuntu turned out to be no issue at all. muon software center seems to have everything i want so far but i do like the ubuntu center a little better because its easy to check the overall progress of downloads and installs but i cant even find a progress option in muon.

---

### Post by MasterJimmy on 2013-01-28
ok now im having a really weird issue. i installed Ubuntu Software Centre and noticed some strange behaviors that can only be described as it looks like my computeris trying to change back to ubuntu.i started seeing ubuntu instead of kubuntu in the shutdown sequence (the messages it displays when its shutting down after the desktop closes and the screen is black)and now i cant start up. i mean i can log in normally but then alli get is a blank blue desktop with no way to access my apps and files and when i right click i get the same options and menu style as i did in ubuntu with no kubuntu aspects at all. i am using the live usb for now so i can back everything up again before i do a clean install again withou installing USC again, or in hopes i can find a way to fix this. i cant run terminal without the usb in and when i do it only gives readouts for the live system and not my native OS. any ideas what happened? i tried to google it but couldnt find anything useful.

---

