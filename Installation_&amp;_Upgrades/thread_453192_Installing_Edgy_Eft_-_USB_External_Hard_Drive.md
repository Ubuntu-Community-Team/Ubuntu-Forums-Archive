---
title: "Installing Edgy Eft - USB External Hard Drive"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by Mr|C on 2007-05-24
Will someone please, please help.

I'm on my third week of trying to install 6.10 to my Digital Western external usb hard drive. I've followed numerous guides from here and elsewhere on the net and no luck.

When I try to install from the LiveCD, I get an error about not being able to create the partition of ext3.

If anyone can link me to a guide that will work for Edgy Eft, I will be so grateful.

---

### Post by Mr|C on 2007-05-24
Anybody?

---

### Post by Mr|C on 2007-05-24
Please..

---

### Post by Soybean on 2007-05-24
Hmm. Don't know what the problem is, but I saw a post the other day by a guy with a similar problem who switched to ext2 and it worked. So you could try that. 

Also, I think the standard advice would be:
1) Post the exact error message, more information about when it happens, info about your system, etc
2) Try the alternate CD
3) Try it with Feisty

But personally, I'd ignore the standard advice and try the ext2 thing first. ;)

---

### Post by Mr|C on 2007-05-24
I'm at work right now so I don't have the exact error in front of me.

I'll try the alternate CD but I'm sure it wont work. 

I don't want to use Fiesty right now, because I've seen a lot of error with wireless mice and keyboards.

It happens when about 15% through the partitoining.

I'll try making my drive ext2.

Need guides to help me though :
:0 :)

---

### Post by Mr|C on 2007-05-24
I've had a look at [www.pendrivelinux.com](www.pendrivelinux.com) - They have some guides on there. Installing from Linux and from Windows. No guides worked.

---

### Post by Mr|C on 2007-05-24
Help pleaasee :):):)

---

### Post by Mr|C on 2007-05-24
anyone?

---

### Post by confused57 on 2007-05-24
You could try the gparted live cd(approx 45 mb download) & see if you can create an ext3 on your external hd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it's an excellent partitioning tool & may be worth trying...

You might want to open a terminal(Applications---Accessories---Terminal), enter & post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

---

