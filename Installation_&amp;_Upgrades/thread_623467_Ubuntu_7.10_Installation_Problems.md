---
title: "Ubuntu 7.10 Installation Problems"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by sandy_ptc on 2007-11-25
Hi have been trying to install Ubuntu 7.10 on by home PC for some time without success.

I think the problem is with my graphics card not getting detected. I have an Intel 82845G Graphics Controller (64MB) and an LG E700S monitor.


1) I have succeeded in running KNOPPIX 3.9 without any problems so all the drivers required for my system are definately out there. 

2) I tried the safe graphics mode but neither any of the Intel Drivers nor the Generic Drivers would start up the installation. Is there some way I can start the text based installer from this CD.

3) I downloaded the Intel graphics drivers for 82845G, burnt it on a CD and tried the Install from an alternate Driver CD option but it still does not work. Do I have to untar and unzip the drivers before burning it on a CD ?

Any help will be greately appreciated.

Thanks
Sandeep

---

### Post by LaRoza on 2007-11-25
How much RAM do you have?

How old is this computer?

---

### Post by nzadLithium on 2007-11-25
your sure you have the linux drivers and not the windows ones?
also how are the drivers packaged? what extension do they have?

can you get the install to go using the vesa driver?

When you put the ubuntu disk in does it give you an option to boot a text based installer??
If not then you probably need to download the alternate cd to do text based but the vesa driver should work. It's work on every computer of run ubuntu on.

---

### Post by sandy_ptc on 2007-11-26
Below are the everest output for my PC.  When I bought the PC the vendor would not give me a warranty for the memory, and today I am noticing that the Memory shows 253 although it ought to be 256 MB. You think that may be the problem, because if it is I can upgrade my memory.

I think I have tried the vesa driver as it the default that loads up in the "Safe Graphics Mode".
I got the linux driver from intel downloads. Yes they were packaged as tar.gz.



    Motherboard:
      CPU Type                                          Intel Pentium 4, 2800 MHz (21 x 133)
      Motherboard Name                                  Intel Sea Breeze D845GVSR  (3 PCI, 2 DIMM, Audio, Video)
      Motherboard Chipset                              Intel Brookdale-G i845GV
      System Memory                                      253 MB  (PC2700 DDR SDRAM)
      BIOS Type                                              AMI (09/22/04)
      Communication Port                                Communications Port (COM1)
      Communication Port                                ECP Printer Port (LPT1)

    Display:
      Video Adapter                                     Intel(R) 82845G Graphics Controller  (64 MB)
      3D Accelerator                                    Intel Extreme Graphics
      Monitor                                                LG E700S  [17" CRT]  (1420234)

    Multimedia:
      Audio Adapter                                     Intel 82801DB ICH4 - AC'97 Audio Controller [A-1]

    Storage:
      IDE Controller                                    Intel(R) 82801DB Ultra ATA Controller
      Floppy Drive                                      Floppy disk drive
      Disk Drive                                           ST340015ACE  (40 GB, 5400 RPM, Ultra-ATA/100)
      Optical Drive                                      HL-DT-ST CD-RW GCE-8525B  (52x/32x/52x CD-RW)
      SMART Hard Disks Status                           OK

    Input:
      Keyboard                                          Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
      Mouse                                               Microsoft PS/2 Mouse

    Network:
      Network Adapter                                   D-Link DFE-520TX PCI Fast Ethernet Adapter  
      Modem                                                   SoftV92 Data Fax Modem

    Peripherals:
      USB1 Controller                                   Intel 82801DB ICH4 - USB Controller [A-1]
      USB1 Controller                                   Intel 82801DB ICH4 - USB Controller [A-1]
      USB1 Controller                                   Intel 82801DB ICH4 - USB Controller [A-1]
      USB2 Controller                                   Intel 82801DB ICH4 - Enhanced USB2 Controller [A-1]

---

### Post by gdselzer on 2007-11-26
You need at least 320MB of RAM to run the Live Install.  You will need to use the alternate install CD to install on this machine.

---

### Post by captpay on 2007-11-26
Hi

I am a new user of Ubuntu. I have used a clean and formatted drive. I have downloaded the CD iso file. It has booted up and I have been able to go through all the steps for instalation.

However, when it does the actual instalation it gets to about 24% and then the pop-up just disappears. The live CD page is still working. Unfortunately, when you reboot there is no operating system. It clearly appears that the OS has not finished installing. 

I have tried a number of times but with no success.

Is there something wrong I have done. I also did a CD verification check and this said all was good.

Look forward to hear someone elses opinion.

Thanks

CaptPay

---

### Post by nzadLithium on 2007-11-26
I had a similar problem when trying to use the live gparted cd on a pentium 3 :D it started running then I told it to repartition hard disk it started going then it hung i ran it about 4 times before i gave up and jsut used the one built into the ubuntu text installer. I cant remember why i didnt just use that in the first place.

Anyway i think i should say before i start that its not nice to hijack someone elses thread captpay.

you say it gets to 24% then it stops. What are the specs of the machine your trying to install on coz i had long freezes like that using the text installer on that same pentium 3 i said earlier. Do you mean stops or disappears as in crashes.

Anyone know what the command is to launch the hd install from a terminal so we can find out whats causing the stopping/crash?

If its booted its unlikely u did anything wrong unless you hit the cancel button??

What do you mean the live cd page? do you mean the you can see the desktop and can click icons and they do something??

---

### Post by captpay on 2007-11-26
Hi

Firstly, sorry for 'hijacking' someone elses thread. I saw the title of the thread and obviously wrongly assumed that anyone having issues that match the title of the thread could comment/ask questions. Does this mean I should commence a new thread under same title?

Anyway, my issue is that the pop-up that gives you the progress of the instalation actually just disappears and the harddrive activity stops. I waited on one effort for 20 minutes and nothing ever reappeared. The progress gets to 24% before the pop-up disappears. The installer does put some files onto the harddrive (about 225Mb). On the instalation help document it says once the instalation id complete a final pop-up should ask me to restart the computer. That pop-up never comes up.

I have used the installer that appears to run from the CD and look just like the OS while it goes through the instalation. You seem to be able to use all the features of the OS that is running (but it is from the CD).

My system;

CPU - AMD Athlon XP 2000+
RAM - 768mB
Hardrive - 8Gb completely free
Video Card - NVidia 64mB

I am only using the smaller harddrive to just try this whole new OS out, never having used Linux before. If this all works out I will use another larger harddrive.

The unfortunate result is that I think the installer has 'crashed' as you describe, but it does not give any reason for it or even acknowledge that it has crashed.

Thanks for your comments.

Look forward to your response.

Cheers

CaptPay

---

### Post by sandy_ptc on 2007-11-26
I dig out this thread from this forum :

[http://ubuntuforums.org/showthread.php?t=580020](http://ubuntuforums.org/showthread.php?t=580020)

and looks like I have a lot of company.

I had ordered a live CD for kubuntu 7.04 from this vendor

[www.linuxbazar.com](www.linuxbazar.com) last Saturday and they told me they have already shipped it, so am going to just wait for it to arrive and then am going to take another shot at installation.

---

### Post by nzadLithium on 2007-11-26
sandy with your memory thing. Its kinda odd they wont give you warranty for memory but its pretty normal to have it say you have a bit less than you do. It happens on windows as well. I can't remember exactly what causes this but its something to do with something else in your computer allocating itself some memory which the operating system cannot touch. (It could be memory reserved by the OS? i cant remember. Look it up if your interested if you search through google you should find it no prob.

---

### Post by nzadLithium on 2007-11-26
captpay we need to run the hard disk install throug ha terminal to find out whats causing the crash.
I think you can run by going to applications >> accessories >> terminal then typing cd Desktop then
type ./install

go through the install and once it crashes copy and paste the whole out put from the terminal here. 

Yeah you should have started a new thread but dont worry about it now. (and it is a bit of a misleading thread name, would probably have been better if sandy had entitled it something to do with the problem :D)

---

### Post by sandy_ptc on 2007-12-02
Yes it was a problem with my System RAM. I upgraded the RAM size to 1.25 GB and the Live CD worked perfectly. I was able to install Gutsy in about 30 minutes. 

:)

 I later checked and the Live CD was using about 310 MB of RAM. I guess the minimum system requirement in the install doc for installing from the Live CD which is 256 MB is a bit confusing for some of us novice users and should be changed.

Thanks to the forum for all the help.

---

### Post by younus_malik on 2008-01-24
dont forget that your integrated video card also consume RAM (64MB ?)

---

