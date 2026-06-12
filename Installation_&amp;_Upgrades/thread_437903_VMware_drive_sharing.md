---
title: "VMware drive sharing"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by geezerone on 2007-05-09
Hi

Just got VMware server installed in Dapper and installed Windows XP,  but how does one go about accessing other drives for installing previously downloaded apps etc?

TIA

---

### Post by Scunizi on 2007-05-09
If those other drives are accessable from Ubuntu and not from the VM Xp install then you'll need to "share" them and access via the network.. When you VM another system it's like having another computer within a computer and is seperate.  Things like usb keys have to be accessed by going to VM/Removeable Devices/usb at the top of the VM window.  Once you put a check mark next to the device you want to use in Windz, give it a sec to recognize and load.  By unchecking the usb device removes it from windoz but will not neccessarily reload it in Ubuntu.  Sometimes (read mostly) you have to unplug the usb device from the hub, wait for 5 or 10 secs and plug it back in again.

---

### Post by geezerone on 2007-05-10
Thanks for the reply.

I tried the USB stick but Ubuntu only recognises it and isn't shown in VMware.

Also, how is a share to vmware setup exactly?

TIA

---

### Post by Scunizi on 2007-05-10
For the usb drives.. In the vmware window at the top should be the vmware menu options. If you don't see them you might be in full screen mode.  If that's the case point your mouse to the top of the vmware window and hit F11.  That should bring the menus back.  Once the menu's are back, follow the previous post to find your usb device (drive or stick) and click on it.  That will place a check mark next to it and in a few seconds will activate that device in the VM.  I've noticed that once it is connected then disconnected, Ubuntu will not recognize it unless you unplug it, wait for 5 secs or so then plug it back in again.  

As for drive sharing, you have to "share" a folder or drive on xp in the VM.  If you've never done that you could right mouse click on the start button, choose Explore, find the folder or drive you want to share (c:\ or My Documents), right mouse click on your pic and choose "share" or "sharing".  From there it's menu driven.  After that's done by viewing the network in Ubuntu you should be able to see the machine and usually access the drive or folder.  However, if you've set up the file system on XP to be NTFS you'll be able to copy off of the windows drives into Ubuntu but won't be able to go the other direction.  There are drivers available to make this work but I don't know how to do it.  Most people setup another partition and either format it in fat32 or ext3 then map it as a network drive for access from both sides.  

On a side note, in my gnome environment I can get to my win2kpro vm system and see what's there but I haven't figured out how to do it in the KDE environment.. I'm still a nOOb too..

This link might help [https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29%7C%28shares%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29%7C%28shares%29)

---

### Post by geezerone on 2007-05-16
Thanks for that but getting no where with sharing :( 

\\ubuntu-desktop/media/share/vmshare/   is what I used when adding a network place in Windows XP but says that Windows requires a share to publish to?

TIA

---

### Post by veloce on 2007-05-17
Be aware that sharing a usb device (including usb drives) is different to sharing normal drives.  There are two completely different ways to set them up.

**To get your usb drive working:**

Check that you have a usb controller set up for your vm: with your vm shut down, edit virtual machine settings.  In the list of Devices you should see "USB Controller".  If it's not there you need to add it.

Then start the vm.  Once it is running, got to the VM menu of the console and it should appear in the Removable Devices sub menu (as described in an earlier post).
[B]
To get directory sharing working:[/B]

In Ubuntu, set up a samba shared directory using "System-Administration-Shared Folders"

In the vm browse the network and hopefully the computer and share will appear.

---

### Post by geezerone on 2007-05-31
Thanks for the replies but still can't share
:(

I have setup share for /media/share/vmshare on ubuntu and set to SMB on MSHOME but no joy

---

### Post by veloce on 2007-06-02
> **geezerone said:**
> Thanks for the replies but still can't share
:(

I have setup share for /media/share/vmshare on ubuntu and set to SMB on MSHOME but no joy

how is your virtual network configured?

---

### Post by geezerone on 2007-06-05
Hi

I have a Fat32 share which Ubuntu accesses via the mounted /media folder. The vmware XP OS cannot see anything outside its self including USB memory drives which are instantly only recognised by Ubuntu (which Vmware runs on top of)

---

### Post by veloce on 2007-06-05
> **geezerone said:**
> Hi

I have a Fat32 share which Ubuntu accesses via the mounted /media folder. The vmware XP OS cannot see anything outside its self including USB memory drives which are instantly only recognised by Ubuntu (which Vmware runs on top of)

For the Hard Drive:
In the host (ubuntu) you need to share a directory on the drive using samba (it doesn't need to be fat32 btw - anything ubuntu reads is fine).

Check that vmware has host only networking enabled:  run ifconfig and see if vmnet1 shows up as an interface (like eth0).  If not, you need to run vmware-config-network.pl (assuming you are using vmware 1.0.3)

In the vmware console, with the vm off, make sure that the vm has a virtual network controller.  Edit the settings on that to connect to the host only network.

Turn on the vm, use network browse to find the shared directory.

For USB:
With the vm off, check that you have a usb controller in the hardware.  If not, install one.

With the vm on, in the vmware console select the menu option VM - Removable Devices.  You should get a list of the usb devices that the host has connected.  Click on the one you want the vm to connect to.

---

### Post by geezerone on 2007-06-07
Thanks Veloce. I have installed and got the USB working :D

Can't get the Samba thingy going, if I use host only I cannot browse internet so have to leave that as Bridged.

I tried [ **this** ](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/) and thought I was getting somewhere but get the error "the network path cannot be found" after entering username and password. If I browse for the folder I can 'see the Ubuntu machine name but no folders show up when clicking to expand the machine ( + ). Puzzled.....

******EDIT************ Bingo! Got it working (forgot to add the username in square brackets above share info in samba.conf file)

Not too sure what this made as was more involved than merely adding a share?

---

