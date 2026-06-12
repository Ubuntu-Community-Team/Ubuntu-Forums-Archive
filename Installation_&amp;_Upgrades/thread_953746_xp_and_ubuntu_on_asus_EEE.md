---
title: "xp and ubuntu on asus EEE"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by koenws on 2008-10-20
Hello,

I am trying to install Windows XP and ubuntu on my asus eee 900. Both OS are special eee versions. The laptop has two drives, one of 4GB and one of 16GB. 

The only time when this dual boot actually works is when I install xp on the 4GB drive and let ubuntu use the full 16GB drive. But then there is hardly any space left. 

When I install ubuntu on the 4GB drive, it is impossible to install xp on the 16GB, probably because the OS is slightly bigger than 4GB and changes something to the 16GB drive.

I tried to create partitions with partition magic, but the manual drive configurations during the installation of ubuntu doesn't work. In the full installation setup of Ubuntu, I am unable to choose those partitions. 

The next thing I did was to install XP on the 16GB drive, and then use wubi to install ubuntu. When I finally thought I had the anwer, the following error showed up on start-up: 

*Reboot and select proper Boot device or Insert boot media in selected boot device and press a key*

I am out of ideas here, does anybody know how to solve this?

---

### Post by 22flames on 2008-10-20
I have an asus and honestly go windows for the bigger partition and i would simply use a usb hdd or use a usb stick for the ubuntu bc its small and let windows hog all the leftover good luck what ever you chose though :)

22FLAMES

---

### Post by koenws on 2008-10-20
But wubi said that ubuntu needs a minimum of 5GB. Is there no way to install both OS on the hard drives?

---

### Post by 22flames on 2008-10-20
there is but i would reccomend installing windows first ..... no cd drive so it would be difficult to install full ubuntu if you can get your hands on a usb cd drive you could just do a dual boot but as is i dont know how you could do it i would get a usb cd drive i have one.:)sry

22FLAMES

---

### Post by koenws on 2008-10-20
Fortunally, I have a USB DVD Drive. But I'm tired of installing windows over and over again, just so that the UBunto installation srews it all up again. I really need this to work, I need both operating systems withouth the loss of 12GB. How can I install Ubuntu on the 16GB drive without the whole drive being used? partition magic didn't work, so did wubi. Is there another way?

---

### Post by 22flames on 2008-10-20
well you could install but make the ubuntu partition 4 or so gigs and make the left over a ntfs partition and store your windows files on that than install windows to the other drive.... :(

22FLAMES

---

### Post by koenws on 2008-10-20
how do you make the Ubuntu installation 4 gig, I only got that option with wubi but then I got the rare error. Howerer, I could try to install xp on the 4GB, then use wubi to install ubunto on the 16GB drive with about 5GB of room. Hopefully I won't get the error because the operating systems are installed on different drives. :-k I think I'll try that first.

---

### Post by 22flames on 2008-10-20
thats what i was saying . and you can make it smaller by just installin it on a smaller partition. :)

22FLAMES

---

### Post by caljohnsmith on 2008-10-20
Have you tried to create partitions with Ubuntu's partition editor "gparted"? Can you use your USB DVD drive to boot the Ubuntu Live CD? If you can, boot all the way into the Live CD (use the "try Ubuntu without changing anything" type option), and when you get to the Ubuntu desktop, press ALT + F2 and type:
```
gksudo gparted
```
And try using gparted to partition your 16 GB drive.

---

### Post by quicksiedo on 2008-10-26
Hi, I've got a question too! 

I've got XP installed on the 16gb SSD of my 901 and I'd like to have ubuntu eee installed on the 4gb SSD. I've gone onto the ubuntu installer but it says that it will wipe everything off everywhere, and I don't want to lose my xp stuff.

Ideally I'd have a large SDHC (16 or 32gb) for ubuntu and xp to share for the home directory and for excess xp stuff.

Is this possible?

Matt :)

---

### Post by caljohnsmith on 2008-10-26
> **quicksiedo said:**
> Hi, I've got a question too! 

I've got XP installed on the 16gb SSD of my 901 and I'd like to have ubuntu eee installed on the 4gb SSD. I've gone onto the ubuntu installer but it says that it will wipe everything off everywhere, and I don't want to lose my xp stuff.

Ideally I'd have a large SDHC (16 or 32gb) for ubuntu and xp to share for the home directory and for excess xp stuff.

Is this possible?

Matt :)
When you go through the Ubuntu installer, choose the "manual" option to set up your partitions, and you should be able to select your 4 GB SSD card to install Ubuntu to; you just need to make sure you select the correct drive (the 4 GB SSD card), and your XP drive should be fine. One important caveat though: at the end of the installation, be sure to click the "advanced" button and tell Grub (Ubuntu's boot loader) to install to /dev/sdb or whichever is your 4 GB SSD card, so that Grub doesn't get installed to your Win XP drive. 

And about your SDHC card, I'm not familiar with using them, but if you can read/write to it and boot it, then I don't see why you couldn't use it for both Ubuntu and XP. :)

---

### Post by quicksiedo on 2008-10-26
Great, thanks for the help. Only problem is that I'm pretty much an absolute beginner when it comes to /this/that so I'm a bit confused. Could you point me in the right direction for understanding how to choose where the ubuntu installation goes please?

Thanks in advance :)

---

### Post by caljohnsmith on 2008-10-26
> **quicksiedo said:**
> Great, thanks for the help. Only problem is that I'm pretty much an absolute beginner when it comes to /this/that so I'm a bit confused. Could you point me in the right direction for understanding how to choose where the ubuntu installation goes please?

Thanks in advance :)
When you go through the Ubuntu installer, at some point near the beginning it lets you specify which drive you want to install Ubuntu to. The drives will be labeled like /dev/sda for your first internal HDD, then /dev/sdb for an external drive (probably your SSD or SDHC card), and so on, and it will show you the drive sizes so you can probably easily figure out which drive is which. It's been so long since I've been through the installer that I can't really give you more specific advice than that, other than what I mentioned in my previous post. :) You might find this webpage helpful since it has a good guide on installing Ubuntu:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

See if that is enough to help you, otherwise let me know. :)

---

### Post by quicksiedo on 2008-10-26
thanks, I'm almost ready to take the plunge! I've chosen my 4gb SDD as the install location with a partition with a mount point of "/". I'd like to use my SDHC card for "/home" but I don't actually have it yet. Will it be alright to install ubuntu without a "/home" partition and then just make one later or will it just not run without the "/home"?

Matt :)

---

### Post by quicksiedo on 2008-10-26
thanks, I'm almost ready to take the plunge! I've chosen my 4gb SDD as the install location with a partition with a mount point of "/". I'd like to use my SDHC card for "/home" but I don't actually have it yet. Will it be alright to install ubuntu without a "/home" partition and then just make one later or will it just not run without the "/home"?

Matt :)

---

### Post by caljohnsmith on 2008-10-26
> **quicksiedo said:**
> thanks, I'm almost ready to take the plunge! I've chosen my 4gb SDD as the install location with a partition with a mount point of "/". I'd like to use my SDHC card for "/home" but I don't actually have it yet. Will it be alright to install ubuntu without a "/home" partition and then just make one later or will it just not run without the "/home"?

Matt :)
Yes, you can install Ubuntu without a /home partition, and the installer will just include /home in the main root "/" partition. I'm almost sure it's not a big deal to move your /home to another drive and just mount it in Ubuntu, but since I've never done it myself, I can't say 100% for certain (I can't think of any "gotchas" though). Let me know how your installation goes. :)

---

### Post by Patb on 2008-10-27
> **caljohnsmith said:**
> Yes, you can install Ubuntu without a /home partition, and the installer will just include /home in the main root "/" partition. I'm almost sure it's not a big deal to move your /home to another drive and just mount it in Ubuntu...
Yes, that's true. And Psychocats comes to the rescue again: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Hope this helps.

Cheers, Pat.

---

### Post by quicksiedo on 2008-10-29
Right, here's an update:

I ran the installer leaving the home directory on the 4gb drive and it worked fine! Then I started looking for a way to move the home to an SDHC card. Unfortunately it seems that many other people have had lots of problems with this so I figured that it would be less hassle just to reinstall ubuntu eee and set the SDHC card as /home right from the start.

The problem with the Ubuntu eee distro is that it can't mount external media out of the box, meaning that as I had set up my SDHC as my home, it couldn't start up because it couldn't find the home! I was about to ask you for some more help because everytime i started up I got this error and it wouldn't let me past the log on screen... but on the thrid attempt, it just worked! Now everything works flawlessly :)

Thanks for all your help!

p.s. i formatted ubuntu and the SDHC to ext2 and got a driver from fs-driver.org to allow windows to read (with the option of write too) from the ubuntu SSD and the SDHC. This way the xp and ubuntu are on separate SSDs and share the 32gb SDHC for all their media :grin:

---

