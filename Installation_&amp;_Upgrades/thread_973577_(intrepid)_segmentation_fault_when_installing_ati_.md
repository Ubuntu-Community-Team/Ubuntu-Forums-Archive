---
title: "(intrepid) segmentation fault when installing ati catalyst 8.10 in intrepid"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by raj9786 on 2008-11-06
I tried to do a search on this topic but to no avail. So I hvae a dell 8600 with an ATI Radeon Mobility 9600 Pro Trubo. I tried a fresh install of intrepid and now im trying to up my 3D acceleration. I tried the method of installing the 8.10 catalyst drivers shown here: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide) . However, when I try the command "sudo aticonfig --initial -f " i get the result: "segmentation fault." I'm kind of new to this so I don't know what to do. I have read the the 9600 card is not supported by the new 8.10 catalyst but, in those same threads, I have seen people say they have a 9600 card and got it to work. Any help is appreciated. Thank you!

---

### Post by tikey on 2008-11-08
I have the same problem. I installed the ati drivers from their homepage and running aticonfig --initial -f gives me a segmentation fault. Running fglrxinfo gives me
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Does anyone have an idea?

---

### Post by sub_acoustic on 2008-11-09
I have the same problem.  But some people have their ati cards working fine under 8.10 so there is, thankfully, a solution somewhere out there.

---

### Post by brenzosa on 2008-11-17
exactly same problem on my machine - Dell Inspiron 6400 with r5xx (Mobility Radeon X1400) -- segmentation fault when doing the aticonfig part, also tried the new 8.11 Catalyst driver, but same problem there

---

### Post by dvinnen on 2008-11-18
I got the same problem.  Trying to get this running on an older Compaq nc6000 with a Mobility 9600.  It looks like everything is going good with the install but when I run "aticonfig --initial -f" I get a "Segmentation fault" error message.

Any ideas?

---

### Post by dvinnen on 2008-11-18
Looks like this bug report has a lot to do with it:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)


I don't get why the driver supplied by ATi isn't working.  When you choose a Mobility 9700/9600 driver you get an up-to-date version (8.11 released Nov. 12, 2008 ) so they haven't dropped support for it yet.

Any ideas?

---

### Post by dvinnen on 2008-11-18
Never could figure anything out.  Ended up deleting all the ati drivers and using the open source ones.  Not happy with the performance of the desktop with them but they'll due till a fix is found I guess.

---

### Post by FlyinRedneck on 2008-11-18
Same problem here, All I have is ATI to work with, I am hoping for a speedy fix. Is there a way to use the TV-Out though?

---

### Post by raj9786 on 2008-12-01
Has anyone firgured this out yet? It seems like a relatively prevalent problem.

---

### Post by sub_acoustic on 2008-12-23
After searching down many avenues I did what I should have tried first. A fresh install of Intrepid solved EVERYTHING.  Ubuntu how could I ever have doubted you!  My advice, do a fresh install don't upgrade.

---

### Post by tikey on 2008-12-25
I did a fresh install in the first place and the problem occured nevertheless. I did a new install and still had the problem, so I did another reinstall and I haven't touched the graphic driver since. Unfortunately I still can't use my second monitor...

---

### Post by kestal on 2008-12-25
> **tikey said:**
> I did a fresh install in the first place and the problem occured nevertheless. I did a new install and still had the problem, so I did another reinstall and I haven't touched the graphic driver since. Unfortunately I still can't use my second monitor...

I am in the same boat as you.

---

### Post by ubuntoyou2 on 2009-01-21
I've the same segmentation problem. 

I believe the new Catalyst drivers are out soon. There seems to be great hope riding on these.  Gamers are salivating over them. The new release will be version 9.1. Delayed due to christmas and out  between now and the end of the month. Usually ATI release the drivers on a wednesday.  Here's hopin'

---

### Post by crc294 on 2009-01-21
Same problem here. I also have an Inspiron 8600 with Mobility Radeon 9600. The ATI drivers used to work on Hardy, but when I upgraded to Intrepid, I encountered this issue. Tried a fresh install, didn't work, so I'm stuck using the open source. Performance does suffer a lot. 

Maybe the new drivers will fix the problem, or maybe we'll see a fix on the Ubuntu side with Jaunty. But thats so far away ...

---

### Post by ubuntoyou2 on 2009-01-29
Good news at last - hopefully. Catalyst 9.1 is out, and this is from the release notes. Download link not working at the moment - could this be the legions of frustrated gamers trying to dl it?

[COLOR="Blue"]Support for New Linux Operating Systems
         This release of ATI CatalystTM Linux introduces support for the following new operating system:
         • Ubuntu 8.10 production support
[/COLOR]

Could this be the end of the seg ment ation problem?

---

### Post by tikey on 2009-01-30
So has anyone tried this already? If so, could someone tell us if it works.
I would especially be interested if the new driver supports a second screen. I have a laptop with an external monitor and so far I never got it to run properly with kubuntu 8.10.

Thanks

---

### Post by ubuntoyou2 on 2009-01-30
I was up till 4am trying to configure it. I no longer have a segmentation fault, just 

[COLOR="Navy"]EE) No devices detected.

Fatal server error:
no screens foun[/COLOR]d

Come back segmentation fault. All is forgiven :-)

As to dual monitors they mention fixes in the release notes

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_91_linux.pdf]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_91_linux.pdf")

---

### Post by tikey on 2009-02-05
Same Problem here. Does anyone know how to get rid of the catalyst again? I tried dpkg-reconfigure but that didn't help at all. I can't start X anymore which is pretty anoying. I'll probably give up on ati. Next laptop will have another graphic card. This costs me way too much nerves!

---

### Post by ubuntoyou2 on 2009-02-08
Hi,

If you created .deb packages and installed them then you need this

sudo dpkg -r <package name>

You'd have created quite a few. Good luck with that!

If you used the ATI installer method then try this (from the installation instructions) to uninstall it.


          1 Launch the Terminal Application/Window and navigate to the /usr/share/ati folder
          2 With superuser permissions, enter the command:
"sh ./fglrx-uninstall.sh"
          You have now successfully uninstalled the ATI Linux Proprietary Driver.

I suppose it won't be long till Catalyst 9.2 is out.  Dare we hope?

---

### Post by tikey on 2009-02-09
Thanks!
The second worked and I now have a working system again.
Now that I know, that it is easy to install and uninstall the driver, I might try 9.2 but I actually don't have much hope that the driver will work (and I'm not talking about a second monitor or any other 'fancy' stuff).

---

### Post by ubuntoyou2 on 2009-02-20
Glad that worked out.

9.2 is out. I haven't tried it; used up my dl allowance so have to wait a few days.  Hopefully this'll do the trick.  I mean; they have to get it right sooner or later  :0

---

### Post by ubuntoyou2 on 2009-02-22
OMG!!!  It worked.  9.2 worked. Finally,after all those drivers, 8.10, 8.11 and 8.12 for which I'd such high hopes for a merry graphic xorg xmas!!! Then 9.1 failed too. So with trepidation it was onto 9.2.  And it works. No staying up till all hours trying to get the thing to work. No seg men tat ion or device not found. Not a single problem. 

Anyway, joy of joys.  I used this method 

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

I created more packages than the guide does but installed them all anyway.

9.2 it's the one for you all you frustrated mobiltiy radeon 9600 users.  It does the business.

:D  :p :)

---

### Post by tikey on 2009-03-04
I installed the 9.2 yesterday but unfortunately nothing works no. That is, I can't even get the system back.

The following happened:
- I installed the catalyst 9.2 driver (download from the ati website, creating the packages, installing the packages, running aticonfig --initial -f)
- after that I rebooted and both monitors were showing the same picture with the same resolution (which looks weird as my laptop has a 4:3 display and the external monitor is 16:10).
- so I tried aticonfig --initial=dual-head -f and after that everything was broken. The system starts, but when there should be the login screen. I can't see anything anymore. Sometimes it shows a black screen, sometimes some pink stripes. Booting without the external monitor doesn't help, either. 
- Normally, when this happened, I used Ctrl+Alt+F1 to switch to terminal mode and fixed the problem there. But this doesn't work. When I try to switch, the display doesn't change.
- I then booted with the live-dvd, mounted my harddrive and edited the xorg.conf. Unfortunately this didn't change anything.

So I now can't use my computer at all. If anyone has any idea what I can do, I would be very happy if you let me know!!!

Sorry for the long post
   Thomas

---

