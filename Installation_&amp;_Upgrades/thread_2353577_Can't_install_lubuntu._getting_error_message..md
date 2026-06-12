---
title: "Can't install lubuntu. getting error message."
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by mohaafan on 2017-02-23
I'm trying to install lunbuntu 16.10 32bit version on HP pavilion 525W 

Current OS: Windows XP Pro 32 bit
pentium 4 2.4ghz
1GB RAM
100GB HDD
8MB (that's megabytes) graphics memory

I burned the iso onto a CD then I was presented with the main menu when I booted from the CD. After I choose to install lubuntu, the lubuntu logo appears and hangs for a long time and then I am presented with the following error message. Something about unexpected child device config size... does the computer not have the required minimum hardware requirements or it is not compatible for lubuntu? Can i install puppy linux on this computer? Thanks for the help.

[[IMG]https://image.ibb.co/m3D2bF/Ni_BRax_J_Imgur.png[/IMG]]("https://ibb.co/hwJDiv")

---

### Post by ajgreeny on 2017-02-23
You say you burned it to a CD; did you mean CD or DVD as the iso file of Lubuntu is too large to go on a CD?

If it really was a CD, that may be your problem, though I would have expected the burning software to tell you there was insufficient room.

Can the machine boot from a usb?  That may be the best way to proceed if you can.

---

### Post by mörgæs on 2017-02-23
This is very old hardware and the install is not necessarily like on a new computer.

I suggest that you first install a text-only system using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). When that works we can take a look at the graphics interface.

I also suggest 16.04.2 in stead of 16.10 for old hardware (as opposed to new, where people should use the latest release). They are likely to work equally well but the former has support until april 2019.

Edit: Now I see that the processor is also overheating. Have you opened the case and (gently) vacuum cleaned all fans and cooling fins?

---

### Post by Impavidus on 2017-02-23
You also have several I/O errors on the dvd drive. That suggests a bad burn, a bad dvd or a bad dvd drive. You may have to clean that too.

---

### Post by mohaafan on 2017-02-23
> **ajgreeny said:**
> You say you burned it to a CD; did you mean CD or DVD as the iso file of Lubuntu is too large to go on a CD?

If it really was a CD, that may be your problem, though I would have expected the burning software to tell you there was insufficient room.

Can the machine boot from a usb?  That may be the best way to proceed if you can.

I burned it onto a DVD and I tried every which way to boot it from a usb, but was unsuccessful.  I tried using USB ZIP and USB FDD options in the bios (this bios does not have a USB-HDD option) and even used partionguru to make the usb stick bootable in the USB ZIP format, but no success. The blank black screen shows a blinking cursor at the top left corner and nothing happens. BTW, I did change the boot order to boot from the "removable device" first.

> **mörgæs said:**
> This is very old hardware and the install is not necessarily like on a new computer.

I suggest that you first install a text-only system using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). When that works we can take a look at the graphics interface.

I also suggest 16.04.2 in stead of 16.10 for old hardware (as opposed to new, where people should use the latest release). They are likely to work equally well but the former has support until april 2019.

Edit: Now I see that the processor is also overheating. Have you opened the case and (gently) vacuum cleaned all fans and cooling fins?

I'll try the minimal iso and the cleaning suggestion and report back.

> **Impavidus said:**
> You also have several I/O errors on the dvd drive. That suggests a bad burn, a bad dvd or a bad dvd drive. You may have to clean that too. Ok. I'll do this also. Thanks for the replies guys. I'll report back.

---

### Post by yoshii on 2017-02-24
Don't use a .zip for a USB boot, use an .ISO and don't use uNetBootIn, use something like YUMI or some other alternative.  Also, make sure your computer's BIOS is ready and able to boot from USB.  You may have to disable SecureBoot for this.

---

### Post by mörgæs on 2017-02-25
> **yoshii said:**
> You may have to disable SecureBoot for this.

The Pavilion 525W is from a time before a software vendor decided to lock hardware 'secure'ly to their operative system. It only has Bios and hence no boot restrictions.

---

### Post by RobGoss on 2017-02-25
I would recommend trying Lubuntu LTS instead of 16.10 might be a better choice and use the ISO file as directed 

If you can boot from a **USB** I would also recommend doing that, **DVD** are sometimes problematic and can produce all sorts of error messages when trying to install the OS. The 1-GB of memory tells me you will have problems with other versions of Linux unless you stick to the lighter versions for better performance 

Can you even boot in to the live media?

---

### Post by mohaafan on 2017-03-01
I was able to burn the miminal iso version 16.04 and installed it along with lubuntu desktop via bootup to DVD, but youtube videos were still skipping and lagging badly in chrome browser and firefox -- no improvements compared to win xp. In fact, it was much worse. So I reinstalled win xp. 

Some observations:

1. This time, I was able to install lubuntu from a DVD. So, in the original situation, I think the computer did not have enough graphics memory (only has 8MB) for the full install GUI, hence the error message "unexpected config size". I might upgrade the video card on this computer soon.

2. In win xp, youtube vids were very laggy, but if I download the video from youtube to my desktop and play it with media player classic it plays smoothly without any lagging or skipping. If I play it with VLC media player though it is laggy and skips heavily. Seems like I need to use a lightweight browser but browsers like pale moon and midori lack the features needed for youtube video playback in the browser. They also lack a lot of the browser extensions I need.

3. Apparently, this desktop computer does not have a bios that allows bootup to USB-HDD, only USB-ZIP AND USB-FDD. So, I was not able to install lubuntu via USB stick.

Thanks for the help guys. Much appreciated.

---

### Post by mörgæs on 2017-03-01
You are welcome.

Xp has been out of support for some years meaning that a large number of security holes are unfixed. I wouldn't install in on any kind of hardware, new or old. 

I don't think it makes sense to upgrade the video card. Lack of memory and processor power will be the next bottlenecks you encounter. Better to search for a used (but younger) computer as a replacement.

---

