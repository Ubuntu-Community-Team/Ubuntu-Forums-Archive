---
title: "[SOLVED] Windows Server NetBoot via PXE - file not found - solution"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by maarten80 on 2007-06-13
Hi all,

I tried installing (x)ubuntu on a laptop (travelmate 350 PIII 700Mhz 256Ram) without floppy or cd. Additionally it turned out not to support booting from a usb device so that didn't work either. Then tried the netboot from windows on the same machine, no succes either (can be seen here: [http://ubuntuforums.org/showthread.php?t=469809]("http://ubuntuforums.org/showthread.php?t=469809"))

Then discovered what PXE booting over LAN meaned which the laptop did support. This went like a breeze! Although I had to do some (very) minor adaptations to the tftp settings

There is a very good howto in the wiki on how to setup a server on the windows machine you want to use as a server
[https://help.ubuntu.com/community/Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")

I used a WinXP machine as server with wireless connection to the router, the target laptop was LAN connected to the router (ie cablewise). The server setup went great (I am a noob, just follow the howto).

However, at first I got errors like: *PXE-T01: TFTP error: File not found*. Meaning the connection was ok, but the boot files could not be found. So I fiddled a bit to point it to the correct directories. You can see my changes marked below.

----
_from the wiki_ + **changes**:

Run Tftpd32.exe and click the DHCP tab 
in the default router box, put the address of your internet gateway (usually 192.168.0.1 or 192.168.1.1 for residential routers) 
in the ip pool starting address box put your gateway's address + 1 to the last number (Example: 192.168.0.2) 
Size of pool = i said about 10 
if your network is something like 192.168.0.1 then your network mask should be 255.255.255.0 

Set the Bootfile field to the location of the pxelinux.0 file (example "\netboot\pxelinux.0) 
**I had to make this  /netboot/pxelinux.0**

Set the WINS/DNS server address to the address of your main router (192.168.0.1) 
Leave the domain name blank, unless you need to change it. 

**Set the current directory you see at the top of this window to c:\cb**

Hit the "Save" button and then click "settings" 
on the settings menu Check the following and leave the others how they are. 

PXE Compatibility 
translate unix file names 
allow / as virtual root

**Set the base directory (again at the top of this window) to c:\cb**

----

After it found the files it worked like a charm!
(I also tried pointing it to the .iso file to avoid all the downloading but that didn't work)

I post this here as I don't know how to add it to the wiki, hope it's helpfull to some of you

---

