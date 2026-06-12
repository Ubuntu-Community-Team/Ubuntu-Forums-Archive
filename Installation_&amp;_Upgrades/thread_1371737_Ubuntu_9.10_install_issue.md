---
title: "Ubuntu 9.10 install issue"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by bugs6 on 2010-01-03
Hi,

Im very new to linux but i got a live cd ages ago in a linux for dummys book that had 7.4 for something on it i recently installed it on an older computer removing windows, but i then realised that this version was many releases behind and so wanted to upgrade.

So i thought i would do a fresh install of 9.10, downloaded the iso image then used infrarecorder to burn the image on the slowest speed and then loaded the CD on my computer, i then run the install and get the flashing ubuntu symbol but then it either hangs on purging configuration files for gdm-guest session or sometimes reachs a load of cant find value for something like apps/netbbok-launcher/favourites or something.

any help appreciated thanks in advance

---

### Post by bugs6 on 2010-01-04
Still havent got anywhere i tried writing multiple CDs and downloading the iso image again incase it was bad ive set my computer to boot from CDs.

anyone have any ideas??

---

### Post by losi on 2010-01-04
Hi,
What computer have?
losi

---

### Post by bugs6 on 2010-01-04
I have an old dell machine with all built in components except a network card that was added.

ive tried again today and i did a CD check and there was no defects the installation just stops and the disc stops spinning.

---

### Post by yogesh.girikumar on 2010-01-04
Hi,

    The issue could be anything. It could be a corrupt ISO or a bad hardware, it would be easier to find out what the problem could be if you provided details like
       
[LIST=1]
[*]where you got your ISO file from and
[*]what kind of hardware you're using.
[*]It helps to also select "Check this CD for defects" option [which is seen after booting off the CD] before you try installing the OS.
[*]It's also worth trying a different CD Burning software and checking the integrity of the file by using a MD5 checker.
[/LIST]
       To learn about MD5 cheking, the following link could help if you're already using linux, It's got a cool tutorial : [URL="https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file"]https://help.ubuntu.com/community/HowToMD5SUM#Check%20the%20iso%20file
[/URL]        

And if you're using windows.... [http://www.fastsum.com/](http://www.fastsum.com/)
~~
[Yogesh G]("http://www.fastsum.com/")

---

### Post by bugs6 on 2010-01-04
- I got it from the ubuntu website and selected great britain as my location

- Its a dell dimension 1100 with all graphics and sound cards all onboard the motherboard, except a belkin wireless network card.

- I checked the CD and it had no defects

- and i will try a different burner.

I left the install running today it sat on "purging configuration files for gdm-guest session" for ages then finally moved onto a few lines saying " no value set for app/network-booter/favourites" or something like that then seemed to just stop completely.

---

### Post by bugs6 on 2010-01-04
My new 9.10 CD now after selecting install ubuntu then the flashing ubuntu symbol and finally it gets to 

"starting remaining crypto disks"

and then seems to stop any idea?

im going to try 9.04 then if that works just update.

---

### Post by bugs6 on 2010-01-04
ive tried multiple discs multiple iso burning and all manner of things on my bios settings 

can someone please help me out im sure it will be something simple i just dont know what

---

### Post by bugs6 on 2010-01-05
well just wanted to let people know that the alternate install worked on my computer although now it wont boot up it gets as far as the ubuntu symbol and then just a black screen with a white line at the top left corner and just hangs there any help would be appreciated?

---

### Post by UsedBits on 2010-01-05
One must 'slow burn' the CD to improve the odds that it is actually bootable.
 
If that isn't your issue, than please know that 9.10 is terribly unstable, especially with respect to X.  I started with 9.04 and loved it.  Then I made the mistake of upgrading to 9.10, thinking that it was ready for prime time.
 
9.10 is NOT ready for prime time.  Instead, upgrade back to 9.04 and wait until 9.10 developers have identified and worked out the kinks.

---

### Post by kansasnoob on 2010-01-05
If that old Ubuntu live CD worked (7.04 maybe) try booting to the Live Desktop (that is choosing to try Ubuntu without installing) and from the live Desktop go to terminal and post the output of these commands:

```
lspci | grep VGA
```

```
cat /proc/cpuinfo
```

```
free -m
```

---

### Post by yogesh.girikumar on 2010-01-06
Hi,
   	There are a few suggestion that I would like to make about your issue that you can try.
   	Firstly during the install, you can run the installation in a safe graphics mode. This is done by pressing F4 while the live cd menu is being displayed and selecting "safe graphics mode".


   	[[IMG]http://bmp.in/thumbs/screenzyz.png[/IMG]]("http://bmp.in/?v=screenzyz.png")


[http://bmp.in/?v=screenzyz.png](http://bmp.in/?v=screenzyz.png)


   	Secondly, I suggest that you do a text mode install without any GUI so that you can take care of video driver issues, if any, after the installation. You can use alternate installation disk from [http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso](http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso) for a text mode install.
   	Also, there are some video related BIOS settings that you might like to try changing. You may also like turning the OS install mode on/off. You may be able to find the BIOS manual for your model on Dell web site.
   	Check and let me know if that helps.
   	Yogesh.

---

### Post by Bartender on 2010-01-06
Dell 1100??  How much RAM does it have?  The LiveCD probably won't install if you only have 256.

---

### Post by yogesh.girikumar on 2010-01-11
Hi,
   	There are a few suggestion that I would like to make about your issue that you can try.
   	Firstly during the install, you can run the installation in a safe graphics mode. This is done by pressing F4 while the live cd menu is being displayed and selecting "safe graphics mode".
   	

[IMG]http://bmp.in/thumbs/screenzyz.png[/IMG]


   	Secondly, I suggest that you do a text mode install without any GUI so that you can take care of video driver issues, if any, after the installation. You can use alternate installation disk from [http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso](http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso) for a text mode install.


   	Also, there are some video related BIOS settings that you might like to try changing. You may also like turning the OS install mode on/off. You may be able to find the BIOS manual for your model on Dell web site.


   	Check and let me know if that helps.
   	Yogesh.

---

