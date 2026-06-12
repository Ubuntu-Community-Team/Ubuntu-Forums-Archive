---
title: "Failed to Initialize HAL"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by LittleBlue on 2006-06-16
I've just installed dapper.  I'm getting the message
"Failed to Initialize HAL"

I have a few questions:

1)   What is HAL?
2)   How do I fix the problem?
3)   Is this a show stopper? Do I need to go back to Breezy?

I found mentioned in the forum that the problem may be related to a smbs entry in /etc/fstab.  I have no such entry in /etc/fstab.

Any help is appreciated.

Thank you
Alan

---

### Post by kufford on 2006-06-17
You say that you are "getting" the message? As in more than once? I got the message after the first boot, but it went away after that...

---

### Post by LittleBlue on 2006-06-17
[QUOTE=kufford]You say that you are "getting" the message? As in more than once? I got the message after the first boot, but it went away after that...[/QUOTE]

Thank you for the suggestion.  I did try rebooting, but I still get the message.

---

### Post by sbooth on 2006-06-17
Wish I could help.  I had the same problem... and since it's an intermittent problem, I can't be sure I don't still have it!

With me it was definitely related to automounting two samba shares in my fstab - when I stopped the automounting the 'failed to initialize HAL' message went away.

I downloaded some 60-something updates yesterday, put the automounts back in fstab and rebooted... without getting the problem.  But that was just one reboot - haven't rebooted again so don't know if the problem has gone (am hopeful!)

Being a relative newbie, I don't understand enough to guess at what might be causing the problem.  Hope someone does though.

---

### Post by rcarring on 2006-06-17
HAL is short for 'hardware application layer' and is used to translate low-level hardware/devices by the main operating system layer to the presentation layer (your desktop), and would handle such things as the display adapter, media disks, sound and so on.

I checked my boot files, at least the folder hal and the rcS.d folder and hal isnt called at all under my fresh install of Dapper, leastways I don't know where precisely the hal is called into play.

---

### Post by sbooth on 2006-06-18
Nope... reboot again today (mucking around with fonts and stuff) and got the Failed to initialize HAL error again.  Taken automount of samba shares out of fstab again and it works, again.  Ho hum.

---

### Post by dylanv on 2006-07-31
[QUOTE=rcarring;1148609]HAL is short for 'hardware application layer' and is used to translate low-level hardware/devices by the main operating system layer to the presentation layer (your desktop), and would handle such things as the display adapter, media disks, sound and so on.[QUOTE]

Your definition is correct, but HAL stands for Hardware Abstraction Layer. See [this wikipedia entry]("http://en.wikipedia.org/wiki/Hardware_Abstraction_Layer").

---

### Post by nemesa on 2006-07-31
Hi!

It's a known bug and the dev-team is "working on it".

You can find solutions here:
[https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874](https://launchpad.net/distros/ubuntu/+source/hal/+bug/44874)

---

### Post by LittleBlue on 2006-09-20
I'd like to thank everyone who has responded.  After looking at related threads, I still have the problem.  The problem for other people seems to revolve around samba network shares using the auto option in /etc/fstab.

I have no network shares.  Here is my /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I also checked /var/log/syslog to see if I could get any clues. No luck.

Because of this error, I'm still using Hoary.  I'm hoping edgy will fix the problem when it is released.

I've pretty much given up hope for dapper.  Once again, thank you to all responders for trying to help.

---

### Post by Jose Catre-Vandis on 2006-10-14
I have had this error along with Power Manager - dbus issues many times along the way. Moving away from samba network shares to nfs network shares helped alot, but my other "on PC" were still causing problems. I found that by creating "fixed" mount points for these, instead of allowing Ubuntu to create them helped to reduce the incidence of this error. For example, I have Xp on my first partition, and normally Ubuntu will identify this and put an icon on the desktop called "XP". when hal fails, I get hda1 instead and no cdrom access. By creating a folder in media or mnt called XP, and then editing the correct line in /etc/fstab, e.g. from /dev/hda1 /media/hda1 to /dev/hda1 /media/XP my hal problem goes away. HTHS

[EDIT]

However, its back again. this problem is a real downer as far as Ubuntu is concerned!

---

### Post by bewire on 2006-10-19
Hi, I get the same warnings and believe my HP Photosmart 7260 is part of the problem. It looks like the warnings only shows if the printer is connected to the USB cable at boot.

Edit: I had problems with this printer when booting XP as well. The system hung for 10-15 minutes before booting when the printer was connected (no problems when the printer wasn't connected).  HP Photosmart 7260 has ports for different memory cards and I suspected that the system had problem when loading them.

bewire

---

### Post by [woodstock] on 2006-10-29
I got this error message (failed to initialize HAL) right after performing the dist-upgrade from Dapper to Edgy. I have no samba shares (I am using ssh for networking) in my fstab.

I have found a method of solution that might work for others a well: after turning off the auto login option for GDM the error message does not occur anymore. It might be inconvenient to login every boot-up, however I consider manually mounting external devices even more inconvenient.

This behaviour concludes that a "timing problem" might be behind that error message. Some process hasn't finished yet while another service (gnome?) might already depend on its successful termination. Unfortunately I don't know enough to come up with a more sophisticated solution that clears the faults instead of just the symptom.

---

### Post by jgcamp99 on 2006-11-18
I get this same error message only when I try to autologin in Edgy. I disable the autologin and it doesn't error the HAL initialization.

I also notice 2 hdd partitions don't mount or are visible when the HAL fails to initialize properly. I give it enough time @ the login screen and this is the time it takes to type in the userid and password and this seems to be enough time to initialize HAL properly. the drives show up like it's supposed to. Hmmmm, in my case it seems like maybe Gnome loads too fast and these drives aren't initialized and mounted by Edgy ? I checked the fstab file and there is no samba code that I read.

---

### Post by zoob on 2006-11-19
Good call!  I was getting the same and it would fail to mount my 2 USB Drives and CD-ROM drives.  I disabled auto login and all is well.  

Thanks,

Kevin

> **jgcamp99 said:**
> I get this same error message only when I try to autologin in Edgy. I disable the autologin and it doesn't error the HAL initialization.

I also notice 2 hdd partitions don't mount or are visible when the HAL fails to initialize properly. I give it enough time @ the login screen and this is the time it takes to type in the userid and password and this seems to be enough time to initialize HAL properly. the drives show up like it's supposed to. Hmmmm, in my case it seems like maybe Gnome loads too fast and these drives aren't initialized and mounted by Edgy ? I checked the fstab file and there is no samba code that I read.

---

### Post by jgcamp99 on 2006-11-21
> **zoob said:**
> Good call!  I was getting the same and it would fail to mount my 2 USB Drives and CD-ROM drives.  I disabled auto login and all is well.  

Thanks,

Kevin

It took me a few tries to realize that I wanted to attempt to fix it as root. I've re-enabled root to be allowed to login in and the default autologin was for the Ubuntu user. I'd get that message and then have to logout to get in as root and the message disappeared as root. I couldn't find anything on a fix, but then tried disabling the autologin and the problem disappeared.

It's pretty strange, some are reporting this with Dapper, I never had it happen with Dapper and that was 5 months of continuous usage (I'm MS Windows free today, yayyyyyyyyyyyy !). My initial install of Edgy was clear of this message as well, it popped up not long after having to reinstall Edgy ? There have been a couple of updates for Edgy since it's introduction, who knows, Ubuntu is into security for the OS, that's why root is disabled for passwords and the gnome gui login. Maybe this HAL error is a nudge or push to have auto-login disabled, even though gnome allows it ? I know I'm not automatically logging in because of it.

---

### Post by zoob on 2006-11-23
I have a work around for this.  Instead of using the auto login I used the timed login set for 5 seconds.  It seems to stop the HAL error.

Kevin

> **jgcamp99 said:**
> It took me a few tries to realize that I wanted to attempt to fix it as root. I've re-enabled root to be allowed to login in and the default autologin was for the Ubuntu user. I'd get that message and then have to logout to get in as root and the message disappeared as root. I couldn't find anything on a fix, but then tried disabling the autologin and the problem disappeared.

It's pretty strange, some are reporting this with Dapper, I never had it happen with Dapper and that was 5 months of continuous usage (I'm MS Windows free today, yayyyyyyyyyyyy !). My initial install of Edgy was clear of this message as well, it popped up not long after having to reinstall Edgy ? There have been a couple of updates for Edgy since it's introduction, who knows, Ubuntu is into security for the OS, that's why root is disabled for passwords and the gnome gui login. Maybe this HAL error is a nudge or push to have auto-login disabled, even though gnome allows it ? I know I'm not automatically logging in because of it.

---

### Post by knoxautoguy on 2006-11-26
I had this problem in Edgy, right after upgrade.  Followed suggestions in many threads, such as:
  1. Edit /etc/fstab file to "noauto" for NTFS volume
  2. Timed log-in for session
  3. Disabled volume manager in Start-up, and finally
  4. Deleted firefox from Start-up (my own idea)

The last step, deleting firefox from start-up under System/Sessions, seems to have eliminated the HAL error. 

I did this because of one post that explained that HAL might return an error due to delays caused by automatic log-in (which I wasn't using). 

For some reason, I still get firefox on startup, which is great, but I don't know why it still comes up after deleting it from the startup :-k

Keep in mind that I'm very inexperienced in Ubuntu/GNU/Linux

---

### Post by ChrisG_UK on 2007-02-18
The 5 second timed login solution works well for me. Whoever came up with that - thank you!

---

### Post by alexmoon on 2007-02-26
Sorry if this question is a bit silly - I've been looking around the forums and google for answers, but I'm still quite new to ubuntu and such.

I've been getting "Failed to Initialize HAL" too, and it didn't seem to be having an effect so I mentally filed it away as "something to deal with later". Then, last night my battery just stopped charging when it was plugged in. Is there any chance the two could be related?

This is just a wild guess, although it seems most likely that it's the battery itself that's failed. It just seemed strange that the battery would stop working completely without some kind of significant performance loss first...it's been charging fine up until last night, without any problems as far as I've seen.

Thank you.

---

### Post by Dubstar_04 on 2007-02-26
I am also suffering with this problem and it results with my sound device being given a different name each time the pc boots, which in turn means that i have to set the sound device up in mythtv everytime the pc is restarted. Very very annoying indeed and i'm desperate to find a solution.

---

### Post by robwales on 2007-03-06
I have tried pretty much all of the above to no avail in fixing HAL problem. I also find that when I open my Power Management Preferences (using notebook, no Windows install) whether plugged in or not that the Power Managemetn Preferences window freezes and can only be closed by a reboot.
I can mount my CD but not my flash drive.
I had experimented with an XP and Ubuntu dual system and when have now reformatted and installed Ubuntu only. The onyl thing I have done different is that I installed WINE this time.

Very frustrating.

---

