---
title: "Grubloader won't install; windows 7 &amp; 11.04 dual boot (pics)"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by mooseman99 on 2011-07-24
[SIZE="3"]Hey everyone,
A few months ago I tried to upgrade from 10.10 (which was installed fine on my computer alongside windows 7) to 11.04.  When I tried, the installation failed because grubloader couldn't install.

**Now**, I finally decided to format my entire hard drive and do a clean install of Windows 7 (Ultimate 64 Bit) and Ubuntu (11.04 64 Bit)

However, even with a clean formatted disk with a fresh Windows 7 install, Ubuntu is having the same grubloader problem.

Apologies for the camera pictures, I took screenshots but Ubuntu wouldn't mount my flash drive.

Here are my partitions before installing:
[IMG]http://i51.tinypic.com/sb7foz.jpg

Ubuntu recognizes Windows 7 and I choose to install alongside it:
[IMG]http://i52.tinypic.com/2ufx8nd.jpg

The installer does its thing, gets almost to the end, and then this happens:
[IMG]http://i55.tinypic.com/2exljwz.jpg

**^^ It gets stuck there.  I can't click OK, I can't X-out, the installation is frozen. (I can open other programs fine) I've waited a half-hour and I still can't click anything in the installer**

_The last time_ I tried to install (I've tried many times), it got stuck here(same problem, waited 30 minutes, can't click anything):
[IMG]http://i54.tinypic.com/23vz5a0.jpg

I would really appreciate any help![/SIZE]

---

### Post by Quackers on 2011-07-24
It seems that you are using a raid array. You need to install grub to the raid array (ie /dev/mapper/isw_decghhaeb), not /dev/sda. Assuming that the raid array is recognised in the installer.

---

### Post by mooseman99 on 2011-07-24
[SIZE=2]> **Quackers said:**
> It seems that you are using a raid array. You need to install grub to the raid array (ie /dev/mapper/isw_decghhaeb), not /dev/sda. Assuming that the raid array is recognised in the installer.
I am using a raid 0 array

Is there any way to do that manually?  Since the installer freezes?
Could I do like [/SIZE]
sudo mount /dev/mapper/isw_decghhaeb /mnt 
sudo grub-install --root-directory=/mnt/ /dev/sda 


[FONT=Arial][SIZE=2]that's what everyone says to do to install it manually but the second command still has /dev/sda[/SIZE][/FONT]

---

### Post by mooseman99 on 2011-07-24
Update: After 4 more reinstalls I got it to not freeze and tried installing it on isw_decghhaeb_Volume0 and Volume0p1 but neither worked

---

### Post by oldfred on 2011-07-24
I thought with RAID you had to use the alternate install version to have the extra drivers installed. It is a text install version not the gui, but not really different other wise.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

Since it is more text based I do not know if there are a lot of changes or not:
Alternate install example win 10.04:
[http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html)

---

### Post by mooseman99 on 2011-07-25
Thanks Quacker & Oldfred!
The link you sent was old but I found the alternative text-based installer here:
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

when it asked where I wanted to install grub, i said
dev/mapper/isw_decghhaeb_Volume0
and it worked like a charm!  I have windows and ubuntu dual-booting fine now

(actually, first I tried to install grub to dev/sda and it messed up my boot and I had to use bootrec.exe from the windows 7 recovery cd, but that's another story)

thank you so much!

---

### Post by Quackers on 2011-07-25
Nice :-)
The alternate installer is recommended but it seems from my experiments that 11.04 can be installed via the normal live cd if you install kpartx first.

As you have found out mooseman99, if you are using a raid0 array and you write anything to the individual drives (/dev/sda or /dev/sdb, whatever) you will break the raid array. oops.

Well done anyway - it's no mean feat installing to fakeraid :-)

---

### Post by drs305 on 2011-07-25
> **Quackers said:**
> The alternate installer is recommended but it seems from my experiments that 11.04 can be installed via the normal live cd if you install kpartx first.


So you just install kpartx from the LiveCD Desktop, then click the "Install Now" button and run the installation as normal?

---

### Post by Quackers on 2011-07-25
No sir, I tried but no good. I installed kpartx to the live desktop.
I needed to create and format the partitions beforehand (if left the installer can fail during the formatting stage). Then run the installation selecting the /dev/mapper/isw_xxxxxxxx drive for the bootloader and choosing not to format the previously made partitions.
When the installation finished and asked for a restart I did not restart.
I chrooted into the new application and installed kpartx to the new root partition.
Then it was good.

EDIT Please note that I tried this with Intel fakeraid only and with 11-04! 10-10 did not need these steps.

---

### Post by drs305 on 2011-07-25
Thanks for the explanation. I figured it was a bit more complex but hope springs eternal ...  ;-)

---

### Post by Quackers on 2011-07-25
In us all! :-)

---

### Post by YannBuntu on 2011-07-25
Hi
Isn't it an Ubiquity bug that should be reported to Ubiquity's devs on Launchpad ?

---

### Post by Quackers on 2011-07-25
I don't know whether it's a bug or not to be honest. I'm not sure of the actual problem, as such. As has been said already in this thread 10.10 live cd works fine but 11.04 doesn't. Having said that the recommended method is via the alternate installer anyway, but I had problems with getting that to format the partitions as well.

---

