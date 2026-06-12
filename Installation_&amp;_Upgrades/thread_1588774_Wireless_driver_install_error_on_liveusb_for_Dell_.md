---
title: "Wireless driver install error on liveusb for Dell Inspiron Mini 9"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by pintle on 2010-10-05
Greetings

I have a persistent liveusb with ubuntu 9.10 that I installed using the method on [http://www.pendrivelinux.com](http://www.pendrivelinux.com) 

I use it on a Dell Inspiron Mini 9 netbook (that boots Mac OS X from its SSD). An ubuntu persistent liveusb works just great for occasional linux development and testing, but ubuntu 9.10 will be EOL next year, and I want to stay current.

I've installed ubuntu 10.04.1 LTS on a liveusb using the method on 

[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

After I've booted the liveusb, under the network menu I see this:

Wireless Networks
 device not ready
 
A menu appears that looks like a PCI card with a lock on it. I select the only item under that menu, "Install Drivers". This gives a dialog that says "No proprietary drivers are in use on this system. Proprietary drivers do not have public source code..." etc. Under Ubuntu 9.10, I could at this point select "Broadcom STA wireless driver" and click the "Activate" button, and it would work. So I did that in 10.04.1.

It says, "Downloading and installing driver..."

While it's doing this, the "kerneloops" menu item appears. Then a dialog that says, 

Sorry, the package "bcmwl-kernel-source 5.60.48.36 +bdcom-0ubuntu3" failed to install or upgrade.

You can help the developers fix the package by reporting this problem

Then another dialog that says 

SystemError: installArchives() failed.

Hmmm...

What the heck is happening here?

Well, it turns out that the error messages are wrong. I restarted and the DM9/ubuntu 10.04.1 was able to connect to the wireless network. 

tl;dr: Proprietary wireless driver installation works, but it claims that it doesn't.

---

### Post by samjam on 2010-10-05
I'm getting pretty much the same error with a 10.10 live USB install on a Dell Inspiron 1545.

---

### Post by G33shooter on 2010-12-14
Any updates on this issue? I would like to install Ubuntu 10.10 netbook remix on my HP mini-110 3110nr but don't want to do it if I can't get wireless to work.  I am having the same error message, " SystemError: installArchives() failed." when trying to install the broadcom driver from the live USB.

---

### Post by aytech on 2010-12-14
First thing I would do is to plug in via cable and update the system, it helped me with my Lenovo netbook.

---

### Post by elsalsa on 2010-12-15
I ran into the same problem installing wireless drivers for a Dell Mini on a 10.10 Live USB (the bcmwl-kernel-source stuff).

I think the problem is related to non-valid initrd.img and vmlinuz in /, and I think I have found a workaround:

1. Remove 10.10 desktop, and install 10.10 netbook remix instead.

2. Press any key on the splash screen to skip the install selection screen.

3. Log in as live user ubuntu with a blank password. /initrd.img is now valid.

4. I didn't bother to check if vmlinuz was valid, and I pointed the link to a different location (this may not be necessary):
sudo rm /vmlinuz
sudo ln -s /cdrom/casper/vmlinuz /vmlinuz
see [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023)

5. Install the proprietary wireless driver from the driver icon that pops up on the taskbar/toolbar/whatever it is in linux. It should complete successfully.

This seems to work well, but I've noticed that all software packages have to be installed while logged in as live user ubuntu; I install stuff as ubuntu, then it is available to me while logged in as a different user. Hope this helps.

---

### Post by elsalsa on 2010-12-15
Looks like I was mostly right, but didn't notice a few things until just now when I screwed something up and had to start all over.

The first time you boot the 10.10 netbook remix, you must let the splash load, and choose the 'try netbook running from this usb' option, then wait for half a forever, then it will say that you must log in as ubuntu/blank password.

Log in as ubuntu, and verify that /initrd.img is valid - it should have a box icon, and its size in the bottom will be 15.6Mb when you click on it once.

Next, run the two commands I posted earlier to re-create the vmlinuz link.

And finally click the hardware driver icon in the upper right to install the wireless driver.

After this point, it seems like everything works fine if you skip the splash on boot.

---

