---
title: "Samba4 Sucks"
date: 2014-11-21
forum: Installation &amp; Upgrades
---

### Post by joejvj on 2014-11-21
I recently upgraded my server from Ubuntu 12.04 to 14.04. In the process, Samba was also upgraded from 3.x to 4.x. It broke everything.

I have 4 machines on my network: 2 Windows 7-64bit, 1 Windows 7-32bit, and a linux mint box. All of the windows machines broke in some way or another. Two of them (the Win7-64-bit and Win7-32bit) exhibited a 10-15 second delay when first connecting. After that, they seemed to work fine. The other Win7-64bit machine didn't have the connect delay but was very, very slow with file transfers.

This is a very simple stand-alone workgroup setup with no AD or DC. After the upgrade, I used the exact same smb.conf file which was working fine even back to the Samba 2.x days.

After trying numerous registry changes on Windows and messing with smb.conf to no end, I finally found the fixes to make all the machines work. I'm posting this in case you are running Samba4 in stand alone server mode and experiencing weird problems that can't be solved. There are two things that fixed it:
(1) Change your boot up to start nmbd and smbd. DO NOT run 'Samba' on startup.
(2) Disable SMBv2 in your Windows boxes.

These 2 items fixed all my unrelated samba issues across multiple machines. I do believe that Samba4 does not work properly with SMBv2, at least in the stand alone server mode.

---

### Post by ghanson59 on 2015-02-10
Joe,
I've just experienced the same issue. I am noticing that Samba isn't loading properly because running smbclient -L localhost -U% after reboot gives the "Connection to localhost failed" error. Upon checking I'll see that nmbd is running but smbd is not.
Adding IFACE=eth0 and started udev-finish in smbd.conf doesn't help.
I'm kind of new at this so could you list the steps on how to force boot to start nmbd then smbd rather than "Samba"?
Also, where can I find SMBv2 within Windows settings?

Thanks, man. This is driving me crazy.
Greg

---

