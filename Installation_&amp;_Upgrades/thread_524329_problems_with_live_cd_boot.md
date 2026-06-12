---
title: "problems with live cd boot"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by rainforrestguy on 2007-08-13
:confused:hello everyone, i just recieved the ubuntu bootable installation cd and hit road blocks while tryiing to boot it for a test drive. after installing the cd and rebooting the computer i have to hit the F12 key at the start up. i then scroll to the start/install option. it starts loading information and goes to the Ubuntu sreen with loading bar...a screen then comes up saying:" failed to start the X server (your graphical interface). It is likely that it is not set up correctly.Would you like to view the X server output to diagnose the problem?" <yes>  <no>  After selecting YES thefollowing appears: "X window sytem version 7.2.0
                release date: 22 january 2007
                X protocol version 11, revision 0, release 7.2
                build operating system: Linux Ubuntu
               Current OS system: linux ubuntu 2.6.20-15-generic #2 SMP sun
                april 15 07 
               build date: 04 april 2007
               module loader preset
              markers: (--) probed, (**) from config file, (==)informational.
              (ww) warning, (EE) error, (NI) not implemented, (??) unknown.
              (==) log file : "/VAR/LOG/XORG.0.LOG" time--------
              (==) using config file: "/ETC/X11?XORG.config"
               (ee) vesa (0): NO MATCHING MODES
              (ee) SCREEN (s) FOUND, BUT NONE HAVE A USABLE CONFIGURATION.
                 FATAL SEVER ERROR: NO SCREEN FOUND
                               <OK> (I SELECTED)
next screen reads : the Xserver is now disable4d. restart GDM when it is configured correctly. 
                               <ok> (selected)
 please wait
to run command asadministrator (user "root"), use "Sudo <command>".
See "man sudo_root" for details.
ubuntu@ubuntu:~$__ (flashing)
i entered "root" and got a message reading: -bash:root command not found.

don't know what to do cann anyone please help me!

---

### Post by merlinus on 2007-08-13
Try this:

At the command prompt, type sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

Then type:

startx

-merlin

---

### Post by rainforrestguy on 2007-08-13
I tried everything that was suggested and still end with the same error as above! I've read the problems others have had with the xserver and tried the solutions that were posted for them......I can't get my computer to boot from the live cd!!! I went to the link to download the alternate cd....BUT... I live in the rainforrest of Costa Rica and my ISP is stone age (the download will take 24hrs) So, is there anything else that I could try? I have a Dell Inspiron 9400, intel(R) core(TM) 2CPU T5200@1.60GHZ, 1.00 GB RAM, ATI Mobility Radeon x1400, 32 bit OS, Windows Vista Buisness (which I'm not fond of, but it does WORK!)
Somewhere out there there is a simple answer to satisfy my simple mind.
PLEASE HELP!

---

