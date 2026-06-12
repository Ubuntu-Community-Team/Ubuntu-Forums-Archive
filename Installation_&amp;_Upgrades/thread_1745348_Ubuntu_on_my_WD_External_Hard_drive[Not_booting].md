---
title: "Ubuntu on my WD External Hard drive[Not booting]"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by worldblackstar on 2011-04-30
I have recently installed the ubuntu in my WD External Hard drive.  I have follow the instructions and partition as 
100mb /boot primary 
4gb swap area logical
10gb /home logical
10gb /root logical 
specified the grub installation in external HDD.

after installation.  Ubuntu is not booting from external hard disk.  it is not detected at all.  My external HDD is working fine.  

My questions are:
What mistake i am doing here?
Is there any other thing to do?

---

### Post by Hedgehog1 on 2011-05-01
**You are just about there** - because each hard drive is isolated, you need to use the 'Boot Selector' from your computers BIOS.

The F12 key allows me to select it on my office Computer.

The F11 Key allows me to select it on my home desktop Computer.

The F8 Key allows me to select it on my home laptop Computer.

You may need to mess about with rebooting to find the right key - when you get it you will see a list of drives to boot from. Select the external and away you go!

***The Hedge***

:KS

---

### Post by worldblackstar on 2011-05-01
I forget to include this information:

I give the first priority for wd book by prossing F2 .

When i load the ubuntu from pen drive,it is working fine. 

But when i boot from wd external hard drive, it fails

---

### Post by Dutch70 on 2011-05-01
Lets have a look at your boot info script. Someone should be able to help if I can't, but we will need to see this.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step or you will lose the formatting & I doubt if anyone will even look at it.

---

### Post by worldblackstar on 2011-05-05
I can't  understand what you are saying.  Anyone have experience of wd external hard disk with ubuntu? If so please help me to boot.

---

### Post by valuta on 2011-05-12
I have the same problem. And previously I was using a freecom 40gb drive with external power supply (Yes a really old device) Works like heavens with Ubuntu 10.10, Cause of the hassle having to plug it in to a power source I decided to go for an upgrade and bought a 1TB WD my passport.

I tried installing a live ubuntu, and a full fledged version. I got stuck after trying to select the device to boot from (f8) there were 2 WD drives to choose from, tried both one gave a black screen the other one a blinking _.

This happened with both the Live 10.10 and a full fledged 10.10 (installed from an official ubuntu disc.)

If it just WD messing with my new drives?
I'm quite sure I haven't done anything wrong since my actions worked before.

I hope this information will make it easier to find a lot of people a fix...

@hedge
that's where I got stuck --read above--

@dutch
Do you mean the live used for installing it to the hard drive or the one on the hard drive (the last one is not one since he used a swap area.)

---

### Post by wkulecz on 2011-05-12
Depending on which WD external drive you have, it may have a "CDROM" partition with mostly useless windows software :(.  

This will mess things up if you have the CDROM boot priority higher than the external device in your BIOS.  It also may just generally mess things up because of the non-standard partiton table that Linux may not currently be able to deal with.

I hated it and had to use a windows system to download and run a removal utility from the Western Digital web site.  I believe it wipes your data if you run it so its another hassle to contend with.

---

### Post by valuta on 2011-05-12
I used my old linux to fully format the drive (remove all partitions and have ubuntu put itself into place so there were no other partitions at all.
It used to have that partition, but that one is now gone, could you link to that page, it might be quite useful for people who don't like to mess around with formatting drives.

---

