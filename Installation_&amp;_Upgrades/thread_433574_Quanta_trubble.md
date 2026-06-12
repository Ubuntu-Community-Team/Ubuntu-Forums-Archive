---
title: "Quanta trubble"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Buster222 on 2007-05-05
I installed Quanta 3.5.6 on a fresh KUbuntu 7.04 and it worked fine. Then I installed quite a few other applications: Thunderbird, Firefox, etc. and after that Quanta chraches during startup. Starting Quanta from the comman line (as a normal user) results in: 
 
 X Error: BadDevice, invalid or uninitialized input device 167 
 Major opcode: 144 
 Minor opcode: 3 
 Resource id: 0x0 
 Failed to open device 
 X Error: BadDevice, invalid or uninitialized input device 167 
 Major opcode: 144 
 Minor opcode: 3 
 Resource id: 0x0 
 Failed to open device 
 QObject::connect: Cannot connect (null)::initiateDrag(QWidget *) to QuantaApp::slotTabDragged(QWidget*) 
 KCrash: Application 'quanta' crashing... 
 
 The (shortened) error log from KCrash looks like this: 
 
 (no debugging symbols found) 
 Using host libthread_db library "/lib/libthread_db.so.1". 
 (no debugging symbols found) 
 (no debugging symbols found) 
 (no debugging symbols found) 
 etc 
 etc 
 (no debugging symbols found) 
 (no debugging symbols found) 
 [Thread debugging using libthread_db enabled] 
 [New Thread 47276951501616 (LWP 5986)] 
 (no debugging symbols found) 
 (no debugging symbols found) 
 etc 
 etc 
 (no debugging symbols found) 
 (no debugging symbols found) 
 (no debugging symbols found) 
 [KCrash handler] 
 #5 0x00002aff7f7ad62c in QObject::installEventFilter () 
 from /usr/lib/libqt-mt.so.3 
 #6 0x00000000004c13a1 in ?? () 
 #7 0x00000000004c1ba8 in ?? () 
 #8 0x00000000004c2218 in ?? () 
 #9 0x00002aff845f78e4 in __libc_start_main () from /lib/libc.so.6 
 #10 0x000000000045bae9 in ?? () 
 #11 0x00007fff2f0b9b78 in ?? () 
 #12 0x0000000000000000 in ?? () 
 
 However, when I start Quanta as root (sudo) from the comman line it doesn't crash. How comes? 
 Any ideas anyone?

---

### Post by sposmen on 2008-05-07
I had a similar problem today, i tried your suggestion starting the program with another user so it works well. 

So, i erase the .kde folder on my user folder and it start normaly on my profile.

I think it's not the better option, but while developers gets a solution it could be one.

It erase some personal configurations of Quanta...and don't know if more applcations depending of too.

It accours becouse it depends of many kde libraries.

> **Buster222 said:**
> I installed Quanta 3.5.6 on a fresh KUbuntu 7.04 and it worked fine. Then I installed quite a few other applications: Thunderbird, Firefox, etc. and after that Quanta chraches during startup. Starting Quanta from the comman line (as a normal user) results in:...

---

