---
title: "Problems re-installing after upgrade crash"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by andrew_01 on 2011-08-07
I've had 10.10 on my laptop for a while now and was downloading the upgrade for 11.04 with the update manager. However, I encountered a problem which is partly my fault. I had my internet dongle plugged in whilst waiting for the upgrade to install (i thought maybe it might need to get some more info off the net). It then went to the page to shut down, which caught me by surprise because it usually lets you know when you have to switch to restart. The dongle was still plugged in, i quickly unplugged but the screen froze and i couldn't get it to re-boot so had to switch off and start again. Obviously ubuntu wouldn't boot and being somewhat of a novice i thought the best thing to do was to uninstall in windows vista and re-install. I keep encountering the same problem when i try to install ubuntu and i get the message :
 
permission denied
 
users\andrew\appdata\local\temp\wubi-10.10-rev197.log
 
I thought it might be to do with using the same username and passwords (i've had this problem before when re-installing) but it isn't. I also downloaded 11.04 and put it on a cd and usb stick but when i go to click on wubi it doesn't run. Do you think I've damaged the hard drive in some way (i read about this on the wubi wiki page) and will be unable to re-install ubuntu now? I hope not, i'd hate to go back to windows. I am also deeply annoyed at myself. If anyone could let me know that would be great. Cheers.

---

### Post by bcbc on 2011-08-07
It's unlikely you've done any damage to your hard drive. There could be a number of reasons for the installation failure - post the logfile %temp%\wubi-10.10-rev197.log and it should indicate the cause.

But by uninstalling you deleted your old install that you were trying to upgrade (and any data on it). 

If you are using ubuntu predominantly then you should probably do a direct install, rather than Wubi.

PS even on a real install it's advisable to backup prior to installing. And if Ubuntu freezes use Alt+SysRq R-E-I-S-U-B to restart rather than powering down manually.

---

### Post by andrew_01 on 2011-08-08
Ok thanks for that. Do i look for the temp.log file in Run on windows? Also, how do you directly install ubuntu, can you download it straight on? Cheers..

---

### Post by bcbc on 2011-08-08
click START, type in the following:
```
%temp%\wubi-10.10-rev197.log
```

To install normally, you need to download the ISO and burn to CD (or create a bootable USB) and then boot your computer and select to boot from the CD/USB.  Instructions here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Since you are partitioning you should back up important data first. Although the risk is generally low, there is always a small risk.

PS you can check out this guide as well [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by andrew_01 on 2011-08-08
Ok thanks for replying, still having some problems tho'. I can't get the cd for 11.04 to work, i go to click on the wubi logo and it does nothing. This is the log message i get for this :
 
08-08 20:42 INFO   root: === wubi 11.04 rev211 ===
08-08 20:42 DEBUG  root: Logfile is c:\users\andrew\appdata\local\temp\wubi-11.04-rev211.log
08-08 20:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Andrew\\Downloads\\wubi.exe"']
08-08 20:42 DEBUG  CommonBackend: data_dir=C:\Users\Andrew\AppData\Local\Temp\pyl34A6.tmp\data
08-08 20:42 DEBUG  WindowsBackend: 7z=C:\Users\Andrew\AppData\Local\Temp\pyl34A6.tmp\bin\7z.exe
08-08 20:42 DEBUG  WindowsBackend: startup_folder=None
08-08 20:42 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 55, in run
  File "\lib\wubi\backends\win32\backend.py", line 163, in remove_existing_binary
  File "\lib\ntpath.py", line 90, in join
TypeError: unsubscriptable object
 
Same as if i try the wubi windows installer. There's a rather long message i get from the log when i try to re-install 10.10 (i have it on a cd). I'll post that later. Cheers..

---

### Post by bcbc on 2011-08-08
It could be a bad burn on the 11.04 cd. It's recommended to burn at the slowest speed possible. Even then I guess there could be errors. You can boot your computer from the CD, press a key when you see the keyboard icon at the bottom centre (to get the extended menu) and then select "Check CD for defects" (not sure of the exact wording).

---

### Post by andrew_01 on 2011-08-08
Ok i've downloaded the iso again and will burn it using the recommended Infra Recorder (which i used the last time) program that's on the ubuntu download page. Thanks for you help.

---

### Post by andrew_01 on 2011-08-14
Ok here we go..

I have been unable to install 11.04 (inside windows) from the cd, i click on the wubi logo and it does nothing. I decided to remove windows using gparted and have tried to install ubuntu as the main operating system, using the cd from boot. However, the first time i tried it seemed to be installing fine, then got up to the point where it says checking hardware, then the laptop just switches itself off (it made a clicking sound). I tried again, same result. I can get it to work from the demo mode but the same problem occurs when i try to install. I've put windows vista back on now and am using that. Do you think i have damaged the hard drive, or some other component? When i run chkdsk on windows (and it did this before i took it off and still does now it's been re-installed) windows fails to boot after the restart (chkdsk doesn't find any problems with the hard drive btw). When i hard reboot it comes up with a screen saying there maybe errors after recent changes to hardware/software and gives me the option to start normally or check for errors/fix/repair but this option doesn't work. So have i damaged the hard drive in some way and do you know if there are any programs you can download that may be able to fix the problem? If not, i'll just have to take it somewhere to see if i can get it repaired :( . Cheers..

One other thing, i couldn't get 10.10 to install as the sole operating system either, i got a message saying it was unable to mount on the filesystem.

---

### Post by bcbc on 2011-08-14
It does sound like some hardware issue - if after running chkdsk, windows doesn't start. And shutting down while checking hardware during the installation of 11.04.

When you ran chkdsk which option did you use? "Scan for and attempt recovery of bad sectors?" (chkdsk /r from repair prompt).
Another thing you can do is boot the live environment and run the Disk Utility, click on the hard disk and see if it reports any errors - check the SMART status if your hard disk supports this.

---

### Post by andrew_01 on 2011-08-15
yes i ran chkdsk to repair any bad sectors. i'll try the boot option you suggested. thanks.

---

