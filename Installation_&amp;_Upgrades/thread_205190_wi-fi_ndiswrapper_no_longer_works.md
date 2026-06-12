---
title: "wi-fi ndiswrapper no longer works"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Ray Hamilton on 2006-06-28
I recently upgraded from Breezy to Dapper.  Afterwards, I had an xserver problem that I fixed using the sticky post here.  My main problem now is that my wi-fi connection no longer works.  In Breezy I  set it up using ndiswrapper.  I presume I have to do it again in Dapper (because the kernel has changed?) but the instructions I used previously don't seem to work in Dapper.  This is particularly strange because someone else has followed my instructions and got their exact same Wanadoo USB adaptor working under Dapper. What am I doing wrong and what do I need to do now?

---

### Post by Dr. Nick on 2006-06-28
ndiswrapper shouldnt need to be totally reconfigured, What happens alot of times is that a new kernel will include support for the wireless card by default. If this new built in driver doesnt work then you wireless wont work, but if you leave the driver loaded it will block ndiswrapper from getting a chance to work.

That being said you can see if you have native drivers now that you didnt have in breezy by running this command from a terminal

**lsmod**

since you mentioned your card is a USB then look at the line that says usbcore and make sure only ndiswrapper,usbhid,ehci_hcd,uhci_hcd appear on that line. If you get somethin else thier like prism2_usb, islsm_usb or something similar you probably have a conflict.

To resolve it type

sudo modprobe -r *driver_name*

then

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper 

that will work temporarily, you can make it permanent by blacklisting the driver.

If you need help then just post the lsmod output and make sure ndiswrapper says driver and hardware present

---

### Post by az on 2006-06-28
[QUOTE=Ray Hamilton]I recently upgraded from Breezy to Dapper.  Afterwards, I had an xserver problem that I fixed using the sticky post here.  My main problem now is that my wi-fi connection no longer works.  In Breezy I  set it up using ndiswrapper.  I presume I have to do it again in Dapper (because the kernel has changed?) but the instructions I used previously don't seem to work in Dapper.  This is particularly strange because someone else has followed my instructions and got their exact same Wanadoo USB adaptor working under Dapper. What am I doing wrong and what do I need to do now?[/QUOTE]
I would suggest that the problem is either that there is a linux driver now for that device and trying to use ndiswrapper on a device that is already claimed by a driver results in none of them working.

Remove your ndiswrapper config, reboot and see if wireless works out-of-the-box.  If not, find out what driver isbeing loaded for the wireless device (device manager) and blacklist it.  Then use ndiswrapper.

It may also be that the version of ndiswrapper is newer and that the .inf file that you are using is too old for it.  The one that comes with your device may be too old to use.  See the ndiswrapper wiki list for what the current driver for your device it.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by Ray Hamilton on 2006-06-28
I have done a lsmod and the results indicate that I have "driverloader" loaded.  I remember now that I tried this product (a free trial version) as an alternative to ndiswrapper when the latter did not work the first couple of times.  However, before I used "driverloader" to load any drivers, I had one more go with ndiswrapper and had success.  I then forgot to remove it and at times had problems with the internet becoming unavailable, which I put down to some interference from this "driverloader".  However, the problem seemed to go away and so I forgot about driver loader.  Any ideas as to how to remove "driverloader" - I tried modprobe -r ... and this seemed to be successful, but trying the instructions to "restart" ndiswrapper results in:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

I note that when doing a search for ndiswapper it seems to be in two places:
/lib/modules/2.6.12-9-386...
/lib/module/2.6.15-25-386...

Finally, in reply to azz: how do I remove my ndiswrapper config? is this the one in /etc/modprobe.d

Thanks for all the help so far - I think we are close to solving this one

---

### Post by Dr. Nick on 2006-06-28
the modprobe -r *module* is only a temporary fix, once the device or computer is restarted the driver can reload itself.

When you tried to reload ndiswrapper were you sure to use "sudo" before modprobe ndiswrapper.

You should be able to remove driver loader, it may be different depending on how it was installed, was it a .deb or a source compile? Deb should be removeable from synaptic, source can be a bit harder.

You could just add the driverloader module to the blacklist

---

### Post by Ray Hamilton on 2006-07-03
For azz: I am still awaiting your reply

For Dr. Nick

I have now removed "driverloader" using synaptic. And after a re-boot jsut to be safe, the relevant part of lsmod result:
usbcore    104188 3 ehci_hcd, uhci_hcd

"sudo ndiswrapper -l" gives:
prisma02    driver present,  hardware present

"sudo ndiswrapper -m" gives:
modprobe config already contains alias directive

"sudo modprobe ndiswrapper" gives the FATAL ERROR mentioned above.

What do I do now, please?

The USB LED is now lit when it wasn't before.  This is hopeful because it is similar to when I set things up with Breezy.

---

### Post by az on 2006-07-03
To delete ndiswrapper config, yes delete the files in /etc/ndiswrapper or run

sudo ndiswrapper -e prisma02 

To blacklist the module that linux loads automatically, insert the line

blacklist prism54
to /etc/modprobe.d/blacklist

sudo gedit /etc/modprobe.d/blacklist

Also, get rid of driverloader.

---

### Post by Dr. Nick on 2006-07-03
A few questions. 

Are you trying to build ndiswrapper from source , or using the apt-get version.

You are correct in assuming that the new kernel will require you to re-setup parts of ndiswrapper. If you compiled it from source for breezy, and now are in dapper and can not get it to recompile then it will not work.

If you are doing a source compile , you must make sure to build ndiswrapper against the newest kernel you have,

If you are doing a source compile then I will ask if you have ever tried using the version in synaptic?

The fatal error you recieve seems to be pretty generic, it could be several things that cause it.

Good luck, In the mean time you might be able to restart into your old kernel from breezy and have ndiswrapper work if you need wireless.

---

### Post by Ray Hamilton on 2006-07-04
for Dr. Nick: I am using the ndiswrapper that came with Breezy and that I installed with synaptic.  Is there a different version with Dapper? I have done an upgrade not an actual installation, so I do not think I can restart into my old kernel?

for azz: the wi-fi adaptor does not work out of the box, after following your instructions - still no success.

for anyone: I don't know if this helps:
dmesg produces: ndiswrapper version 1.1 loaded (preempt=no,smp=no)
ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1536) check system for messages from 'loadndiswrapper'

Any thoughts?  and how do I check system for messages from 'loadndiswrapper'?

---

### Post by Dr. Nick on 2006-07-04
Not sure how to check the logs for load ndiswrapper, but you should be able to choose your old kernel at the grub start screen.

Way up at post 4 you said ndiswrapper apperas in  /lib/modules/2.6.12-9-386.. so the 2.6.12-9-386 kernel should still be installed.

The only thing I could think is that this version of diswrapper doesnt like that driver you are trying . If you could get back to your old kernel from grub then you could see if it works thier, If it doesnt work then possibly the ndiswrapper version change from breezy to dapper may be to blame. 

I have herad its best to not upgrade ndiswrapper once you get it working since it isnt the best at "backwards compatablity". If you are able to get it all set up again somehow then you can lock the version in synaptic so it wont update.

---

### Post by Ray Hamilton on 2006-07-11
Okay.  I have been doing a lot of investigating and have found that Dapper definitely uses a different version of ndiswrapper to Breezy.  I have followed the wiki information to remove my existing ndiswapper (why is there no way to check whcih version it is when running? - wrong place to ask I guess). I downloaded the one listed for Dapper and installed it using dpkg.  However when I try to run it, it cannot be found.  dpkg reported that it was updating/replacing the previous version.  Any ideas?
I am going to re-install the one listed as being for Breezy and see what happens.  It can't make it any worse than it not working. ](*,)

---

