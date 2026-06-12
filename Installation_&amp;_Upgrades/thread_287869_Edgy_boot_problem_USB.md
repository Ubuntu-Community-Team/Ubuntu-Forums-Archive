---
title: "Edgy boot problem: USB?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Whiski on 2006-10-29
Hello,

(Short version)[LIST]
[*]Upgraded from Dapper to Edgy - no apparent problems
[*]GUI Update manager had problems with upgrading some packages
[*]Was still able to use Kubuntu, and no problems after rebooting
[*]Now, all of a sudden a few days later, the boot process freezes after mounting all USB ports (tried removing all devices, same error), and finally when done loading kjournald.
[*]Same problem in recovery mode. Can't even access the prompt.
[/LIST]

(Long version)
I recently upgraded from (Kubuntu) Dapper to (Kubuntu) Edgy using the official guidelines from Ubuntu. During the upgrade, there were some packages that returned Error code 1. Nevertheless, things seemed to work fine after booting in failsafe, executing ```
apt-get -f install
``` and rebooting again. I was able to use the os as usual, except for the gui update manager. There were some ~1000 packages to upgrade, and after about 800 of them, i got an error message that said something similar to *Could not install package. Might break package seal.*

Edgy still worked, but after a few days (and reboots) the update manager still wouldn't download the packages i had yet to upgrade.

This morning though, I turned the computer on and the booting sequence froze. In normal mode, the progress bar only made it one step before everything froze. In recovery mode, i made it all the way to the mounting of USB ports and units. Then it froze. I tried removing all USB units, but it still froze at the same place during boot. When I go failsave with no USB devices plugged in, it stops booting right after Loading kjournald... Done.

Thus, I can't access the login screen, nor can I get to the prompt in recovery mode.

Does anyone know what has gone wrong, and how to fix it?

System specs:
Intel P4 @ 3 GHz
ATI AIW Radeon 8000SE

Kind regards 
Niklas

---

### Post by Whiski on 2006-10-29
Updated with more info about when the booting sequence stopped, which is after:

Loading kjournald... Done.

---

### Post by Whiski on 2006-10-29
This is what the boot process output is before it all stops:

(Mounting the usb ports...)
[...]
Begin: Running scripts/local-bottom ...
Done.
Done.
Begin: Running scripts/init-bottom ...
[17179576.432000] kjournald starting. Commit interval 5 seconds
Done. 


And then nothing at all. Just a blinking marker allowing me to type, but nothing happens when i press enter. Ctrl+C doesn't do anything eighter.

If i plug in a USB device, a line of text appears confirming that the device has been plugged in, so the system isn't dead, it just thinks it's done...

If i leave the computer standing still like that for a couple of minutes, the screen turns completely blank.

---

### Post by flonejek on 2006-10-29
I have same issue though after about 20 mins my box reached a login screen then i couldn't login/exit to console because my usb kbd/mouse weren't working, out of curiosity what motherboard/usb interface do you have? (mines a gigabyte K8N geforce 6100 with an nforce 430 chipset)

---

### Post by Whiski on 2006-10-29
How did you solve the problem?

I have a Soltek mainboard, though no specs for it.

---

### Post by flonejek on 2006-10-29
hehe, unfortunately im not working on a solution atm, trying an aptitude kernel downgrade using a live cd and chroot, if that doesnt work ill just hang on till someone smarter than me works out whats going on ;P

edit: gah livecd does boot succesfully but no usb either..., downloading dapper livecd now (I use rewritables and overwrote my dapper disk ](*,) )

---

### Post by Whiski on 2006-10-29
Ah :/

Well, be sure to post a how-to in this thread if you manage to fix it.

I've booted my computer to wait and see if I get a login after 20 mins.

Edit: Nope, didn't get anywhere...

---

### Post by Whiski on 2006-10-29
> **flonejek said:**
> edit: gah livecd does boot succesfully but no usb either..., downloading dapper livecd now (I use rewritables and overwrote my dapper disk ](*,) )

What was it you were going to try using the Live cd? I've got no clue about what to do here. I wish I could just revert to my dapper installation, or pretty much anything but this void state.

---

### Post by Whiski on 2006-10-29
I think I sorted it out. This is what I did:

Edit the recovery mode in the GRUB menu, append *init=/bin/bash* to the kernel line. Boot.

Once I got a prompt, i tried 

*dkpg --configure -a*

but it would complain about /usr/local/sbin and /usr/sbin not being in PATH. So i did

*PATH=/usr/local/sbin:/usr/sbin:/usr/local/bin:/usr/bin:/sbin:/bin*

and ran dkpg --configure -a again. It worked, and after a reboot i was able to log in as usual.


Edit: Running the Adept updater now reveals that Compiz seems to have been the crook. It was marked [COLOR="Red"]BROKEN[/COLOR], so I marked it Request removal, and applied the other updates.

Edit 2: Adept update still has stuff it wants me to upgrade, but gives error when trying to commit... Gosh.

---

### Post by flonejek on 2006-10-29
Wow, cool!, yeah sorry bout that the downlload was taking ages and it was 1am over here but I went to sleep, I just did the same thing using the livecd and it worked!, wierd package issues heh...

---

