---
title: "downgrade to 10.10 from early upgrade 11.04"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by BrittanF on 2011-02-25
I recently installed the early upgrade from Ubuntu 10.10 to 11.04. For some reason my system didn't fully install the full upgrade. I can't run anything unless I start it in worksafe low graphics version. I tried several times to complete the download or install updates but with no success.

 I'm wondering if there's a way to downgrade back to 10.10. I tried downloading the version off the ubuntu site but my new os doesn't seem to have file browser. Any folder I open automatically opens in archive manager so I can't burn to disk or move to a usb.

Is there perhaps a way to just run install for 10.10 directly from the download. I don't need to save any of my current files so that's not a major concern. I just want a fully functional os again. 11.04 is still too buggy.

---

### Post by zvacet on 2011-02-25
To complete upgrade di you tried

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

sudo apt-get -f install
sudo dpkg --configure -a
```

If nothing of above works tray to open Brasero( it is under sound & video) and then select iso for burning.

---

### Post by Kiean on 2011-02-25
Most Linux magazines come with a ubuntu live cd I think that's prObaly the best way to downgrade

---

### Post by Frogs Hair on 2011-02-25
A downgrade is not possible , you can complete the upgrade or reinstall.

---

### Post by yungballla6 on 2011-04-23
hi. I installed ubuntu 11.04 beta 2 and I messed around with compiz and now I can barely do anything without the screen becomming frozen or not being able to exit any app. I was wondering if its possibleto fix this. 

Thank you

---

### Post by Nickname1 on 2011-04-28
I have the same problem but before i login if i chose "ubuntu classic" it works just fine. I too am wondering if there is a way to fix this problem.

---

### Post by Scorp_X on 2011-05-01
> **Frogs Hair said:**
> A downgrade is not possible , you can complete the upgrade or reinstall.

I have the same problem, I reinstalled version 11.04 from the cd, but the problem is not fixed... I will reinstall 10.10....

---

### Post by mk169474 on 2011-05-02
When Ubuntu (Unity) loads I get a message 'unable to detect system tray'.Also played with compiz config. I see only my wallpaper, Alt+F2 doesn't work, no dash, no panels. Rigth mouse click works fine, F1 button opens help and all I get from Unity so far. Ubuntu Classic works fine so far. Any ideas? 
tnx

---

### Post by mk169474 on 2011-05-02
Added CCSM shortcut on desktop while in Ubuntu Classic version, then started CCSM in Ubuntu Unity and turned Ubuntu Unity Plugin on.

---

### Post by treerink on 2011-06-09
I successfully downgraded from 11.04 to 10.10. All files and settings were unaffected, but those packages installed extra with the Synaptic Package Manager and with Ubuntu Software Center, you have to install again. But I must say it works even better then before. Really happy with 10.10 again. Also under Ubuntu Classic (you can chose at user-login) 11.04 was quite unstable. 

See this instruction:
  [http://www.youtube.com/watch?v=QGnsYuWS0xY&feature=related](http://www.youtube.com/watch?v=QGnsYuWS0xY&feature=related)
And take care (as mentioned in the instruction) that the username and the machine name are equal to before (saves troubles later) 
After the restart take the   2.6.35-28-generic-pae  option in the boot menu instead of the  2.6.38-8-generic-pae (which probably is the default on top of the boot list). In the other distributions all kind of things like sound and wireless don't work)

To make this   2.6.35-28-generic-pae    the default, the easiest way is first to install the startupmanager by:
  System -> Administartion -> Synaptic Package Manager ->  search: startupmanager -> apply
and then adjust the default distribution to boot by:
  System -> Administartion -> StartUp-Manager -> ..wait a bit... ( -> Boot options ) --> Default operating system -> chose from the drop-down menu: 'Ubuntu, with Linux 2.6.35-28-generic-pae'
If you have a duo-boot with windows7, you can here chose  windows7 as the default as well of course.
(keywords: ubuntu 10.10 boot order edit,  see [http://www.hackourlife.com/change-default-boot-order-for-grub-in-ubuntu-10-10-maverick-meerkat/](http://www.hackourlife.com/change-default-boot-order-for-grub-in-ubuntu-10-10-maverick-meerkat/))

---

