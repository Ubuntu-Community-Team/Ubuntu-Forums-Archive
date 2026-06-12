---
title: "Ubuntu Install issue on a Windows 8 pre-installed Acer Revo"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by XEWKhCJ on 2013-10-17
Hi all,

Just to put it out there at the start, I'm a bit of a ubuntu newbie. I'm a developer so only really use this as a webserver to develop on. 

My actual dev server running Ubuntu Server 12 died a couple of days ago, so I brought a Asus Revo ([spec here]("http://www.ebuyer.com/500387-acer-revo-rl70-nettop-pc-dt-smeek-008")) as a quick and easy box to use as a local webserver.

Installed Ubuntu Server 12 as the only OS fine (no dual boot), but when trying to reboot into the OS I got the message "Reboot and Select proper Boot Device, or Insert Boot Media in selected device and press a key".

I've tried re-installing and tweaking the settings in the installer (done about 5 clean installs now), and also googled and searched this forum for similar circumstances, of which there are a few. However either the other issues are solved by solutions which don't work for me, or the issues which are the same as mine have no real answer provided (apologies if I've missed a topic somewhere?).

To go back to basics I downloaded a Live/Install CD of Ubuntu Desktop 12 and followed this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) guide under "Installing Ubuntu Quickly and Easily via Trial and Error". Unfortunately it led to the same result, the "select proper boot devise" error on boot.

I've got Secure Boot disabled, and there's no option in the BIOS setup to change the EUFI settings.

Here is my Boot Info/Repair paste: [http://paste.ubuntu.com/6253051/](http://paste.ubuntu.com/6253051/)

Any help would be much appreciated.

Thanks!

---

### Post by oldfred on 2013-10-17
You show that you installed the signed kernel, so you should be able to boot with secure boot on. 
BIOS should have options to turn secure boot off. Some then only have CSM, but may still boot UEFI if efi partition found and if not found then boot in BIOS mode. Others have specific switches for CSM/BIOS on or off. UEFI on or off and secure boot on or off.

You UEFI shows this:
 BootOrder: [COLOR=#ff0000]0001[/COLOR],0003,0002,0000
Boot0000  Windows Boot Manager	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...5................
Boot[COLOR=#ff0000]0001[/COLOR]* ubuntu	HD(1,800,2f000,4a2d10a5-aaee-42d5-9670-5a867f94ec93)File(EFIubuntushimx64.efi)

If that is not working as default boot, then you may have one of the buggy UEFI that only boots Windows. Boot-Repair has a rename work around where it renames the Windows efi file to be shim which has the Microsoft signing key. They modify UEFI and make it hard coded to only boot bootmgfw.efi.

---

