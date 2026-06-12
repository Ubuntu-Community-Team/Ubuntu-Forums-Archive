---
title: "Stuck on 3/7 ubuntu 10.04 installation."
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by De5 on 2012-12-14
I have an acer aspire one, and I am planning to turn it into a desktop computer. Half the keyboard doesn't work, battery is broken, and mousepad is unresponsive 90% of the time. 
Anyways, I am getting ubuntu 10.04 because I think its the only one that can run on my acer netbook. I went to boot it up and it worked without installing yet, just the "try now" option. I tried installing and when I get to step 3 (keyboard layout/settings), I click next and it just keeps loading. I left it on for 1 hour and nothing changed. I can't use a CD to install it, because it's a netbook. So I am using a usb. Is the USB the problem? Any solutions to this? 

Thanks to whoever read this.

---

### Post by chadk5utc on 2012-12-14
Installation from USB on a netbook can be really slow

---

### Post by De5 on 2012-12-14
> **chadk5utc said:**
> Installation from USB on a netbook can be really slow

Thanks for the quick reply, do you know how long it will take?

---

### Post by chadk5utc on 2012-12-14
that mostly depends on the hardware how much ram the PC has? if its installed from a thumb drive? or usb cdrom? the rom of course would be the way to go if you had one available. If not it can be done with a thumb drive Im not sure how long really it can vary? I had an external cdrom which worked great on mine(Asus1000HE) with SSD and max ram.

In the even you said there was a keyboard issue try using a usb keyboard so the internal one doesnt cause delay?

---

### Post by sudodus on 2012-12-14
> **chadk5utc said:**
> ...
In the even you said there was a keyboard issue try using a usb keyboard so the internal one doesnt cause delay?

+1

It is important to have at least one working keyboard and is nice but not necessary to have a working mouse too during installation and of course later on. I don't know what problems could be caused by the fact that the built in keyboard and touchpad are faulty.

In my experience it is as fast to install from a standard USB pendrive as from a CD/DVD drive.

In case it won't work to install like this, check a couple of things:

1. How many primary partitions are there on the internal drive? If four, you can't create another one for Ubuntu. There are ways to get around it, but check when booted from a live session with the install Ubuntu USB drive! Use ***gparted*** or
```
sudo fdisk -lu
```

2. Can you take the internal drive out of the netbook? If it is a standard 2.5" HDD, it should be possible. Then you can install Ubuntu into the HDD attached to some other computer. As long as you don't install any proprietary drivers, it should work nicely after re-installation into the netbook. And the fully installed Ubuntu system should recognize keyboard and mouse via USB.

---

### Post by De5 on 2012-12-14
Just had it on step 3 of 7 for 12 hours, still didn't move on to step 4.... Gonna try ubuntu 11.04 and see what happens

EDIT: It is a 2.5 HDD but I tried taking it out. Pretty much impossible. Also It has Windows Xp on it, which is now not working. On the loading screen it just keeps... loading.. I was planning to erase my whole HDD now that I transferred all my stuff to another computer and just use ubuntu.

---

### Post by chadk5utc on 2012-12-14
+1 to Sudodus

Have you tested the install media that your using? there is a couple ways that you can test your installer.
1 check the md5sums for integrity
2 when the installer starts you get the option to test media I forget the exact wording?
as with any software it can and sometimes should be tested to ensure its integrity. It could be(likely or not) that the file your installing from is bad or was corrupted during the download process?? just another thought.

---

### Post by De5 on 2012-12-14
> **chadk5utc said:**
> +1 to Sudodus

Have you tested the install media that your using? there is a couple ways that you can test your installer.
1 check the md5sums for integrity
2 when the installer starts you get the option to test media I forget the exact wording?
as with any software it can and sometimes should be tested to ensure its integrity. It could be(likely or not) that the file your installing from is bad or was corrupted during the download process?? just another thought.

Completely forgot to mention, I had this same problem a year ago on the same netbook, when the keyboard and mousepad was fully working. Believe me, I tried everything I could. I just put XP on it and it worked perfectly.

---

### Post by chadk5utc on 2012-12-14
> **De5 said:**
> Completely forgot to mention, I had this same problem a year ago on the same netbook, when the keyboard and mousepad was fully working. Believe me, I tried everything I could. I just put XP on it and it worked perfectly.

do you have a way to install the laptop drive into your desktop? or laptop drive adapter. I have had great luck with netbooks running linux

---

### Post by sudodus on 2012-12-16
How many primary partitions are there on the internal drive? If four,  you can't create another one for Ubuntu. There are ways to get around  it, but check when booted from a live session with the install Ubuntu  USB drive! Use ***gparted*** or
```
sudo fdisk -lu
```

---

### Post by Topsiho on 2012-12-16
I have an acer aspire one, with an 8GB SSD, and it works well, though rather sluggishly, with Ubuntu 12.04.1. I let the Ubuntu installer decide how the SSD (hard disk) should be partitioned, it has a / partition of 7 GB, and a /swap partition of 1 GB.

Usually, on larger disks, I do the partitioning myself, but not on this very small one.

I also tried Lubuntu, and Xubuntu, but as I like to use Firefox and LibreOffice, there was not so much gain, speaking of speed.

I think, if you try to put Ubuntu next to Windows (dual boot), on a too small disk, that there is not room enough to copy the necessary files onto the disk, and start the install. The install stops perpetually.

As far as I remember changing the disk is a no-go area, if you are not experienced in opening up a notebook physically way to the very limit. There are descriptions how to do this, on the web, for my Aspire One at least, but I feel way too fainthearted for that.

Topsiho

---

### Post by Topsiho on 2012-12-16
I forgot to mention that 10.04 is not worth the trouble of installing anymore, as the support for 10.04 will end in April next year.

Topsiho

---

