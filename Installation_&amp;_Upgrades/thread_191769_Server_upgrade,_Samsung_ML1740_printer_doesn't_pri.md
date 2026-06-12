---
title: "Server upgrade, Samsung ML1740 printer doesn't print now"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by GrumpySmurf on 2006-06-07
Hopefully there's someone who enjoys CUPS and printers more than me out there*

I had a server install of Breezy on my home LAN server (host ipa) and upgraded to Dapper when it was released the other day. Now, I cannot print to my shared Samsung ML1740 printer. Here's the vitals:

The CUPS web interface via [http://ipa:631/printers](http://ipa:631/printers) shows the following:

```
samsung_ml1740 (Default Printer) "Printer not connected; will retry in 30 seconds..."
	Description: samsung_ml1740
Location: usb://Samsung-ML1740
Make and Model: Samsung ML-1740 Series (SPL II)
Printer State: processing, accepting jobs, published.
Device URI: usb://Samsung/ML-1740
```

I don't understand why it thinks the printer is not connected when the state is "processing, accepting jobs". Further, lshw shows:

```
*-usb:0
     description: USB Controller
     product: VT82xxxxx UHCI USB 1.1 Controller
<snip>
     *-usbhost
        product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        vendor: Linux 2.6.12-10-686 uhci_hcd
        physical id: 1
        bus info: usb@1
<snip>
      *-usb UNCLAIMED
           description: Printer
           product: Samsung ML-1740 Series
           vendor: Samsung Electronics Co., Ltd.
           physical id: 1
           bus info: usb@1:1
           version: 1.00
           serial: 2W61BAAX315562N0
           capabilities: usb-1.10 bidirectional
           configuration: maxpower=0mA speed=12.0MB/s

```
I have the Samsung drivers / stuff:

/etc/cups/ppd/samsung_ml1740.ppd
/usr/share/cups/model/ML-1740spl2.ppd

If I left out any details required to further troubleshoot this issue, let me know. I've scoured documentation and google searches but cant seem to find anything indicating the critical issue, that the CUPS web page says the printer is disconnected AND the state is "processing"

*I loathe printers. More than any other device or facility on any type of computer. I hates them more than Gollum hates hobbits.

---

### Post by Ivan Matveich on 2006-06-08
Run gnome-cups-manager. Remove your printer and then add it again. Maybe that will fix the problem...

---

### Post by GrumpySmurf on 2006-06-08
This is a server install. I don't have GNOME installed.

---

### Post by Ivan Matveich on 2006-06-08
I guess you could remove the cups packages, delete the configuration files, and then reinstall them and add the printer again... that's what I would try, anyway.

---

### Post by GrumpySmurf on 2006-06-10
Except this isn't Windows, where completely uninstalling something removes hidden registry settings and oftentimes fixes issues.

My main concern is why updating the package from the breezy version to the dapper version caused my printer to stop functioning properly. That is either a bug with the CUPS package, or with the dapper upgrade - nothing else changed on my system, other than what I've done to try to make it work again.

---

### Post by Ivan Matveich on 2006-06-11
Heh, well: Have fun debugging that horrible printing system...

---

### Post by GrumpySmurf on 2006-06-15
Well I think it's ironic... I actually wrote the 5.10 howto on setting up samsung printers here:

[http://www.ubuntuforums.org/showthread.php?t=160788](http://www.ubuntuforums.org/showthread.php?t=160788)

And yet now I can't get the printer to function. lpinfo -v shows:
```

lpinfo -v
direct hp:/no_device_found

```
Perhaps its time to open a bug in launchpad...

---

### Post by GrumpySmurf on 2006-06-15
Bug report #49802 opened:

[https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/49802](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/49802)

---

