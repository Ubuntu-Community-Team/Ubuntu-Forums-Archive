---
title: "BIOS won't boot ubuntu"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by Jalaska13 on 2011-02-13
I've been working with installing ubuntu on a very large volume of computers recently, and many of them won't boot from ubuntu or its educational derivative, edubuntu, because it doesn't recognize it as a legitimate OS.  It will give me errors such as "no valid operating system" and things like this.  Does anybody know how I can force it to recognize, from CD, DVD, or USB, a ubuntu-based operating system and boot from it?

---

### Post by sikander3786 on 2011-02-13
Welcome to the forums :-)

How did you prepare the installation media i.e, CD, DVD or USB? Step-by-step,

1. Download intended Ubuntu release here.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

2. Check the MD5SUM just to make sure the image is healthy and save you troubles later.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. Burn to CD/DVD at the lowest possible speed. DVDs are known to cause some troubles so I'd recommend CD. Make sure you choose burn image to disc option and not a data disc.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

3b. Or burn the image to a USB drive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

4. Make your CD/USB drive, **first boot device** in Bios.

5. Let us know about your progress :-)

---

### Post by Jalaska13 on 2011-02-13
I've done all of the above; I know how to create live and install disks and USBs and whatnot; that's not my problem.  The problem is that some computers simply refuse to boot from ubuntu; they don't recognize disks with it as having an OS installed on them.  These are, btw, disks that have worked perfectly well on other computers.

---

### Post by sikander3786 on 2011-02-13
Can you please post the hardware specs of those computers which are unable to boot Ubuntu. Specially the motherboard make and model.

Are you sure the Bios was configured properly to boot from the external media? Or even, the Bios has the capability to boot external media? Does it successfully boot some other OS CD/DVD or USB?

---

### Post by Jalaska13 on 2011-02-13
sikander3786:
It's definitely set up to boot from external devices; no problems there, although I will admit I've not tried it with other OS disks like xp.

As for the specs:

Dell Dimension 4600
BIOS Version A06

Not sure what the motherboard is, but there's some setting in the BIOS that I've never seen before called "OS Install Mode" that is defaulted to off.  I'm going to set it to on to see what that does.

---

### Post by sikander3786 on 2011-02-13
I haven't experienced that either but it has something to do with the boot process. A quick Google returned this.

> OS Install Mode
	
Turns the OS Install Mode on and off. The default is Off. When set to On, memory is limited to 256 MB to allow the installation of older operating systems that have 2 GB memory limits.

---

### Post by Jalaska13 on 2011-02-13
Update: The OS Install Mode didn't do anything useful.  It says it limits the memory allowed, but that didn't matter because it still gave me the same errors before ever booting successfully (which it never did)

---

### Post by sikander3786 on 2011-02-13
Just found that it is intended for older OS like 9x Windows.

If you feel confident, you can try resetting your Bios to defaults or upgrade the Bios. We might be missing something :-k

---

### Post by Jalaska13 on 2011-02-13
Ah.  Thanks!  I doubt resetting will work, but upgrading might; I'll try that.

---

### Post by Jalaska13 on 2011-02-13
Well, that's annoying...  I wiped the disk inside the computer, and all of the bios updaters require you to be on the computer itself running windows, which I am not.  I'm on a mac right now, and the box I want to update is empty.  Does anybody know where I can get the updaters as disk images instead of exe programs to install the installer?

---

### Post by sikander3786 on 2011-02-13
You can get a .exe and use a floppy drive to install it. But the floppy still needs the MS DOS system files.

> 
Run the BIOS update utility from MS DOS environment (Non-Windows users)


NOTE:You will need to provide a bootable DOS diskette. This executable file does not create the MS DOS system files.


   1. Copy the file D4600A12.EXE to a bootable floppy.


   2. Boot from the floppy to the MS DOS prompt.


   3. Run the file by typing Y:\D4600A12.EXE (where y is the drive letter where the executable is located).

---

### Post by Jalaska13 on 2011-02-13
Wait, how do I get an MS DOS prompt on a computer that only has a BIOS on it and nothing else?  The hard drive has been fully wiped.

---

### Post by sikander3786 on 2011-02-13
> **Jalaska13 said:**
> Wait, how do I get an MS DOS prompt on a computer that only has a BIOS on it and nothing else?  The hard drive has been fully wiped.
You still need to boot a Windows 98 CD I think. Then you can use the floppy disk as Bios upgrade source.

---

### Post by mr clark25 on 2011-02-13
it sounds like the booting from the floppy should bring you to one.

---

### Post by williamts99 on 2011-02-13
You can get a floppy boot disk image from [http://www.bootdisk.com](http://www.bootdisk.com)


From the Dell site where you download the BIOS:
```
Run the BIOS update utility from MS DOS environment (Non-Windows users)


NOTE:You will need to provide a bootable DOS diskette. This executable file does not create the MS DOS system files.


    Copy the file D4600A12.EXE to a bootable floppy.


    Boot from the floppy to the MS DOS prompt.


    Run the file by typing Y:\D4600A12.EXE (where y is the drive letter where the executable is located).
```

---

### Post by Jalaska13 on 2011-02-13
Thanks!

---

### Post by penguinv on 2011-02-14
> **Jalaska13 said:**
> I've been working with installing ubuntu on a very large volume of computers recently, and many of them won't boot from ubuntu or its educational derivative, edubuntu, because it doesn't recognize it as a legitimate OS.  It will give me errors such as "no valid operating system" and things like this.  Does anybody know how I can force it to recognize, from CD, DVD, or USB, a ubuntu-based operating system and boot from it?

You are trying hard.
1. can you tell us the specs of your computer... brand bios memory
2. Will it boot to the CLI of linux?
3. Will it boot to the CLI of DOS?
4. Have you tried a different hard drive? (seems easier than redoing the MBR and there are things "lower than" the MBR. In Windows one gets to alter them with DEBUG. (shivers in my memory)

OK what I am looking at is
1. is it the bios
2. is it on the hard drive

Thanks. I will return.

Zen Beginner, constantly.

---

### Post by penguinv on 2011-02-14
> **sikander3786 said:**
> You still need to boot a Windows 98 CD I think. Then you can use the floppy disk as Bios upgrade source.

You want to "go into" the bios and see what you can set.

Someone here is vague on what a bios does and what an operating system does.

---

### Post by penguinv on 2011-02-14
> **Jalaska13 said:**
> sikander3786:
It's definitely set up to boot from external devices; no problems there, although I will admit I've not tried it with other OS disks like xp.

As for the specs:

Dell Dimension 4600
BIOS Version A06

Not sure what the motherboard is, but there's some setting in the BIOS that I've never seen before called "OS Install Mode" that is defaulted to off.  I'm going to set it to on to see what that does.

I posted twice in this thread before seeing that we have the same computer. Bingo. I use ubuntu. I offer my assistance.

It's not just luck you know. First suggestion: see if you can set your bios to "defaults" second: do you have Windows installation disks? If you never got the SP2 from Dell they will send them to you for free. Yes really there are some advantages from going Dell.

I got this because it was old and it never worked. I had to replace the Nvidia card and it is golden - although the video port on the m'board never worked for me.

I'm with you... 

Why do I suggest that you get the Windows installation disks. Well I got a new HD. :) And I formatted it one way with linux (Ubuntu) gparted stuff, then I changed it and oops. Gparted would now "quit unexpectedly". No one seems to help, inc on #ubuntu, so ... I reformatted it with the windows disks in the slow "takes all night for 1T" way. After that it works.  Go figure.

But tell me what happens after you reset the bios and I'll go look at mine. But I'd like you to report on which BIOS you have. and if there is any kind of firmware update associated with it.

It's really good how Dell will support things, (Though I'd prolly not buy Dell new.)

OK again, I'm with you...

---

### Post by Jalaska13 on 2011-02-16
Well, I finally got around to installing XP and running the BIOS upgrade, upgrading it from version A6 to A12 (no idea if that means they're 6 versions apart...).  It will now boot successfully from Ubuntu.  Yay!  That said, it still won't boot from an Edubuntu CD, but I'll figure that out later; it may be because Ubuntu was on a USB and Edubuntu was on a CD.  The CD drive configuration in this box is a bit odd...

---

### Post by williamts99 on 2011-02-16
> **Jalaska13 said:**
> Well, I finally got around to installing XP and running the BIOS upgrade, upgrading it from version A6 to A12 (no idea if that means they're 6 versions apart...).  It will now boot successfully from Ubuntu.  Yay!  That said, it still won't boot from an Edubuntu CD, but I'll figure that out later; it may be because Ubuntu was on a USB and Edubuntu was on a CD.  The CD drive configuration in this box is a bit odd...

Also, if the group of computers you want to install onto are the same machines, you can just clone the hard drives using something like clonezilla.

---

### Post by Jalaska13 on 2011-02-16
> **williamts99 said:**
> Also, if the group of computers you want to install onto are the same machines, you can just clone the hard drives using something like clonezilla.

You, sir, are quite correct.  Although my method of choice would be OS X Disk Utility, but same idea.

---

