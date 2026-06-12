---
title: "Ubuntu Install [Errno 30] Read-only file system: '/target/bin'."
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by neutronforrest on 2012-02-01
I'm having real issues installing 11.10.  I have computer I built a few years back where I had Windows Vista installed.  I have decided to ditch windows and install Ubuntu.  I have Ubuntu installed on my computer at work and enjoy it.  However, I have had no luck installing Ubuntu on my home computer.  The details of my system are.


Motherboard:  Xfx nForce 680i LT SLI
CPU: Intel E4500 2.2 GHz
HDD:  Seagate 400 gb
Video Card:  nVidia GeForce 8800 GT


I first installed Ubuntu along side Vista and it worked great.  I had a dual boot where I could load Vista or Ubuntu.  This leads me to believe that my computer has no issues with Ubuntu.  It even recognized my video card.


Now came the nightmare.  I tried to install Ubuntu on the computer and wipe everything off.  I keep getting the following error.
 
  [Errno 30] Read-only file system: '/target/bin'.    Curiously I can install Windows XP to this HDD with no issues.  I have tried 




[LIST=1]
[*]Updated my bios from Xfx.
[*]Used SeaTools and confirm my HDD is okay.
[*]Removed memory to minimum.
[*]Tried using both CD and USB with 10.04 and 11.10...all give the same error...:(
[/LIST]
I am so stuck I don't know what to do.  Any suggestions for what to try next would be appreciated.

---

### Post by cortman on 2012-02-01
Just a suggestion: Can you completely format the HD with a Windows 7 or Vista disc? I don't remember if XP has that option. Just format, not install.

---

### Post by neutronforrest on 2012-02-01
I can try to do that.  I have the Vista disk.  I just got off the phone with XFX and they said they rarely get issues with this board.  So I think I can eliminate that.  He did mention that I should try to set pci=nomsi.  I think I can do that from the boot options.  I am looking but don't see it yet.

I am curious...why should I format with windows.  Can I format wth seatools?
Thanks for the reply...it is getting quiet...like I am missing something very simple...

---

### Post by cortman on 2012-02-01
> **neutronforrest said:**
> 
I am curious...why should I format with windows.

Because Ubuntu wasn't working. Sometimes it takes Windows to destroy Windows. I haven't used Seatools, but it may work. I would try Windows.
Let us know how it works!

---

### Post by neutronforrest on 2012-02-01
I was told by a friend of mine that the command 

dd if=/dev/zero of=/dev/hda bs=512 count=1

Will wipe the disk..Is this true?
Again..any help would be appreaciated...:)

---

### Post by cortman on 2012-02-01
> **neutronforrest said:**
> I was told by a friend of mine that the command 

dd if=/dev/zero of=/dev/hda bs=512 count=1

Will wipe the disk..Is this true?
Again..any help would be appreaciated...:)

Possibly, yes, that command might work. If you can boot into a live CD or USB to run it, though, you could also try using GParted to delete all partitions and format.

---

### Post by neutronforrest on 2012-02-01
I tried that...I talked with XFX and they said to try pci=nomsi in the Ubuntu BootOptions.

---

### Post by cortman on 2012-02-01
Try using the Windows disk and let us know how it works.

---

### Post by neutronforrest on 2012-02-01
So...nothing works.  I was able to install Fedora 15 without any issues.  I am bummed...I prefer Ubuntu but it will not install...anyone have any suggestions?

Chad

---

### Post by cortman on 2012-02-01
> **neutronforrest said:**
> So...nothing works.  I was able to install Fedora 15 without any issues.  I am bummed...I prefer Ubuntu but it will not install...anyone have any suggestions?

Chad

A bad live CD or USB (whichever you were trying to install with) could be the problem. Burn a new disc and you should be able to overwrite Fedora (install over it).

If you were able to install Fedora, you WILL be able to install Ubuntu.

---

### Post by neutronforrest on 2012-02-02
For Ubuntu I have tried a CD with both 10.04 and 11.10 and they both give the same error.  I also tried a USB from pendrive where I installed Ubuntu on it.  That worked on my laptop with np problem but it would not install on my desktop.

For Fedora I used Unetbootin and it installed without any issues.  Last night I tried using Unetbooting to install Ubuntu and again I got the same error.  I then reinstalled Fedora without any issues.  I am going crazy...I wish I knew what the problem.  I talk with a friend last night and said the Ubuntu kernel is most likely the issue.  But I am not sure what I do next...

Chad

---

### Post by cortman on 2012-02-02
Very strange. I googled around using [Googlubuntu]("http://www.googlubuntu.com/") and it seems that RAID can cause it, corrupt CD's or ISO images can cause it, HD failure, overheating, etc., trying to install using a SATA CD drive and an IDE HD, etc.
I guess it's possible that you've downloaded a corrupt image a couple times. You can verify that it's not corrupted by checking the MD5Sum. See [here]("https://help.ubuntu.com/community/HowToMD5SUM") for detailed instructions on how to do that (you can do it in Fedora or off a live CD).
If the MD5SUM's hold out, could be your HD is failing.

---

### Post by neutronforrest on 2012-02-02
I am not sure.  I checked my HDD with SeaTools and it appears fine.  It is a few years old and very possible.  I don't think I have a bad download.  I have installed Ubuntu on both my home server and laptop.  My guess is that during the install, Ubuntu has a "kernel" that triggers something to see the HDD as read only.  I do not know enough about kernels and the like so I am stuck there.

I did ask a guy from work to bring in a spare HDD and I am going to try that tonight...just as a check.  Outside of this I am not sure.  Just to be clear I have called XFX and he said my MoBo should have no trouble with linux...

I have to admit..this is super frustrating...Chad

---

### Post by cortman on 2012-02-02
> **neutronforrest said:**
> I am not sure.  I checked my HDD with SeaTools and it appears fine.  It is a few years old and very possible.  I don't think I have a bad download.  I have installed Ubuntu on both my home server and laptop.  My guess is that during the install, Ubuntu has a "kernel" that triggers something to see the HDD as read only.  I do not know enough about kernels and the like so I am stuck there.

I did ask a guy from work to bring in a spare HDD and I am going to try that tonight...just as a check.  Outside of this I am not sure.  Just to be clear I have called XFX and he said my MoBo should have no trouble with linux...

I have to admit..this is super frustrating...Chad

I understand your frustration. Try it on the other HD, that sounds like a good idea.
The kernel is basically the software version of the CPU. It's the interface program between the rest of your OS and your hardware.
Also, the Linux kernel is used by ALL linux distros, so your Fedora installation is using the same kernel as Ubuntu (possibly a slightly older or newer rev).
"The kernel" is a single file program, about 80-100 MB in size, and is located in /boot.

---

### Post by neutronforrest on 2012-02-02
I was talking with one of IT guys here at work and he said that the kernal used by Ubuntu is not the same as the one used by Fedora.  Does anyone know how/why the Ubuntu kernel will not install on my machine whereas the newer version 3.0...he said...from Fedora will allow for installation?

I do not have much knowledge about the different kernals used by different distro's...

Thanks..Chad

---

### Post by cortman on 2012-02-02
Fedora may use a different version (2.68 as opposed to 3.1, or whatever), but the Linux kernel is the Linux kernel.

---

### Post by neutronforrest on 2012-02-02
I used the Ubuntu alternate live cd and the install was successful.  Solved

---

### Post by cortman on 2012-02-02
> **neutronforrest said:**
> I used the Ubuntu alternate live cd and the install was successful.  Solved

Terrific! Sorry I wasn't much help.

---

### Post by cyruzz on 2012-02-05
I am facing the same problem with the exception, that the alternative ubuntu version didn't work for me. :(

Any suggestions? 

I've tried several version, that i'checked before burning on cd.

---

### Post by neutronforrest on 2012-05-05
I have seemed to encounter another issue with Ubuntu.  I was able to install Ubuntu using the LiveCD a few months back.  My computer was somewhat stable.  It would freeze while I was working on it and would get errors such input/output error.  It would complain about bad sectors.  This led me to believe my HDD was failing.  

I waited till Ubuntu 12.04 was available on performed the upgrade.  It crashed during the upgrade.  I then tried to reinstall using 11.10 with the alternate live CD.  It would not install.  I then ordered a SSD drive thinking my issue was my older HDD.  Again...still will not install.  I don't understand.  Does this mean motherboard is failing.  I am so frustrated.  I did try using a USB stick also...nothing is working.  I even tried installing Fedora and I get the same error.

---

### Post by cortman on 2012-05-07
> **neutronforrest said:**
> I have seemed to encounter another issue with Ubuntu.  I was able to install Ubuntu using the LiveCD a few months back.  My computer was somewhat stable.  It would freeze while I was working on it and would get errors such input/output error.  It would complain about bad sectors.  This led me to believe my HDD was failing.  

I waited till Ubuntu 12.04 was available on performed the upgrade.  It crashed during the upgrade.  I then tried to reinstall using 11.10 with the alternate live CD.  It would not install.  I then ordered a SSD drive thinking my issue was my older HDD.  Again...still will not install.  I don't understand.  Does this mean motherboard is failing.  I am so frustrated.  I did try using a USB stick also...nothing is working.  I even tried installing Fedora and I get the same error.

This is unfortunate. To diagnose the problem I'll need more info though- at what point does it freeze up when trying to install Ubuntu? Can you get to the live desktop, or does it freeze within a couple seconds of choosing the boot device?

---

### Post by neutronforrest on 2012-05-07
Hi...it works fine on the live cd.  I have tried the ubunru alternate live cd and freezes halfway through installation of the files.  I then tried using a usb stick and the same thing happens.  I tried both ubuntu 11.10 and 12.04.  I don't understand.  I guess I could try windows again.  Is there anyway to know if it is my motherboard?

---

### Post by cortman on 2012-05-07
> **neutronforrest said:**
> Hi...it works fine on the live cd.  I have tried the ubunru alternate live cd and freezes halfway through installation of the files.  I then tried using a usb stick and the same thing happens.  I tried both ubuntu 11.10 and 12.04.  I don't understand.  I guess I could try windows again.  Is there anyway to know if it is my motherboard?

It could be the motherboard. See this [thread.]("http://ubuntuforums.org/showthread.php?t=1366552")

---

### Post by neutronforrest on 2012-05-13
I was able to install ubuntu 12.04 but it has some issues.  Actually, it just freezes upon a reboot.  I have found this to be a bug.  Have you encountered this issue?

Also, I have come across another issue.  When I first put this computer together I installed windows vista.  A friend of mine helped me and in order to install windows he made my motherboard look like a dell.  When I went to Ubuntu I flashed the motherboard and thought this would remove the dell motherboard image. 

However, with one of the updates I saw a conflict with a package and a reference to a dell.  This leads me to think ubuntu thinks my motherboard is still a dell.  Does anyone know how I would check and see if my motherboard still looks like a dell?  Also, does anyone know why the restart freezes?

Thanks...Chad

---

