---
title: "Can't boot from USB on ASUS Eee PC 1215T"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by st1led on 2013-10-20
Hi everybody! I have an ASUS Eee PC 1215T that I can't boot from USB (a Sandisk Cruzer Micro 8GB). I googled a bit, but I really think I have done everything right. At the moment, the Eee PC does not have any OS installed, so the only thing I can do is create a bootable USB device (from another computer), and boot from the USB stick to install Ubuntu.

Here is what I did:

[LIST=1]
[*]Downloaded Ubuntu 13.10 x64 
[*]Used [Rufus]("http://rufus.akeo.ie") to create a bootable USB by specifying in the options the ubuntu ISO. 
[*]Set up in the BIOS the following things:
[LIST=1]
[*]Boot Device Priority: [Removable dev.] as 1st Boot Device 
[*]Boot Settings Configuration: Quiet Boot Disabled 
[*]OnBoard LAN Boot ROM: Disabled 
[/LIST]
  
[*]To be even more sure that I'm really booting from the USB, I hit the ESC key when I read the POST message, and when the "Please select boot device:" popup appears, I select "USB: SanDisk Cruzer" 
[/LIST]

At this point, there is just the black screen with a blinking cursor on the second line from the top. No further input is possible.

Ideas?

---

### Post by sudodus on 2013-10-21
Welcome to the Ubuntu Forums :-)

1. Have you checked with ***md5sum***, that the download was successful? See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Try ***some other method*** to create the USB boot drive. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Do you intend to make a dual boot system or an Ubuntu only system?

---

### Post by mörgæs on 2013-10-21
Some of the Sandisks contain an annoying software package called [U3]("http://en.wikipedia.org/wiki/U3"), which should be removed before using the stick. I have one of them which works fine after being liberated from U3.

---

### Post by LukeMorrison on 2013-10-21
Is the Asus a 64-bit machine? My guess is that you are trying to install a 64-bit operating system on a 32-bit machine, which as far as I know is not possible. Try the 32-bit .iso and see if you can boot from there.

Luke Morrison

---

### Post by mörgæs on 2013-10-21
If that were the problem the system would have given an explicit error message about 32/64 bit. It would not fail silently.

Boot options like NOMODESET might be necessary, though.

---

### Post by LukeMorrison on 2013-10-21
I don't mean to be contrary, but I have a 32-bit machine (no lm flag in /proc/cpuinfo) which if I run a 32-bit .iso loads up fine, whereas with a 64-bit .iso, it gives the exact same symptoms as the OP.  It does not even give an option for nomodeset.  I have been able to repeat this on two separate machines and I get the same behaviour with multiple .iso files.  Maybe it is a bug, but it is repeatable.

---

### Post by mörgæs on 2013-10-22
That sounds strange. For testing I just tried to boot a 32 bit computer with a 64 bit ISO, and it gave me a 

**This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU.**

Well, let's hear from original poster what happens with a 32 bit ISO. I don't expect it will make any difference (also because I believe the processor is a 64 bit AMD Neo which should be able to run everything).

It's an interesting problem, if it's repeatable. Please open a new thread about the missing error message for others to chip in.

---

### Post by st1led on 2013-10-25
Hi everybody, thank you for your support. Time for a bit of follow-up:

[LIST=1]
[*]The iso download was succesful, as I checked the MD5 hash
[*]One of the first thing I did when I got the stick, was removing the U3 bundle software. I hate it!
[*]As I checked [here]("http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_1215T/#specifications"), the 1215T has a AMD® Athlon™ II Neo K125 processor, that [supports]("http://www.notebookcheck.net/AMD-Athlon-II-Neo-K125-Notebook-Processor.33851.0.html") 64bit.
[*]I also tried creating a bootable stick with the 32bit version, but with no luck. When I try to install Ubuntu, I have the same black screen with the cursor and no error message.
[/LIST]

The good news is that in the end I made it work. Apparently the problem was in a combination of some bad blocks in the stick, and the procedure to burn the ISO. After many tries, some of which a bit mindless, the installation started. To be honest I can't exactly say what I did, but to everybody that might have a similar problem I would suggest to change USB stick or to check it for memory errors.

See you around!

---

### Post by mörgæs on 2013-10-25
Good, please mark the thread 'solved'.

---

