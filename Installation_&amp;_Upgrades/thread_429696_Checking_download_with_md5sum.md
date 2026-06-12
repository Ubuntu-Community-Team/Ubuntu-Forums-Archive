---
title: "Checking download with md5sum"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by tc101 on 2007-05-01
I just downloaded the fiesty live CD and then did the checksum to make sure it got downloaded correctly.  I followed the directions here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I got this result:

tomcarr@tomcarr-desktop:~/Desktop$  md5sum ubuntu-7.04-desktop-i386.iso
e296e3468358789904097fc8df29609a  ubuntu-7.04-desktop-i386.iso

but I have no idea what this means or if I have a problem, since the directions are for an earlier version of ubuntu

---

### Post by dannyboy79 on 2007-05-01
the md5sums were probably located on the same webpage that you downloaded ubuntu from. according to here ([http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/) ), the md5sum you have put above is correct as I verified it with the link I provided. next time all you do is go to a similar page that I linked you to and open the md5sums text file and you'll see all the correct md5sums for each of the Ubuntu version. You can go ahead and burn the cd SLOWLY and install Ubuntu. Welcome to Ubuntu.

---

### Post by psusi on 2007-05-01
In the directory you downloaded the iso from there should be an md5sums file that lists the sums for each of the files.  If the one it lists for that file matches the result you got there, then the file is as it should be.

---

### Post by tc101 on 2007-05-01
> You can go ahead and burn the cd SLOWLY and install Ubuntu

The utility I am using will not let me select a slow speed.  The drop down box was set to "Maximum speed" and did not allow me to change it.  Should I run md5sum on the CD after it is finished, or should I use another utility?  And if so, what utility should I use?

---

### Post by tc101 on 2007-05-01
Well I can't write it because my CD is 650MB and the file is 697.MB so I have to go buy some larger CD.

---

### Post by dannyboy79 on 2007-05-01
turn overburn or whatever it's called. nero can do this. what software are you trying to burn it with? actually you might be right, i didn't even know they still made 650mb cd's. i only buy the 80min/700mb cd's but still try to give the overburn option as it does allow you to burn all the way up to the edge of the cd. o ryou could install using the iso. follow this guide ([http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)) BUT ONLY if you downloaded the alternate install cd.

---

### Post by tc101 on 2007-05-01
I am using something that comes with Nautilus.  I see it when I click the Places menu.  It is just called CD/DVD creator on the drop down menu.  I don't see an overburn option and I will be passing a store where I can get some new CDs later so I will just do that.  These 650mb CDs are pretty old.

---

### Post by dannyboy79 on 2007-05-02
you could just use the command line using cdrecord, this is what you could try

cdrecord dev=ATAPI -scanbus 

will find where your burner is at 

cdrecord -v speed=4 -overburn driveropts=burnfree dev=ATAPI:0,0 -pad -data [name of iso image]

or if it's a sata burner I think you might need to follow this:

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=95895&highlight=slackware+cdrecord+dev3DATAPI+scanbus](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=95895&highlight=slackware+cdrecord+dev3DATAPI+scanbus)

OR


you could just try out gnomebaker or similar burning program.

Nautilus burner is very basic, good for just data you know will fit on the dvd or cd, it might even be able to burn audio files but I haven't done that yet but I have Nautilus burner to burn backup copies of my xbox iso files.

---

### Post by psusi on 2007-05-02
For ISOs, right click -> Write to Disc works great in nautilus.

---

