---
title: "HP scanner, prints but doesn't scan?"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by DaveMoss on 2010-09-21
I have just installed ubuntu 10.04, and now trying to get all the hardware working.  The HP PSC2170 printer scanner will print, but nothing happens when I try to scan.  below are the results of attempting to debug the problem:

  root@david-desktop:/home/david# [COLOR=#ff0000]scanimage --list-devices [/COLOR] 
 device `hpaio:/usb/PSC_2170_Series?serial=MY343C66GP73' is a Hewlett-Packard PSC_2170_Series all-in-one  
 
    root@david-desktop:/home/david# [COLOR=#800000]scanimage --test -d 'hpaio:/usb/PSC_2170_series?serial+MY343C66GP73' [/COLOR] 
 scanimage: open of device hpaio:/usb/PSC_2170_series?serial+MY343C66GP73 failed: Error during device I/O 

 root@david-desktop:/home/david# [COLOR=#ff0000]sane-find-scanner 
[/COLOR]
    found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x2b11 [PSC 2170 Series]) at[COLOR=#ff0000] libusb:[/COLOR]002:002 



In using Simple Scan, I get a error FAILED TO SCAN, Unable to connect to scanner, but Document -> Preferences lists the device as being there.


Device Manager -> USB OHCE Controller -> hub -> Device lists the device.


Config Editor -> Apps -> Simple Scan -> selected Device lists HP device.


I have somehow overlooked something, but from what I can research, I am not sure of what 


Any and all help will be appreciated.  Thanks in Advance!


Dave

---

### Post by copperhead on 2011-01-14
Did you ever get an answer to your problem?  I'm having the same issue.

---

### Post by rdh61 on 2011-04-15
I've been having this issue too, but only since 2 weeks. Before that it worked normally.

---

