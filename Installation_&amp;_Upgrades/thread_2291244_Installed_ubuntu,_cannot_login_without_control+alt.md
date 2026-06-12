---
title: "Installed ubuntu, cannot login without control+alt+delete, boot in recovery"
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by joshua31 on 2015-08-18
I am running an Hp pavilion g6 2269wm laptop that has been upgraded to a total of 8 GB 1333 Ram, and an AMD a10-4600m APU. It comes with a 500GB HDD 5400rpm. That being said, I could not get some things to work on the windows 8.1 OS that i would like to have, and decided to just install ubuntu 15.04 on as the only OS instead. Works great, usually no problems, although in order to boot, I have to restart the boot process by hitting control+alt+delete and then booting in recovery mode, then resuming a normal boot. Reason being, it with load the screen to input the encryption pass, but I cannot enter anything. It will not allow me to do any sort of input. That is about the time i have to do the control+alt+delete. With the newest upgrade to the kernel .26 from .25, I could not even boot up from the recovery mode. I had to switch back to the .25 kernel recovery just to access the laptop and even type this now. Anybody willing to help a guy out here with some fix ideas?
-Josh

---

### Post by oldfred on 2015-08-18
UEFI or BIOS install?
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If UEFI:
      
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[URL="http://ubuntuforums.org/showthread.php?t=2218154"]http://ubuntuforums.org/showthread.php?t=2218154
[/URL]
 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[URL="http://ubuntuforums.org/showthread.php?t=2227889"]http://ubuntuforums.org/showthread.php?t=2227889
      [/URL]
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by joshua31 on 2015-08-18
I am not able to access the efi folder. It says I do not have the permission to do so, even though I am admin over the laptop... help?

---

### Post by oldfred on 2015-08-18
I found that also with  a 15.04 install.
I have 14.04 on my SSD as my main working install and when I installed 15.04 on sdb, it still overwrote the /EFI/ubuntu entry in my sda working install. But I could not fix it from 15.04.

I found they changed the mount parameters in fstab. And just changing them and reloading fstab does not update, until you reboot.

       14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat [COLOR=#ff0000]   defaults[/COLOR]        0       1
15.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1

Change the parameter to from umask=0077 to defaults.
      
 sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
or 
sudo nano /etc/fstab
Then run this and if no errors it just reloads fstab with no messge. But parameters are not changed until reboot.
 sudo mount -a



You could also use live installer.

---

### Post by joshua31 on 2015-08-18
What is live installer, and how do i use it?

---

### Post by oldfred on 2015-08-18
How did you install Ubuntu?
That is the live installer. 
When you boot it should give you two choices, one to install and one to test (live) Ubuntu by running it from DVD or flash drive. Then you know if it will work, even if a bit slower from DVD or flash drive than from a hard drive.

---

