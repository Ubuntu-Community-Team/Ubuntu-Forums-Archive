---
title: "brother printer installing/uninstalling - ubuntu newbie (big time)"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by fastpaddy on 2010-12-21
Hi

I followed the directions from the brother website and succesfully installed my brother 150c printer. Along the way I managed to install a 1000c printer too. So I deleted it from the printer list like you do in windows. I then started getting errors when trying to install other upgrades/software. the long and the short of it is. I deleted the 150c printer too. I tried to reinstall with a deb package but still did not see the printer. this is the error I now have:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dests_available': [('PDF', None)], 'cups_queue_listed': False}
Page 4 (Local or remote?):
{'printer_is_remote': False}
Page 5 (Choose device):
{'cups_device_attributes': {'device-class': u'direct',
                            'device-id': u'MFG:Brother;CMD:HBP,BRPJL;MDLCP-150C;CLSRINTER;',
                            'device-info': u'Brother DCP-150C',
                            'device-location': u'',
                            'device-make-and-model': u'Brother DCP-150C'},
 'cups_device_listed': True,
 'cups_device_uri': 'usb://Brother/DCP-150C'}
Page 6 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_NZ',
 'user_locale_messages': 'en_NZ'}

Hope someone can help. I'm learning as I go, but this one I have not been able to resolve

---

