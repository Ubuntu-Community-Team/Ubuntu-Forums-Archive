---
title: "Failed Upgrade From 10.04 to 10.10 - Can't Open Terminal To Run Commands"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by bry72 on 2011-04-29
Hey guys,

Yesterday I tried upgrading from 10.04 to 10.10 using the upgrade manager.  About half way through, my computer froze up and the only thing I could do was reboot my computer.  It had already finished downloading all the upgrades and the computer froze while it was trying to install the upgrades.

When I boot my computer and the Grub screen appears, I chose the Ubuntu OS (I have a dual boot system of Ubuntu and Windows XP).  When it goes to boot Ubuntu, it gives me a blank screen and then a box in the right hand corner that says this:

"Install problem!
The configuration defaults for GNOME Power Manager have not been  installed correctly. Please contact your computer administrator."

Then the screen remains blank.  No cursor, no mouse pointer, nothing.

I have researched this error message and it is either caused by not having any free space on my hard drive or that the upgrade packages weren't installed properly.  In my case, it could be both.  It is definitely the packages not be installed properly but I don't know how to find out if there is no free space on the hard drive partition for Ubuntu.  Some of the solutions are to use the following commands in the terminal:

sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get --reinstall install ubuntu-desktop

The last command might cause me to lose previous settings, so that would be a last resort if the first two commands don't work.

So my main issue is that I cannot open a terminal.  My computer is set up to automatically log in.  When my computer boots, I have the Grub screen which allows me to choose the Ubuntu OS, Ubuntu in recovery mode or Windows Xp.  However, when I choose Ubuntu in recovery mode and select "c" for the command line, it does not recognize the "sudo" command.  Same when I choose the command line in the regular Ubuntu OS.  When I type "sudo apt-get clean" (without quotes), it says "Sudo command not found."

I cannot find the command lines that would be the equivalent of a "sudo" command to use in recovery mode.  If you hit the TAB key while in the command line of recovery mode, if gives a list of commands but I don't see a way to open up a terminal window.

For example, when I type terminal_input, it just says, Active: Console, Available: usb_keyboard."

I have also tried selecting the Ubuntu OS, waiting for it to boot and then hitting Ctrl+Alt+F1 but it does not give me a log in screen.  I have tried Ctrl+Alt+F2 and Ctrl+Alt+F7 and neither of those give me a log in screen either.  It is just a blank screen.  No cursor or mouse pointer is visible.

All I want is the ability to open up the terminal so I can run "sudo apt-get clean" and "sudo dpkg --configure -a".

If anyone knows how this can be done, please give me step by step instructions on how to do it.

Thanks.

---

### Post by dino99 on 2011-04-29
Applications -> Accessories -> Terminal

---

### Post by bry72 on 2011-04-29
> **dino99 said:**
> Applications -> Accessories -> Terminal


That would be fine if Ubuntu actually booted up.  I have already stated that it does not boot up and just gives me a blank screen.  I can't get to the desktop screen so this does nothing for me.

---

### Post by dino99 on 2011-04-29
even if you boot in recovery mode ? ("shift" key down at bios end process to see grub menu)

then select either: "repair packages" or "failsafe graphic"

---

### Post by ebbr.bugs on 2011-04-29
I second that. I have the same problem. In my case the installation process hung up right after the installation of gvfs on which point I had only one choice - pull the plug.
The normal grub boot item brings a blank screen (no errors reported), the recovery option brings a kernel panic. Older versions give the same result as the recovery option.

---

### Post by bry72 on 2011-04-29
> **dino99 said:**
> even if you boot in recovery mode ? ("shift" key down at bios end process to see grub menu)

then select either: "repair packages" or "failsafe graphic"

Here is how my computer boots from turning off to on:
1.  Shows Toshiba Screen giving option of F2 for BIOS and F12 for Settings
2.  Next screen is the GRUB Menu.  It has a 9 second timer if you do not hit any keys.  Once you select an up or down key, the timer stops.
3.  The list on the GRUB Menu has Ubuntu with its version number, Ubuntu with the same version number for recovery mode, memory test, Windows XP.

When I highlite the Ubuntu recovery mode, I can either hit "enter" to boot it in recovery, select "e" for edit or "c" for command line.

When I hit "enter" to boot it in recovery, instead of getting a menu list where you can highlite things, I get 3 pages of data listings that end with:

"Begin:  Running/scripts/init-bottom...
 Done. "

Then it has a blinking cursor at the very end.  It does not allow me to scroll up the page to see what all of the data is.  At this page,  I have tried Ctrl+Alt+F1, Ctrl+Alt+F2 and Ctrl+Alt+F7 to get the terminal to come up but it does nothing.  It just has the blinking cursor.

If I hit Ctrl+Alt+Del at this page, it will take me to a new screen that has about half a page of data and ends with it saying that it will now restart the system.  You have about 1 second to view the data before it automatically restarts the computer.  It does not give you an option of stopping the restart.

I'm not sure why I don't get a menu when I hit "enter" in recovery mode.  I have read of other people getting the 3 pages of data like me that ends with a blinking cursor.

One other thing to mention is that in my GRUB menu, I have a listing of like 5 different Ubuntu versions.  Each version has a string of numbers and periods.  An example would be 2.45.30.01  That's not the correct number, just giving an example.  I do know the first one on top ends in .31, has a recovery version, then another version ending in .30, recovery version, .29, recovery version, etc.  I think it goes down to .27

So that is where I am at.  I did some research and it mentions using BASH commands if you select "c" to get to the command line in recovery mode.  However, the website page I saw didn't give any commands that were the equivalent of "sudo apt-get clean" or "sudo dpkg --configure -a".

Any thoughts on BASH commands that would work to bring up the terminal or a way to actually get to the recovery menu screen instead of 3 pages of data and ending with a blinking cursor?

I have a LIVE CD for version 10.04 but it does not allow you to run root commands in the terminal.  I know the username is "ubuntu" and you leave it blank for the password.  I've done this and it successfully logs me in.  However, running any sudo commands in the terminal does nothing.  It just goes to the next line "ubunutu@ubunutu>" waiting for the next command to be typed in.

---

### Post by MAFoElffen on 2011-04-29
> **bry72 said:**
> Here is how my computer boots from turning off to on:
1.  Shows Toshiba Screen giving option of F2 for BIOS and F12 for Settings
2.  Next screen is the GRUB Menu.  It has a 9 second timer if you do not hit any keys.  Once you select an up or down key, the timer stops.
3.  The list on the GRUB Menu has Ubuntu with its version number, Ubuntu with the same version number for recovery mode, memory test, Windows XP.

When I highlite the Ubuntu recovery mode, I can either hit "enter" to boot it in recovery, select "e" for edit or "c" for command line.

When I hit "enter" to boot it in recovery, instead of getting a menu list where you can highlite things, I get 3 pages of data listings that end with:

"Begin:  Running/scripts/init-bottom...
 Done. "

Then it has a blinking cursor at the very end.  It does not allow me to scroll up the page to see what all of the data is.  At this page,  I have tried Ctrl+Alt+F1, Ctrl+Alt+F2 and Ctrl+Alt+F7 to get the terminal to come up but it does nothing.  It just has the blinking cursor.

If I hit Ctrl+Alt+Del at this page, it will take me to a new screen that has about half a page of data and ends with it saying that it will now restart the system.  You have about 1 second to view the data before it automatically restarts the computer.  It does not give you an option of stopping the restart.

I'm not sure why I don't get a menu when I hit "enter" in recovery mode.  I have read of other people getting the 3 pages of data like me that ends with a blinking cursor.

One other thing to mention is that in my GRUB menu, I have a listing of like 5 different Ubuntu versions.  Each version has a string of numbers and periods.  An example would be 2.45.30.01  That's not the correct number, just giving an example.  I do know the first one on top ends in .31, has a recovery version, then another version ending in .30, recovery version, .29, recovery version, etc.  I think it goes down to .27

So that is where I am at.  I did some research and it mentions using BASH commands if you select "c" to get to the command line in recovery mode.  However, the website page I saw didn't give any commands that were the equivalent of "sudo apt-get clean" or "sudo dpkg --configure -a".

Any thoughts on BASH commands that would work to bring up the terminal or a way to actually get to the recovery menu screen instead of 3 pages of data and ending with a blinking cursor?

I have a LIVE CD for version 10.04 but it does not allow you to run root commands in the terminal.  I know the username is "ubuntu" and you leave it blank for the password.  I've done this and it successfully logs me in.  However, running any sudo commands in the terminal does nothing.  It just goes to the next line "ubunutu@ubunutu>" waiting for the next command to be typed in.
At the Grub Menu screen > press " e " Manuever down to the kernel boot line and go to it's end > Type in  " text " > Press <ctrl>X and it will boot into a linux text console (without Xwindows starting).  

If it boots the Sys, you  will be asked to log in via username/password.  Tell me how it goes.  This step is important to confirm that the kernel/system itself is booting on your machine... and it what is occurring is a Sys problem or an Xorg problem.

---

### Post by bry72 on 2011-04-29
> **MAFoElffen said:**
> At the Grub Menu screen > press " e " Manuever down to the kernel boot line and go to it's end > Type in  " text " > Press <ctrl>X and it will boot into a linux text console (without Xwindows starting).  

If it boots the Sys, you  will be asked to log in via username/password.  Tell me how it goes.  This step is important to confirm that the kernel/system itself is booting on your machine... and it what is occurring is a Sys problem or an Xorg problem.

As I pointed out in a previous post, my system logs in automatically when it boots.  I don't get a login screen.  However, I tried doing what you asked.

You did not specify whether to do this with regular OS or in recovery mode, so I tried it in regular OS.  You also did not specify what a "kernel boot line" looks like, so here is what is shown when I hit "e" after highlighting my OS (Ubuntu, with linux 2.6.32-31-generic) :

record fail
insmod ext2
set root - '(hd0,5)'
search --no - floppy -fs-uuid --set (followed by a long string of numbers a letters ending in)   \f86
linux /boot/vmlinuz-2.6.32.31-generic root=uuid= (followed by a long string of numbers and letters) ro quiet splash
initrd /boot/initrd.img -2.6.32-21-generic

I didn't know what the "kernel boot line" was, so I went to the one that ends in "quiet splash" and after the words, I put in a space and type in "text" (without quotes).  I then hit Ctrl+X.  It took me to a blank screen that had a flashing cursor in the top left hand corner.  It would not allow me to type anything (at least not anything I could see) and after 10 minutes, it still showed a black screen with a blinking cursor.

I restarted the computer and then went down to the very last line "initrd/boot/..." and after the word "generic", I put in a space and typed in "text" (without the quotes).  I then hit Ctrl+X.  This took me to the Ubuntu 10.04 screen, then a blank screen and then it gave me the message in a box in the right hand corner:

"Install problem!
The configuration defaults for GNOME Power Manager have not been   installed correctly. Please contact your computer administrator."

This message stays up for about 5 seconds and then you are left with a blank screen.  No mouse pointer, no cursor.

This is the original problem I was running into.

Hopefully that gives you some insight into whether it is a Sys problem or an Xorg problem.

One poster mentioned hitting "enter" when highlighting "recovery mode" and it should give you a menu of items to select from.  My system is not doing that.  It is giving me 3 pages worth of data that ends with:
 "Begin:  Running/scripts/init-bottom...
  Done."
Then I have a blinking cursor at the bottom but it won't allow me to type anything.

So we are back to finding a way to get a terminal screen.  Is there a BASH command to do this in recovery mode?

And just a refresher, this was caused by the computer freezing up during the installation process of upgrading from 10.04 to 10.10 using the upgrade manager.  It had already downloaded all the upgrades.    Either I do not have enough free disk space or freezing up mid way through the installation has messed things up or both.

---

### Post by bry72 on 2011-05-01
Anyone else have any suggestions?

---

### Post by mdemuro on 2012-10-14
Hi Bry, any news? Did you re-installed or you sorted out some magic?

---

### Post by wildmanne39 on 2012-10-14
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

