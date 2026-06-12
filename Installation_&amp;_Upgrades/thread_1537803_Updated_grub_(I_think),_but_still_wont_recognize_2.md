---
title: "Updated grub (I think), but still wont recognize 2nd Linux partition"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-07-24
So I am experimenting with other linux distros.....I just installed a small partition with OpenGEU, the one still based on Ubuntu.....now it wont recognize Mint. Ubuntu Studio is next on my list, but before I invest any more work I want to make sure I can add more partitions to grub, not just the most recent linux partition....Any help?

I think that future distros of linux should have a fix for this....if you install linux it should detect every other operating system on the disk, not just windows plus the most recent linux install.



Does it help if you install /boot separate? I always create a / and /home partition but never separate boot. Does that make life easier?

---

### Post by tommcd on 2010-07-24
Hmmm, I never heard of OpenGEU before. You learn something new every day around here!
So what distos do you currently have installed? I assume you have:
OpenGEU
Mint
*anything else*??

Also, when you installed OpenGEU, did you let it install it's grub to the MBR? Or to it's root partition, or somewhere else?
Which distro controls your MBR? This is important.

In any case, since I am not familiar with OpenGEU, you should be able to boot your Mint live CD and reinstall Mint's grub2 to the MBR like this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Just use the first method listed there. That should work.
Then boot Mint and run:
```
sudo update-grub
```
And it should update your /boot/grub/grub.cfg file to include OpenGEU, and what ever else you have.
If you want to run multiple distros, like I do, you need to keep track of which distro controls the MBR, and update grub2 accordingly.

I currently boot: Windows XP, Ubuntu 10.04, Slackware 13.1, and Salix 13.1 all from Ubuntu's grub2. I never have a problem with this. I have never used a separate boot partition. It is not necessary these days.

FYI: Since I boot several distros, I like to use a separate /data partition for my data. That way each distros home partition lives inside that distros root partition. This way, all those hidden (start with a period) configuration files and directories in your home partition are kept separate for each distro so they can't conflict with each other.

---

### Post by Nick_Jinn on 2010-07-25
I think I discovered part of the problem....

sudo update-grub 

This command didnt help me....However, if I install a second linux OS on another primary partition and import the settings during installation it seems to allow me to boot into either OS at startup.....That was when i installed GOS and imported OpenGEU....Ive been playing and expirimenting.

So maybe I should just reinstall Mint on a new primary partition, import the settings, and see what happens.

Or maybe there is something wrong with Mints loader.....it crashes if you have Mint and MoonOS on the same HDD.

I also notice that when I download GOS or OpenGEU it says UBUNTU instead of GOS or OpenGEU.....maybe because they are based on Ubuntu.


I am going to expiriment with Elive and Android86, and then I am going to erase and redo everything the way I plan to keep it. 



PS, how do I update grub if its kept on a separate /boot partition? Same way?

---

### Post by tommcd on 2010-07-25
> **Nick_Jinn said:**
> 
sudo update-grub 

This command didnt help me...
So maybe I should just reinstall Mint on a new primary partition, import the settings, and see what happens.
When you installed Mint, where did you elect to install Mint's grub2?? If you chose the default (to the MBR), then simply reinstalling Mint's grub2 as per the link in my last post, and then running "*sudo update-grub*", should fix this straight away.

FYI: If you are installing multiple distros that all want to install grub2 (or even grub-legacy), you should choose one distro to install it's grub to the MBR. For the other distros, you should install their grub2 to their own root partition. Then boot the distro whose grub2 controls the MBR and simply run:
```
sudo update-grub
```
And this should be all that is needed in most cases.
> **Nick_Jinn said:**
> 
PS, how do I update grub if its kept on a separate /boot partition? Same way?
I *think* so.
I have never used a separate boot partition. A separate boot partition was needed in the old days when many computer's BIOS could not read past the first few sectors on the hard drive. This is not needed nowadays. I don't think this will be of any advantage to you for this issue either.
Here is a great reference for dual booting:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
It mostly covers dual booting with Windows; but there is a lot of good info there.
And specifically for grub2:
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
Read the stuff on booting any distro from the grub2 prompt:
[http://members.iinet.net/~herman546/p20/GRUB2%20Edit%20Mode.html](http://members.iinet.net/~herman546/p20/GRUB2%20Edit%20Mode.html)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)
This will allow you to boot anything in a pinch. You need to get up to speed on grub2.
also:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
You may also want to check out the *Super Grub Disc*:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

This (hopefully) should allow you to boot any of your distros. It will also reinstall grub2 for you if you wish.

---

### Post by kansasnoob on 2010-07-25
> Does it help if you install /boot separate?

NO! It often causes problems on a multi-boot!

---

### Post by kansasnoob on 2010-07-25
There is no need to reinstall Mint! If you're going to multi-boot you need to learn how to tell what version of grub each OS uses, how and where to install (or reinstall) grub, etc.

A good place to start would be if you'd post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then I'll try to show you how to read the results.

---

### Post by Nick_Jinn on 2010-07-25
Well here is the crux.....I am using default installations save for separating root and home.....I dont know what versions of grub they are using or how to install grub on a partition I am not currently using.

Having those skill sets would probably help me....I will probably go back and read those links after a few hours sleep.

---

### Post by tommcd on 2010-07-25
> **Nick_Jinn said:**
> Well here is the crux.....I am using default installations save for separating root and home.....I dont know what versions of grub they are using or how to install grub on a partition I am not currently using.

What version of Mint are you using??
If it is 9.10 or 10.04, it uses grub2.
Have you tried reinstalling Mint's grub2 to the MBR as per the first link I posted??? 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
And then boot Mint and run:
```
sudo update-grub
```
I really think this is all you need a this point.
If this fails, you could try "method 2", then "method 3" listed there.

Or try that Super Grub Disc. This problem is *precisely* what the Super Grub Disc was created for.

Please take the time to read through those references on grub2 I posted earlier. Essentially everything I know about grub2 was taken from those references.

---

### Post by Nick_Jinn on 2010-07-25
[FONT=monospace]As I have said before, it didnt help when I used [/FONT]
sudo update-grub 

It didnt add Mint back to the load order.....but there are some quirks with how I intalled and set up the partitions. I am going to try to give Mint its own logical partitions and each OS its own logical partitions and then see if that helps. 


But yeah, I ran that command and it didnt add Mint back.....



There are some quirks with Mints loader though. Its not the same as Ubuntu. I can dualboot MoonOS and Ubuntu, but trying it with MoonOS and Mint and it crashes.


Does the same thing happen with OZOS? Does anyone even know the bug I am talking about?

---

### Post by tommcd on 2010-07-27
> **Nick_Jinn said:**
> [FONT=monospace]As I have said before, it didnt help when I used [/FONT]
sudo update-grub 

Please read this *carefully* !!!
As I have said before (NOTE: This is the **third** time!!!!!!)
*You first need to reinstall grub2 to the MBR from the Mint live CD as per the link that I have given you several times already*!!!!!
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
*Have you tried reinstalling Mint's grub2 to the MBR as per the above link*?
You need to do that first. Is there a reason you have been unwilling or unable to try that? If so, then please explain.

Or try using the **Super Grub CD** as per the link I posted earlier.

Have you tried anything at all that I have suggested ??????

> **Nick_Jinn said:**
> 
There are some quirks with Mints loader though. Its not the same as Ubuntu. I can dualboot MoonOS and Ubuntu, but trying it with MoonOS and Mint and it crashes.
If you can't reinstall grub2 to the MBR from the Mint live CD for some reason, get the Ubuntu 10.04 alternate install CD. Burn that to a CD and boot it up. When the CD boots, choose the option "*rescue a broken system*". Then work your way through that until you come to the point where it gives you the option to reinstall grub2 to the MBR.

And ... as I have said before ... 
You will really need to get up to speed on grub2 if you ever hope to dual boot more than one linux distro. I have given you several reference articles for grub2 already.

You can easily boot as many distros as you want from Ubuntu's grub2. I do it; and I have no problems with it.
Whether you choose to learn how to do that or not is entirely up to you. As with anything else in linux, it is always your choice.

---

### Post by Nick_Jinn on 2010-07-27
I understood you the first time. I will read those how tos on how to reinstall grub, but I think there might be something quirky with Mint because I can dual boot Ubuntu and MoonOS, but not Mint and MoonOS. There might be a little more to this.

Before you came along I was told that updating grub might fix it, but it didnt. I did understand what you were saying though, I just didnt know how to reinstall grub to another partition. Ill try reading that. 


But I have already moved on and reinstalled the OS. It will be just in case I have problems next time.

---

### Post by Nick_Jinn on 2010-07-27
Thanks. That last one should be helpful. The first time I didnt read it because you kind of overwhelmed me with links. There is only so much time in a day....thank you for helping though. That last one should have everything I need if I run into this problem again.

---

### Post by louieb on 2010-07-27
> **kansasnoob said:**
> ...A good place to start ...
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


+1 If your going to boot multiple Linux distributions - and wonder what is going on with the boot sequence and GRUB - this script is a must have - lots of good information - will really help you get and keep things straightened out.

---

