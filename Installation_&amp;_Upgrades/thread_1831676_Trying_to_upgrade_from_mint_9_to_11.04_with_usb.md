---
title: "Trying to upgrade from mint 9 to 11.04 with usb"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by Jverm on 2011-08-23
Having a bit of troubles. I have created the startup disc using a 2gb fat32 USB. The bios on this computer gives me options to boot from floppy, ls120, hard disk, CDROM, zip, USB-FDD, USB-zip, USB-CDROM, USB-HDD, LAN.  
I have no idea which USB to pick so I've tried all of em. And every one gives me this. 

[http://i1177.photobucket.com/albums/x345/jverm/8dd6e05c.jpg](http://i1177.photobucket.com/albums/x345/jverm/8dd6e05c.jpg)

Anyone wanna help me out?

---

### Post by westie457 on 2011-08-23
> **Jverm said:**
> Having a bit of troubles. I have created the startup disc using a 2gb fat32 USB. The bios on this computer gives me options to boot from floppy, ls120, hard disk, CDROM, zip, USB-FDD, USB-zip, USB-CDROM, USB-HDD, LAN.  
I have no idea which USB to pick so I've tried all of em. And every one gives me this. 

[http://i1177.photobucket.com/albums/x345/jverm/8dd6e05c.jpg](http://i1177.photobucket.com/albums/x345/jverm/8dd6e05c.jpg)

Anyone wanna help me out?

Hi. Looking at the screenshot this is the POST listing however I could be wrong on that.
In the BIOS should be a tab called BOOT with a few options in it.
The main option here is to set boot-device priority. That is CD drive, Hard-drive, USB-drive, Lan.

Below this is the option to set DRIVE priority. That usually lists the internal hard drives but sometimes lists a connected USB drive.

Best for you to look there and set the boot order for each option.

Hope this helps.

---

### Post by Jverm on 2011-08-23
This is what I've changed it to now. And the same screen as before shows up. 

[http://i1177.photobucket.com/albums/x345/jverm/711ee5a8.jpg](http://i1177.photobucket.com/albums/x345/jverm/711ee5a8.jpg)

---

### Post by e79 on 2011-08-23
Looking at your first picture, if I understand correctly, your boot order is correct and your PC is trying to boot of your USB stick, but could not because of the message "unknown keyword in configuration file".

After a bit of Goggling, I stumbled on [http://alexsleat.co.uk/2010/11/27/how-to-fix-unknown-keyword-in-configuration-file-ubuntu-usb-boot/](http://alexsleat.co.uk/2010/11/27/how-to-fix-unknown-keyword-in-configuration-file-ubuntu-usb-boot/)  which seems to be related to your problem.

Here's the resume :

> 

.....just plug the USB flash drive into a computer (that works) and : 
[LIST=1]
[*]Open the the syslinux folder in the root of the flash drive.
[*]Inside is a file called syslinux.cfg you&#8217;ll want to edit that.
[*]Find the line &#8220;ui gfxboot bootlogo&#8221; and simply remove the &#8220;ui &#8220;.
[*]Save and try booting again.
[/LIST]
 Below is how my syslinux.cfg file looks after editing:
 # D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
 Alternatively it looks as though there is another way of fixing this  issue if there is no &#8220;ui&#8221; in the file, this is to do as followed (as  pointed out in the comments below):
 
[LIST=1]
[*] Type &#8220;help&#8221; and press enter
[*] Hit Enter again
[/LIST]
 This should boot correctly and shouldn&#8217;t need to be done every time.
I'd suggest you try their fix to see if it solves it.

Hope this helps

---

### Post by Jverm on 2011-08-23
I got the comp to boot from USB, then I got that error message as seen here. 
[http://i1177.photobucket.com/albums/x345/jverm/cb4ea465.jpg](http://i1177.photobucket.com/albums/x345/jverm/cb4ea465.jpg)

But I entered help, it gave me a list of commands and then I hit enter, like the instructions and then it just opens up another line.

---

### Post by uRock on 2011-08-23
Please do not post large images.

---

### Post by Jverm on 2011-08-23
Sorry man that's the only size I got. I'll post links from now

---

### Post by e79 on 2011-08-23
Humm..seeing your last post make me believe this didn't solved your problem at all but created a new one instead....

Could you redownload the Ubuntu .iso (maybe yours is corrupted)  and recreate your USB stick to see if the same issue occurs ?

---

### Post by Jverm on 2011-08-23
Yeah I googled around and found I had to update squashfs-tools to 4.0 and recreate the USB. 
Rebooting now...

EDIT: nothing changed, still says unable to find a medium containing a live file system.

---

### Post by e79 on 2011-08-23
Then could you try with UNetbootin (available from the Software Center) or if you have another Windows installation, give a try to [Universal USB installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") ?

What I'm trying to find out is if your USB is defective by going through elimination process

---

### Post by alfmarius on 2011-08-25
Many people (including me) have problems with this. Another thread:
[http://ubuntuforums.org/showthread.php?t=1779418](http://ubuntuforums.org/showthread.php?t=1779418)

I've read alot about this issue now, and still have not found a workable solution.

---

