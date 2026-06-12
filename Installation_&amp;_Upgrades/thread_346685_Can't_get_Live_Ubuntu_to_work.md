---
title: "Can't get Live Ubuntu to work"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by une on 2007-01-26
I want to run ubuntu as a Live CD at my work (Windows) PC without altering the HD at all. I plan on using persistent /home on a USB memory key in combination with the LiveCD.
I have a CD with 
ubuntu_6.06.1-desktop-i386.iso
on it.
I checked the hashes and all is OK.
I just tried to test it on my home PC that has 2 HD (Windows and Mandrake Linux).
I put the CD in a CD/DVD drive and changed my BIOS settings to boot from that CD/DVD drive.
I restarted and no ubuntu, my regular Mandrake install on my HD booted up.
This HD (the one with Mandrake on it) was the next on the boot sequence list in BIOS after the CD/DVD drive containing the ubuntu .iso CD.
I had my Windows HD disabled.
What went wrong? The CD spun for a short time on startup, but that was it.
Is a LiveCD different to the regular desktop download? The different .iso file names shown on the ubuntu hash page indicates that perhaps a "LiveCD" .iso is a different file to the regular desktop .iso. However I can find no place to download a "LiveCD" .iso on the ubuntu site.

---

### Post by une on 2007-01-26
I am not sure but I think the problem may be the way in which I burned the CD. 
I picked up the following valuable warning at Puppy Linux at;
[http://puppylinux.com/cd-puppy.htm](http://puppylinux.com/cd-puppy.htm)

[COLOR="Green"]WARNING FOR NEWBIES:
If you don't know anything about burning an ISO file to CD, read the documentation that comes with your CD-burner software. The biggest single mistake is that people treat the "puppy-2.xx-xxxx.iso" file as just a file, and write it to CD. Any decent CD-burner software will have a special menu selection for writing an ISO file to CD. You will know that you have succeeded if, after burning it, you use a file manager such as Windows Explorer to look at the CD and you see the files "image.gz", "vmlinuz", etc. If you see the file "puppy-2.xx-xxxx.iso" then you did it wrong!
The thing to understand about an ISO file is that it is a snapshot of the entire contents of a CD, so has lots of files inside it.[/COLOR]

I then found out how to do the burning the correct way using k3b at
[http://www.pclinuxonline.com/wiki/BurningIsoK3B](http://www.pclinuxonline.com/wiki/BurningIsoK3B)

As I use Mandrake Linux on my desktop there were no instructions for burning the iso image to disc on the Ubuntu website at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I believe that the help offered at the Ubuntu website could be improved by including a warning similar to that shown above as is presented on the Puppy Linux website. This is critical information for newbies and I would have failed to realize my mistake (I am assuming my CD burning method is the cause of my problem) if I had used the Ubuntu help page only. Help for using k3b is maybe a bit too specific for inclusion in the Ubuntu CD burning help page, but it  was valuable.

I will post back to let all know if the way I burnt the CD was the problem.

---

### Post by louieb on 2007-01-26
The Ubuntu live CD works just like any other Linux live CD.
So lets get to the usual suspects.[LIST]
[*]Bad download. You checked the hashes so probably not the problem.
[*]Burned as file, Should be burned as image. Maybe. Did you burn as image with a program such as ISO Recorder or Burncdcc? If  Ubuntu...iso is the only file on the CD then this is a problem.
[*]Bad burn. Maybe. I have better luck burning at a slow speed. use 2x or 4x.
[*]BIOS just won't boot the CD. You changed the boot order in BIOS. Probably not the problem.[/LIST]Let us know how the persistent home works out. I don't know that Ubuntu Live has an easy way of doing that. I have never tried it.
For a little more information check out the psychocats link in my signature.
I see you found the problem. Good Luck

---

### Post by une on 2007-01-27
OK, I did not burn as an image. Rather I just burnt the .iso as a file. I now knew what to do. So I downloaded ubuntu 6.10 i386 and burnt to CD as an image. I checked md5sum hashes and all was OK. I then booted from CD/DVD drive and ubuntu sort of worked. The following appeared as follows;

*Text on a black screen saying;*
**Unknown keyword in config file**
*A GUI menu then appeared and I selected;*
**Check CD for defects**
*Then a window appeared saying;*
**Loading Linux Kernel**
[I]It started at 4% and never moved past this, it was frozen.
I then got an error window saying;[/I]
**I/O error - Error reading boot CD**
*While this error window was displayed, at top of screen text appeared saying;*
[B]Loading /casper/vmlinuz...isolinux: Disk error 80, AX=4200, drive 9F
[/B]

A bit dissapointing. Any ideas on what went wrong?

---

### Post by louieb on 2007-01-27
So lets get back to the usual suspects.[LIST]
[*]Bad burn. Maybe. I have better luck burning at a slow speed. use 2x or 4x.
From the messages this is what I think the problem is. The CD check program did not even get far enough to tell if you if the CD passed the checksum test or not.
 I have not had much success with  the burn program suggested in the Ubuntu wiki even though it is open source. That is why I suggested ISO Recorder or Burncdcc.  also burn the CD at a slow speed 4x or 2x.[/LIST]I hope that is what the problem is. If is not -  Well  have you noticed that some PC makers such as HP and Compaq seem to have a version of windows tailored to there hardware. Well Linux is not tailored that way. What Linux has is cheat codes. Cheat codes are options you give the kernel at boot. There are a bunch of them. I have no way of telling which on are needed (if any) for any given PC. Do a google/linux search on cheat codes.
One thing to note: Cheat codes are used by the Linux kernel and are not usually distribution specific.

---

### Post by une on 2007-01-27
I tried the CD on another PC and it worked flawlessly. I did the CD check and no errors were found. The PC it did not work on has an ASUS P4B motherboard and it runs Mandrake 10 Linux and Win XP without problems.
In answer to your question about the persistent home, it may not the best place to say this but to be honest the Puppy Linux system of using a Live CD in combination with a USB memory stick works flawlessly on every PC I have tried it on, including the PC ubuntu failed to run on.

---

### Post by Pobega on 2007-01-27
> **une said:**
> I tried the CD on another PC and it worked flawlessly. I did the CD check and no errors were found. The PC it did not work on has an ASUS P4B motherboard and it runs Mandrake 10 Linux and Win XP without problems.
In answer to your question about the persistent home, it may not the best place to say this but to be honest the Puppy Linux system of using a Live CD in combination with a USB memory stick works flawlessly on every PC I have tried it on, including the PC Ubuntu failed to run on.

That's because PuppyLinux is made to run on LiveCDs, while Ubuntu is made to be a real distro (Installed on the hard drive). PuppyLinux falls into the same category as Damn Small Linux, and FeatherLinux; They're made for live use, while Ubuntu is made to be installed to a hard drive.

Also, try re burning at 2x speed (I believe you can do this in K3B), and see if that helps out at all. If not, I would possibly blame the computer's CD drive, unless it works flawlessly with other CDs (Have you tried PuppyLinux on it?).

---

### Post by une on 2007-01-27
No trouble at all with Puppy Linux Live CD on the same PC and no other troubles with the CD/DVD drive. Strange why my Ubuntu CD doesn't like that PC.

---

