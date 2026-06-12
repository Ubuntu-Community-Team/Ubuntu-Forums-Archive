---
title: "Solved ATI Radeon AGP Driver"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by jmacdallas on 2008-08-01
Okay, after sitting with this problem for ages, reading and reading through forums and trying absolutely everything, I think I finally have a working solution to what looks like a pretty common complaint. 

**Set up**
Ubuntu 8.04 Heron (fresh install)
ATI Radeon X1950XTX AGP 256 MB
Intel 875P chipset
[B]
Symptoms:[/B]
Heron installs easily and well. However, once you enable the restricted drivers and reboot, you get either a black (or white) screen of death and you can't do anything - not even drop down to the terminal prompt.

The following solutions don't work individually and all give the same problem as above
Method 1: 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually)
Method 2:
[http://www.linuxmint.com/forum/viewtopic.php?t=6317](http://www.linuxmint.com/forum/viewtopic.php?t=6317)
Doing it through Envy also doesn't work.
[B]
Problem:[/B]
AFAIK the reason this occurs on Radeon X1k cards is because the chip on the card is PCI-E, but the bus connecting it to the board is AGP. The prop. drivers combined with Hardy battle to deal with this conflict. This is further complicated on Intel motherboards with 8xx chipsets.

**Solution:**
Okay, this solution works for my setup but it should work for most Intel based systems as well. I started on a fresh install so there were no other drivers or config entries left lying around.

**Step 1: Disable Intel EDAC modules**
```
sudo nano /etc/modprobe.d/blacklist
```

Add the following to the file 

# EDAC modules to fix false PCI-E detection
blacklist i82875p_edac
blacklist edac_mc

Reboot. Don't install any updates from this point on.

(And **don't** reboot until everything is finished)

**Step 2: Install proprietary driver**
Use the manual install option from this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually)

Once you open the terminal, **don't** close it again. Once the driver is installed you won't be able to shutdown using the GUI, and you won't be able to open the terminal either to complete step 3.
  
It is important to follow manual guide, and to follow it to it's conclusion. Note that when I say follow it to it's conclusion, I mean keep on reading until you get to the end of the whole Wiki post and take special notice of the part that says configure the driver. 

The important part is coming up next. Don't close the terminal!

**Step 3: Workaround for VMEM problem**
From Alastair at ATI and xMachina.
> 
1) Look up exactly how much video RAM your card has, eg from the box, receipt, or the ATI control centre in windows (it will either be 256MB or 512MB). I'm going to use 256MB but substitute as appropriate.
2) edit your /etc/X11/xorg.conf, and add the following line at the end of the fglrx device section:
```
Option "MaxGARTSize" "256"

```
3) edit your grub boot instructions for your kernel in the /boot/grub/menu.lst file, adding vmem=256 to your kernel boot line for your main kernel, e.g.:
```
title Ubuntu 8.04, kernel 2.6.24-16-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-16-386 root=UUID=64fa7a1b-a8d7-45fb-a891-a81f3977bc13 ro quiet splash vmem=512
initrd /boot/initrd.img-2.6.24-16-386

```


**Step 4: Shutdown and correct BIOS settings**
Shutdown using the terminal by typing 

```
shutdown -r now 

```

Then, when the computer reboots. Go to your BIOS by pressing DEL and look for the setting related to AGP memory. (For Gigabyte boards, you will have to press Ctrl F1 to get advanced options) It may be in something like "Advanced Chipset Features." Change it to the same value as the others, eg 256Mb.

That should be it - your installation should work fine.

This worked for me and I have been able to replicate it twice. 5000+ fps in glxgears and direct rendering on. No major testing with Compiz done just yet, but preliminary tests seem pretty stable.

Post here if it worked for you?

Edit: Two weeks on and no problem. Compiz, Emerald and all the special effects work great (except the cube thing in Emerald doesn't render well.) Going to try it with Unreal Tournament next, but I'm confident it'll hold up.

---

### Post by garferi on 2008-10-18
ATi driver version 8.10 sooolved the problem on my Ubuntu Hardy Heron 8.04.1 system! :) 6 months needed to solve this, lol :D
Download it from [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run").
Put it to your home folder and copy the code to the terminal, than follow the instructions of the graphical installer.
```
sudo sh ati-driver-installer-8-10-x86.x86_64.run
```
After the installation paste these to terminal:
```
sudo aticonfig --initial -f
```
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

Restart your computer.

The newest driver in every month is [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").
I also have Compiz-Fusion working, and about 4000 FPS in glxgears. :)
Now I have just one problem, the videos are blinking in the players. I have waiting for the solutions...
Thx!

Good luck All!

---

### Post by jhansonxi on 2009-03-25
3.2GHz P4
875P chipset
PowerColor HD2600 512MB AGP
Jaunty Alpha 6

This solution worked for me.  The only issue I had was that the BIOS limited the AGP aperture to 256MB so I set everything to that.  Everything worked (after disabling Compiz).  Then I decided to try setting everything to 512 in spite of the BIOS limitation and it still worked.  Tested:

Chromium
Alien Arena
UT2004 (max settings w/shadows)
Doom 3 (max settings)

I didn't have as much success on Hardy.  Chromium and Alien Arena kept locking up at exit (I didn't try the other two).

In addition to setting vmem in the kernel line in menu.lst you should also add it to the "# defoptions=" line so it is automatically added to the next kernel version you install.  Leave the # as it is looked for by the updater.  Only ## lines are comments.

---

