---
title: "Install doesnt recognise previos system"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by loseby on 2010-04-04
Have a 120g Solid State Drive and 500 gig sata drive. When I go to install 9.10 it is slow and when it gets to the partitioner it shows a message something like "Computer doesn't have an O/S on it"  ... now the partitioner shows the 120g SSD and it shows the 500 gig sata as the drive to be installed on which I want but 

If it doesn't recognise the previous system then I assume it wont install GRUB on my boot drive ie. the SSD and if does recognise the SSD as the boot drive then it wont add Win7 as an alternative system to boot to.


any suggestions

---

### Post by sikander3786 on 2010-04-04
> **losbey said:**
> Have a 120g Solid State Drive and 500 gig sata drive. When I go to install 9.10 it is slow and when it gets to the partitioner it shows a message something like "Computer doesn't have an O/S on it"  ... now the partitioner shows the 120g SSD and it shows the 500 gig sata as the drive to be installed on which I want but 

If it doesn't recognise the previous system then I assume it wont install GRUB on my boot drive ie. the SSD and if does recognise the SSD as the boot drive then it wont add Win7 as an alternative system to boot to.


any suggestions

Hi.

Is your Win 7 installation booting fine? I mean if it has its boot loader in MBR of the SSD drive you are mentioning, Ubuntu should see it.

No matter what is happening just go through with the installer until the very last step where it asks you to re-confirm all the configuration. You should see a button labelled "Advanced Configuration" or something like that. There you will be able to select the drive you want to install GRUB on.

Recognize your HDD and set the option to "sda" or "sdb" which ever is your 120 GB SSD and proceed with the installer.

And you will be able to add your Win 7 installation to the GRUB menu later.

There are lots of threads about GRUB 2 configuration.

And still the community is there if you have any further problems.

Hope it helps.

Sikander.

---

### Post by loseby on 2010-04-07
tried it on my main commputer after swapping DVD drives ( different problem ) and get the same message so its not the SSD drive unless the WD Raptor suffers the same problem as SSD  ie. dont recognise non standard drives

Or is there a problem with Win7 and Ubuntu ?   I dont want to play around with my Win7 installation . I would like GRUB on the raptor and Ubuntu on my 640 gb hard drive ( 200 gig for Ubuntu and the rest for Windows .

Now if I select the 640 GIG drive and partition it the way I want it will most probably put the GRUB on that drive and I would have to make that the boot drive and then somehow modify GRUB so it gives me a choice of booting WIN7. 

Also I have some data on that drive and am worried that when I partition it wont recognise the data / programs I have on it.

edit...tried again with same result. Here is the actual message 

[COLOR="Red"]The computer has no operating systems on it[/COLOR]

and the drive that Win7 64 BIT is on shows as this

[COLOR="Red"]SCS13 (sda) - 300.1 GB ATA WDG WD300HLFSD-O[/COLOR]

So maybe it wont recognise win7 because its 64 bit ?

---

### Post by loseby on 2010-04-09
[COLOR="Red"]from IPW in the ocau forums I got this[/COLOR]

sudo update-grub

Now that put win7 into grub but on booting to it got "invalid signature"

[COLOR="Red"]and IPW from ocaufound the following link that fixed the problem
[/COLOR]
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8262566&postcount=18]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8262566&postcount=18")

> [I] Re: Grub "Invalid Signature" error when booting windows
I had this same problem after and update to Ubuntu 9.10. Took forever to find solution - nothing on this thread worked, but lead me in right direction.
Noticed when I did sudo update-grub it came back with weird errors so did this:
sudo apt-get install os-prober
sudo os-prober, made sure it showed both linux and windows
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
sudo update-grub (came back clean)
reboot (all is well)[/I]

---

