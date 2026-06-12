---
title: "impossible to boot from cd with an old PC"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by endrylthalan on 2005-02-15
Hello,

My question is : is ti possible to launch ubuntu CD install from a floppy disk as I can't boot on the CD ?
 ](*,) 

I set in the BIOS a correct boot sequence with CDROM first but it does nothing.
The CD is OK (perfectly boot with a newer machine) and checked in expert mode.

 :?  Can you help me please ?

---

### Post by orion_114 on 2005-02-15
The only problem I can think of is maybe your CDROM Drive isn't working correctly?
Is the CD-ROM working properly ? Can you access information on a CD in your current OS on the machine ?
Did you try the CDROM Drive in the new machine or the Ubuntu disc ?

---

### Post by endrylthalan on 2005-02-15
The CDROM drive is working nicely with the current OS  :-|

---

### Post by orion_114 on 2005-02-15
What system are you trying to install onto ?
Maybe you don't meet the minimum system requirements ?
I cant seem to get Ubuntu on two Pentium MMX (200Mhz, 64 MB RAM) systems.

---

### Post by endrylthalan on 2005-02-15
The current system is a P III 333 with 64 Mo
I've heard about launching the install from debian boot floppies, but there should be some modifications to perform on the disk ?

---

### Post by endrylthalan on 2005-02-15
I, now, have a shell thanks to the debian disks, the CDROM is mounted but I don't know what to do now  :-|

---

### Post by az on 2005-02-15
"I set in the BIOS a correct boot sequence with CDROM first but it does nothing."

It ignores it?  Can your cdrom read a burned cd?

---

### Post by endrylthalan on 2005-02-15
It can read burned CD as I said I can read the disk with the current OS.
But the warty install cd is ignored at the boot sequence.

My problem, now, is to launch the installation sequence from debian floppies.
They helped me with with mounting warty cdrom but now I don't know what to do.

---

### Post by orion_114 on 2005-02-16
OK I'm not an expert and I have never tried anything like this before but ....
Can you now read the information from your disc through command line ?
If you can then I think all you would need to do is run the install application
I think you just type linux in the command line ? Anyone else got any suggestions ?

---

### Post by endrylthalan on 2005-02-16
I tried a Knoppix live CD to check but it's not working either (this CD perfectly works on "standard" machines)

So I'm booting from Debian Sarge boot disks (boot, root and then cd-drivers disks)
It's detecting hardware, then check the Ubuntu CD and find no kernel.
I continue the install without loading kernel module.
What is strange is that it's taking components from the CD.
I reach the main menu ask to mount the cd then execute a shell.
I go to /cdrom/ then type linux as you said but it doesn't work...
I don't know how to launch the install program now. Anyone knows ?

Should I try with an unstable Debian set of boot disks ?

---

### Post by endrylthalan on 2005-02-16
I'm just trying Smart Boot Manager now and it seems to work
I eventually found this :
[http://www.ubuntulinux.org/support/documentation/howto/SmartBootManagerHowto/](http://www.ubuntulinux.org/support/documentation/howto/SmartBootManagerHowto/)
 
Have a nice day and thank you for your help

---

### Post by javi7v on 2005-04-20
try this [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

rawwrite the image in a floppy, set floppy boot in the bios and finally select the cd-rom from the booting program

it worked for me

---

### Post by ed_agamemnon on 2005-04-22
you could try installing like this [http://www.ubuntuforums.org/showthread.php?t=28948&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=28948&highlight=floppy) 

... i think that might solve a few problems :)

---

