---
title: "Installing Ubuntu from SD card - Toshiba laptop help"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by tony82 on 2015-07-04
Hello,

I'm trying to install Ubuntu from an SD card on my Toshiba Portege r830 with windows 7 already installed. The problem I'm running into is that the Toshiba BIOS doesn't support booting from an SD card. It will recognize a USB drive and CD drive. 

I don't own a thumb drive and don't have access to any blank media at the moment.

So far I have attempted to boot from a rooted Galaxy S4 using DriveDroid to mount the .iso. It seems to want to boot from there although I was trying from the internal memory which I think is too slow to be effective. Also, I don't want to just run Ubuntu from USB but actually install it. 

So I have created the installation disk onto the microSD card via the software from PenDriveLinux and using an microSD to SD adapter. Now I can put the microSD back into my Galaxy S4, and I can get the laptop BIOS to boot from the S4 like a thumb drive, BUT I don't know how to mount the entire installable image onto the SD card in order to make it bootable. I only know how to mount the original .iso image.

Does anybody have any ideas on how I could make this work? I feel like I'm close but just hitting a wall. Any help is appreciated.

---

### Post by Bucky Ball on 2015-07-04
Welcome. So you're saying you can't boot directly from the SD card when you start the machine? If you can, you should be taken to the 'Try Ubuntu' 'Install Ubuntu' etc. No mounting of anything required.

Bit confused as to what you are trying to mount from the SD card if it is created with PenDriveLinux. That should have created bootable install media which you boot from and that's it. Try or install Ubuntu. 

I use Unetbootin myself. Don't know if that will make any difference. Are you positive you are creating a disk image to boot from and not simply moving the .iso from one place to another? That won't boot.

---

### Post by ubfan1 on 2015-07-05
I'm a bit confused too, but second Bucky's suggestion of using unetbootin instead of pendrivelinux.  No current experience with either, but in the past, I had better luck with unetbootin.

---

### Post by tony82 on 2015-07-05
> **Bucky Ball said:**
> Welcome. So you're saying you can't boot directly from the SD card when you start the machine? If you can, you should be taken to the 'Try Ubuntu' 'Install Ubuntu' etc. No mounting of anything required.

Bit confused as to what you are trying to mount from the SD card if it is created with PenDriveLinux. That should have created bootable install media which you boot from and that's it. Try or install Ubuntu. 

I use Unetbootin myself. Don't know if that will make any difference. Are you positive you are creating a disk image to boot from and not simply moving the .iso from one place to another? That won't boot.


Yes, that is what I was trying to say. The BIOS in this laptop (and apparently in a lot of Toshibas) doesn't allow booting directly from the SD card, so I wasn't able to run it directly off of the SD card. 

This doesn't mean I'm not an idiot though. I did get it to install. What I didn't realize is that when simply booting Ubuntu it gives you the option to either start a live session or install directly. It turns out that I didn't need to use PenDriveLinux at all. 

The DriveDroid app on my phone creates a virtual thumb drive and you can "mount" an image onto that virtual thumb drive. So essentially all I had to do was mount the Ubuntu .iso in DriveDroid, restart the laptop with my phone connected via USB, and select the "thumb drive" from the BIOS boot menu.

The only catch was that I had to first download the .iso to my SD card rather than my phone's internal memory so that when the image was "mounted" it was actually reading it from the (faster)SD card. When I had tried to run it from the phone's HDD it was much too slow and the laptop was overheating, thus the reason that I didn't end up making it to the install screen.

So, everything is good now. I have it all set up to dual boot and I didn't even have to buy a thumb drive! :p It's funny how it all seems so simple once you figure it out.


*EDIT*

Another reason I was getting stuck is because of the nature of the DriveDroid app. That app lets you mount an .iso or other image file, but doesn't let you transfer multiple files to one partition. When I used the PenDriveLinux(which I thought I needed) software I was left with a whole bunch of files that I couldn't figure out how to use exactly. This is where I got stuck until I realized I could just use the .iso file as-is.

---

### Post by Bucky Ball on 2015-07-06
Good news! Please see the second link in my signature. 

Enjoy the ride. :)

---

