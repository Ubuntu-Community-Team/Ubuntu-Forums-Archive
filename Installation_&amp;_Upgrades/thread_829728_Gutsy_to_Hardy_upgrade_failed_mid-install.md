---
title: "Gutsy to Hardy upgrade failed mid-install"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by Gokee2 on 2008-06-15
Hello all,

I decided to update a laptop from Xubuntu gutsy to hardy today.  It got about half way through installing packages and the update manager went away...  Just gone.  I was watching a movie (not on the computer) while the upgrade was taking place and the screen went into screen saver.  A little while later I touched the touchpad to take it off the blank screen so I could see how the upgrade was coming as I had done the last few times it went into screen saver, but when the screen came up the update manager was gone!

I tried restarting the update manager but it did not start (from the xfce menu).  Not knowing the command to start the update manager myself I went ahead and checked out what apt-get said.  It said it was not finished and that I needed to run a dpkg command (dpkg -f?) so I did.  That finished fine and I decided to restart.  However when it came back up my wireless did not work.  I tried unchecking and rechecking the driver box, it seems to only install bcm43xxcutter.  The wireless light comes on when the driver is checked.

iwlist scanning comes up empty but with more then one wireless thing?

wmaster0  Interface doesn't support scanning.
eth1      No scan results

ifconfig looks like 

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:b9:a6:33
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feb9:a633/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14657094 (13.9 MB)  TX bytes:3310834 (3.1 MB)
          Interrupt:18 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:90:4b:a6:b8:9c
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:900 (900.0 B)  TX bytes:900 (900.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-A6-B8-9C-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

The laptop has a broadcom 43xx chipset so it has been using ndiswrapper (just clicked the check and everything worked in gutsy).  

So I looked for ndiswrapper,

lsmod |grep ndiswrapper

Comes up empty.

I try modprobing it
sudo modprobe ndiswrapper

Goes fine so I try
lsmod |grep ndiswrapper

And get
ndiswrapper           192920  0
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd

However I still can`t see anything with iwlist scanning.

I attached a full lsmod in case that helps.


The wireless network card is the only thing I have found so far that the failed upgrade broke.  Anyone know of a good way to check that everything else is "normal"?  I thought about posting this in networking but decided this was the "right" spot.

Thanks!

---

### Post by Pumalite on 2008-06-15
Memory? Graphics?

---

### Post by Gokee2 on 2008-06-15
There is a restricted driver for graphics that I think is working, I have not tested it through to make sure (it does not have much of a graphics card). It does have a problem in boot up through showing a whitish screen with a bunch of other colors.  I think its because usplash has the wrong resolution again though, but I have not checked.  It had the wrong resolution when I first installed gutsy and I had to fix it. Its got 512 MB ram and a bunch of space left on the hard drive, I will check how much later today when I am at the laptop.

---

### Post by Pumalite on 2008-06-15
You are good to go. Burn anew CD. Do md5sum, burn at 4x or less. Reinstall. You can go for Ubuntu 8.4. Let me know if you have problems.

---

### Post by Gokee2 on 2008-06-15
I was rather hoping to do something other then a fresh install.  I guess I could go that way but that would take a long time, and I would have to reconfigure a bunch of stuff.  Any other ideas?

Thanks!

---

### Post by Pumalite on 2008-06-15
[http://ubuntuforums.org/showthread.php?t=780531](http://ubuntuforums.org/showthread.php?t=780531)
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by Gokee2 on 2008-06-16
Well it seems to have fixed itself.  Not really sure what went on but I clicked the network icon one time and my wireless network was listed!  I also found out ndiswraper seems to no longer used and instead bcm43xx?  I don`t know I did not really look into it much just noticed no ndiswrapper in my lsmod.

Suspend now works (Edit: Not really it works if its not left in suspend...  If you put the computer in suspend and leave it it dies.)!  Hardy seems to have helped this laptop.

Also anyone happen to know how to mark this thread as solved? (Edit: Found it.  Edit in the first post.  I had tried that but not been able to get it to work.  Don`t know why its right there....)

Thanks

---

