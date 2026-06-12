---
title: "Can I Get By W/ A Little Help...."
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by Lady Day on 2006-02-28
:-k I knew it would come to this. I have been endlessly searching and researching. Anywho... I successfully installed Ubuntu, however, as with anyone  who comes here, I have issues.  Let's just get to it: 1)I can't connect to the internet. The OS runs on its own hardware (a TCP), and I was able to get a MN-510 adapter from Microsoft. I don't know that I have to configure the adapter or not as both the power and wireless lights are green. After issuing a series of commands I do know that there is no "address" for what is seemingly recognized as an "eth0." I have a Windows network using a MN-700 router and a Westell 2200 modem.I can ping just fine between the Windows systems.  2) ***Before going any further, if I am trying to copy files from a CD, is "/mount"
the command? Maybe that would answer the configuration question, as I cannot seem to be able to install anything from a cd/external source, and nothing seems to be just automatically "read" when I insert a cd. Or could it be the drive?  3)I have read up on NdisWrapper, looking for my card, but I cannot find my pciiid (11c1:0440) for a D-Link. Okay, running out of room and patience..:evil:

---

### Post by o_fortuna on 2006-02-28
[QUOTE=Lady Day]:-k I knew it would come to this. I have been endlessly searching and researching. Anywho... I successfully installed Ubuntu, however, as with anyone  who comes here, I have issues.  Let's just get to it: 1)I can't connect to the internet. The OS runs on its own hardware (a TCP), and I was able to get a MN-510 adapter from Microsoft. I don't know that I have to configure the adapter or not as both the power and wireless lights are green. After issuing a series of commands I do know that there is no "address" for what is seemingly recognized as an "eth0." I have a Windows network using a MN-700 router and a Westell 2200 modem.I can ping just fine between the Windows systems.  2) ***Before going any further, if I am trying to copy files from a CD, is "/mount"
the command? Maybe that would answer the configuration question, as I cannot seem to be able to install anything from a cd/external source, and nothing seems to be just automatically "read" when I insert a cd. Or could it be the drive?  3)I have read up on NdisWrapper, looking for my card, but I cannot find my pciiid (11c1:0440) for a D-Link. Okay, running out of room and patience..:evil:[/QUOTE]
When you put a CD in the drive, it should automatically mount and appear on your desktop. Then it should be under the Places menu and you can drag and drop stuff from the CD to the Desktop, and deal with them from there. If it doesn't, the command is
```
mount /dev/cdrom
```
If they are .deb files, open up a terminal (Applications-->Accessories-->Terminal) and do this:
```
cd Desktop
sudo dpkg -i %PACKAGE%.deb
```
where %PACKAGE% is, of course, the name of the package before .deb.

As for your other questions: let me get this straight. You have 1) a wireless USB card 2) A modem 3) A d-link

So, which one are you trying to access the net with? Are you connected to the net via modem, and trying to access it over wireless? Do you have a wireless USB *and* a wireless PCI device on the same computer? For the pci device (if that's what it is), do this in the terminal
```
lspci
```
and post anything that looks like it's about your d-link.

As for the USB wireless, those are generally less well supported for linux, so I'm not sure what to do with it...

---

### Post by Lady Day on 2006-02-28
:???: I am connected to the Internet with the computer in question via wireless USB adapter (Microsoft MN-510).  The D-Link information after I lspci is: 00000:00:0a.0 Ethernet controller:d-Link System Inc RTL8139 Ethernet (rev 10).  I have proceeded as far as iwconfig and been told that there are no wireless extensions on lo, eth0, wlan0 and sit0.

As I indicated, I have solid green lights on the Microsoft MN-510 USB adapter that is plugged directly into the cpu.  Pinging (-c 4 127.0.0.1) results in 4 transmitted/received and 0% lost.  

When I ifconfig, only eh0, this time **without[B]**[/B], an ipaddress and lo with the ipaddress 127.0.0.1 No wlan or anything else.

Thanks:-|   Awaiting your suggestions...:-k

---

