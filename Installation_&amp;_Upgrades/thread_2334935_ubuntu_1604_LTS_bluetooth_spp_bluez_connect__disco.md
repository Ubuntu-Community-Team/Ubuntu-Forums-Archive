---
title: "ubuntu 1604 LTS bluetooth spp bluez connect / disconnect and ModemManager problems"
date: 2016-08-24
forum: Installation &amp; Upgrades
---

### Post by einhexenmeister on 2016-08-24
i have 2 desktops and one schlepptop with new installs of rev 1604.1 lts

what i describe here was working flawless with 1404 and 1404.3 lts

a udev rule with providing a group policy for dialout is also in place

KERNEL=="rfcomm*", GROUP="dialout"

pairing a bluetooth spp serial device with bluetooth manager works

connecting the bt spp serial device with bluetooth manager works in a limited way, as does the following commandline

 "[FONT=monospace][COLOR=#000000]sudo rfcomm connect /dev/rfcomm0 00:15:FF:F3:24:B1"

[/COLOR][/FONT]opening of the rfcomm0 serial port now will (might) only succeed under "sudo" permission level, otherwise a "couldn't open /dev/rfcomm0" will be the result (tested with cutecom and my own app using a serial port)

killing the ModemManager process and connecting again (after disconnect) will allow a normal user to open the bluetooth rfcomm port sucessfully

and now the 2nd issue, which seemed to linger on and off for about 7 plus years ... it worked in rev 1404

using the disconnect button at the bottom of the bluetooth manager popup dialog indicates the disconnect action, BUT it did not disconnect ... the port can still be opened
pushing the disconnect line with the device name indicated in the 4th line doesn't do anything (not sure if it should)

any subsequent connect action with the bluetooth manager to connect to the same device will now iterate through the rfcomm0 ... rfcomm7 and more port names, since the device was not really disconnected

the connection of the newly assigned rfcommx will disconnect the previously "still" connected one

not using the bluetooth manager and using the command line as indicated above will provide a command line workaround which will close the rfcommx port and prevents this port number iteration

summary :

don't use bluetooth manager, use the "rfcomm connect xx:xx ...:xx" on the commandline to connect and disconnect

if u can only connect with sudo permission, kill the ModemManager process and reconnect and a bit praying perhaps, like always in linux :)

[FONT=monospace]cheers [/FONT][FONT=monospace]!!!

[/FONT]

---

