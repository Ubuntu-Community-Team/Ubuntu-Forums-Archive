---
title: "Logitech Dinovo bluetooth keyboard fails after upgrade to 11.10"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by mgmiller on 2011-10-12
I have a Logitech Dinovo bluetooth keyboard/trackpad that was working perfectly in Natty (11.04).  After upgrading to Oneiric (11.10) it no longer worked at all and kept popping up a bluetooth connect dialog that consistently failed.

How to fix for 11.10:
```
gksudo gedit /lib/udev/rules.d/62-bluez-hid2hci.rules
```How to fix for 12.04 (thank you QuadeHale) 
```
gksudo gedit /lib/udev/rules.d/97-bluetooth-hid2hci.rules
```Look for the line under "# Logitech devices" that  starts with:
KERNEL=="hiddev*"
and change it to:
KERNEL=="hidraw*"

Leave the rest of the line intact.

Save the file and restart the machine.  (You probably really only need to log off and back on).

If you are doing an upgrade, ( I just did 11.10 to 12.04), at the very end, when it's ready to restart, just _**do the edit as above before restarting**_.  That way your keyboard/trackpad/mouse will continue to work after the restart.  If you restart first, you will lose the bluetooth keyboard/mouse and you will have to plug in a wired keyboard/mouse to make the changes.

I have entered a bug on this at:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/872940](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/872940)

---

### Post by Parrameister on 2011-10-14
Thanks - worked a treat.
I had to use the onscreen keyboard for typing (lent my normal wired keyboard out as thought I wouldn't need it again).

My logitech keyboard and mouse is a Logitech MX5500 Keyboard Mouse combo.
(logs reported device id's so match was OK with config line in rules file) 
:)

---

### Post by cep1980 on 2011-10-14
Thank you for solving this.

---

### Post by dwlima on 2011-10-14
Thank you very much for solving this also.

---

### Post by mrboojive on 2011-10-17
Worked for me too, thanks!

---

### Post by desliz on 2011-10-18
Thanks again.  I have a MX550 keyboard and a MX Revolution mouse.  It worked for me, but volume keys on the keyboard stil doesn't work, while in 11.04 was fine.

---

### Post by jbussdieker on 2011-10-18
Thanks! I was getting the grant access to service prompt too for my Logitech MX5500 Performance Mouse. Updated the config file, disconnected the USB receiver for a second then plugged it back in and it's working!

---

### Post by mgmiller on 2011-10-19
> **desliz said:**
> Thanks again.  I have a MX550 keyboard and a MX Revolution mouse.  It worked for me, but volume keys on the keyboard stil doesn't work, while in 11.04 was fine.

Take a look in  system settings -> keyboard ->Custom Shortcuts and see if the volume up down settings are correct.  You can change them by just clicking on the volume up shortcut for example and then hitting the volume up key on your keyboard.

---

### Post by alfonso78 on 2011-10-19
Thanks! It also worked for my BTKB-7866 KeySonic ACK-340BT
[http://www.keysonic.de/](http://www.keysonic.de/)

---

### Post by dwlima on 2011-10-20
Thank you so much. Works on my bluetooth MX revolution keyboard and mouse. Boy, was that a nuisance.

---

### Post by uv_goth on 2011-10-20
Unfortunately my volume and media keys aren't registered as keystrokes.

Any suggestions?

(I'm using Kubuntu and already have the keyboard layout set to the dinovo so no idea why not working!)

---

### Post by mgmiller on 2011-10-20
I am not using Kubuntu.  I have the Unity interface in Ubuntu and all the media keys and "Star Trek transporter" volume slider on the Dinovo keyboard work as expected.

Sorry

---

### Post by icarus101 on 2011-10-20
My Logitech DiNovo stopped working after last update to 11.04 and I couldn't find anything relevant to fix it so upgraded the machine to 11.10 but still no joy.  I have tried the fix outlined above (many thanks) but it has not worked for me.  My machine is a dual boot (Ubuntu/Win7) and I cannot even select which OS to load.  By default it loads Ubuntu first.  Do you know if there is also a GRUB file that needs to be updated? 

+1 to the comment on nuisance factor (though not having the machine has given me space to get some much needed painting and decorating done over the last couple of weeks)

UPDATE - My keyboard is working again.  The only additional thing I did was to press the reset button I found on the bluetooth transceiver after booting.  Many thanks [mgmiller]("http://ubuntuforums.org/member.php?u=55008") for this post.

---

### Post by lillem4n on 2011-10-21
First hit on google. Works like a charm. Big thank you!

---

### Post by kgsbu2 on 2011-10-28
Thanks, worked for me. 
MX-5000 keyboard and MX Laser mouse.

---

### Post by walt9z on 2011-10-30
You, sir or madam, are a Linux god.  The unwashed masses thank you.

---

### Post by mgmiller on 2011-10-30
> **walt9z said:**
> You, sir or madam, are a Linux god.  The unwashed masses thank you.

:lolflag:I prefer to think of myself as a "sir".  

Now go get washed before you eat dinner!  :popcorn:

---

### Post by variuxdavid on 2011-11-02
It worked for me, but with one modification:

```
gksudo gedit /lib/udev/rules.d/62-bluez-hid2hci.rules
```The original was ...hic.rules, which didn't exist on my machine.

Thanks!
David
[variux.com]("http://www.variux.com")

---

### Post by woodsby on 2012-01-04
This solution breaks the ability to connect my wiimotes in Dolphin-emu. Any ideas how to fix this problem without affecting other bluetooth devices?

I think the posted solution is the same fix that has been used to fix the dinovo for the last several releases.  I thought I read a while back that this will break all other bluetooth functionality.

---

### Post by efflandt on 2012-01-04
Yes this has been an ongoing problem since at least 10.10 (or was it 10.04?). But it had to be changed in a different file in rules.d/ before.  That is strange because with the included dongle, the Dinovo works for CMOS setup or Windows without any driver at all, but would fail to do anything once an Ubuntu installation iso booted or I think past grub menu of installed system, without this fix.

---

### Post by ezzy25 on 2012-03-24
> **variuxdavid said:**
> It worked for me, but with one modification:

```
gksudo gedit /lib/udev/rules.d/62-bluez-hid2hci.rules
```The original was ...hic.rules, which didn't exist on my machine.

Thanks!
David
[variux.com]("http://www.variux.com")

Thanks mgmiller and variuxdavid for posting this.  Worked perfectly using the command quoted (the original didn't work for me either).  I just installed Ubuntu for the first time ever and was about to pull my hair out because the Logitech Divino bluetooth keyboard is the only keyboard I have.  I got rid of my old wired keyboard because the Divino even works in the BIOS before any OS is loaded.  I thought I was going to have to go back to Windows there for a minute...

---

### Post by mgmiller on 2012-03-25
> **variuxdavid said:**
> It worked for me, but with one modification:

```
gksudo gedit /lib/udev/rules.d/62-bluez-hid2hci.rules
```The original was ...hic.rules, which didn't exist on my machine.

Thanks!
David
[variux.com]("http://www.variux.com")


Quite Right!   I had to look at my original post twice to see the difference.  I have edited it to the correct path.  

Thanks for the catch.

---

### Post by QuadeHale on 2012-04-16
I would like to note in this extremely helpful thread that in Precise (12.04) this file has been apparently "moved", so now the command is:
```
gksudo gedit /lib/udev/rules.d/97-bluetooth-hid2hci.rules
```.
Just a heads up. Thanks for figuring this out. Remember to restart and/or log out and back in!

---

### Post by mgmiller on 2012-04-23
> **QuadeHale said:**
> I would like to note in this extremely helpful thread that in Precise (12.04) this file has been apparently "moved", so now the command is:
```
gksudo gedit /lib/udev/rules.d/97-bluetooth-hid2hci.rules
```.
Just a heads up. Thanks for figuring this out. Remember to restart and/or log out and back in!

Thank you.  I have amended the original post to reflect the change.

I also mentioned to make the change after the upgrade but before rebooting so the change takes effect without any further fuss.

---

### Post by icarus101 on 2012-06-09
Many thanks for this thread. It has cured my woes not just once (11.10) but a second time with the 12.04 update.   I keep a second ps2 wireless keyboard and mouse plugged in and ready just in case but I hate using them. Having my Logitech Dinovo working again is just smooth! :-)

---

### Post by nbourne on 2013-01-01
> **mgmiller said:**
> I have a Logitech Dinovo bluetooth keyboard/trackpad that was working perfectly in Natty (11.04).  After upgrading to Oneiric (11.10) it no longer worked at all and kept popping up a bluetooth connect dialog that consistently failed.

How to fix for 11.10:
```
gksudo gedit /lib/udev/rules.d/62-bluez-hid2hci.rules
```How to fix for 12.04 (thank you QuadeHale) 
```
gksudo gedit /lib/udev/rules.d/97-bluetooth-hid2hci.rules
```Look for the line under "# Logitech devices" that  starts with:
KERNEL=="hiddev*"
and change it to:
KERNEL=="hidraw*"

Leave the rest of the line intact.

Save the file and restart the machine.  (You probably really only need to log off and back on).

If you are doing an upgrade, ( I just did 11.10 to 12.04), at the very end, when it's ready to restart, just _**do the edit as above before restarting**_.  That way your keyboard/trackpad/mouse will continue to work after the restart.  If you restart first, you will lose the bluetooth keyboard/mouse and you will have to plug in a wired keyboard/mouse to make the changes.

I have entered a bug on this at:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/872940](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/872940)

Thanks for posting this fix it.  It also worked for me when my keyboard stopped working following an upgrade from Ubuntu Studio 12.04 to Ubuntu Studio 12.10

---

