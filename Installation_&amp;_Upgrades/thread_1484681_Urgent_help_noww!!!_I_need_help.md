---
title: "Urgent help noww!!! I need help"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by helpmeimessedup on 2010-05-16
HELP! i got a dell netbook, and i did the usb method of install linux. I got the lnux up. and i wen t to the disk utility, i clicked some format thing in the gui partion, AND NOW MY WINDOWS DOESNT EXIST, all my FILES ARE GONE, ALL MY EXAM REVISION!!! all MY YEARS CLASSWORK!  i hVE, school tomorrow, i use a laptop in sckool, and my exams start in 3 days, so i cant use my computer.

AND

IT WONT INSTALL, the netbok  installer thing freezes on the keyboard stage!!!!


HELPP!!!

---

### Post by helpmeimessedup on 2010-05-16
i dont care if i loose the windows, i just NEED MY FILES!!! and a working os

---

### Post by iponeverything on 2010-05-16
[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

---

### Post by helpmeimessedup on 2010-05-16
thank youu, im downloading it now...

---

### Post by helpmeimessedup on 2010-05-16
on the wiki page, what version do i use???

---

### Post by helpmeimessedup on 2010-05-16
waht test disk version is needed for ubuntu netbook 10.04

---

### Post by bcbc on 2010-05-16
You should be able to install it with:
```
sudo apt-get install testdisk
```

---

### Post by helpmeimessedup on 2010-05-16
> **bcbc said:**
> You should be able to install it with:
```
sudo apt-get install testdisk
```

im a mega noob, how do i do that?

---

### Post by helpmeimessedup on 2010-05-16
what operating system version of test disc do i need
i got the ubuntu netbook 10.04
currently on a usb only
how would i use the test disc wen i get it

I AM A NOOB \, so please help , cause i stuffed up my netbook

---

### Post by bcbc on 2010-05-16
Boot the live cd (boot ubuntu install disk select 'try without any changes'), click on the top left, accessories, terminal, then type```
sudo apt-get install testdisk
```

You might as well run the  [bootinfoscript]("bootinfoscript.sourceforge.net") and post the results back as well.

---

### Post by helpmeimessedup on 2010-05-16
how do i enable the component universe

---

### Post by bcbc on 2010-05-16
System, Administration, Software Sources...second checkbox

---

### Post by helpmeimessedup on 2010-05-16
It doesnt install!!

---

### Post by bcbc on 2010-05-16
What sort of error are you getting? More information is better... cut and paste from terminal if you have to.

---

### Post by helpmeimessedup on 2010-05-16
SORRY. it says
reading package lists...done
building dependency tree
reading state information...done
E:couldn't find package testdisk

---

### Post by bcbc on 2010-05-16
Double check you enabled the universe repository. It should have prompted you to update the available software afterwards. If not, or just in case, try ```
sudo apt-get update
``` and after that ```
sudo apt-get install testdisk
```

---

### Post by nmyrick on 2010-05-16
Try going to your System Menu > Administration > Synaptic Package Manager, 
then enter Testdisk in the search menu.  If you find it, then right click and click 'Mark for installation', then click 'Apply' in the toolbar.

---

### Post by helpmeimessedup on 2010-05-16
oh same errors, that first code did something,

ill connect to the internt! now

---

### Post by nmyrick on 2010-05-16
Also, if you are running the system off of the Live CD, then it won't install, since you can't write to the CD.  You need to be running Ubuntu off of the USB.

---

### Post by bcbc on 2010-05-16
You can install it off the live cd, it just won't be around the next time you boot.

---

### Post by nmyrick on 2010-05-16
How's it coming along?

---

### Post by helpmeimessedup on 2010-05-16
im running it off the usb stcik, the one were u put the iso on for boot, the install doesnt work yet, any help there, the install freezes on key board set up!

---

### Post by bcbc on 2010-05-16
You probably want to use photorec to recover your data. 

```
NAME
       photorec - Recover lost files from harddisk, digital camera and cdrom

SYNOPSIS
       photorec [/log] [/debug] [/d recup_dir] [device|image.dd|image.e01]

       photorec /version

DESCRIPTION
          PhotoRec  is  file  data  recovery software designed to recover lost
       files including video, documents and archives from Hard Disks and CDRom
       and lost pictures (Photo Recovery) from digital camera memory. [COLOR="Red"]PhotoRec
       ignores the filesystem and goes after the  underlying  data,  so  it'll
       work  even if your media's filesystem is severely damaged or formatted.[/COLOR]
       PhotoRec is safe to use, it will never attempt to write to the drive or
       memory support you are about to recover lost data from.

```
PS... I haven't used it myself. Also, I believe it's part of testdisk, so you still have to install that.

Good luck with this... I am signing off shortly. Here's some parting advice:  Don't panic. Take your time before you do anything or you could make it worse. Post as much information to make it easier for people to help you. Research the commands before you run them blindly.

---

### Post by helpmeimessedup on 2010-05-16
wait but how do i even install the ubuntu! im still running on the usb stcik!! how do install testdisk please help, i dont think i have root privaleges! i realy am clueless

---

### Post by helpmeimessedup on 2010-05-16
i just did the update thing! now installing test disk

how do i use it
and how do instal ubuntu

---

### Post by bcbc on 2010-05-16
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by garvinrick4 on 2010-05-16
> **helpmeimessedup said:**
> what operating system version of test disc do i need
i got the ubuntu netbook 10.04
currently on a usb only
how would i use the test disc wen i get it

I AM A NOOB \, so please help , cause i stuffed up my netbook

Sorry I just noticed you have a lot of help going on in your thread that I just noticed.
You are in capable hands. Have a nice day.

---

### Post by lisati on 2010-05-16
Threads merged.

Please be patient, we are all volunteers here, and the people who have responded so far are doing their best.

---

### Post by nmyrick on 2010-05-16
Once Testdisk is installed, open the terminal and enter 'sudo testdisk'
Then enter your password, then select to keep a log, then select the drive you want to scan for files, then select proceed.

---

### Post by nmyrick on 2010-05-16
It should come up with a list of files after you do that.

If testdisk doesn't find the files, then you may have to purchase some data recovery software.  One that is really good is Power Data Recovery, although it costs $90.  I had to use it on my 300gb USB hard drive when I had accidentally reformatted it.  In that case, testdisk did not find the files, but Power Data Recovery did.

Here is the website [http://www.powerdatarecovery.com/](http://www.powerdatarecovery.com/)

Whatever you do, **DO NOT** install Ubuntu until you have recovered your files, otherwise you will lose them for good.

---

### Post by nmyrick on 2010-05-16
I'm going to have to sign off now.  I hope someone else can pick this up and help.

---

