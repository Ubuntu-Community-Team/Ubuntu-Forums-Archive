---
title: "Problem with Windows 10 and Ubuntu 14.04?"
date: 2015-12-18
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2015-12-18
Have been triple booting Win 7, Ubuntu 12.04 & 14.04 for a couple years with no problems. They all run fine on two drives. W7 in on a 2TB HDD and Ubuntu 12.04 & 14.04 are on a SSD.

Recently got a new SSD that dual boots  12.04 & 14.04.

Installed W10 on a SSD using a flashdrive with the W10 ISO on it. Disconnected both other drives when doing this W10 install. W10 install was quick, took 5 minutes and then 6 minutes of updates, etc., then W10 was good to go. Ran W10 some, did some downloads of fav apps/programs and all ran great! Played around with W10 a bit to see what it does. Then shutdown PC and reconnected the other SSD  that dual boots 12.04 & 14.04. Then restarted PC. Because I didn't know what GRUB would do I hit F12 key when rebooting then select the SSD with Ubuntu on it. Select 14.04 and it started/runs fine. Shutdown. Do a restart, hit F12 as before, select SSD with Ubuntu and select 12.04 this time and it starts/runs with no problem and runs fine. 

The problem is on the next restart I just left PC alone and it attempts to go right into W10 but won't start. Get error message saying W10 can't find boot device to start W10. W10 suggests trying to repair this error but can't! Made a few attempts at correcting this with Windows but it won't fix it! W10 appears dead now. Because W10 installs so fast, I did a fresh install again after disconnecting the other SSD. Again W10 runs fine as the sole SSD in my PC but went to the same error and went dead when reconnecting with the other SSD! 

Out of curiosity I shutdown then reconnected the HDD with W7 on it with the Ubuntu SSD and all 3 OSs run fine, as they did in the past. It's just W10 that won't run when connected to the other SSD with Ubuntu on it. 

Had to reinstall W10 again and it is running fine while being the only drive in the PC. 
Reconnected both SSDs together but only boot up Ubuntu using F12 key to keep from messing up W10 again. 

Question is what do I need to do to get W10 to play nice with Ubuntu?

---

### Post by oldfred on 2015-12-18
How are you booting Windows 10? UEFI or BIOS?

Then are you booting from BIOS/UEFI or from grub menu? Or one time boot key like f10 or f12?

Grub will not boot Windows if not in same boot mode. 
Grub will not boot Windows if UEFI secure boot is on. 
And I do not think grub boots the hibernated Windows. Windows 10 is always hibernated with its fast start setting. You need to turn that off. 
But you should be able to directly boot from either UEFI or BIOS (if Windows in MBR of Windows drive).
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by cybrsaylr on 2015-12-18
Was  booting Windows 10 with BIOS.
Then hit F12 and select the SSD with Ubuntu which takes me to GRUB choices of 14.04, 12.04 & W7.
When selecting SSD with W10, I just get error messages.

Didn't realize all that other stuff is going on now......

---

### Post by cybrsaylr on 2015-12-18
Thanks oldfred.
The first option of your link worked:
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
Now W10 starts up by default as the first OS.

To get my 2 Ubuntu versons to boot I have to hit F12 on start up then select the one desired after GRUB appears.

Hitting F2 to get into setup only shows the SSD with W10 as the first boot device.
The other SSD with Ubuntu is not shown.
But after hitting F12 in startup, it goes to GRUB which shows all 3 OSs, Ubuntu 14.04, 12.04 and Win7.

---

### Post by oldfred on 2015-12-19
With Multiple installs or multiple drives I suggest running the Summary Report from Boot-Repair. If nothing more than to document many settings and current configuration. It uses the bootinfoscript as part of the report and I normally run the bootinfoscript as part of my rsync backup.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

[/URL]
 Updated fork  as orginal bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by cybrsaylr on 2015-12-19
OK I hit F2 on startup. It had the SSD with W10 as first boot device, which caused W10 to boot first.
I changed that and made the SSD with Ubuntu the first boot device and now GRUB appears allowing Ubuntu to boot first.

If I want to run W10, I hit F12 and select the SSD with W10 to boot up instead. 

Vaguely recall doing this in the past but forget since it is very seldom needed or done.

---

### Post by cybrsaylr on 2015-12-20
FWIW....

Now have a Quadruple boot system, by adding the 2TB HDD with Win7 and a storage partition to this PC.

Had been triple booting Win 7, Ubuntu 12.04 & 14.04 for a couple years with no problems. 
They all ran fine on two drives. W7 in on a 2TB HDD and Ubuntu 12.04 & 14.04 are on a SSD.
Recently got another SSD and installed Win10 on it.
So now PC has 3 drives installed and all 4 OSs appear to be running A-OK.

On boot up GRUB shows 14.04, 12.04 and W7.
Have to hit F12 on initial boot up to select and get W10 to run, which is really no problem.

---

