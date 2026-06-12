---
title: "hard drive boot help required"
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by skippylou on 2016-09-11
Three HDs totally screwed up.  Don't ask how, I could never explain.  Tried installing ububtu 16.04LTS all went fine until the end telling be that boot was damaged.  Went tp [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and followed instructions without success.  Here is the pastebin link:

[http://paste2.org/XH1XcPbV](http://paste2.org/XH1XcPbV)

Let me know what other info you need.

Hope I am in the right place.

Thanks

---

### Post by Bucky Ball on 2016-09-11
```
Please do not forget to make your BIOS boot on sdb (60.0GB) disk!
```

This is at the end of your boot repair output. I'd suggest you boot to the BIOS and make sure it is set to boot from the correct drive.

Odd thing is, looks like the system has decided that your drives are sdb and sdc with your boot repair USB being sda! This is going to cause some confusion and never seen it before. No idea how or why that has happened. Systems like the first drive to be sda and when they're not ...

Also, have no idea what the sdb5 partition is. This is a dual-boot Ubuntu machine with Sabyon. I have no idea about how Sabyon works so no idea whether that plays any part in this.

---

