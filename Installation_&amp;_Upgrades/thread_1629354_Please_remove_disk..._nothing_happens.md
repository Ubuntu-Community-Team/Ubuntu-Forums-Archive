---
title: "Please remove disk... nothing happens"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by dukebd711 on 2010-11-23
I went through the installation steps to install Ubuntu. I chose to wipe the disk and install Ubuntu, my time zone, USA keyboard, etc. After the installation was complete a dialog displayed stating the installation was complete. I clicked the Restart button, the disc tray popped out and the message "Please remove disk... press Enter to Continue." was displayed. I removed the disk, closed the tray and pressed Enter. Nothing happened. I pressed the num pad's enter button, nothing. After pressing both Enters 137 times and every other key on the keyboard I did a hard shut down. 
 
When I started the computer back up Ubuntu booted and everything seemed fine but I can now not restart my computer. If I do the black screen with the 5 (maybe it's 4 not sure) dots display underneath "Ubuntu". One by one the dots turn red until the fourth dot is red. The system then appears to freeze. The fifth dot never turns red.
 
So I cannot restart my computer, I must always shut it down and turn it back on.
 
Anyone else had this problem? Anyway to fix it? 
 
Thanks for any help.

---

### Post by dukebd711 on 2010-11-23
This is version 10.04 LTS

---

### Post by davidmohammed on 2010-11-23
welcome to the forums.

Some issues like yours can be due to the graphics card in your computer.  Do you know what it is?

Can you use the CD and the install option "try without installing" - does it boot to a desktop?  If it does, open a terminal session and type

lspci | grep VGA

post the reply here.

Depending on the graphics card, maybe a boot option such as nomodeset will work for you.

---

### Post by dukebd711 on 2010-11-29
The system's output is:
 
07:00.0 VGA compatible controller: nVidia Corporation G71GL [Quadro FX 3500] (rev a1)
 
Thanks for your help.

---

### Post by oldfred on 2010-11-29
I have an Nvidia card and this is what I did:

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

One user with just a Nvida chip said the  xforcevesa worked.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by dukebd711 on 2010-11-29
I put the installation disc back in, pressed the spacebar when the keyboard and human figure was displayed, pressed F6, selected nomodeset and installed as usual.  The system froze as it did before when the "Please remove the disc..." screen was displayed.

---

### Post by dukebd711 on 2010-11-29
> **oldfred said:**
> I have an Nvidia card and this is what I did:
 
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
 
After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
 
One user with just a Nvida chip said the xforcevesa worked.
 
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0
 
grub doesn't load when I start the machine, it just boots to Ubuntu.
 
I edited the grub.cfg and replaced quiet and splash with nomodeset and shut down.  Upon restart the computer froze after writing a bunch of checks.  I restarted again and Ubuntu loaded.
 
I'm installing updates, will install the nvidia driver and will see what happens after that.

---

### Post by oldfred on 2010-11-29
The shutdown after install from a CD is a minor bug only related to the shutdown.

If you only have one system, grub does not show a menu unless you hold down the shift key from BIOS until menu appears.

The nomodeset on install is not carried over to the install. I had to reenter it on first boot.

---

