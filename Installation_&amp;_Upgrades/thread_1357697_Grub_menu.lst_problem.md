---
title: "Grub menu.lst problem"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by j22 on 2009-12-17
Problem: I do not have the Grub menu.lst file that I can find.  The computer successfully dual boots into Ubuntu and XP.  Do I need the menu.lst file?  Should I leave well enough alone? Would like to change Grub timeout.

I am a new user of Ubuntu and Linux.  I have recently installed 9.10 in a dual boot configuration with XP.  Ubuntu was placed on a new hard drive so that it would be independent of XP, from the hard drive perspective. The new drive has three partitions - 0 being the / with Ubuntu and Grub installed there, 1 being swap, and 2 being NTFS for future data sharing with XP.   After install, I could not get Grub to load and run - the computer would always go directly into the XP bootup.  The thread below by bigdiesel with his external drive problem helped by pointing me to assign the hard drive priority in Bios.  This allowed Grub to load and it works.  I would like to change the timeout in the menu.lst file but it is not in /boot/grub/ nor can I find it in anywhere.  I have done numerous searches on all folders.  If it's there, it's super secret. Have partially read the Grub manual on it's web page.

Thanks, j22

---

### Post by darkod on 2009-12-17
9.10 comes with the new grub2 which doesn't use menu.lst. That's why you don't have it and it's normal. The main config file is grub.cfg in /boot/grub but it's best not to be edited manually. It is created from all config settings by executing
sudo update-grub

You can change the timeout in /etc/default/grub with
sudo gedit /etc/default/grub

You need to do the update-grub after that.

---

### Post by chuina on 2009-12-17
There are 3 TIMEOUT in /etc/default/grub

```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
```

which one (and how) to edit/comment with hash to see the grub menu ?
I'm using single booting with Karmic.

Thanks.

---

### Post by darkod on 2009-12-17
I'm not sure for single boot, I guess you can try commenting out with hash both where hidden is mentioned.

---

### Post by kansasnoob on 2009-12-17
> # GRUB_TIMEOUT=5 - No change from Grub Legacy. This is the number of seconds before the default entry is automatically booted.

    * Setting this value to -1 will cause the menu to display until the user makes a selection.
    * To display the menu on each boot use a value of 1 or higher.
    * This command defers to the GRUB_HIDDEN_TIMEOUT command. If the hidden display is interrupted by a key press, the GRUB_TIMEOUT counter begins its countdown.
    * In addition to editing the file as root, you can also run the following commands the check and change the default timeout value. The first checks the existing timeout, the second replaces the value. Replace T with the new value.
      Code:

      cat /etc/default/grub | grep 'GRUB_TIMEOUT='   # Checks current TIMEOUT value.
      sudo sed 's/GRUB_TIMEOUT=5/GRUB_TIMEOUT=T/g' -i /etc/default/grub  # Change TIMEOUT value. Replace T with new value.

# GRUB_HIDDEN_TIMEOUT=0

    * The menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * The setting may depend on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
            According to some of the GRUB 2 developers, in Ubuntu the menu will not be hidden any time there are other OSs found by os-prober, regardless of this setting. This is in keeping with the Ubuntu Team's goal towards booting: [https://wiki.ubuntu.com/DesktopExper...pec#Bootloader](https://wiki.ubuntu.com/DesktopExper...pec#Bootloader)
          o No other OS Detected: The menu will be hidden.
    * For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
    * 0 The menu will not be displayed. There will be no delay. When this entry is set to 0:
          o The user may force displaying the menu as the computer boots by holding down the SHIFT key.
          o During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key.
    * If enabled, the splash screen designated in 05_debian_theme will be displayed. This setting hides the menu only.

# GRUB_HIDDEN_TIMEOUT_QUIET=true

    * true - No countdown is displayed. The screen will be blank.
    * false - A counter will display on a blank screen for the duration of the GRUB_HIDDEN_TIMEOUT value.


From:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by j22 on 2009-12-20
Thanks to Darkod, Chuina,and Kansasnoob for the pointers.  Was able to finally resolve my problem.
-- j22

---

