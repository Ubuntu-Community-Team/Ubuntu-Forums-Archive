---
title: "BIOS Flash Troubles With FreeDOS"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by drauchomyn on 2011-08-10
I'm having problems flashing my BIOS from CD using FreeDOS.  I have meticulously followed the instructions here: [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

I have an Intel Server Board SE7505VB2 ([http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Server+Products&ProductLine=Intel%C2%AE+Server+Boards&ProductProduct=Intel%C2%AE+Server+Board+SE7505VB2]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Server+Products&ProductLine=Intel%C2%AE+Server+Boards&ProductProduct=Intel%C2%AE+Server+Board+SE7505VB2")).

The instructions from the vendor are as follows to upgrade to BIOS release 1.10:

1. Extract phlash16.exe, AUTOEXEC.BAT, OEMPHL.EXE, OPTIONS.BAT, 1.bat, 2.bat and BIOS.wph to a 1.44 floppy    diskette.
2. Boot the system to pure DOS mode.
3. Run A:> 1.bat for auto mode, 2.bat for user mode.
4. When BIOS flash is over it will show message and beep, then reboot.
**Note:** The boot to DOS must be non-HIMEM management environment. 



When I copy the seven above mentioned files to /tmp/floppy, then burn a bootable CD and reboot, the following lines appear in FreeDOS:


InitDisk can't get drive parameters for drive 03
Bad or Missing Command Interpreter \COMMAND.com /E:256 /P
Enter the full shell command line:

When I try to type in A:> 1.bat, it returns:
Bad or Missing Command Interpreter: A:> 1.bat

Does anyone know what this means or how to solve the problem?

---

### Post by steve11911 on 2011-08-10
In the notes near the bottom of the page[shift key]:
 
 [http://downloadcenter.intel.com/Detail_Desc.aspx?lang=eng&changeLang=true&DwnldID=5871](http://downloadcenter.intel.com/Detail_Desc.aspx?lang=eng&changeLang=true&DwnldID=5871)

---

