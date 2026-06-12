---
title: "can't boot from USB, please help."
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by pouya314 on 2010-07-26
Hi, 

I am trying to install Ubuntu Netbook Remix on my hp mini 210. So I followed the instructions on ubuntu website on how to create a USB drive (using universal USB installer on windows) and install ubuntu off of that usb stick. However, the problem I have is that when I restart, my computer doesn't seem to be able to boot from that usb stick for some reason (even though i have changed the boot order in BIOS but when I choose boot options on startup, there is no "boot from usb" option. only internal hard disk.)

any help is appreciated.

Thanks,

---

### Post by bocaccio on 2010-07-26
Download and use UNetbootin

It works like a charm!! That will boot almost anything you put on it. 

I am on a Asus eee pc 1005peb netbook and that is how i booted netbook remix.

---

### Post by pouya314 on 2010-07-26
> **bocaccio said:**
> Download and use UNetbootin

It works like a charm!! That will boot almost anything you put on it. 

I am on a Asus eee pc 1005peb netbook and that is how i booted netbook remix.
So, are you saying that my USB stick is not bootable because of Universal installer?

---

### Post by oldfred on 2010-07-26
Look under hard drive options for another drive which is your USB flash drive.

I do not know about your HP mini but my system has a ton of USB boot options, none will boot a flash drive. Until I accidentally left a USB boot drive in and was choosing a different hard drive did I realize on my system a USB flash drive is a hard drive choice.

---

### Post by Nick_Jinn on 2010-07-26
You have to install a USB drive differently. You have to use the "create startup disk" option, rather than the regular install with choosing the USB drive.

Also, you might have to use your F buttons to load it....like I have to hold down F8 or F9 at startup to get any USB device to work.

---

### Post by bocaccio on 2010-07-26
Sorry I misunderstood you. I go in the bios and actually had to scroll down 3 times in the boot menu. 

Pick my USB drive
Then make it the first boot device.

---

### Post by bocaccio on 2010-07-26
> **Nick_Jinn said:**
> You have to install a USB drive differently. You have to use the "create startup disk" option, rather than the regular install with choosing the USB drive.

Also, you might have to use your F buttons to load it....like I have to hold down F8 or F9 at startup to get any USB device to work.


I trust you know what you are talking about. But I did not install this one any different than I would with a live disc. I just hit the install icon on the front/favorites screen and it installed just fine. 

I may have misunderstood you. The install went very smooth though.

---

### Post by Nick_Jinn on 2010-07-26
> **bocaccio said:**
> I trust you know what you are talking about. But I did not install this one any different than I would with a live disc. I just hit the install icon on the front/favorites screen and it installed just fine. 

I may have misunderstood you. The install went very smooth though.

Right. Its possible to load it that way, depending on how GRUB is set up I think.....but if you want it to be plug and play on any PC you might want to go back and reinstall it with the startup disk creator from live CD....or you can do it from an intalled desktop if you have the CD image.

That could be why it downloaded but you are having trouble booting it.



Or if by "install" you mean that its BOOTING just fine now....well, awesome. Im glad you got it working.

---

### Post by bocaccio on 2010-07-26
> **Nick_Jinn said:**
> Right. Its possible to load it that way, depending on how GRUB is set up I think.....but if you want it to be plug and play on any PC you might want to go back and reinstall it with the startup disk creator from live CD....or you can do it from an intalled desktop if you have the CD image.

That could be why it downloaded but you are having trouble booting it.



That is also why i got this snappy little usb powered samsung dvd writer for my netbook. So If need be I can use a live disc instead of booting from usb.

---

### Post by Nick_Jinn on 2010-07-26
Did you get it to boot from USB?

---

### Post by pouya314 on 2010-07-26
Nick, let me try once more after work. I will keep you posted.

---

### Post by Nick_Jinn on 2010-07-26
Try reinstalling with the startup disk creator, over your current USB install....then keep playing with your f buttons at startup until it gives you a boot loading from device screen.

---

### Post by bocaccio on 2010-07-26
> **Nick_Jinn said:**
> Did you get it to boot from USB?


Yes i mainly just got the optical drive so i can make backups and if i ever do need it i'll have it.

---

### Post by pouya314 on 2010-07-26
Nick, I tried once again. I get to the page where I can select which device to boot from. But the only option I am given is the netbook's internal hard drive. I am a bit confused here. So I would appreciate if you could explain a bit more about the process, especially "startup disk creator" and how to use it. pls note that I am currently running wondows 7 on my netbook. Thanks buddy.

---

### Post by Nick_Jinn on 2010-07-26
While its possible to boot from USB using the regular -to hard drive- installation method, it can cause problems with GRUB....the reasons for this can be complicated, bu the best bet is to go back and use the startup disk creator.



So its simple....You can do it from an installed version of Ubunt OR from live CD....it doesnt matter.

Boot into Ubuntu from CD or hard drive.....go to 'system' > Administration > 'Startup disk creator'....Click on it. 


On the top of the pop up program box you will see "Source disk ISO or CD image".....Click on the box to search for your ISO image or if you already have your ubuntu CD in the optical drive click on that option.

Next option is 'Disk to use". Select the USB device you want to install it on. You might want to erase it with Gparted first. Leave it unpartitioned. 

Finally you have the choice between having it lose all your information on shutdown, or having space for your /home and /data where you can save your files and settings....I prefer set aside space for this.....For a 8gb flash card I would use 3gb....but it depends on how much programs you want to add. I think 3gb is the maximum you can allocate. You could choose less.....for 4gb I would chose 1gb or 1.5gb. For 2gb I would choose a few hundred MB. For 1mb I would chose puppy linux or knoppix instead, or not reserve any room for storage,

Then click "Make startup disk" and the process will look very much like how you installed it to hard drive.


Now you can load from USB drive as a hard drive, but its going to be a problem when you take the USB device on other computers depending on how GRUB is set up and those computers might not boot from it......That is why we use the startup disk creator utility because it has special settings for being a bootable portable flash drive. 


Be aware that the F buttons can be different on different computers. You might have to keep playing with it on a new computer. Also, make sure you are in the RIGHT boot screen. There are a few that look like you are in the bios but they are not the correct one....keep looking, but AFTER you reinstall with the startup disk.


Hope that helps.

---

