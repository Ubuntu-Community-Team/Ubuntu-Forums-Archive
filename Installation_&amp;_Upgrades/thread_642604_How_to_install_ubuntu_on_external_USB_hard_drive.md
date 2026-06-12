---
title: "How to install ubuntu on external USB hard drive"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by r3n0 on 2007-12-16
I have a laptop running windows vista and i have an extra external usb hard drive that i would like to put ubuntu or wubi on it.  I installed wubi on the external no problem and when i turn on my computer to boot up ubuntu the loading screen comes on and i got the following error

On the the hard drive line is says
No buffer space available


so then i restarted andded Boot to USB hard drive as the first priority and then i get the following error

NTLDR is missing, ctrl-alt=del to restart



any ideas how to get this to work?:

thanks so much

---

### Post by logos34 on 2007-12-16
> **r3n0 said:**
> I have a laptop running windows vista and i have an extra external usb hard drive that i would like to put ubuntu or wubi on it.  I installed wubi on the external no problem and when i turn on my computer to boot up ubuntu the loading screen comes on and i got the following error

On the the hard drive line is says
No buffer space available


so then i restarted andded Boot to USB hard drive as the first priority and then i get the following error

NTLDR is missing, ctrl-alt=del to restart



any ideas how to get this to work?:

thanks so much

You might want to go back and read the wubi docs...I think it has to be installed on the windows C: drive (ubuntu runs as a loopmounted filesystem within windows).  

That said, why don't you just do a regular install of ubuntu on the usb drive?

---

### Post by r3n0 on 2007-12-16
i was unaware, ill try to install just ubuntu

---

### Post by logos34 on 2007-12-16
you might want to take a look at [this]("http://ubuntuforums.org/showthread.php?t=80811") before you install (->post#502).  Shows how to do it without overwriting your windows bootloader on the internal mbr.

---

### Post by r3n0 on 2007-12-17
great info thanks a lot

one minor problem, i have a 2.5 inch hard drive and i was reading that that is a problem since the hard drive doesnt spin right away


has anyone out there gotten it to work on a 2.5 " external drive?

---

### Post by Coombabah on 2007-12-17
> **r3n0 said:**
> great info thanks a lot

one minor problem, i have a 2.5 inch hard drive and i was reading that that is a problem since the hard drive doesnt spin right away


has anyone out there gotten it to work on a 2.5 " external drive?

After playing with grub on external usb hard drives and usb flash drives booting usb seems to be surprisingly easy.

I've installed Gutsy on a Seagate FreeAgent Go 2.5" external drive and it seems to be working well so far.
I had to find a Windows computer and change the Seagate drive settings with it's supplied software to stop it spinning down after 3 minutes and causing errors.

I used the Live DVD for the install and made lots of partitions so I could select a separate partition when booting on different computers.
You can also copy all the files from a live CD into a spare partition and use grub to boot it instead of using the live CD and adding a grub entry like step 3 from the url below.
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by logos34 on 2007-12-17
> **Coombabah said:**
> I had to find a Windows computer and change the Seagate drive settings with it's supplied software to stop it spinning down after 3 minutes and causing errors.

Or use hdparm to adjust the spin(up/down) time.  See manpage for hdparm.

r3n0,
your Bios might alsa allow you set a delay for hard disk detection (my intel board does), giving the usb drive more time to spin up during POST.

---

### Post by Coombabah on 2007-12-19
> **logos34 said:**
> Or use hdparm to adjust the spin(up/down) time.  See manpage for hdparm.

r3n0,
your Bios might alsa allow you set a delay for hard disk detection (my intel board does), giving the usb drive more time to spin up during POST.

From looking at some of the threads on the Seagate FreeAgent Go spindown issue it looks like hdparm doesn't stop them spinning down and you need to use the Seagate Windows only software until someone reverse engineers and makes a Linux version.
The other option is to patch every Linux OS you use them on.

Edit: No need for windows :) sdparm can disable the spindown on the seagate freeagent go drive if it is still spinning
my drive shows as sda the next line is to check it is the right drive and the line after is to set it to "never"
sudo sdparm -a /dev/sda
sudo sdparm --clear STANDBY -6 /dev/sda

I checked this with the windows freeagent utility and it had changed to never

---

### Post by logos34 on 2007-12-19
> **Coombabah said:**
> From looking at some of the threads on the Seagate FreeAgent Go spindown issue it looks like hdparm doesn't stop them spinning down and you need to use the Seagate Windows only software until someone reverse engineers and makes a Linux version.
The other option is to patch every Linux OS you use them on.

Note taken.  

When will hardware vendors finally start supporting linux?  (Hitachi is the only drive manufacturer I think that even acknowledges the existence of linux).  Jeez, it's like nearly '08.  How much can it possibly cost them to write a *nix version of their utility sw?  Lots more people would probably buy external hard drives for dual booting if only linux support was there to encourage them.

---

