---
title: "Errors During Setup In Live CD. Pls Help!!"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by androan on 2011-03-27
Hi! I am new here. I have been using Windows XP for a very Long Time. I recently tried to Install Ubuntu 10.10 and Faced a Problem that black screen with Cursor Blinking. That Problem was solved with selecting nomodeset in Other Options. And After I deleted the 'quiet' 'splash', An Error In Commands:
Mounting Root directories......
Mounting <Some Other System Directory>.....
Done.
Done.
Stdin: Error 0

Every Other Commands before that or After that were all Successfully Done. The Setup Progressed but after the last command
Sensor........[OK] 
The Setup did not Progress at all. Even after 10-20min.
The Same With Ubuntu 9.10 Original and Writing the CD Image many times and Changed DVD Writer Too. ](*,):cry:
Please Please Help ME!!!!
My Computer Configuration is:
Windows XP 32-bit
Intel Pentium 4 CPU 2.40GHz
1.25GB RAM
80GB Hard Disk
256MB Nvidia 5200FX Graphics Card
DVD RAM Drive.

---

### Post by PCNetSpec on 2011-03-27
Can you provide further info, such as make and model of motherboard... It may help search for known issues.

---

### Post by androan on 2011-03-27
My Motherboard is a Old Intel 845 Chipset not sure of the Full Model Number.
Thank you for the Quick Response.:)

---

### Post by PCNetSpec on 2011-03-27
You might want to try the **i915.modeset=1** kernel boot parameter (though I didn't think this was needed any more), or one of the other workarounds detailed here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
or
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)
and
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

If this is during installation, you could even try the **xforcevesa** parameter.

---

### Post by androan on 2011-03-27
That did not solve the Problem.(The Progress was stopped at First). The Error Occurs after Successful Mounting of System Root File System and Other Directory but The Error Pops up Stdin: Error 0. 
Please need Another Solution.
Thank You!

---

### Post by PCNetSpec on 2011-03-27
Stdin is an input error, so I'm *guessing* your CD/DVD player can't read the disk, have you tried a different drive.

I've also come across similar issues where the drives are connected strangely, eg. hard drive on IDE0 but set a salve

or

CD on IDE0, hard drive on IDE1, both set as master, but hard drive set as first boot device.

etc.

Also, someone else on the web said just disabling his floppy drive in BIOS fixed the issue.

---

### Post by androan on 2011-03-27
The DVD Drive is New and I just Bought it Yesterday since The Old Would not Write. I think DVD Drive is Perfectly Fine. I have a Floppy Drive is Old does not Function(Dont Have Floppy to check it). Will Check And Give Feedback Very Soon.
Thank you Very Much!

---

### Post by androan on 2011-03-27
Checked About the Connections, THere is no strange Setting up of Connections. I have Installed XP and 7 too Without Any Problems. But Why Such a Thing in Linux(Ubuntu)? Is there Anything Else I can do to Solve the Problem.
Please Help ME!!! :cry:

---

### Post by PCNetSpec on 2011-03-27
Have you tried the Alternate install CD ?

[http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/)

---

### Post by androan on 2011-03-27
No. I haven't tried it as it is for Very Low Systems. It says it is for lower RAM than 256MB and I have 1.25GB and No Network network Access. Will I not be able to Run full desktop environment reasonably? Is there Network Access In the Edition?
By The Way, Could it be a Problem with my Hard Disk? Because It is kind of Slow in C:\ Drive and a Few Problems I have Been Facing!

---

### Post by androan on 2011-03-27
Desperate Bump ](*,):-({|=Help![-o< :icon_frown:

---

### Post by androan on 2011-03-27
Please Help Me Guys! I have No Idea What to do Next!? Please Help Me!
Desperate Bump ](*,):-({|=Help![-o< :icon_frown:

---

### Post by PCNetSpec on 2011-03-27
There's a possibility it's your drive, but if it works in Widows.....

The alternate install CD is not for low end systems, but it CAN be installed on "lower" end systems, as it doesn't use a graphical installer (so the install routine requires less memory)... you end up with exactly the same Ubuntu, and the Alternate CD can deal with software RAID for example... worth a go.

---

### Post by androan on 2011-03-28
Installed successfully using alternate version. Now when I boot into Ubuntu without splash it freezes at
*Starting AppArmor profiles
Pls help ME!!
Nomodeset is already set and I tried setting Intel parameters but it don't solve the problem
Help!!!!
Recovery Also does not work!

---

### Post by androan on 2011-03-28
Pls help me!!!!!
Help!!!!!
:'(  :-[

---

