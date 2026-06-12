---
title: "[Solved] Upgrade to 7.10 hangs on shutting down bluetooth services"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by The Chef on 2007-10-25
I initiated an upgrade from Feisty Fawn to Gutsy Gibbon 7.10 using the update manager, clicking on the icon when prompted.  The upgrade process hung on shutting down Bluetooth services, did not complete and the upgrade failed.  From that point, I would still get a graphical login screen, but after logging in I would only get a turquoise blue screen with a working mouse cursor and nothing else.  However, I could activate virtual terminals and perform text commands by typing ctrl-alt-F1 through F6; so, I knew that Linux was running, but X or the windows manager or Gnome were failing to load.  (A more technical user could say which.)

I am running a Dell Dimension 8250 desktop PC
I have no bluetooth devices attached to the PC
I have an SD (and other size) flash memory card reader/writer inserted into a USB port.

I tried many things to fix this, but only found one that worked.:

Disconnect the flash memory card reader from the USB port (I got this lead off of another forum as a comment buried in a list of HIGHLY technical fixes for similar symptoms.)

Boot from Grub into Recovery Mode (I would speculate that a normal boot followed by ctrl-alt-F1 into a virtual terminal would work also, but I would further speculate that you would need to do everything I did in the recovery terminal as a “sudo” super user.)

At the recovery terminal Ubuntu prompt enter “apt-get install bluez-utils” [the Blue tooth services]

I then removed and reinstalled this package because I am superstitious and also wanted to tempt an error message.  This is probably unnecessary, but here is what I did: enter “apt-get remove bluez-utils” then after successful completion enter “apt-get install bluez-utils”

After taking these steps, and leaving the flash memory card reader unplugged, I was able to run update manager and have a successfully installed 7.10 Gutsy Gibbon distribution from upgrade.

The only ill effect I found from going through this process (which includes some unsuccessful steps I have not mentioned above) was that my keyboard defaulted to Generic US layout.  This was easily rectified using Gnome <System><Preferences><Keyboard> utility. 

Note also that in trying to solve this I tried booting off a live 7.10 disk, and this would hang also with the flash memory card reader attached to the USB port.  So, there is a real incompatibility issue.

Here are some key words to help navigate people here: 7.10 upgrade hang bluetooth blue screen flash memory reader USB port

Hope this helps someone.

---

