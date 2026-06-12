---
title: "After upgrade to 10 from 9.x Wireless fails"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by ESimard on 2010-11-20
Hi, I upgraded from 9.x to 10.10.  Under 9.x my wireless usb dongle worked correctly.  After upgrade it does not.  I checked the dongle on another machine and it works correctly.  I inserted a usb memory stick and the system found it as a drive correctly.  I assume from this that both the dongle and usb port are ok.  The wireless device is a D-Link G122 A2 which is on the supported list (it ran out of the box on 9.x).  The link light does not come on so I am assuming that the process to identify it as a wireless device is not running.  If this is correct how do I proceed from here?  What other steps need be taken?

Thanks in advance
_Ernie

---

### Post by ESimard on 2010-11-21
Forgot to note that lsusb does show the wireless device correctly so the system knows it there.
_Ernie

---

### Post by mörgæs on 2010-11-21
This forum might help you better:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by ESimard on 2010-11-22
Hi, all

I will try the other form if the following doesn't yield any info.

Even though I didn't need it in ubuntu 8x or 9x, I tried installing ndiswrapper and adding the windows driver for the D-Ling G122 Rev A2.  Now I get several wireless locations, so that part is working.  However I cannot complete a connection.  The passwords and other configurations worked previously and I did reenter them just in case but still no connect.  

The logfile shows the following on each insertion of the dongle:

Nov 21 15:28:35 ernie-desktop kernel: [ 3183.428644] ndiswrapper (iw_set_auth:1602): invalid cmd 12

Nov 21 15:28:35 ernie-desktop kernel: [ 3183.428729] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)

Nov 21 15:28:46 ernie-desktop kernel: [ 3194.727522] ndiswrapper (set_iw_auth_mode:601): setting auth mode to 7 failed (C0010015)

Any clue as to what the error mean? 

ernie@ernie-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"2WIRE183"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:25:3C:17:4A:29   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

Thanks Ernie

---

