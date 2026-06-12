---
title: "frusterated to all hell"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Imoen on 2009-10-19
I spent 6 hours trying to install Kubuntu 9.10 and it would not do anything but get half way through and then crash. Now I installed Ubuntu 9.10 and figured that I can just add the KDE Desktop environment but I can't find the sources link and GPG Key to add to the sources list. 

Everything I try to install with the Software center I get:
The connection to the daemon was lost. Most likely the background daemon crashed.

I am constantly getting dumped to the login screen with no errors to give me a clue why. That happened when I was just running off the disk too but I figured that it might be because I was running off the disk. 

Can anyone help me with any of these issues? I love Ubuntu and don't want to have to go back to using Windows after being a Ubuntu user for more then a year now but I can not deal with loosing everything I work on every 20 minutes or so when I'm dumped back to the login screen.

---

### Post by oboedad55 on 2009-10-19
> **Imoen said:**
> I spent 6 hours trying to install Kubuntu 9.10 and it would not do anything but get half way through and then crash. Now I installed Ubuntu 9.10 and figured that I can just add the KDE Desktop environment but I can't find the sources link and GPG Key to add to the sources list. 

Everything I try to install with the Software center I get:
The connection to the daemon was lost. Most likely the background daemon crashed.

I am constantly getting dumped to the login screen with no errors to give me a clue why. That happened when I was just running off the disk too but I figured that it might be because I was running off the disk. 

Can anyone help me with any of these issues? I love Ubuntu and don't want to have to go back to using Windows after being a Ubuntu user for more then a year now but I can not deal with loosing everything I work on every 20 minutes or so when I'm dumped back to the login screen.

In case you're not aware, Ubuntu 9.10 is still in beta testing. If you have a working jaunty or hardy system you may want to stay with it at least until karmic has been released. As it is now lots of updates are still coming through, usually multiple times daily. What you describe is not necessarily unusual, if you look through the karmic testing forum.

---

### Post by Imoen on 2009-10-19
I realize that it's still in the beta testing and not going to be released for 10 more days. I was running 8.10 on my computer perfectly until my motherboard died. Then I had to start using a different computer and first I just put my hard drive in it and tried to just use it like that but I was having the same problem with the dumping back to the login screen which I figured was because my computer hardware was much older then the computer I'm using now. So then I installed a fresh copy of 8.10 but the dumping continued and after much frustration it was suggested to me to try the beta version because they are still debugging it and may have some clue to what the problem is and the cause to the problem maybe would be fixed in the upgrade but now I see that it hasn't, which is why I said that I don't want to have to use Windows but will be forced to if there's no fix for the problem.

---

### Post by cariboo on 2009-10-19
Do you have the same problem when using Synaptic to install packages and update the archives?

You also may want to open a terminal and type:

```
sudo apt-get -f install
```

just to make sure there are no missing dependencies.

You also may want to have a look at the log files in /var/log to see if there is any indication why you are getting dropped to the login window.

---

### Post by Imoen on 2009-10-19
in user.log it says:

Oct 19 19:44:39 kristie-desktop bonobo-activation-server (kristie-2389): could not associate with desktop session: Failed to connect to socket /tmp/dbus-CRxTps1Z1m: Connection refused
Oct 19 19:54:44 kristie-desktop pulseaudio[1516]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error
Oct 19 20:07:43 kristie-desktop pulseaudio[1516]: reserve-wrap.c: Failed to acquire reservation lock on device 'Audio0': Input/output error

sudo apt-get -f install doesn't find anything missing

---

### Post by Imoen on 2009-10-19
in Synaptic anything I choose to install I get a message:

{SOMETHING}:
 Depends: {SOMETHING} but it is not going to be installed

{SOMETHING} = anything I have selected

---

### Post by VMC on 2009-10-19
> **Imoen said:**
> ... I was running 8.10 on my computer perfectly until my motherboard died. Then I had to start using a different computer and first I just put my hard drive in it and tried to just use it like that but I was having the same problem with the dumping back to the login screen which I figured was because my computer hardware was much older then the computer I'm using now. So then I installed a fresh copy of 8.10 but the dumping continued and after much frustration it was suggested to me to try the beta version because they are still debugging it and may have some clue to what the problem is and the cause to the problem maybe would be fixed in the upgrade but now I see that it hasn't, which is why I said that I don't want to have to use Windows but will be forced to if there's no fix for the problem.Part of the problem is that you tried to upgrade 8.10 from a hard drive that has a different computer. That will never work. Do a fresh install of karmic. 

Also give us some details of your new hardware - video, ram, cpu, anything else you can think of.

Output the following for starters:

```
sudo fdisk -l

sudo blkid
```

---

### Post by Imoen on 2009-10-19
I guess I didn't really say very well, when I was told to try the beta it was a complete new fresh install, not upgrade from 8.10.

My hardware is:
Processor: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
Motherboard: [Foxconn G31MV-K](http://www.foxconnchannel.com/product/Motherboards/detail_overview.aspx?id=en-us0000376)
RAM: 1024MB DDR2
Hard drive: WDC WD2000JD-22HBC0, 200 gig SATA300
DVD-RW Drive: HP  DVD Writer 640
CD-ROM: SAMSUNG CD-ROM  SC-148A
Video: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (onboard)
Monitor: ASUS VW198
Mouse/Keyboard: A4Tech RF USB Wireless


sudo fdisk -l
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05c405c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23952   192394408+  83  Linux
/dev/sda2           23953       24321     2963992+   5  Extended
/dev/sda5           23953       24321     2963961   82  Linux swap / Solaris

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd69c4e4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS


sudo blkid
/dev/sda1: UUID="13676ba0-178d-449c-93b4-04cee3def3ef" TYPE="ext4" 
/dev/sda5: UUID="097e7706-a7a4-49f4-95e2-25c56d7722c1" TYPE="swap" 
/dev/sdb1: UUID="B680752B8074F2EB" LABEL="The_Garage" TYPE="ntfs"

---

### Post by cariboo on 2009-10-20
Could paste the output of:

```
lspci
```

in yur next post, it is much more specific than the description you gave.

---

### Post by Imoen on 2009-10-20
Oct 20 00:21:22 kristie-desktop console-kit-daemon[852]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Oct 20 00:21:22 kristie-desktop console-kit-daemon[852]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Oct 20 00:21:22 kristie-desktop console-kit-daemon[852]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Oct 20 00:21:22 kristie-desktop gdm-simple-slave[4017]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 20 00:21:22 kristie-desktop acpid: client 2315[0:0] has disconnected

That's in the syslog file at the time of the most recent dumping.



kristie@kristie-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

---

### Post by Imoen on 2009-10-20
and again:
Oct 20 00:30:35 kristie-desktop bonobo-activation-server (kristie-4314): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Kbs6WJggM6: Connection refused
Oct 20 00:30:35 kristie-desktop gdm-simple-slave[4327]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Oct 20 00:30:35 kristie-desktop acpid: client 4018[0:0] has disconnected
Oct 20 00:30:35 kristie-desktop acpid: client connected from 4328[0:0]
Oct 20 00:30:39 kristie-desktop gnome-session[4367]: WARNING: Could not launch application 'polkit-gnome-authentication-agent-1.desktop': Unable to start application: Failed to execute child process "/usr/libexec/polkit-gnome-authentication-agent-1" (No such file or directory)

---

### Post by VMC on 2009-10-20
> **Imoen said:**
> Everything I try to install with the Software center I get:
The connection to the daemon was lost. Most likely the background daemon crashed.

I am constantly getting dumped to the login screen with no errors to give me a clue why. That happened when I was just running off the disk too but I figured that it might be because I was running off the disk.This is kind of contradictory. If you can install or try to install software you must be already logged on.

Or you get logged on and get dumped at unknown times. Check home dir and examine both ".xsession-errors" and ".xsession-errors.old" for any clues.

Also, the fact that it happens using a livecd is most likely hardware related - video driver perhaps.

---

### Post by Imoen on 2009-10-20
Yes, when I get dumped out it's just at random times. Then I log back in and have to re-open everything that I had been doing/using as if I just logged in the first time.

.xsessions-errors.old:
(gnome-settings-daemon:4444): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4444): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/kristie/.config/metacity/sessions/10810650d3e104bdc125601664995802700000044300001.ms: Failed to open file '/home/kristie/.config/metacity/sessions/10810650d3e104bdc125601664995802700000044300001.ms': No such file or directory

** (nautilus:4468): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4468): WARNING **: No marshaller for signature of signal 'DownloadFinished'
** (gnome-panel:4467): DEBUG: Adding applet 0.
** (gnome-panel:4467): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:4467): DEBUG: Adding applet 1.
** (gnome-panel:4467): DEBUG: Adding applet 2.
** (gnome-panel:4467): DEBUG: Adding applet 3.
** (gnome-panel:4467): DEBUG: Adding applet 4.
Initializing nautilus-gdu extension
** (gnome-panel:4467): DEBUG: Adding applet 5.
** (gnome-panel:4467): DEBUG: Adding applet 6.
** (gnome-panel:4467): DEBUG: Adding applet 7.
** (gnome-panel:4467): DEBUG: Adding applet 8.
** (gnome-panel:4467): DEBUG: Adding applet 9.
** (gnome-panel:4467): DEBUG: Adding applet 10.
gnome-system-log: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(nautilus:4468): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.27 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(nautilus:4468): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.28 of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts
firefox: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.


.xsessions-errors:
(gnome-settings-daemon:4822): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:4822): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/kristie/.config/metacity/sessions/10ef621a955cedd34125601806241223200000048080001.ms: Failed to open file '/home/kristie/.config/metacity/sessions/10ef621a955cedd34125601806241223200000048080001.ms': No such file or directory
** (gnome-panel:4845): DEBUG: Adding applet 0.
** (gnome-panel:4845): DEBUG: Initialized Panel Applet Signaler.

** (nautilus:4846): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:4846): WARNING **: No marshaller for signature of signal 'DownloadFinished'
** (gnome-panel:4845): DEBUG: Adding applet 1.
** (gnome-panel:4845): DEBUG: Adding applet 2.
** (gnome-panel:4845): DEBUG: Adding applet 3.
** (gnome-panel:4845): DEBUG: Adding applet 4.
** (gnome-panel:4845): DEBUG: Adding applet 5.
** (gnome-panel:4845): DEBUG: Adding applet 6.
Initializing nautilus-gdu extension
** (gnome-panel:4845): DEBUG: Adding applet 7.
** (gnome-panel:4845): DEBUG: Adding applet 8.
** (gnome-panel:4845): DEBUG: Adding applet 9.
** (gnome-panel:4845): DEBUG: Adding applet 10.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by VMC on 2009-10-20
Here's some discussion about that "GLib-CRITICAL **: g_propagate_error: assertion" errors you got.

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg301662.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg301662.html)

---

