---
title: "No bluetooth found in ubuntu 22.04 error"
date: 2022-07-23
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2022-07-23
I have tried to configure my keyboard to use Bluetooth on ubuntu 22.04,  bluetooth was enabled in the settings I could enable and disable it, but could not make the keyboard work,  then I google
and  run some commands ... not in the setting I see Bluetooth not found  and plugin a dongle to use bluetooth.
When I run sudo systemctl status bluetooth.service
 bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:bluetoothd(8)

Then
sudo systemctl restart bluetooth

sudo systemctl restart bluetooth
xxx@xxx:~$ sudo systemctl status bluetooth.service
&#9675; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:bluetoothd(8)

Jul 23 10:58:37 xxx systemd[1]: Condition check resulted in Bluetooth service being skipped.
Jul 23 11:02:42 xxx systemd[1]: Condition check resulted in Bluetooth service being skipped.
Jul 23 11:12:30 xxx systemd[1]: Condition check resulted in Bluetooth service being skipped.

Then
sudo modprobe btusb
xxx@xxx:~$ sudo systemctl restart bluetooth
xxx@xxx:~$ sudo systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-07-23 11:16:58 CEST; 5s ago
       Docs: man:bluetoothd(8)
   Main PID: 30321 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18931)
     Memory: 1.9M
        CPU: 110ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;30321 /usr/lib/bluetooth/bluetoothd

Jul 23 11:16:57 xxx systemd[1]: Starting Bluetooth service...
Jul 23 11:16:58 xxx bluetoothd[30321]: Bluetooth daemon 5.64
Jul 23 11:16:58 xxx systemd[1]: Started Bluetooth service.
Jul 23 11:16:58 xxx bluetoothd[30321]: Starting SDP server
Jul 23 11:16:58 xxx bluetoothd[30321]: Bluetooth management interface 1.21 initialized

even  after that the bluetooth  is not enable in settings 
I am using asus stationary computer
Thanks in advance

---

### Post by TheFu on 2022-07-23
I understand that you want to use bluetooth.

If you don't know the risks, please put this search into your favorite web search tool: "hacking bluetooth is trivial"
Read a few of the most recent articles and know that since the beginning, BT has been very non-secure. The BT industry has effectively ignored security for the sake of convenience.

Sure lots of people use it.  Some people have been screwing with others using BT when in crowds, conferences, hotels, libraries, and other places that people go. It is just so easy and sad, er ... so I hear.

Sadly, the best answer for all bluetooth devices is to disable it, avoid it, and not use it.

Speakers are one thing, but mice and keyboards are like providing a remote keyboard logging device to anyone within about 1km.
[https://www.techradar.com/news/bluetooth-devices-could-be-hacked-from-a-kilometre-away](https://www.techradar.com/news/bluetooth-devices-could-be-hacked-from-a-kilometre-away)

I was hacked while at a conference through bluetooth and I knew better.  My laptop was freshly installed, freshly patched, the day before, but I'd forgotten to disable BT in the BIOS. It was never on any network at the conference. Not wifi nor wired.  I've since added a script to the system boot process to remove the BT module and purge the BT packages which seem to be added back by some others as dependencies from time to time.  A few of those dependencies have me scratching my head - they don't make any sense at all.

---

