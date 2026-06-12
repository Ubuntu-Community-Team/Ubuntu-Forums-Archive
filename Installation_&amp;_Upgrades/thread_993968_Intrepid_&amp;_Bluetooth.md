---
title: "Intrepid &amp; Bluetooth"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by zkab on 2008-11-26
Has anyone got Bluetooth working for Intrepid :confused:

Have MS Wireless Entertainment Keyboard 8000 / Laser Mouse 8000 and they both worked 100% in 8.04 ... but after upgrading to 8.10 the keyboard stopped working ... mouse works OK
Have googled and found alot of people having the same problem but no solution.

How can Ubuntu team release an upgrade that don't work for basic things like connecting bluetooth devices (specially when it worked in eariler releases)... there is always problems when upgrading in Ubuntu ... don't they have any quality control group.

There is no way that people migrate from Windows to Ubuntu if there are major problems with every Ubuntu upgrade ...

---

### Post by HyRax on 2008-12-26
The Intrepid issue is known and being worked on. In the meantime, try [this workaround](http://ubuntuforums.org/showpost.php?p=6438656&postcount=6) to dull the pain somewhat. :)

---

### Post by zkab on 2008-12-26
Thanks :)

---

### Post by saturnine fei on 2008-12-28
Does anyone know if the fix being worked on will include the ability to pair devices like my HT800 Headphones, though come to think of it I can't pair my printer either as Ubuntu flashes a message by during the pairing process that looks like a request to enter a pin and then fails to provide opportunity to do so?  Its far to quick to read it so I can't change the printers pin to match the request either.

If this Linux thing is going to work it can't require every user to become a system administrator.  We morons need this stuff too.

---

### Post by HyRax on 2008-12-28
> **saturnine fei said:**
> Does anyone know if the fix being worked on will include the ability to pair devices like my HT800 Headphones, though come to think of it I can't pair my printer either as Ubuntu flashes a message by during the pairing process that looks like a request to enter a pin and then fails to provide opportunity to do so?  Its far to quick to read it so I can't change the printers pin to match the request either.

I can use my TDK BT50 headphones without any problem. Older versions of Ubuntu had an issue with flash-by PIN requests which is why it generally became easier to initiate pairing from the device as opposed to from Ubuntu, but with Intrepid, I have had no such issues pairing from Ubuntu now.
> **saturnine fei said:**
> 
If this Linux thing is going to work it can't require every user to become a system administrator.  We morons need this stuff too.
Hehehe - pairing under Windows actually involves more steps than Ubuntu does! Ubuntu has a minimum 4 steps to pair something, five if you have to enter a PIN.

---

### Post by saturnine fei on 2008-12-28
Hmmmmm... interesting.  I have, on google searches, found others who had this problem without any resolution short of downgrading back to hardy.  Is there a particular upgrade or download I need to solve the flash-by problem?

I have sort of given-up on bluetooth under Ubuntu until I saw this thread.  I bought a dongle for my desktop and it doesn't work.  From what you say, I may just need an update that isn't happening automatically.  I am guessing this because you reference having to enter a pin and yet Ubuntu never provides me the opportunity to do so.

---

### Post by HyRax on 2008-12-28
> **saturnine fei said:**
> Hmmmmm... interesting.  I have, on google searches, found others who had this problem without any resolution short of downgrading back to hardy.  Is there a particular upgrade or download I need to solve the flash-by problem?

I have sort of given-up on bluetooth under Ubuntu until I saw this thread.  I bought a dongle for my desktop and it doesn't work.  From what you say, I may just need an update that isn't happening automatically.  I am guessing this because you reference having to enter a pin and yet Ubuntu never provides me the opportunity to do so.

Sounds to me that your installation has something weird going with it. Boot up on a LiveCD and try connecting to your Bluetooth device that way, so you have a 100% clean environment to test with. If the system prompts you properly for your PIN, then you know your HDD-installed Ubuntu has something up with it (or at least something in your Gnome config is doing it). Consider creating a new user with a clean desktop on your machine to test that theory.

---

### Post by nco on 2009-01-14
I've tried live CD from Ubuntu, Fedora, Suse and Mint and all bluetooth is broken on both my eeepc and my Satellite pro.

Think it is a kernel problem.  It certainly isnt detecting my hardware but the bluetooth layer on top of that seems to be installed correctly.

Lets hope a fix is availabel soon

N

---

### Post by HyRax on 2009-01-14
> **nco said:**
> I've tried live CD from Ubuntu, Fedora, Suse and Mint and all bluetooth is broken on both my eeepc and my Satellite pro.

Think it is a kernel problem.  It certainly isnt detecting my hardware but the bluetooth layer on top of that seems to be installed correctly.

Lets hope a fix is availabel soon

N

Hang on - what EeePC are you using? I have absolutely no problems with Bluetooth on my EeePC, both with the vanilla generic kernel and the array.org custom kernel.

Is your Bluetooth adapter even enabled??

---

### Post by nco on 2009-01-15
Its a ASUS 701 running eeesypc (A Ubuntu 8.10 release with custom kernel already applied)

I can't switch bluetooth on.

I now have it working on my TOshiba satellite pro by using omnibook driver.

despite Toshiba utilities being installed on install there is no toshiba-acpi (been removed from the kernel) so I could not switch on the bluetooth adapter on my P300.  I only had partial laptop functionality. 

Any tips on getting it working on the eeepc 701?

thanks
Neil

---

### Post by HyRax on 2009-01-15
The 701 does not come with native Bluetooth, which means you must be using a USB adapter (like I am).

Regardless of what distro you are using, we need to confirm that the system recognises that you have a Bluetooth adapter connected. Open a terminal window and type in:
```

$ tail -f /var/log/messages

```

...and while that's showing you live log output, connect your Bluetooth adapter and confirm that the log acknowledges its connection with no error messages. If all is good, the Bluetooth icon should suddenly appear in your system/notification tray.

For example, my system outputs the following to the log to show my Bluetooth hardware being picked up:

```

Jan 14 06:25:11 lamaar kernel: [   11.721403] Bluetooth: Core ver 2.13

Jan 14 06:25:11 lamaar kernel: [   11.745449] Bluetooth: HCI device and connection manager initialized
Jan 14 06:25:11 lamaar kernel: [   11.755096] Bluetooth: HCI socket layer initialized
Jan 14 06:25:11 lamaar kernel: [   12.188089] Bluetooth: Generic Bluetooth USB driver ver 0.3

```

Break the live log output with CTRL + C and then type in **lsusb** to see what the system is determining as currently connected on the USB bus:

```

$ lsusb
Bus 008 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)**
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$

```

If you can see an adapter listed, then you should be fine. If not, then perhaps your adapter has issues? Try booting up a LiveCD/LiveUSB copy of Ubuntu and see if your adapter is being picked up int he log - disconnect and reconnect. Try it on another PC to double-check. Perhaps your Bluetooth hardware is actually faulty, etc? It's a process of elimination.

---

### Post by meistercobbman on 2009-01-15
All I know is, my bluetooth works fine in intreped. I'm using a Lenovo R61 with integrated Bluetooth. But, it DIDN'T work until I turned it on in Window's first, then rebooted back into Ubuntu. 

(This has been true with other features as well, such as volume. Somehow if my volume is turned low in windows, then when I reboot into Ubuntu the volume will also sound low even if Ubuntu says it's turned all the way up. Don't know if it's just my machine or if this happens to everybody)

---

