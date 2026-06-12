---
title: "How to upgrade Ubuntu 10.10 server to the latest working edition?"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-01-14
Hi folks,

I have Ubuntu 10.10 server (64bit) running as guest on Oracle VirtualBox.  It is for testing only.  I expect to upgrade it to the latest version.  I found following document;

How to upgrade from Ubuntu 10.04, 10.10, 11.04 to Ubuntu 11.10 Oneiric Ocelot | Desktop & Server
[http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/](http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/)

Would it be relevant for my application?

"update-manager-core" already installed
/etc/update-manager/release-upgrades
Prompt=normal

Thanks in advance.

B.R.
satimis

---

### Post by MAFoElffen on 2012-01-14
> **satimis said:**
> Hi folks,

I have Ubuntu 10.10 server (64bit) running as guest on Oracle VirtualBox.  It is for testing only.  I expect to upgrade it to the latest version.  I found following document;

How to upgrade from Ubuntu 10.04, 10.10, 11.04 to Ubuntu 11.10 Oneiric Ocelot | Desktop & Server
[http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/](http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/)

Would it be relevant for my application?

"update-manager-core" already installed
/etc/update-manager/release-upgrades
Prompt=normal

Thanks in advance.

B.R.
satimis
Yes. If you initially installed Server 10.04, /etc/update-manager/release-upgrades is going to say "prompt=lts".  That you'll have to change to "prompt=normal".  Update and Upgrade before doing any do-release-upgrade. 

Upgrading the update-manager-core is a safety thing... going 9.10 to 10.04, it was a requirement. 10.10 through 12.04, it doesn't seem to be needed. I rarely see it doing anything.

Reboot after making the update/upgrades and you should see a message after login saying a newer release is available. The so a do-release-upgrade. After it is done, do an update/upgrade to make sure is has current updates. Reboot, repeat.

---

### Post by satimis on 2012-01-15
Problem after upgrade

VM on VirtualBox

during upgrade
grub install devices:
[*] ~ /dev/sda1 (254MB; /boot)

after reboot
error: symbol not found 'grub_env_export"
grub rescue>ls
(hd0) (hd0,msdos5) (hd0,msdos1)

I think I put a wrong path for grub.  I don't have a liveCD.  Please advice how to fix the problem.  TIA

B.R.
satimis

---

### Post by darkod on 2012-01-15
The grub bootloader usually goes to the MBR, which is /dev/sda.

Not a partition which contains the partition number after sda.

Even if you are running only the server edition it's better to have a live cd at hand for fixes. Can you download the desktop image? IN VM you should be able to boot from the ISO directly, even without actually burning a CD. But if necessary burn a CD and boot the VM with it.

Then post the list of your partition you can get with:
sudo fdisk -l (small L)

---

### Post by darkod on 2012-01-15
According to this you can boot from the grub rescue prompt as long as the other files are present:
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)

You can try booting like that. If you manage to do it, just install grub2 again to the MBR with:
sudo grub-install /dev/sda

Note: The above would only work if you manage to boot your system from the rescue prompt. It does not work from live mode.

---

### Post by MAFoElffen on 2012-01-15
> **darkod said:**
> The grub bootloader usually goes to the MBR, which is /dev/sda.

Not a partition which contains the partition number after sda.

[COLOR=Red]Even if you are running only the server edition it's better to have a live cd[/COLOR] at hand for fixes. Can you download the desktop image? IN VM you should be able to boot from the ISO directly, even without actually burning a CD. But if necessary burn a CD and boot the VM with it.

Then post the list of your partition you can get with:
sudo fdisk -l (small L)
Agreed. I use LiveCD's for maintenance and fixes on my 5 home servers. Easy on tweaks, fixes and rescues.

Easy on you- is that your install is VM and can just select the ISO in VM as being in your VM CD Drive..  Boot your VM on it and reinstall Grub from it.

---

### Post by satimis on 2012-01-16
> **darkod said:**
> According to this you can boot from the grub rescue prompt as long as the other files are present:
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)

You can try booting like that. If you manage to do it, just install grub2 again to the MBR with:
sudo grub-install /dev/sda


Hi,

I tried follows before posting without results.

1. set prefix=(hd0,1)/boot/grub
The Ubuntu system is on sda1
2.* set root=(hd0,1)
3. insmod normal
4. normal

On 3) above it complained no system found.

grub rescue>ls > 
(hd0), (hd0,msdos5) (hd0,msdos1)


satimis

---

### Post by satimis on 2012-01-16
> **MAFoElffen said:**
>  -snip-

Easy on you- is that your install is VM and can just select the ISO in VM as being in your VM CD Drive..  Boot your VM on it and reinstall Grub from it.

Hi,

Thanks for your advice.

The VM was cloned on another VM.  All installations were made direct on Internet.

satimis

---

