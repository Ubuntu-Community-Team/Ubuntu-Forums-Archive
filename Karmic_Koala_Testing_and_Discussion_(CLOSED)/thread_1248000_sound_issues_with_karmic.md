---
title: "sound issues with karmic"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ki4jgt on 2009-08-23
Karmic doesn't recognize that I have speakers. The sound program simply reads internal audio but not speaker recognition is available.

---

### Post by ki4jgt on 2009-08-23
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

---

### Post by bluesscream on 2009-08-23
had some sound issues this morning too. Is your system fully upgraded?
I clicked around on the panel speaker control icon, right click opened some for me unknown (pulse?) control stuff, I set the alert slider to max and back to medium and after some reboots everything worked fine.
Think developers made some scanning for devices and their properties which need some time to save config files on hd.

---

### Post by kansasnoob on 2009-08-23
I was able to get my sound working using 'gnome-alsamixer' (available in synaptic), but it's still not quite right.

Some of the toggles cause others to move and I get random mutes, but gnome-alsamixer (which shows up in Sound & Video) makes it fairly easy to deal with.

Just remember this is an Alpha 4. It's very unstable because it's still under construction. Think of it as a "hard hats required" area:)

---

### Post by psyke83 on 2009-08-23
Install and run "pavucontrol" (PulseAudio Volume Control), then check the setting on the Configuration tab to ensure that your speakers are setup correctly.

---

