---
title: "Mouse issue on VMware guest os on ubuntu 9.10 host"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by sharathke on 2009-11-26
Hi,

I have a weird problem after I upgraded my Ubuntu 9.04 to 9.10. I had VMWare server 2.0.1 working fine fine on Ubuntu 9.04. After the upgrade it stopped working & I had to follow the instructions in [http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html) to get it working. But now the mouse is behaving weirdly, inside guest OS (Windows XP Professional, Service pack 3) mouse clicks work only on a small portion of the screen, ie top left half of the screen. If I do multiple clicks (right,middle,left) on other parts of the screen sometimes it works. 

Any suggestions? I have even upgraded VMware server to 2.0.2. Still facing same issue.

Thanks in advance,
Sharath

---

### Post by DCorso on 2009-12-08
I'm having the same issue.  Any solution?

---

### Post by hurrells on 2009-12-17
Hello.

I am (was having) having these types of problems too.
I have a fresh Ubuntu KK 9.10 host with new VMware Server 2.0.2 with patches.
Running an XP guest that was a fresh build on a Vista host with VMServer 2.0.1

1. I can only click in the upper-left portion of the screen.
Reducing to 1024x768 screen size has no effect

2. I adjusted my mouse setup in the .vmx file per:
[http://communities.vmware.com/message/1309964;jsessionid=38B6773F3F3726A98C75DC71EEE0129F](http://communities.vmware.com/message/1309964;jsessionid=38B6773F3F3726A98C75DC71EEE0129F)

usb:0.deviceType = "mouse"
usb:0.present = "FALSE"
mouse.vusb.enable = "FALSE" <-- this was the only line I was missing.

It seems to have helped a bit to add the above last line.

Like I say, you can click on things only in the upper-left corner. Weird.


Cheers
STephen

---

