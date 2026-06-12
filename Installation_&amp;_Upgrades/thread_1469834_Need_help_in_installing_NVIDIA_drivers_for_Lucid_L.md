---
title: "Need help in installing NVIDIA drivers for Lucid Lynx"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ganeshmallyap on 2010-05-02
Hi,

Today I did a clean install of Lucid Lynx AMD64 on my desktop.  The installation process went on smooth. After installing all the necessary software addons I got a notification from the system that proprietory drivers for NVIDIA card are available and I clicked the Activate button shown on the dialogue box.  it started downloading and after installation it prompted for restart of the computer.  

While restarting at the boot screen itself I received a error prompt and the message reads something close to the following -

"UBUNTU is running in low graphics mode.

The following error was encountered.  You may need to update your configuration to solve this.

(EE): <timestamp> Failed to initialize the NVIDIA kernel mode. Please see system's kernel log for additional error messages and consult the NVIDIA Readme for details.

NVIDIA (0) ***aborting*** 
(EE)  Screen(s) found, but none have one usable configuration."

I was not sure how to fix this.  I clicked on boot using low resolution mode and tried to reinstall the system one more time.  But the same error popped again.  I happily used NVIDIA proprietory drivers on my Karmic Koala AMD64 without a single issue.  My desktop is made of Intel Dual Core CPU with 4 GB DDR2 RAM and NVIDIA mother board GeForce 7100/nForce 630i and I use LG Flatron W1642S monitor.  I have also noticed that the default driver does not recognize my monitor model as well.

Finally for the third time I reinstalled my system and required software applications except NVIDIA proprietory drivers.  I need help as to how to handle this problem and on a worst case if I need to rollback this driver to nouveau (default) how to do that.  Thanks in advance.

Regards
Ganesh

---

### Post by brawd on 2010-05-02
Hope this helps, I had a similar problem, but my machine held together well enough for me to establish that version 96 was the one for me. The recommended driver turned out to be big trouble.

I'm using AMD64x2 with Asrock alive motherboard with built in graphics.

To find them go:

System
Admin
Hardware drivers

After installation you will probably need to reboot.

regards,

brawd

---

### Post by ganeshmallyap on 2010-05-03
Finally my graphics card issue got resolved.  I found some information on a website and the link for that article is [http://www.ubuntugeek.com/howto-inst...ucid-lynx.html]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html").  


1) Download Newest Nvidia drivers from [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")
 2) Open module blacklist as admin[INDENT]gksudo gedit  /etc/modprobe.d/blacklist.conf
[/INDENT]Add these lines and save:[INDENT]blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
[/INDENT]3) Uninstall any previously installed Nvidia drivers:[INDENT]sudo  apt-get --purge remove nvidia-*
[/INDENT]4) Reboot your computer
 5) When an error message pops up saying that Ubuntu cannot load  Nvidia  drivers, choose Exit to terminal (Exit to console)
 6) Login and cd to the directory where you saved your file
 7)Install drivers[INDENT]sudo sh  NVIDIA-Linux-x86_64-195.36.24-pkg2.run
[/INDENT]:cool:Start GDMsudo  service gdm start

---

### Post by jsgarvin on 2010-05-04
ganeshmallyap's steps above probably work (I haven't tried), but I don't think I would call that a real solution. Hack/work-around would be a more apt term.

Ultimately, we should be able to install the drivers via System > Administration > Hardware Drivers, and have them work. Obviously, something is not quite right (which is to be expected with a brand new release).

I was able to start up in the low graphics mode and get into the Hardware Drivers section to remove the Nvidia driver to get back to normal. Hopefully a fixed driver will be available soon. I'll try holding out for it before resorting to a manual install.

---

### Post by jsgarvin on 2010-05-05
FYI, I got the nvidia driver installed and working.  For me, the following steps worked.

1. Get back to a clean slate by booting into low-graphics mode and using System > Administration > Hardware Drivers to remove the nvidia drivers that I installed via the same window.

2. Reboot

3. Follow only step 2 of ganeshmallyap's instructions above to add the blacklist entries.

3. Reboot (probably not necessary, but just to be safe)

4. Go back to System > Administration > Hardware Drivers and reinstall the nvidia drivers

5. Reboot again.

6. Joy ensues.

---

### Post by Glesshoppa on 2011-01-26
Noob question here. System boots to Low Graphics Mode, No other options work here except to run in console. So I am trying to download the proper drivers from Nvidia but cannot browse to there site in console.  I downloaded the correct drivers using my MAC but the effected systems does not recognize or mount a thumb drive or external drive and does not read contents of a cdrom. Is there anyway of navigating to the Nvidia site via console and downloading the proper driver? 

Thanks in advance.

---

### Post by wojox on 2011-01-27
Sure

```
w3m -v http://www.google.com
```

---

