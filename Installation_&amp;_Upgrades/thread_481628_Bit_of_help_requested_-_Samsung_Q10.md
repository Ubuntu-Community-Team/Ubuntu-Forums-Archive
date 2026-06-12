---
title: "Bit of help requested - Samsung Q10"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by SputSput on 2007-06-22
Hi, 

I'd appreciate a little help/advice

So I've got a Samsung Q10 laptop that I've being playing silly buggers trying to get Feisty installed. I dont know how well it'll perform but I thought I'd give it go.

I'll say now that the disk I've been using came from Linux Magazine but as far as I can tell it's not been altered from the standard ISO.

So, firstly, the install falls over (as do many distros) when trying to find the firewire CD drive. So I tried a network install. I'm running through a ethernet-wireless network bridge for ease on my side. A PXE boot starts well, gets an address but wont download the pxelinux file. It worked once and started the base install and then fell over. I'm sorry to say I didnt get the details of this.

So as windows was installed I tried Wubi. The base system installed a certain amount but then fell over. I tried it twice and it fell over at the same point as the other network install, the first from the GB archives, the second from the default ones. Again, I know I'm not helping myself but I didnt get the details.

So I tried following this, the FromKnoppix install suggestion on the wiki ( [https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix) ) though the base install part said the package wasnt installed.

Today I tried the "Install from Hard Disk" section from here: [http://news.softpedia.com/news/Alternative-Installation-Methods-for-Feisty-53461.shtml](http://news.softpedia.com/news/Alternative-Installation-Methods-for-Feisty-53461.shtml)
I copied the disk to an ext3 primary partition. I'm booting from the ultimate boot CD I have and launching GRUB v0.95 then editting a boot selection to the menu to use what's suggested in the tutorial but not having much luck. The CD structure is on an ext3 parition on hda1 but it when I tell grub to boot this it comes back "file not found" when running the Kernel line.

Anyone got any ideas on the best way to progress? I think the best way would be to get the CD drivers loaded on the install. I've just not got any great idea how I should go about it. I guess sticking them on a HDD partition and pointing the install to them would be the best way to go but I've really no idea what I'm doing on this front.

So, guys, suggestions please.


That was a long first post. Thanks for reading to this point if you did.

Cheers

---

### Post by Ultra Magnus on 2007-06-22
Hi, sorry to hear you're having problems - I had a look around - I was able to find a page from someone who managed to install Linux on the samsumg Q10 - unfortunately its red hat and from a few years ago but I hope it helps - [http://www.linux-on-laptops.com/samsung.html](http://www.linux-on-laptops.com/samsung.html) - It appears he also had trouble with the firewire drive.

If you want to try a boot across the internet and you are using a wireless card then you may need to configure your wireless - I did a network boot a while ago but cant remember whether it lets you access a command lines - if it does, you can try

code : ifconfig 

to find your card - it will be something like eth1 or something

code: sudo ifconfig eth1 up
code: sudo iwlist eth1 scanning

find the connection you are looking for and note its essid - in my case belkin54g

code: sudo iwconfig eth1 essid belkin54g 
code: sudo dhclient 

Hope some of that was helpful!

---

### Post by SputSput on 2007-06-23
Thanks for the tips.

Turns out I could get the install working off the original CD by pointing the installer to /dev/scd0 when it fails to autodetect the drive. If I'd have bothered reading what the installer suggested I might have saved myself a good few hours :)

Never mind. It's all go now. Can't say the rest of the install is going to be ok but that's at least one hurdle hurdled.

Thanks again.

---

### Post by SputSput on 2007-06-23
Well the good news is it installed (eventually), the bad news is the HDD is a bit fscked. A new one is on order.

---

