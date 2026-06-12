---
title: "How to: Install Ubuntu 7.10 w/ a Separate /home Partition"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by justinmiller87 on 2008-02-18
[size="7"]How to: Install Ubuntu 7.10 with a Separate /home Partition[/size]

[SIZE="5"]Introduction[/SIZE]

The following guide is an instruction on installing Ubuntu 7.10 with a separate /home partition. A separate /home partition is important because if something goes wrong with your data, it is possible to do a reinstall of Linux without affecting your /home folder. The /home folder in GNU/Linux is basically the equivalent to the "Documents and Settings" folder under Microsoft Windows XP. If you have multiple users on your system you will see multiple folders, ie: /home/justin/ & /home/johndoe/. This is basically the equivalent to the "My Documents" folder for each user under Microsoft Windows XP. This isn't a failsafe way to make sure your data is preserved in the event of a meltdown, backing up is the only safe way to do that, but it is helpful if backups do not occur often. Unlike under Windows, you won't see separate drives for partitions like a c:, d:. etc. Everything will fall under the / folder, including all CD-ROMs, floppy drives, external devices, etc. This also includes partitions. Your /home folder will be in a separate partition, but it will look like it is a subdirectory of the / folder. You can think of / as your c:\ drive if you are used to running Windows.

[SIZE="5"]What You Will Need:[/SIZE]

[LIST]
[*]Computer with the following minimum system requirements:
[list]
[*]233 MHz Processor
[*]384 MB RAM
[*]10 GB Hard Drive
[/list]
[*]Ubuntu 7.10 Alternate Install Disc, available from [http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-i386.iso](http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-i386.iso)
[*]Wired Internet connection
[*]Calculator
[/LIST]

[SIZE="5"]Preparation:[/SIZE]

This guide assumes that all data will be destroyed on the hard drive in which you are installing, so make sure that all data has been backed up. You must also burn the Ubuntu 7.10 disc to a CD. If you are using Windows and do not have a commercial CD-burning software such as Roxio Easy CD Creator or Nero Burning ROM, install the following freeware tool to help you: [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

[SIZE="5"]Installing:[/SIZE]

[LIST=1]
[*]Ensure your computer is connected to your network.
[*]Turn on your computer.
[*]Insert the Ubuntu 7.10 Alternate Disc into the CD-ROM tray on your computer.
[*]You should see the screen in Fig. 1:
[Figure 1: Initial Ubuntu Gutsy Gibbon Alternate Menu](http://www.justinandlindseymiller.com/images/ubuntuss/fig1.jpg)
[list=A]
[*]Reboot the computer if the screen in Fig. 1 does not appear and look for Fig. 1 again.
[*]If Fig. 1 does not appear this time, reboot once again and check your BIOS settings to ensure that the CD-ROM is first in the boot menu.
[/list]
[*]Select the first choice, "Install in text mode," by pressing "Enter."
[*]Scroll through the language selection screen shown in Fig. 2 to choose your language by using the "Up" and "Down" arrow keys.
[Figure 2: Language Selection Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig2.jpg)
[*]Press "Enter" to select your language and continue to the next screen.
[*]Scroll through the country  selection screen shown in Fig. 3 to choose your country by pressing the "Up" and "Down" arrow keys.
[Figure 3: Country Selection Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig3.jpg)
[*]Press "Enter" to select your country and continue to the next screen.
[*]Choose "No" on the Ubuntu installer main menu screen shown in Fig. 4 by pressing the "Right" arrow key and pressing "Enter."
[Figure 4: Keyboard Detection Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig4.jpg)
[*]Scroll through the keyboard origin screen shown in Fig. 5 by pressing the "Up" and "Down" arrow keys.
[Figure 5: Keyboard Country Origin Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig5.jpg)
[*]Press "Enter" to select your keyboard origin and continue to the next screen.
[*]Scroll through the keyboard layout screen shown in Fig. 6 by pressing the "Up" and "Down" arrow keys.
[Figure 6: Keyboard Layout Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig6.jpg)
[*]Press "Enter" to select your keyboard layout and continue to the next screen.
[*]Wait for the next few screens to continue automatically until Fig. 7, Configure the network is shown.
[Figure 7: Configure the Network Screen.](http://www.justinandlindseymiller.com/images/ubuntuss/fig7.jpg)
[*]Choose your wired Internet NIC. In most cases it is "eth0." Press "Enter" to continue to the next screen.
[*]Type a name for the computer on the network in the screen shown in Fig. 8. Press "Enter" to continue to the next screen.
[Figure 8: Configure the Network Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig8.jpg)
[*]Wait for the next few screens to continue automatically until Fig.9, Partition Disks is shown.
[Figure 9: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig9.jpg)
[*]Determine how big your partitions will be using a calculator:
[list]
[*]Calculate a minimum of 4 GB for your / partition. The best bet is 25% of the hard drive's space, but 40 GB is more than enough if your hard drive will accommodate the space.
[*]Multiply the amount of RAM you have by two. This will be your swap partition.
[*]Use all remaining free space for your /home partition.
[/list]
[*]Choose "Manual" by pressing the "Down" arrow key and pressing "Enter."
[*]Choose the hard drive in your system by looking for a line that contains either the term "(sda)" or "(hda)" by scrolling with your "Up" and "Down" arrow keys as shown in Fig. 10 and pressing "Enter." 
[Figure 10: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig10.jpg)
[*]Select "Yes" on the warning screen shown in Fig. 11 by pressing the "Left" arrow key and pressing "Enter." This will return you to the screen in step 18.
[Figure 11: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig11.jpg)
[*]Press the "Down" arrow to highlight the line containing the text "pri/log" and press "Enter" as shown in Fig. 12.
[Figure 12: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig12.jpg)
[*]Select Create a new partition on the screen shown in Fig. 13 by pressing "Enter."
[Figure 13: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig13.jpg)
[*]Type in the hard drive space you wish to use for the "/" partition and press "Enter" on the  screen shown in Fig. 14. REMINDER: You can use any size you like, but it must be a minimum of 4 GB.
[Figure 14: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig14.jpg)
[*]Choose "Primary" on the screen shown in Fig. 15. by pressing "Enter."
[Figure 15: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig15.jpg)
[*]Choose "Beginning" on the screen shown in Fig. 16 by pressing "Enter."
[Figure 16: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig16.jpg)
[*]Scroll down to "Done setting up the partition" on the screen shown in Fig. 17 by pressing the down arrow and pressing "Enter"
[Figure 17: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig17.jpg)
[*]Press the "Down" arrow to highlight the line containing the text "pri/log" and press "Enter" as shown in Fig. 18.
[Figure 18: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig18.jpg)
[*]Select "Create a new partition" on the screen shown in Fig. 13 by pressing "Enter."
[*]Type in the hard drive space you want to use for the "/home" partition and press "Enter" on the screen shown in Fig. 19. REMINDER: Be sure to leave free space equal to 2*RAM for your swap.
[Figure 19: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig19.jpg)
[*]Choose "Primary" on the screen shown in Fig. 15. by pressing "Enter."
[*]Choose "Beginning" on the screen shown in Fig. 16 by pressing "Enter."
[*]Scroll down to "Done setting up the partition" on the screen shown in Fig. 20 by pressing the "Down" arrow and pressing "Enter."
[Figure 20: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig20.jpg)
[*]Press the "Down" arrow to highlight the line containing the text "pri/log" and press "Enter" as shown in Fig. 21.
[Figure 21: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig21.jpg)
[*]Select "Create a new partition" on the screen shown in Fig. 13 by pressing "Enter."
[*]Press "Enter" to select the remaining space on the hard drive as shown in Fig. 22.
[Figure 22: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig22.jpg)
[*]Choose "Primary" on the screen shown in Fig. 15. by pressing "Enter."
[*]Choose "Beginning" on the screen shown in Fig. 16 by pressing "Enter."
[*]Press the "Up" arrow to highlight the "Use as:" line and press "Enter" as shown in Fig. 23.
[Figure 23: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig23.jpg)
[*]Press the "Down" arrow to highlight "swap area" and press "Enter" as shown in Fig. 24.
[Figure 24: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig24.jpg)
[*]Scroll down to "Done setting up the partition on the screen shown in Fig. 25 by pressing the "Down" arrow and pressing "Enter."
[Figure 25: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig25.jpg)
[*]Verify your screen looks similar to the one shown in Fig. 26.
[Figure 26: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig26.jpg)
[*]Scroll down to "Finish partitioning and write changes to disk" and press "Enter." NOTE: If you want to change your mind, choose "Undo changes to partitions" and no changes will be made to your system.
[*]Choose "Yes" on the screen shown in Fig. 27 by pressing the "Left" arrow and pressing "Enter" to overwrite all previous data on the system.
[Figure 27: Partition Disks](http://www.justinandlindseymiller.com/images/ubuntuss/fig27.jpg)
[*]Wait for the next few screens to continue automatically until Fig. 28, "Configure time zone" is shown.
[Figure 28: Configure Time Zone](http://www.justinandlindseymiller.com/images/ubuntuss/fig28.jpg)
[*]Select your time zone on the screen shown in Fig. 28 by using the "Up" and "Down" arrow keys and pressing "Enter."
[*]Select "Yes" on the screen shown in Fig. 29 by pressing "Enter."
[Figure 29: Configure the Clock](http://www.justinandlindseymiller.com/images/ubuntuss/fig29.jpg)
[*]Type in your full name on the screen shown in Fig. 30 and press "Enter"
[Figure 30: Set up Users and Passwords](http://www.justinandlindseymiller.com/images/ubuntuss/fig30.jpg)
[*]Type in a username for your account or press "Enter" to accept the username given as shown in Fig. 31.
[Figure 31: Set up Users and Passwords](http://www.justinandlindseymiller.com/images/ubuntuss/fig31.jpg)
[*]Type in a password for your account and press "Enter" on the screen shown in Fig. 32.
[Figure 32: Set up Users and Passwords](http://www.justinandlindseymiller.com/images/ubuntuss/fig32.jpg)
[*]Type in the same password again and press "Enter" on the screen shown in Fig. 33.
[Figure 33: Set up Users and Passwords](http://www.justinandlindseymiller.com/images/ubuntuss/fig33.jpg)
[*]Wait for the next few screens to continue automatically until Fig. 34, "Configure the package manager" is shown. NOTE: This process will take about five minutes in most cases and may seem like it has hung up at times.
[Figure 34: Configure the Package Manager](http://www.justinandlindseymiller.com/images/ubuntuss/fig34.jpg)
[*]Type in any HTTP proxy information and press "Enter." In most cases, this should just be left blank.
[*]Wait for the next few screens to continue automatically until Fig. 35, "Finish the installation" is shown. NOTE: This process will take about 20-30 minutes in most cases and may seem like it has hung up at times, particularly on the screen that says "Configuring apt" shown in Fig. 36.
[Figure 35: Finish the Installation](http://www.justinandlindseymiller.com/images/ubuntuss/fig35.jpg)
[Figure 36: Configuring Apt](http://www.justinandlindseymiller.com/images/ubuntuss/fig36.jpg)
[*]Remove the CD-ROM from the tray when it opens.
[*]Press "Enter" on the screen shown in Fig. 35 to reboot the computer.
[*]Wait for the system to load through the screen shown in Fig. 37.
[Figure 37: Ubuntu Loading Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig37.jpg)
[*]Type your username you setup in step 50 on the log-in screen shown in Fig. 38 and press "Enter."
[Figure 38: Ubuntu Login Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig38.jpg)
[*]Type your password you setup in steps 51 and 52 on the log-in screen shown in Fig. 39 and press "Enter."
[Figure 39: Ubuntu Login Screen](http://www.justinandlindseymiller.com/images/ubuntuss/fig39.jpg)
[*]Enjoy your new Ubuntu system! (Fig. 40)
[Figure 40: Ubuntu Fully Loaded](http://www.justinandlindseymiller.com/images/ubuntuss/fig40.jpg)
[/LIST]

---

### Post by K.Mandla on 2008-02-19
Moved to Installation and Upgrades.

---

