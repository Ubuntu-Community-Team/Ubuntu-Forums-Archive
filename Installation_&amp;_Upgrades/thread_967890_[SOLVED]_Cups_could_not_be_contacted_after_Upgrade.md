---
title: "[SOLVED] Cups could not be contacted after Upgrade to 8.10."
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by jgkellt001 on 2008-11-02
Having upgraded to 8.10 my printer (Brother MFC-215 C) no longer works. It appears that CUPS is no longer recognised, even though it's definitely installed. (I've unistalled and reinstalled cups.)  Although I've used Linux for the last 2 years I'm no expert and I appear to be stuck. Like everyone else I need my printer and I don't want to have to go back to the MS environment just to print!. This has got to be an upgrade bug as everything was fine before the upgrade.

Thanks in advance to you who can help.

JGK Essex UK.

Solved by Loading Ubuntu and ditching Xubuntu.

---

### Post by coalcracker on 2008-11-02
> **jgkellt001 said:**
> Having upgraded to 8.10 my printer (Brother MFC-215 C) no longer works. It appears that CUPS is no longer recognised, even though it's definitely installed. (I've unistalled and reinstalled cups.)  Although I've used Linux for the last 2 years I'm no expert and I appear to be stuck. Like everyone else I need my printer and I don't want to have to go back to the MS environment just to print!. This has got to be an upgrade bug as everything was fine before the upgrade.

Thanks in advance to you who can help.

JGK Essex UK.

I have the same problem after updgrading to 8.10

---

### Post by jernejk on 2008-11-02
I also had issues with cups - there were errors regarding cups during upgrade. Luckily I had backup of entire system, so I'm back to Hardy.

---

### Post by jgkellt001 on 2008-11-02
> **jernejk said:**
> I also had issues with cups - there were errors regarding cups during upgrade. Luckily I had backup of entire system, so I'm back to Hardy.

Unfortunately I didn't think I'd need to back up. So i still have the printing problem1 All suggestions are welcome.

---

### Post by Marc Higgins on 2008-11-03
Same here. i have posted a bug Bug #289759:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/289759](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/289759)

can i suggest you also post to this same bug report (if you have the same bug)

Im my case our kyocera km3232e running ppd 8.2 longer works after upgrading to Ubuntu 8.10 intrepid, It prints blank pages & displays error. It is the same with a new install running ppd 8.4

diagnostics are below but I think this line is important 'printer-state-message': u'/usr/lib/cups/filter/pstopdf failed',

Linux dell640m 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux. Cups version 1.3.9-2,

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Kyocera-KM3232e (default)>,
 'cups_instance': None,
 'cups_queue': 'Kyocera-KM3232e',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'socket',
 'cups_printer_dict': {'device-uri': u'socket://10.0.0.53:9100',
                       'printer-info': u'Kyocera-KM3232e',
                       'printer-is-shared': True,
                       'printer-location': u'dell640m',
                       'printer-make-and-model': u'Kyocera KM-C3232',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/pstopdf failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 176220,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Kyocera-KM3232e'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'CIE': u'PrnDef',
                                            u'ColorModel': u'CMYK',
                                            u'Colorreprod': u'Auto1',
                                            u'Duplex': u'DuplexNoTumble',
                                            u'InputSlot': u'PF700A',
                                            u'Jog': u'None',
                                            u'KCBooklet': u'None',
                                            u'KCCollate': u'PrnDef',
                                            u'KCContone': u'False',
                                            u'KCFold': u'None',
                                            u'KCPunch': u'None',
                                            u'KCRotate': u'None',
                                            u'KCStaple': u'None',
                                            u'KCSuperWatermark': u'None',
                                            u'KCVersion': u'Default',
                                            u'KmManagment': u'Default',
                                            u'MediaType': u'PrnDef',
                                            u'OutputBin': u'None',
                                            u'PagePolicy': u'On',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Rotate': u'False',
                                            u'StapleCount': u'None'},
                               u'InstallableOptions': {u'InstalledMemory': u'1024MB',
                                                       u'Option17': u'DF710',
                                                       u'Option18': u'HardDisk',
                                                       u'Option19': u'One',
                                                       u'Option21': u'False',
                                                       u'Option22': u'True',
                                                       u'Option25': u'False',
                                                       u'Option26': u'True'},
                               u'JCL': {u'JCLBlueLevel': u'None',
                                        u'JCLEconomode': u'Off',
                                        u'JCLGreenLevel': u'None',
                                        u'JCLHalftone': u'Gradation',
                                        u'JCLHueBlue': u'None',
                                        u'JCLHueCyan': u'None',
                                        u'JCLHueGreen': u'None',
                                        u'JCLHueMagenta': u'None',
                                        u'JCLHueMaster': u'None',
                                        u'JCLHueRed': u'None',
                                        u'JCLHueYellow': u'None',
                                        u'JCLLightnessContrast': u'None',
                                        u'JCLLightnessGamma': u'None',
                                        u'JCLRedLevel': u'None',
                                        u'JCLSaturation': u'None'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/pstopdf failed',
 'printer-state-reasons': [u'none']}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 313223L}
Page 8 (Print test page):
{'test_page_job_status': [(False,
                           505,
                           'Kyocera-KM3232e',
                           'Test Page',
                           'Stopped',
                           None),
                          (False,
                           506,
                           'Kyocera-KM3232e',
                           'Test Page',
                           'Stopped',
                           None)],
 'test_page_successful': True}

---

### Post by kiriath-arba on 2008-11-03
I am experiencing exactly the same problem with CUPS and my Brother MFC-215C printer after having upgraded to Ubuntu 8.10 Intrepid.   Also did not think to back up 8.04 Hardy!

---

### Post by feng85jie on 2008-11-03
[Air Filter](http://www.chinafengjie.com/air-filter/)Ruian Fengjie Auto parts manufacture CO.,LTD is a company specilized in Filter and Filter components service.

---

### Post by garry4o on 2008-11-08
Same problem with my Brother HL2070N network printer after upgrade from Hardy. I'm also having trouble finding anything about network connections, although there must be one somewhere, as firefox works fine.

---

### Post by d4nnyt on 2008-11-09
I think I'm having the same problem too with my Brother DCP-120c after upgrading to Intrepid. I have tried reinstalling cups and like others in this thread it didn't solve the problem.

I don't want to ditch xubuntu to solve the problem :(.

Danny.

---

### Post by d4nnyt on 2008-11-22
I half solved the problem I had by terminal;

sudo /etc/init.d/cups.dpkg-new restart

---

### Post by rickdog on 2008-12-02
I just upgraded to 8.10 on one of my computers and ran into this problem. I've checked a whole slew of forum posts and googled it, but fail to see how any of the [solved] ones actually *solve* this problem.

Now d4nnyt's half-solution (sudo /etc/init.d/cups.dpkg-new restart) is the only thing that's half-worked for me. Does anyone know how to make this stick? I shouldn't have to do this every time I boot.

---

### Post by cariboo on 2008-12-02
Can any of you that are having this problem access  the cups web page on your computer? To do this in the address bar of your favorite web browser type:

```
http://localhost:631
```

If you can't, it means that cups is not running, to start cups, in a terminal type:

```
sudo /etc/init.d/cups restart 
```

The above poster that used dpkg in the command, I don't know where you came up with that command, but it shouldn't work as there is no cups.dpkg-new in that particular directory. When I try to run the command, this is what I get:

```
sudo /etc/init.d/cups.dpkg-new restart
[sudo] password for jim: 
sudo: /etc/init.d/cups.dpkg-new: command not found
```

Jim

---

### Post by rickdog on 2008-12-04
well, interestingly enough, this is what i have to go through:

(this is of course after localhost:631 is not found upon a fresh reboot)

```
rick@laptop1:~$ sudo /etc/init.d/cups restart
[sudo] password for rick:
sudo: /etc/init.d/cups: command not found
rick@laptop1:~$ sudo /etc/init.d/cups.dpkg-new restart
 * Restarting Common Unix Printing System: cupsd
[ OK ]
rick@laptop1:~$
```

pretty strange huh? maybe when i upgraded, the cups package was never properly installed?

anyone?

---

### Post by d4nnyt on 2008-12-14
I ran into that same thing "command not found".

I solved it by opening the folder /etc/init.d/ in thunar and deleting the broken 'cups' link. (I found that the icon which said 'cups' had an x next to it, this is what I deleted).

I then reinstalled cups and cups worked properly, however I still cannot get my printer to work.

Hope this helps.

---

