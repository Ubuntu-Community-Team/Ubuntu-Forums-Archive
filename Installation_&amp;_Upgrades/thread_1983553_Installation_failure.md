---
title: "Installation failure"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by TaKsi on 2012-05-20
Hi!

Trying to install ubuntu 12.04 on my pc but i get this screen.  :(
first try'd it with a usb-stick then try'd it with a dvd same problem 
try'd to instal 11.10 to.
i'm trying to convert my parents to use ubuntu instead of windows :P
doing a half-assed job for now :lolflag: but yeah

computer specs;
AMD Athlon 64x2 Dual core processor 4400+ 2.3Ghz
Nvidia Geforce 210  512MB RAM

Pretty basic thing as you may know but yeah they dont need much...

please help so i can make two more ubuntu followers/believers :P

thanks!


[ATTACH]218338[/ATTACH]

---

### Post by grahammechanical on 2012-05-20
Did you run Ubuntu as a live session first? How did that go? Is this what happens when you select Install at the welcome screen? Please tell us in detail what you see on the screen up until the point when these messages appear.

From the information that you give it is not clear if this is happening during the loading of the live session, the install process, or the first reboot to load the Ubuntu desktop.

Regards.

---

### Post by miegiel on 2012-05-20
What **[color=#dd4814]grahammechanical[/COLOR]** said + Can you boot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode"), or does that crash too?

---

### Post by jadtech on 2012-05-20
looks clear to me any how  they have tried the dvd and USB and this is what they get trying to boot live disk ..

---

### Post by miegiel on 2012-05-20
> **jadtech said:**
> looks clear to me any how  they have tried the dvd and USB and this is what they get trying to boot live disk ..

I was thinking it was after the installation :) Anyway ... checking the DVD/USB for disk errors might be a good idea too (it's one of the options in the menu after you boot the installation disk).

---

### Post by TaKsi on 2012-05-21
> **grahammechanical said:**
> Did you run Ubuntu as a live session first? How did that go? Is this what happens when you select Install at the welcome screen? Please tell us in detail what you see on the screen up until the point when these messages appear.

From the information that you give it is not clear if this is happening during the loading of the live session, the install process, or the first reboot to load the Ubuntu desktop.

Regards.

No welcome screen, first i get the screen with the little icons at the bottom, then it gives a pinking stripe ( don't know if that is the right way to say it :p) and then i get the other screen
I never even get to a welcome screen :lolflag:

I've taken a few new photo's maybe this helps

[ATTACH]218376[/ATTACH]


[ATTACH]218375[/ATTACH]


Thanks

---

### Post by miegiel on 2012-05-21
> **TaKsi said:**
> [ATTACH]218375[/ATTACH]

Those icons mean something like "For human intervention, press any key".

Press a key and you'll get the liveCD boot menu. One of the options is to check the installation disk for errors. Try that first.

Can you also shed some light on how you put the liveCD on a USB stick (there are several methods), did you wipe the USB disk before putting the .iso on it, etc.

---

### Post by TaKsi on 2012-05-21
> **miegiel said:**
> Those icons mean something like "For human intervention, press any key".

Press a key and you'll get the liveCD boot menu. One of the options is to check the installation disk for errors. Try that first.

Can you also shed some light on how you put the liveCD on a USB stick (there are several methods), did you wipe the USB disk before putting the .iso on it, etc.


:lolflag: first cup of ubuntu here! :P

I pressed a button :P and try'd everything and they all go to the screen with the blinking stripe, disk error test also, and then i get the same screen as in my first post.

Only the memory test works did it no errors...

the usb disk was formatted and i used it for two other computers (laptops) without problems...

:confused:

---

### Post by miegiel on 2012-05-21
> **TaKsi said:**
> :lolflag: first cup of ubuntu here! :P

I pressed a button :P and try'd everything and they all go to the screen with the blinking stripe, disk error test also, and then i get the same screen as in my first post.

Only the memory test works did it no errors...

the usb disk was formatted and i used it for two other computers (laptops) without problems...

:confused:

Ok, I guess it's safe to assume there's nothing wrong with the USB stick. I don't think your parent's PC has memory troubles, or else they would have had issues running windows too.

My 1st suspect would be the graphics card. If the motherboard has onboard graphics you can try installing ubuntu without it or temporarily using a different card and sticking it back after installing and updating ubuntu and (if necessary) installing nVidia's proprietary drivers. There are also alot of threads in the forum from people having trouble with nVidia graphics cards, maybe you can find inspiration in one of those threads (just be wary of really old threads with old solutions).

Alternatively you can remove all the hardware you don't need to install ubuntu and after installing and updating it, stick the hardware back one by one.

---

### Post by oldfred on 2012-05-21
You mention nVidia. That requires the nomodeset on liveCD and first boot after install until nVidia drivers are installed.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
**To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.**
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by TaKsi on 2012-05-22
> **oldfred said:**
> You mention nVidia. That requires the nomodeset on liveCD and first boot after install until nVidia drivers are installed.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
**To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.**
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu



Hi, 

No modeset 'try ubuntu without install' gives a blinking stripe
No modeset 'acpci_osi= Back to 'first post' screen 
No modeset 'linux' same
No modeset no acpi - go's further and gives this screen first 

[ATTACH]218460[/ATTACH]

then this 

[ATTACH]218461[/ATTACH]

and then go's further to linux but is unbelievably slow...

so try'd 'no acpi' and 'irqpoll' as suggested by linux screen, graphics are alot faster :guitar:

linux is installed but can't get into low graphics mode

try'd as you said the nomodeset change

then try'd the changes i did - nomodeset no acpi irqpoll -

but wont go further then the screen i attached :|

[ATTACH]218462[/ATTACH]

i must be doing something wrong :mad:

...

---

### Post by oldfred on 2012-05-22
With 512MB of RAM you are at the lower end of full Ubuntu. You could try Lubuntu or Xubuntu?

It does look like it is taking a long time and having issues with something. Whatever settings you need to get liveCD to work are required to get first boot to work and many times then you have to add those parameters to grub for every boot.

---

### Post by TaKsi on 2012-05-22
> **oldfred said:**
> With 512MB of RAM you are at the lower end of full Ubuntu. You could try Lubuntu or Xubuntu?

It does look like it is taking a long time and having issues with something. Whatever settings you need to get liveCD to work are required to get first boot to work and many times then you have to add those parameters to grub for every boot.


the 512 MB ram is from the graphics card... sorry
i have 3GB of RAM 

Is there somewhere i can see which settings i used to boot ?

regards

---

### Post by oldfred on 2012-05-22
All the data that goes by on the screen is in the log files. That sometimes can tell if some driver is repeatly trying to load and then failing, or some partition or driver that takes forever to load.

There is log file viewer to look at log files and they are in /var/log and some applications in folders in that folder.

---

### Post by TaKsi on 2012-05-22
> **oldfred said:**
> All the data that goes by on the screen is in the log files. That sometimes can tell if some driver is repeatly trying to load and then failing, or some partition or driver that takes forever to load.

There is log file viewer to look at log files and they are in /var/log and some applications in folders in that folder.


How can you use a log file viewer without beeing in ubuntu?

I'm still a newby sorry   :redface:

:p

---

### Post by wildfire365 on 2012-05-22
I have downloaded Ubuntu 12.04 and I can't get it to boot. I have  a computer with windows on it and wanting to put Ubuntu on it but can't get it to start booting have nothing starting at all. I put the disk in and hit F12 to get to the boot option and nothing happens for a while then it boots to windows. Any help will be great Thnaks.

---

### Post by TaKsi on 2012-05-22
> **wildfire365 said:**
> I have downloaded Ubuntu 12.04 and I can't get it to boot. I have  a computer with windows on it and wanting to put Ubuntu on it but can't get it to start booting have nothing starting at all. I put the disk in and hit F12 to get to the boot option and nothing happens for a while then it boots to windows. Any help will be great Thnaks.


not really on topic :P 

do you use a dvd or usb?
you can also change your booting device in the cmos setup utility

---

### Post by oldfred on 2012-05-22
If not booting, you can mount the install partition and manually view the files.

# change example of sda1 to your install partition
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
cd /mnt/sda1/var/log
# show all the log files (many)
ls
# view dmsg
gksudo gedit /mnt/sda1/var/log/dmesg

---

### Post by TaKsi on 2012-05-22
> **oldfred said:**
> If not booting, you can mount the install partition and manually view the files.

# change example of sda1 to your install partition
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
cd /mnt/sda1/var/log
# show all the log files (many)
ls
# view dmsg
gksudo gedit /mnt/sda1/var/log/dmesg


do i have to create a boot partition as said here?

[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

or do you mean something else... :redface:

---

### Post by oldfred on 2012-05-22
I do not recommend boot partitions unless you have an old computer that can only boot from the first 137GB or possibly servers or server like installs with RAID or LVM. 

The mount I show above is just to see if you install has info in the log files to view on booting errrors. If not installed then there is nothing to view. The installer does not preserve the logs, but may have them until you reboot? Never checked.

---

