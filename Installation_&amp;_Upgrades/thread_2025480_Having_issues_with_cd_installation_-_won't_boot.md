---
title: "Having issues with cd installation - won't boot"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by amorris28 on 2012-07-14
Hey ya'll

So I built this computer about six months ago and was running Windows 7 on it. Now I need to replace the OS for various reasons and I'm attempting to install Ubuntu.

I have an 11.01 cd that I have used to put Ubuntu on my laptop no problem. Now, trying to put it on my desktop I get an error message "terminated by signal 9 (Killed)" and the installation never happens. I found [this post]("http://ubuntuforums.org/showthread.php?p=12101914#post12101914"), but didn't understand the solutions that were being discussed.

I tried adjusting the F6 boot parameters on the install screen to no avail. I heard that there might be a hardware problem installing with an nvidia gpu (I have a GTX 550 Ti). It was also suggested that I try an md5sum and compare the hash to [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes"), but I can't figure out how to check the cd hash.

After getting that far, I decided to try downloading the latest distribution and burning a new cd, so I downloaded 12.04 x64 and burned that and tried to boot from it. However, when I try to install this, I get a blank screen with just a flashing cursor. I checked the 12.04 iso hash and it matched the above webpage.

Sometimes, I get the purple screen with "Ubuntu 12.04" and four flashing dots, but that just leads to a screen with "BusyBox v1.18.5 ... built-in shell (ash)" followed by "(initramfs) unable to find a medium containing a live file system". Just now, I tried using the nomodeset parameter and instead got (initramfs) without the following text.

I googled my problem along with relevant error messages, I searched the forum for posts with similar problems, I asked around the ubuntu IRC channel, and I tried solutions to the best of my computer abilities. However, if I found 12 different pages with someone asking a similar question then I found more than 12 different suggested solutions without a working fix.

Can anyone help me out with this?

Thank you so much,
Amorris

---

### Post by jmfal on 2012-07-14
Welcome to Ubuntu
Take a look at this

[http://www.proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/](http://www.proposedsolution.com/solutions/ubuntu-booting-to-initramfs-prompt/)

---

### Post by amorris28 on 2012-07-14
Checked out that page.

Now the 12.04 disc doesn't reach the install screen. After I boot from the disc drive it gives me this message:

isolinux found something at drive f2 
isolinux found something at drive a0

which is sometimes followed by

Loading bootlogo...

And it gives me a flashing cursor, but I can't input commands. I can only ctrl+alt+del to reboot.

Also, tried the 11.10 disc again and I'm still receiving the "terminated by signal 9" message. Not sure where to go from here.

---

### Post by jmfal on 2012-07-14
Try rebooting to grub >> recovery kernal >> low graphics mode >> to get to desktop

ckeck to see if video drivers is installed

```
lspci -nnk | grep -A2 VGA
```

And post results between [CODE][CODE]  brackets using #

---

### Post by efflandt on 2012-07-15
For 12.04 install with nvidia graphics, try enabling **nomodeset** in the F6 parameters (spacebar to X it).  I had to do that for GTX 550 Ti.  No kernel parameters needed after install.

11.10 was somewhat opposite.  I don't think I need nomodest during install, but definitely had to use it for installed system (in /etc/default/grub).

---

