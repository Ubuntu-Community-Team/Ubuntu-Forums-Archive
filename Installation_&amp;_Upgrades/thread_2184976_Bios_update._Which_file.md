---
title: "Bios update. Which file ?"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by Herby Pepper on 2013-10-31
Hi All
 I am trying to update bios in notebook hp 2133.  
 After study different forums and solution I get here:
 
1. I have: BIOS version: F.02 , newest is F.06;
 2. I download F.06 file which is sp41847.exe;
 3. I install FreeDOS 1.0 on USB(256mb) with UNetbootin;
 4. I copy sp41847.exe into USB.  
 5. I boot FreeDOS from USB on the notebook  [INDENT]the options where:  
  1. Install to harddisk using FreeDOS setup
  2. FreeDOS Safe Mode (don't load any drivers)
 3. FreeDOS Live CD with HIMEM + EMM386
 4. FreeDOS Live CD with HIMEM only
 5. FreeDOS Live CD only
[/INDENT]
   I tried booting from option 2(safe mode) and 5(Live CD only). In bouth cases I get same resolts:
 [INDENT]A:\> b:
 B:\>
 B:\>dir
 (here information about my USB and content)
 B:\>sp41847.exe
 This program cannot be run in DOS mode
[/INDENT]
  
 File sp41847.exe after unpacking :[INDENT]- folder FreeDOS (KERNEL.SYS)
 - folder ISO (ROM.iso)
 - folder Rompaq (68VGU.BIN, AFUDOS.exe, config.sys, gpl2.txt, KERNEL.SYS)
 - cd.html
 - FirmwareUpdate.exe
 - fluppy.exe
 - HPUSBFW.exe
 - KERNELS.ZIP
 - WSSP41847.rtf  
[/INDENT]
 
 My question is:  
 Should I try to install just FirmwareUpdate.exe or ROM.iso or any othere file from sp41847.exe ?  
 Don't want to do it without asking you first because I am doing it first time and I know it could make my notebook unusable.
 Or You have any other ideas how to flashing bios in my case, please answer.

 Thank you.

---

### Post by Mark Phelps on 2013-10-31
My suggestion is that, once you get FreeDOS working and the BIOS update program running, confirm BOTH of the following are true before proceeding with a BIOS update:
1) You have a way to save off the current working BIOS to a media that can be used to restore the BIOS
2) You have a way to restore the BIOS from the version you saved.

If either of these is not true, any attempt to update the BIOS risks "bricking" the machine!

---

### Post by fantab on 2013-10-31
BIOS update should be done ONLY if there are any issues with the hardware/software compatibility or if you want to add any newer hardware to system which needs BIOS update. If everthing is working good then don't update your BIOS.

---

