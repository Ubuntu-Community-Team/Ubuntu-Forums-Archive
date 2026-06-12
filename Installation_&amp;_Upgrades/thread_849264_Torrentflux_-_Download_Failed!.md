---
title: "Torrentflux - Download Failed!"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by invader7 on 2008-07-04
I have installed the newest php,python,apache2,mysql with 100% success.
I installed then torrentflux 2.4...

the only problem is this... after some hours 2 or 5 maybe... torrents die and say Download Failed! with a blue arrow (like seeding)

please help me, what i can do ?? it is very annoying

my apache error log...

```
Traceback (most recent call last):
  File "/var/www/apache2-default/TF_BitTornado/btphptornado.py", line 453, in ?
    run(argv[1],argv[2],argv[3],argv[4],argv[5:])
  File "/var/www/apache2-default/TF_BitTornado/btphptornado.py", line 404, in run
    if not dow.initFiles(old_style = True): 
  File "/var/www/apache2-default/TF_BitTornado/BitTornado/download_bt1.py", line 550, in initFiles
    return self.storagewrapper.old_style_init()
  File "/var/www/apache2-default/TF_BitTornado/BitTornado/BT1/StorageWrapper.py", line 153, in old_style_init
    self.statusfunc(fractionDone = x)
  File "/var/www/apache2-default/TF_BitTornado/btphptornado.py", line 171, in display
    self.writeStatus()
  File "/var/www/apache2-default/TF_BitTornado/btphptornado.py", line 280, in writeStatus
    raise KeyboardInterrupt
KeyboardInterrupt
```

---

### Post by moetes on 2010-12-22
I'm having the same issue, but it do not seems to be related with these errors that appears at apache's error logs. So do not match date, time and times.

---

