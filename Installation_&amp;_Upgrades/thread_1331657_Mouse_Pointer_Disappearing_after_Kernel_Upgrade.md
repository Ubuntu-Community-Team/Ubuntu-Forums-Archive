---
title: "Mouse Pointer Disappearing after Kernel Upgrade"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by sonicrules1234 on 2009-11-19
I am currently using Ubuntu 9.04, and I did a kernel upgrade.  To my horror, after I logged in (the mouse pointer is there when I log in), the mouse pointer disappeared.  

I was still able to figure out where it was because of the hover effects (you know, the brightness change of a button or link when you hover your mouse over it) and quicky changed the settings in System>Preferences>Mouse to show where the mouse is when I pressed control.  

I was looking for a post about this but could not find one that was after a kernel upgrade.  I figured I should turn off compiz since everybody knows it causes problems with some things, and it didnt work.  So I turned compiz back on to Extra and guess what?  The little locator when you press control stopped working.

Frantically, I pressed alt-tab to switch windows.  For some weird reason, it made the mouse pointer re-appear!  I have rebooted and got the same problem but was able to fix it in the same way.  I was hoping there might be a more permanant solution.  I would really appreciate some help with this.  Thanks in advance!

---

### Post by mvyvoda on 2009-11-30
bump

---

### Post by dhavalbbhatt on 2009-11-30
Try using the older kernal and see if you can replicate the issue.

---

### Post by FOBS1 on 2009-11-30
Had the same problem
Deleted partition and reloaded - mouse didn't work, but kernel had upgraded from CD.
Deleted partition and reloaded again without internet
Mouse problem started almost immediately on start of install
Reinstalled 8.04 - no mouse problem.
Seems problem comes in very early in boot process from CD.

---

### Post by dhavalbbhatt on 2009-11-30
What version of the kernal are you using?

---

### Post by rvndrk3233 on 2009-12-11
seeing similar with gnome. disappears, and not always when typing.

*bump* of mouse brings it back.

'uname -a' guys its not that hard.




Linux frybox2000 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux
Ubuntu 9.04, 10 has issues.

---

### Post by b00mer on 2010-05-15
I am experiencing the exact same problem after Upgrading to 10.4.  Never had any problems with earlier distributions.  I can get the cursor to be visible by sudo lshw -c display, but that is only temporary.  If I reboot I have to do that again. 

This is the information I get when I do lshw -c display:
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:ff680000-ff6ffff

I'm runninb this on an old Dell Optiplex GX260 with onboard video.

Anybody have any ideas on how to make the pointer show up on a more permanent basis?

Also, it seems screensavers are giving me problems as well when they never used to.  They just blank my screen and I have to reboot.

---

### Post by dino99 on 2010-05-15
sudo update-pciids && update-usbids
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by Sonicgoo on 2010-05-15
I'm having a few troubles after an upgrade to 10.04 with the mouse and keyboard not showing up. So i am using ssh from another computer to run the commands that you posted and I get the following.

touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

---

### Post by b00mer on 2010-05-16
> **dino99 said:**
> sudo update-pciids && update-usbids
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

Tried this and I get:
 Downloaded daily snapshot dated     2010-05-10 03:15:02
touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

What now?

---

