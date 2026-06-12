---
title: "Help with installation"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by thatguy93 on 2011-07-22
Hey guys,
I decided to install linux on another one of my IBM R52 laptops.
But this time I seem to be having an issue.
I followed all the steps correctly from the Ubuntu download page. Put Ubuntu on a USB with the suggested program. 

Now I boot from USB, and all I get is a black screen that says:

> SYSLINUC 4.04 EDD 2011-04-18 COPYRIGHT (C) 1994-2011 H. Peter Anvin et al

It just does this, and nothing else. I have tried restarting, and reinstalling on the USB. It just keeps doing this. Its been sitting at this screen for about 20 minutes now.

So what have I done wrong? lol

---

### Post by thatguy93 on 2011-07-22
Okay so I currently I am installing in windows, via WUBI.
Only thing is, on this computer there is only 27GB of free space. I wanted to format the HD first. 
Anyway to do this? Or should I just cancel and install it some other way?

---

### Post by e79 on 2011-07-22
Here's what I would do:

1. Try to redownload the ISO and recreate your bootable USB.

2. Try your USB on any other machine and see if it boots. If it does, you  can suspect something is not compatible or is wrong with your laptop. I don't know if the ['acpi=off']("https://help.ubuntu.com/community/BootOptions") would help in your case.

3.  If it does not, check to make sure your USB stick has no problems

EDIT : Posted to late, I'm def tired and slow tonight lol

---

### Post by thatguy93 on 2011-07-22
> **e79 said:**
> Here's what I would do:

1. Try to redownload the ISO and recreate your bootable USB.

2. Try your USB on any other machine and see if it boots. If it does, you  can suspect something is not compatible or is wrong with your laptop. I don't know if the ['acpi=off']("https://help.ubuntu.com/community/BootOptions") would help in your case.

3.  If it does not, check to make sure your USB stick has no problems

I know it will work, because I installed it previously on my other R52.
Please see post #2, I need some more help lol

---

### Post by e79 on 2011-07-22
> **thatguy93 said:**
> I know it will work, because I installed it previously on my other R52.
Please see post #2, I need some more help lol

Ya I posted it a little late.

Do you have an option in WUBI to 'wipe and use the entire hard-drive' (having never tried the WUBI way myself to be honest) ?

If not, do you have the option to 'repartition/resize the drive', erasing the Windows installation and selecting all the space for Ubuntu (don't forget to create a 'swap' partition of something around twice the size of your RAM) ?

---

### Post by thatguy93 on 2011-07-22
> **e79 said:**
> Ya I posted it a little late.

Do you have an option in WUBI to 'wipe and use the entire hard-drive' (having never tried the WUBI way myself to be honest) ?

Nope.
I wont be able to format my HDD after installation.
So what I might do, is let it install. then try booting from the USB and re-installing. Or I might format my HDD once the installation is done, then re-install.

---

### Post by thatguy93 on 2011-07-22
Okay I cancelled the installation.
I'm going to format my USB, re-download ubuntu, and install it on the USB, then try again.

---

### Post by e79 on 2011-07-22
> **thatguy93 said:**
> Okay I cancelled the installation.
I'm going to format my USB, re-download ubuntu, and install it on the USB, then try again.

OKi, Let us know how that goes. I personally use UNetBootin when creating the USB from a linux install and the ['Universal USB installer']("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") when on Windows[.]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") Do you have any CD/DVD as well laying around so you could burn and try to boot with ?

---

### Post by thatguy93 on 2011-07-22
> **e79 said:**
> OKi, Let us know how that goes. Do you have any CD/DVD as well laying around so you could burn and try to boot with ?

I do. But the only PC I have with a burner is super slow, and wireless. So I wouldnt even attempt it lol

---

### Post by e79 on 2011-07-22
> **thatguy93 said:**
> I do. But the only PC I have with a burner is super slow, and wireless. So I wouldnt even attempt it lol

Slow burning a linux CD is giving you better chances of success, as it is usually recommended for best result (4x speed)  :D

---

### Post by thatguy93 on 2011-07-22
> **e79 said:**
> Slow burning a linux CD is giving you better chances of success, as it is usually recommended for best result (4x speed)  :D

No no, I mean the computer itself is slow lol

---

### Post by thatguy93 on 2011-07-22
No luck. Still getting the same thing.

---

### Post by e79 on 2011-07-22
> **thatguy93 said:**
> No luck. Still getting the same thing.

But does the USB stick work on any other PC ?

---

### Post by thatguy93 on 2011-07-22
> **e79 said:**
> But does the USB stick work on any other PC ?

Yes it does.

---

### Post by e79 on 2011-07-22
> Yes it does.

Then, I know it surely does not help, but :

> I decided to install linux on another one of my IBM R52 laptops.Means that you have at least 2 of those laptop ? One is already working and the other one is the one you are trying to install Ubuntu at the moment ?

Is it possible both have not exactly the same hardware configuration (RAM, video crad, Mobo etc) and/or there is something wrong with it ?

---

### Post by thatguy93 on 2011-07-22
> **e79 said:**
> Then, I know it surely does not help, but :

Means that you have at least 2 of those laptop ? One is already working and the other one is the one you are trying to install Ubuntu at the moment ?

Is it possible both have not exactly the same hardware configuration (RAM, video crad, Mobo etc) and/or there is something wrong with it ?

I tried installing with Wubu, and got an error. Cant remember what it was, but it said a file was missing, and therefore the ISO could not be downloaded.
Yes both IBM R52's are exactly the same. Although this one seems to be the problem child. Hence why I wanted to put Ubuntu on it.

---

### Post by thatguy93 on 2011-07-22
Ah:
[http://www.techrepublic.com/blog/opensource/ubuntu-1104-installation-stumbling-block-and-post-install-impressions/2465](http://www.techrepublic.com/blog/opensource/ubuntu-1104-installation-stumbling-block-and-post-install-impressions/2465)

---

### Post by thatguy93 on 2011-07-22
Well looks like I got lucky.
Just decided to download Wubi, and install.
Seems as though it worked.
However, I dowloaded 11.04, and Wubi said the ISO was 10.04. Weird...

EDIT: Yup I installed Ubuntu 10.04 LTS. Guess thats why it worked! lol

---

### Post by e79 on 2011-07-23
I'm glad you could resolve this issue !

If you feel you no longer need help on this case, please use the thread tools and mark it as solved.

Cheers

---

### Post by thatguy93 on 2011-07-23
> **e79 said:**
> I'm glad you could resolve this issue !

If you feel you no longer need help on this case, please use the thread tools and mark it as solved.

Cheers

Even though we have not actually figured out what the problem was for installing ubuntu 11.04, I will mark it as solved, since I did get 10.04 LTS installed

---

