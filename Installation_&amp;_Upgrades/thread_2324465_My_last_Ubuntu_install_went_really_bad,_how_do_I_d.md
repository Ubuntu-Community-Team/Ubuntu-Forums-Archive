---
title: "My last Ubuntu install went really bad, how do I do it properly this time?"
date: 2016-05-14
forum: Installation &amp; Upgrades
---

### Post by 1two3 on 2016-05-14
Hello, a few weeks ago I had a huge a few huge problems with my Ubuntu installation. 

1. Couldn't boot from DVD
2. Had to go through the grub2 menu every time I boot to HDD where I have Ubuntu installed. And the next screen is supposed to be the disk decrypt password prompt screen but I only reached that screen sometimes so I had to reboot many times before successful.
3. CPU was getting close clogged despite having a Intel core i5-3230M 2.6GHz (3.2GHz). It could happen even for just having 1 YouTube tab open but sometimes it didn't happen even if I have several YouTube tabs open and it could even happen from having tabs open with large images.

Read here for details: [http://ubuntuforums.org/showthread.php?t=2320110](http://ubuntuforums.org/showthread.php?t=2320110)

I went to a computer repair shop and he said that he was able to install windows again by simply using a sub stick. I didn't really think that it really was such a big difference between DVD and usb.. I'm not going to use DVDs again ever at least lol.

But this time I want to make sure I properly install Ubuntu so that there won't be any problems again.

The thing is I asked him for factory computer configuration so that its same as when I bought it but preferably win10 instead of win8.

He said he also installed some drivers but I didn't think much of that at the time.

I was told yesterday that my Acer aspire V3-571G doesn't support win10. There are no drivers that support win10. I found this out when I was going to download the latest bios version driver but it says they are for win8 or win8.1. 

So I guess he installed some win10 drivers not made by Acer to make windows work. 

I'm now not sure which guide to use to install Ubuntu?

Because there's apparently a difference if you have win8 and win8.1 so maybe there's a difference for win10 too? 

Does it matter which drivers I've got installed? 

Should I update bios? In my old thread some people were advising me to do that. But now I have win10 which might not work well then? But then again I bet this older (V 2.15) bios driver is made for win8 too so maybe it won't be harmful to update the bios to 2.21 even though it's also for win8 unless the update can go wrong for using win10 to update the bios instead of win8?

I want to install Ubuntu desktop 16.04 64bit LTS

That's all I can think of at the moment.
Love you all, thanks so much for taking time to help newbies like me :)

---

### Post by RobGoss on 2016-05-14
Hello and welcome, I'm a bit confused are you wanting to dual boot **Windows **and **Ubuntu**? if so the process of doing this will depend on what the specs are for that machine

I would recommend using** Pendrive** to create your USB it seems to be the best in my option here's the link for that [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) I don't like using DVD's but that's just me I always seem to have trouble booting from them

Dual booting these day are more intense do to the fact most of the new machines require **UEFI** with that said it's still relatively easy once you've read what's required, this guide might help you in what's needed. Try reading about it here: UEFI [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

How-to dual boot Windows and Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you just wanted to install Ubuntu then the process it straight forward all you really need to do is choose **try Ubuntu** ina live sessionand see how well it preforms if you like it then just choose **Install **and follow the on screen instructions: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

I'm sure there will more users that may also shed some light on this process

Best of luck

---

### Post by oldfred on 2016-05-14
I think I am one that pointed out Acer does not support Windows 10. Possible drivers issue.
I had searched with Google & your model and found several posts on issues. But that did not stop users from upgrading.
And almost all vendors when called will say they do not support any Linux, but Linux usually works and all drivers are included. Sometimes settings are required to work around specific issues.
Best to search for your model and other users posts on how well system works.

Post this from terminal in live installer, we see repair shops installing in BIOS mode not UEFI mode when they do repairs. System was originally UEFI.
sudo parted -l

Does live installer from flash drive booted in UEFI mode work ok?

---

