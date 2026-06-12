---
title: "How is mobile broadband working for you?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autark on 2010-03-31
As the Lucid Lynx release is getting nearer, I'm getting increasingly worried that it's not going to work for me. The reason is that my Huawei 3G USB modem is not working satisfactorily with Lynx, although it works splendidly with Jaunty:


[LIST]
[*]In Lynx, I usually have to make multiple connection attempts before getting a connection. Most often I have to replug the modem if I was foolish enough to have it inserted from boot.
[*]After resume from suspend, I also have to make multiple connection attempts until successful, whereas in Jaunty the reconnection is automatic.
[/LIST]
I should say I'm using Network Manager to manage my mobile broadband. I am not willing to go back to vwdial or other manual solutions.

I have written a few bug reports that so far have received very little attention, so I'm not very optimistic. But maybe I'm just being unlucky, and everybody else is happy with their mobile broadband on Lynx. Please tell me this is so. In that case I'll just stick with Jaunty. Otherwise, I think there is cause for concern, as there has been a lot of grief for Huawei users on Karmic.

---

### Post by jepong on 2010-03-31
I have a Huawei E1550 and it works... after installing usb-modeswitch

---

### Post by autark on 2010-03-31
> **jepong said:**
> I have a Huawei E1550 and it works... after installing usb-modeswitch
Mine is an E169, by the way. I installed usb-modeswitch once, but it didn't improve things so I uninstalled it.

---

### Post by xfalcox on 2010-03-31
It´s GREAT!
 
I use ZTE MF626, let it plugged, boot, and when I get a desktop i'm already connected! EVER!
 
 
Just changed the auto-mount as mass-storage-device via TELNET, so i don't need the usb-modeswitch thing, and it works fast and automatic...

---

### Post by moviemaniac on 2010-03-31
I also have an E169 and although I rarely use it I have no problems getting it to work. I know it was a PITA in Karmic but Lucid works fine.
However you should not boot with the thing plugged into your computer, but it's the same on Windows machines, too...

---

### Post by autark on 2010-03-31
> **xfalcox said:**
> 
Just changed the auto-mount as mass-storage-device via TELNET, so i don't need the usb-modeswitch thing, and it works fast and automatic...
How would I do that?

---

### Post by xfalcox on 2010-03-31
> **autark said:**
> How would I do that?

Can't tell :(



J/K


[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)

Tested on MF 626 and Onda msa501hs.

Look for the telnet command for you modem in the manual... :popcorn:

---

### Post by autark on 2010-04-02
> **moviemaniac said:**
> 
However you should not boot with the thing plugged into your computer, but it's the same on Windows machines, too...
Nevertheless, the same modem works without a flaw on the same machine with Jaunty, even if inserted from boot. I see no reason to accept this kind of regression.

---

### Post by drucer on 2010-04-02
> **autark said:**
> As the Lucid Lynx release is getting nearer, I'm getting increasingly worried that it's not going to work for me. The reason is that my Huawei 3G USB modem is not working satisfactorily with Lynx, although it works splendidly with Jaunty:


[LIST]
[*]In Lynx, I usually have to make multiple connection attempts before getting a connection. Most often I have to replug the modem if I was foolish enough to have it inserted from boot.
[*]After resume from suspend, I also have to make multiple connection attempts until successful, whereas in Jaunty the reconnection is automatic.
[/LIST]
I should say I'm using Network Manager to manage my mobile broadband. I am not willing to go back to vwdial or other manual solutions.

I have written a few bug reports that so far have received very little attention, so I'm not very optimistic. But maybe I'm just being unlucky, and everybody else is happy with their mobile broadband on Lynx. Please tell me this is so. In that case I'll just stick with Jaunty. Otherwise, I think there is cause for concern, as there has been a lot of grief for Huawei users on Karmic.

My Option Icon 225 USB 3G HSDPA modem worked flawlessly with Ubuntu 9.10, but with 10.04 beta I am having similar issues you described. It is set as "connect automatically", but when it is establishing a connection it takes way, way longer than it did with Ubuntu 9.10. Also, I am experiencing random connection losses. Sometimes after it has connected it cuts the conection suddenly for no reason. Sometimes it is unable to connect after a fresh boot and I have to manually retry and then it is able to connect.

So - something has changed radically - worked 100% flawlessly in 9.10, but 10.04 is having major issues!

---

### Post by pdc on 2010-04-06
I downloaded the latest release of lucid lynx; to see how it would be with some usb modems:

Vodafone 3765-Z; recognised in usb_modeswitch as 

> ZTE K3565
#

;DefaultVendor=  0x19d2
;DefaultProduct= 0x2000

;TargetVendor=   0x19d2
;TargetProduct=  0x0063


I was pleasantly surprised in an initial lsusb that 10.04 had already "flipped" the device; (by what means I do not know); this is a ZTE device;
so all I needed to do was configure to vodafone; and press connect and I had a good connection;

Huawei E220; this again just needed connection; (from the already registered configuration);

ZTE MF636; I have needed wvdial as none of the current distros I have tried will work; my problem is I set up a configuration; and network manager does not list the selection I have made; even though I go back in and check it is there; (and I have flipped the modem to 0031 from 2000)

 ......... here again ..... lucid lynx does not acknowledge in network manager that I have made this selection ..

..... I am encouraged that the Vodafone 3565-Z will work well; previously only fedora 12 had that easy distinction for that modem;

---

