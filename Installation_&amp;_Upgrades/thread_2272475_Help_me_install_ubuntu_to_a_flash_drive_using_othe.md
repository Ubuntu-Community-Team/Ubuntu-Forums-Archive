---
title: "Help me install ubuntu to a flash drive using other flash drive"
date: 2015-04-07
forum: Installation &amp; Upgrades
---

### Post by newbie14 on 2015-04-07
My situation:
My computer at home doesn't have CD reader or DVD reader.
My computer at home only has 2 working u.s.b 2.0 slots.
My computer at home has only 1 hard disk, the hard disk contained a windows operating system.
My computer at home is not connected to the internet.
Getting internet connection to my home computer is impossible.
I have 1 16GB kingston flash drive.
[ATTACH=CONFIG]261146[/ATTACH]
I have 1 32GB toshiba flash drive.
[ATTACH=CONFIG]261145[/ATTACH]
I want the bootable Ubuntu USB flash drive to be set up on the 16 GB kingston flash drive
I want the ubuntu operating system to be installed on the 32 GB toshiba flash drive.
I don't want the installation process touch the windows operating system's hard disk at all.
While I am currently at an internet computer rental, the computer rental uses windows 7 operating system.
The distance between my home and the internet computer rental is 10 kilometers.
what files should I download?
what tools should I use?
what steps should I do?

---

### Post by newbie14 on 2015-04-07
While you are on the internet computer rental, do this:
Step 1: type this in the internet browser's address bar: 
[http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
step 2: the website contains many hyperlinks, find the one that contains this phrase:
ubuntu-14.04.2-desktop-i386.iso
step 3: download the mentioned .iso file to the internet rental's computer. or,
step 4: if you know how to download using torrent, left click the hyperlink that contains this phrase at the end:
i386.iso.torrent
step 5: while you wait for the download to complete, open a new brower
step 6: on the browser you just newly open, type in this hyperlink in the address bar
[https://rufus.akeo.ie/downloads/rufus-2.1.exe](https://rufus.akeo.ie/downloads/rufus-2.1.exe)
step 7: press enter.
step 8: save the rufus file in a folder of your choosing.
step 9: let me know when you have downloaded those two files (the ubuntu.iso, and the rufus.exe).

---

### Post by newbie14 on 2015-04-07
I have finished downloading all the files.
[ATTACH=CONFIG]261149[/ATTACH]
Now, what should I do?

---

### Post by newbie14 on 2015-04-07
bootable Ubuntu USB flash driveNow, do this:
step 10: plug in your 16 GB flash drive to the internet computer rental's computer.
step 11: double left click the rufus-2.1.exe
step 12: If a "user account control" window appears, left click the "Yes" button. Then, the rufus main window should appear.
step 13: at the "device" menu at the top of the rufus window, there is a drop-down menu, left-click it, and left click your flash drive.
step 14: below it, the "Partition Scheme and target system type" menu, there is another drop-down menu, left click it, and left click the "MBR Partition scheme for BIOS or UEFI computers" option.
step 15: below it, the "file system" menu, there is another drop-down menu, left-click it, and left-click the only option that only contains "(default)" word.
step 16: below it, the "new volume label" there is a text box, left-click inside the text box and then type in: "TRYING BUNTU".
step 17: make sure the check box titled "Check device for bad blocks" is EMPTY.
step 18: left-click the "quick format" check box until a check mark appears inside the check box.
step 19: left-click the "create bootable disk using" check box until a check mark appears inside the check box.
step 20: left-click the "create extended label and icon files" check box until a check mark appears inside the check box.
step 21: left-click the button that has a picture of a rectangular box with a disk on top of it. the button is located at the far right of the "create a bootable disk using" check box.
step 22: an explorer window should appear.
step 23: locate the folder where the ubuntu.iso you've just downloaded at, and left-click the "open" button.
step 24: the disabled text box at the mid-bottom part of the rufus window should have been written "READY" automatically.
step 25: at the rufus main window, at the bottom part, there is a "Start" button. Click it with the left mouse button.
step 27: a warning window written " Warning: All data on device (Your drive letter) [16 GB] will be destroyed appears, left click the "OK" button.
step 26: wait while rufus is processing your 16 GB into a bootable Ubuntu USB flash drive. and a progress bar shows the progress.
step 27: let me know when rufus has done processing. (the sign of when rufus finishes its process is the progress bar fully filled with green color and the disabled text box below it has "READY" written on.)

---

### Post by newbie14 on 2015-04-07
Rufus has finished working.
[ATTACH=CONFIG]261151[/ATTACH]
what should I do now?

---

### Post by newbie14 on 2015-04-07
watch it.

---

### Post by newbie14 on 2015-04-10
step 28: go to your home, turn off your computer.
step 29: plug in the ubuntu bootable USB flash disk (the 16 GB)
step 30: Press your home computer's power button
step 31: Immediately press and hold the F12 button on the keyboard. Wait until the monitor shows a box titled "Boot Menu".
step 31a: If step 31 doesn't show "boot menu", press reset on your computer, or hold the power button until, or computer restarts, try pressing other keyboard button.
step 32: press the up / down arrow key on the keyboard until the "USB-ZIP" option is highlighted, and then, press Enter.
step 33: Your monitor should now turn purple. Wait until  a "Install" window appear, showing the "Welcome" step.
step 34: At the left part of the window, an "English" is highlighted in orange, at the other part of the window, there is "try ubuntu" button, and "Install Ubuntu" button. Left click the "Install Ubuntu" button.
step 35: The "Preparing to install ubuntu" step appears. Left click the check box titled "Install this third-party software" until a check mark appears inside the check box.
step 36: On the lower right part of the window, left click the "continue" button.
step 37: Your cursor should now turn to an animated circle cursor, wait until the "install window shows the "installation type" step appears and the cursor turns to a normal pointer cursor.
step 38: Plug in the 32GB flash disk for the installation media.
step 39: left click the "something else" radio button until a dot appears in the radio button.
step 40: left click the "continue" button.
step 41: You will see list of devices you can install the ubuntu on, your 32 GB flash disk may or may not appear on this list. So, left click the "back" button.
step 42: repeat step 39.
step 43: repeat step 40.
step 44: Your 32GB flash disk should now appear on the list, highlight the 32 GB flash disk by left clicking it.
step 45: Below the list, there is a text read "Device for boot loader Installation:", and below that text, there is a drop-down box. left click the drop-down box.
step 46: Left click the name of your flash disk, or if no names appears, left click the option which match the approximate size of your 32 GB flash disk.
step 47: Above the "Device for boot loader Installation there is a disabled "+" button, a "-" button, and a "change..." button. left click the "change..." button.
step 48: An "edit partition" window appears, left click the "+" button, and repeat clicking until the "+" button is disabled.
step 49: At the "use as" drop-down box, left click the "Ext4 journaling file system".
step 50: The "edit partition" window should show new, additional menus, left click the "format partition" check box until a check mark appears inside the check box.
step 51: At the "mount point" drop-down box, left click the "/" option.
step 52: Left click the "OK" button.
step 53: A warning window will appear, the warning window will say "Before you can select a new partition size, any previous changes have to be written to disk. You cannot undo this operation. Please note that the resize operation may take a long time." left click the "continue" button.
step 54: Your cursor will change to a loading, animated circle cursor, wait until the cursor turns back to normal cursor.
step 55: Left click the "Install now" button.
step 56: A warning window titled "Do you want to return to the partition menu?" left click the "continue" button.
step 57: A "where are you" step appears, left click the area on the map, the area where you currently live.
step 58: left click the "continue" button.
step 59: A "who are you" step appears. At the "your name" text box, type in "Fulani".
step 60: at the "your computer's name:" text box, type in "Kompie".
step 61: at the "pick a username" text-box, type in "fulani".
step 62: at the "choose password" text-box, type in "asdf1234".
step 63: at the "confirm your password" text-box, type in "asdf1234".
step 64: left click the "require my password to login" radio button until a dot appears inside the radio button.
step 65: left click the "Encrypt my home folder" check box until a check mark appears inside the check box.
step 66: left click the "continue" button. And then wait 20-30 minutes.
step 67: An "installation complete" notification window appears. Left click the "restart now" button.
step 68: press and hold the F12 button on the keyboard.
step 69: select "USB-ZIP" option, press enter.
step 70: at the next screen, a purple background and a list, an "ubuntu" has already been highlighted, press enter.
step 71: Wait as the computer loads ubuntu. Your monitor may think / assume that the cpu is turned off, and goes to standby mode, but don't panic, it's just the computer loads ubuntu normally, after some seconds, the monitor will turn on again, showing the login screen.
step 72: type in "asdf1234" in the password text box.
step 73: press enter.
step 74: Congratulations. You are now in ubuntu desktop!.

---

