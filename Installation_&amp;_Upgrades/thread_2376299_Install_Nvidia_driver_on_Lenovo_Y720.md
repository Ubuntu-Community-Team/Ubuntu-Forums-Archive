---
title: "Install Nvidia driver on Lenovo Y720"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by xavier12358 on 2017-11-01
Hello,
 
I just  receive my OS free Lenovo Y720. I had so  problem to install Ubuntu , and now I try to install the nvidia driver  of the 1060 GTX.
 
I try to install the 384.90 but the driver is not properly installed. The Nvidia is not correctly showned in the NVidia Setting.
 
Can someone Help me with that?

---

### Post by #&amp;thj^% on 2017-11-01
Have you powered down or rebooted yet?

---

### Post by xavier12358 on 2017-11-01
Indeed I made it . But When I restart I can't acces to my desktop. There is a black screen with a small windows which allow me to try with default resolution. But I still can't get the desktop. I had to remove the driver to be able to get the desktop.

 I also try to directly download the same from Nvidia website. When I try to execute the run file I get:

"The  distribution-provided pre-install script failed! Are you sure you want to continue?"

---

### Post by #&amp;thj^% on 2017-11-01
> **xavier12358 said:**
> Indeed I made it . But When I restart I can't acces to my desktop. There is a black screen with a small windows which allow me to try with default resolution. But I still can't get the desktop. I had to remove the driver to be able to get the desktop.

 I also try to directly download the same from Nvidia website. When I try to execute the run file I get:

"The  distribution-provided pre-install script failed! Are you sure you want to continue?"

It is best to stay with the packages within the software provided by the package manager, (Not downloaded from the Nvidia site)
You may need to add the "nomodeset" option at booting: See this: [https://askubuntu.com/questions/431534/how-to-set-nomodeset-grub2-before-ive-installed-ubuntu](https://askubuntu.com/questions/431534/how-to-set-nomodeset-grub2-before-ive-installed-ubuntu)
This after installing the Drivers from the package manager.

---

### Post by xavier12358 on 2017-11-01
I don't really understand where to put the nomodeset option .

---

### Post by #&amp;thj^% on 2017-11-01
No worries...
you can just use your text editor (gedit or Nano) to get this done.
So run this please I'm going to use nano here:
```
sudo nano /etc/default/grub
```

You look for the line that looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And then add just like mine:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
to save hit <ctrl+o> then enter and to exit <ctrl+x>
now tell grub about the change with:
```
sudo update-grub
```
reboot,

---

### Post by xavier12358 on 2017-11-01
I just try it. I have the same behavior but the screen rendering is very slow. In my dmesg I get that:
```
[  405.223232] kauditd_printk_skb: 11 callbacks suppressed
[   405.223233] audit: type=1400 audit(1509553178.288:66):  apparmor="DENIED" operation="mknod"  profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/4648/fd/2"  pid=4648 comm="lightdm-session" requested_mask="c" denied_mask="c"  fsuid=999 ouid=999
[  405.224464] audit: type=1400  audit(1509553178.288:67): apparmor="DENIED" operation="mknod"  profile="/usr/lib/lightdm/lightdm-guest-session" name="/proc/4650/fd/2"  pid=4650 comm="lightdm-session" requested_mask="c" denied_mask="c"  fsuid=999 ouid=999
[  405.896448] audit: type=1400  audit(1509553178.960:68): apparmor="DENIED" operation="open"  profile="/usr/lib/lightdm/lightdm-guest-session"  name="/proc/sys/kernel/cap_last_cap" pid=4734 comm="dbus-daemon"  requested_mask="r" denied_mask="r" fsuid=999 ouid=0
[  405.908331]  audit: type=1400 audit(1509553178.972:69): apparmor="DENIED"  operation="connect" profile="/usr/lib/lightdm/lightdm-guest-session"  name="/run/systemd/journal/stdout" pid=4734 comm="dbus-daemon"  requested_mask="w" denied_mask="w" fsuid=999 ouid=0
[  405.908332]  audit: type=1400 audit(1509553178.972:70): apparmor="DENIED"  operation="connect" profile="/usr/lib/lightdm/lightdm-guest-session"  name="/run/systemd/journal/stdout" pid=4734 comm="dbus-daemon"  requested_mask="w" denied_mask="w" fsuid=999 ouid=0
[  405.910277]  audit: type=1400 audit(1509553178.972:71): apparmor="DENIED"  operation="open" profile="/usr/lib/lightdm/lightdm-guest-session"  name="/proc/sys/kernel/cap_last_cap" pid=4756 comm="gnome-keyring-d"  requested_mask="r" denied_mask="r" fsuid=999 ouid=0
[  405.912790]  audit: type=1400 audit(1509553178.976:72): apparmor="DENIED"  operation="open" profile="/usr/lib/lightdm/lightdm-guest-session"  name="/proc/sys/kernel/cap_last_cap" pid=4760 comm="gnome-keyring-d"  requested_mask="r" denied_mask="r" fsuid=999 ouid=0
[  405.972773]  audit: type=1400 audit(1509553179.036:73): apparmor="DENIED"  operation="connect" profile="/usr/lib/lightdm/lightdm-guest-session"  name="/run/systemd/journal/stdout" pid=4734 comm="dbus-daemon"  requested_mask="w" denied_mask="w" fsuid=999 ouid=0
[  405.972774]  audit: type=1400 audit(1509553179.036:74): apparmor="DENIED"  operation="connect" profile="/usr/lib/lightdm/lightdm-guest-session"  name="/run/systemd/journal/stdout" pid=4734 comm="dbus-daemon"  requested_mask="w" denied_mask="w" fsuid=999 ouid=0
[  405.975505]  audit: type=1400 audit(1509553179.040:75): apparmor="DENIED"  operation="connect" profile="/usr/lib/lightdm/lightdm-guest-session"  name="/run/systemd/journal/stdout" pid=4734 comm="dbus-daemon"  requested_mask="w" denied_mask="w" fsuid=999 ouid=0
```

---

### Post by #&amp;thj^% on 2017-11-01
What dose this report from the terminal:
```
apt policy nvidia-384
```
But I'm assuming you can login.
Not really understanding you clearly.
BTW what ubuntu version are you on?

---

### Post by xavier12358 on 2017-11-01
I purge all the nvidia's stuff and I reboot. I get that on the terminal:

```
apt policy nvidia-384
nvidia-384:
  Installé : (aucun)
  Candidat : 384.90-0ubuntu0.16.04.1
 Table de version :
     384.90-0ubuntu0.16.04.1 500
        500 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages
```

Indeed I can login when I tape my password the computer always go back to the login page

---

### Post by #&amp;thj^% on 2017-11-01
show me the contents of this please.
```
gedit /etc/default/grub
```

---

### Post by xavier12358 on 2017-11-01
Here is the content:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by slickymaster on 2017-11-01
@xavier12358:

I've edit several of your posts swapping quote for code tags. Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output.

---

### Post by #&amp;thj^% on 2017-11-01
Ok this is how I run mine.
Remove the** "nomodeset"** and replace it with** "nogpumanger"**
So it will now look exactly like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"
```
Seeing that you are on 16.04 you can use this method also:
```
sudo -H /etc/default/grub
```
_don't forget to save the file before closing gedit._
Update Grub again:
```
sudo update-grub
```
now let's clean up a bit with: 

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```
now we will add a PPA with better/newer Drivers with:

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-384
```
Show any errors if any from the above code.
Again [s]Reboot[/s] wait strike that>>> This time lets power off the machine and let the hard drive spin down. Then Power on your machine.
Fingers Crossed.
Thanks slickymaster for the code tags :)

---

### Post by xavier12358 on 2017-11-01
I had no xorg.conf file , only backup files was there. 

Except for that there was no error. But when I reboot my computer I still have the same problem. I am stuck at the login page.

---

### Post by #&amp;thj^% on 2017-11-01
> **xavier12358 said:**
> I had no xorg.conf file , only backup files was there. 

Except for that there was no error. But when I reboot my computer I still have the same problem. I am stuck at the login page.

1.Did you reboot or power off?
2.Are you dual booting with Windows?
3.And is Secure Boot enabled?

---

### Post by xavier12358 on 2017-11-01
I don't really reboot. I shutdown my computer and then boot it.

In fact I had an OS free computer and then I install only ubuntu. I only have Ubuntu and there FreeOS.

Here is my bios:
[IMG]http://www.hostingpics.net/viewer.php?id=556310IMG20171101203111090.jpg[/IMG]
[http://www.hostingpics.net/viewer.php?id=371002IMG20171101203116283.jpg](http://www.hostingpics.net/viewer.php?id=371002IMG20171101203116283.jpg)

[IMG]http://www.hostingpics.net/viewer.php?id=371002IMG20171101203116283.jpg[/IMG]
[http://www.hostingpics.net/viewer.php?id=753802IMG20171101203111090.jpg](http://www.hostingpics.net/viewer.php?id=753802IMG20171101203111090.jpg)

---

### Post by #&amp;thj^% on 2017-11-01
> **xavier12358 said:**
> I don't really reboot. I shutdown my computer and then boot it.

In fact I had an OS free computer and then I install only ubuntu. I only have Ubuntu and there FreeOS.

Here is my bios:
[IMG]http://www.hostingpics.net/viewer.php?id=556310IMG20171101203111090.jpg[/IMG]


[IMG]http://www.hostingpics.net/viewer.php?id=371002IMG20171101203116283.jpg[/IMG]

I'm missing the Bios?
This will help me to help you:
```
sudo apt install inxi
```
And run this:
```
inxi -GsM
```
Post the output back please.
This is what mine looks like:
```
Machine:   Device: desktop System: HP product: 750-417c v: 1.01 serial: N/A
           Mobo: HP model: 828A v: 1.01 serial: N/A
          ** UEFI [Legacy]: AMI v: F.14 date: 09/19/2016**
Graphics:  Card-1: Intel HD Graphics 530
       _  >>  Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]_
           Display Server: x11 (X.Org 1.19.5 ) drivers: modesetting,nvidia
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2
           version: 4.5.0 NVIDIA 387.22
Sensors:   System Temperatures: cpu: 33.0C mobo: N/A gpu: 40C
           Fan Speeds (in rpm): cpu: N/A

```
Ok I now see your links to Bios...What I want to see is in under "Security" in your Bios.

---

### Post by xavier12358 on 2017-11-01
Here is mine :
```

Machine:   System: LENOVO (portable) product: 80VR v: Lenovo Y720-15IKB
           Mobo: LENOVO model: Provence-75I v: NO DPK Bios: LENOVO v: 4GCN24WW date: 04/14/2017
Graphics:  Card-1: Intel Device 591b
           Card-2: NVIDIA Device 1c20
           Display Server: X.org 1.19.3 drivers: (unloaded: fbdev,vesa) FAILED: nvidia
           tty size: 240x67 Advanced Data: N/A out of X
Sensors:   System Temperatures: cpu: 44.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A

```

---

### Post by #&amp;thj^% on 2017-11-01
My friend I'm at a loss here.:(
Need to think on this for a bit.
Can you or have you tried to disable the Intel GPU in your Bios?

---

### Post by xavier12358 on 2017-11-01
I don't see in Bios options to disable GPU.

---

### Post by #&amp;thj^% on 2017-11-01
> **xavier12358 said:**
> I don't see in Bios options to disable GPU.
Ok.
I have that option on mine, it allows me to use the prime-select command.
If I come up with anything useful here I will report back.
You have been a good sport through all of this...Hang in there.
Best Regards

---

### Post by xavier12358 on 2017-11-02
I try to install Lubuntu it seems to be more stable but the drivers still don't work properly but after each installation I can now go to the desktop again.

When I try to launch nvidia-setting in terminal I get that:
```

sudo nvidia-settings 

** (nvidia-settings:9274): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-hssM08DFHh: Connexion refusée

ERROR: An internal driver error occurred


ERROR: Error querying enabled displays on GPU 0 (Missing Extension).


ERROR: Error querying connected displays on GPU 0 (Missing Extension).

** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application profiles will continue to work, but values cannot be prepopulated
       or validated, and will not be listed in the help text. Please see the README for possible values and descriptions.


```

In lspci I have that:

```


01:00.0 VGA compatible controller: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Lenovo GP106M [GeForce GTX 1060]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 95000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 50000000 (64-bit, prefetchable) [size=256M]
    Memory at 60000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 5000 [size=128]
    [virtual] Expansion ROM at 96000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [258] L1 PM Substates
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [420] Advanced Error Reporting
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_378_drm, nvidia_378



```

---

