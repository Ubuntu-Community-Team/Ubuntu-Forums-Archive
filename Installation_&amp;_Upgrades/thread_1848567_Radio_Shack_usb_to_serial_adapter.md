---
title: "Radio Shack usb to serial adapter"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by johnnyg5419 on 2011-09-22
Does anyone know how to install the drivers for a Radio Shack usb to serial adapter? I am a first time user of ubuntu.:(

---

### Post by lkraemer on 2011-09-23
This posting should get you going:
[http://ubuntuforums.org/showthread.php?t=1806972&highlight=dmesg](http://ubuntuforums.org/showthread.php?t=1806972&highlight=dmesg)
Posting #2


lk

---

### Post by johnnyg5419 on 2011-09-23
Again I don't know anything about this system. This is what it says to install adapter.
 
(Q:  How to install PL-2303 Linux driver and compile?  
  
A:  1. Under root folder, create a new folder and copy PL-2303 source code to new folder.
2. Open "Makefile" with GEDIT or KATE under new folder.
3. Modify line 5 "KINCLUDES=/usr/src/linux/include".
Example: "KINCLUDES=/usr/src/linux-2.4.7-10/include". 
You could find folder name on Linux.
4. Open terminal mode and login root user.
5. Go to the new folder and then type "make all" to compile the PL-2303 source code. This will create two files: "pl2303.o" and "usbserial.o".
6. Type "make inst" that will install the PL-2303 Linux driver into Linux.
7. Plug the PL-2303 cable into USB port and key-in "dmesg", it will show "Prolific USB Serial Adapter converter now attached to ttyUSB0 (orusb/tts/0 for devfs)". This means the cable is now working under Linux.
Note: You must login into root user in order to successfully compile and install.)
 
Where do you find or how do you open a root folder and create a folder in it?It also has these files on CD ( It's only support REDHAT 7.3_8.0_9.0). What is a redhat and which one would I use?

---

### Post by lkraemer on 2011-09-24
Yes, I understand that they want you to use their code, then compile, and
install the modules.  What they aren't telling you is you must install the
Header files for your Kernel, and build-essential.

But, before we jump through those hoops, most USB to Serial Dongles will
work out of the box, if you just plug them in a USB Port as their Step 7
explains.  So, start there as explained in the previous posting, and follow
it step by step, posting the output as you go.  It won't take long.


Later, if you must try to Compile their source, which I wouldn't do, have a look at:
[http://ubuntuforums.org/showthread.php?t=1814155&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1814155&highlight=build-essential)
Posting #7


lk

---

