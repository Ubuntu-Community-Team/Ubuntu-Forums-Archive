---
title: "Can't Load Ubuntu on New Hard Drive"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by ToMang07 on 2012-11-08
I'm having an issue with 12.10...

I have a fresh new  hard drive I formatted in XP on my older computer,  then I installed it in my new  computer, and every time I try to boot it will not read the disc, just  goes to the black screen with the cursor blinking. No matter how many  times I try to load it it won't boot from the CD. 

I got the  file from the Ubuntu website....I even used the disc to instal Ubuntu on  my XP computer. Worked fine. But I can't get it to load on the new  computer! [FONT=Times New Roman][B][SIZE=3]

HELP! :sad:[/SIZE]
[/B][/FONT]

---

### Post by critin on 2012-11-08
It might do better if you didn't format it--let ubuntu do that.  But it depends.  
New computers present new boot issues.  Check out the hardware here.

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

When checking the hardware compatibilty forums, you'd save some time by going to the last page first, they are long forums.

---

### Post by Bucky Ball on 2012-11-08
Welcome to the forums. Just a heads up: please use regular sized font for regular text and not bold. 

From the code of conduct:

> Use color and font properties for highlighting portions of your text,  and not for all of the text in your post. Please use the default font  color and properties unless you need to highlight or draw attention to a  part of your post. ALL CAPS is interpreted as screaming.  [SIZE=2][COLOR=pink]Funky[/COLOR][/SIZE] non-uniform font size/color is  difficult for those who are visually impaired. If you are having  problems with reading the font, please adjust your browser.Cheers. :wink:

As this sounds like it might be a graphics issue, try booting from the LiveCD, hit F6 and you should get to some options. Choose 'nomodset' and continue. Let us know how that went.

[QUOTE=critin]It might do better if you didn't format it--let ubuntu do that.  Are you going to dual boot with XP?
New computers present new boot issues.  Check out the hardware here.

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)[/QUOTE]

+1. I'd try mine first, simpler and quicker if it's that, and second option second as possibly the issue. And just to reinforce: Just leave free space to install Ubuntu to and partition it during install by selecting 'Something Else'. Also, you didn't mention the specs of the machine? Old, new, RAM?

---

### Post by ToMang07 on 2012-11-08
Hardware is fine. Like I said, I ran Ubuntu on the newer computer when it was setup as a "Dual Boot" on my XP hard drive. I have a new, blank/formatted hard drive that I want to install a fresh, new copy of Ubuntu onto. 

Getting really sick of swapping the 2 computers in/out. :mad:

What is the difference from a "Live CD" and the download file from Ubuntu? 

The disk is JUST the .iso file. Like I said, it worked before, but that was with an existing (XP Pro) operating system.

Thanks for the help.

---

### Post by critin on 2012-11-08
> I have a fresh new  hard drive I formatted in XP on my older computer,   then I installed it in my new  computer, and every time I try to boot it  will not read the disc, just  goes to the black screen with the cursor  blinking. No matter how many  times I try to load it it won't boot from  the CD.  It isn't clear if you've already installed ubuntu or only the hdd and trying to install ubuntu.  (edit to say this has been answered)

What is it formatted to?  ntfs or ext 4?  Leave it as free space or unallocated.  Does bios see the hdd?
Is there a boot key shown on the bios page?

Live cd is the same cd, but chosen to boot at bios.  When it boots there are options to run as:  Install, Try, etc,,  Choose "Try // Live" is running it on the desktop without installing.  It allows you  to try everything safely before installing.

---

### Post by Bucky Ball on 2012-11-08
I'm presuming these are not identical computers? If it works on one there's no guarantee it will work on another. Not that simple. ;)

---

### Post by ajgreeny on 2012-11-08
With the new disk attached or installed, what is the output from ubuntu terminal of ```
sudo fdisk -l
```That might give a clue about where we are at the moment, as far as that new disk is concerned

---

### Post by Bucky Ball on 2012-11-08
Posted in error.

---

### Post by ToMang07 on 2012-11-08
> **critin said:**
> It isn't clear if you've already installed ubuntu or only the hdd and trying to install ubuntu.  (edit to say this has been answered)

What is it formatted to?  ntfs or ext 4?  Leave it as free space or unallocated.  Does bios see the hdd?
Is there a boot key shown on the bios page?

Live cd is the same cd, but chosen to boot at bios.  When it boots there are options to run as:  Install, Try, etc,,  Choose "Try // Live" is running it on the desktop without installing.  It allows you  to try everything safely before installing.

The new hard drive is NTFS, completely formatted. Never had any OS on it. Bios DOES see the HDD.

Boot key? not sure what you mean. I can enter bios, tell it to boot from CD, but it just goes to a black, blank screen with a flashing cursor. 

There is nothing else. Can't open it, access it, nothing.

> **Bucky Ball said:**
> I'm presuming these are not identical computers? If it works on one there's no guarantee it will work on another. Not that simple. ;)

They are different computers. The older one is a WinXP-Pro P4 (3.6ghz). The newer one is an AMD FX-4170 (4.2ghz). I loaded Ubuntu on the XP HDD and tried it out, just to make sure the new computer was working correctly. (It's a fresh build.) I then put it back in the older computer, formatted the new drive, and installed the new blank hard drive in the new computer. 

> **ajgreeny said:**
> With the new disk attached or installed, what is the output from ubuntu terminal of ```
sudo fdisk -l
```That might give a clue about where we are at the moment, as far as that new disk is concerned

There is no terminal, instal page, nothing. Short of bios reading the CD drive and the HDD, it won't do anything.

---

### Post by Bucky Ball on 2012-11-08
Do you get the same issue with 12.04 LTS? I would give that a try. 12.10 only been released two or three weeks and problematic for some. 12.04 LTS is long-term support release supported until Apri 2017, 12.10 for eighteen months from now.

---

### Post by ToMang07 on 2012-11-08
> **Bucky Ball said:**
> Do you get the same issue with 12.04 LTS? I would give that a try. 12.10 only been released two or three weeks and problematic for some. 12.04 LTS is long-term support release supported until Apri 2017, 12.10 for eighteen months from now.

Hmm...

I'll try the trick mentioned earlier, and if it doesn't work I'll try 12.4.

If that doesn't work.... I may just wait until I get Win 7. Should be here in a week, anyway. I like Ubuntu...when it loads, lol, but I don't want to run my crappy old XP system anymore. 

SOOOOO SLOWWWWWW!!!!!!! 

Again, thanks for the help, fellas!

---

### Post by steeldriver on 2012-11-08
> **ToMang07 said:**
> I got the  file from the Ubuntu website....I even used the disc to instal Ubuntu on  my XP computer. Worked fine. But I can't get it to load on the new  computer! 

Did you do a wubi install on the XP machine? if so it's possible you just copied the ISO file on to the disc, instead of creating a bootable install disc (which is what you need to install to a bare system with no existing OS)

---

### Post by ToMang07 on 2012-11-08
> **steeldriver said:**
> Did you do a wubi install on the XP machine? if so it's possible you just copied the ISO file on to the disc, instead of creating a bootable install disc (which is what you need to install to a bare system with no existing OS)

Ok, this is probably what I need help with then. I followed the direction on the Ubuntu website as best I could to make an install disk. But it is only the .iso file. What/how do I do it differently to make it  a proper bootable disc? Nothing else downloaded from Ubuntu when I downloaded it. :confused:

---

### Post by Bucky Ball on 2012-11-08
Ah, that is what I posted in error earlier then deleted as I figured you'd already installed on the other machine!

Ok, you need to burn the ISO to a CD, but *make a disk image*, don't just copy the ISO. That won't work and is why it isn't. To create a bootable disk _'Burn Disk Image'_ is what you want, or whatever selection achieves that in the software you're using. ;)

You can't do anything like a Wubi install on the blank drive as Wubi need to be installed *inside* Win, is not a permanent solution and intended to try Ubuntu for awhile before you install to hard drive. In my experience problematic.

---

### Post by ToMang07 on 2012-11-08
> **Bucky Ball said:**
> Ah, that is what I posted in error earlier then deleted as I figured you'd already installed on the other machine!

Ok, you need to burn the ISO to a CD, but *make a disk image*, don't just copy the ISO. That won't work and is why it isn't. To create a bootable disk _'Burn Disk Image'_ is what you want, or whatever selection achieves that in the software you're using. ;)

You can't do anything like a Wubi install on the blank drive as Wubi need to be installed *inside* Win, is not a permanent solution and intended to try Ubuntu for awhile before you install to hard drive. In my experience problematic.

Ok, I guess I don't get the difference between the burn methods, but I downloaded "Free Iso Burner" and downloaded it as an ISO. We'll see if it works... .I'll be back....hopefully.

---

### Post by ToMang07 on 2012-11-08
Welp...that did it!

Downloaded a "Free Iso Burner" and burned the .iso file to the disc.... it loaded up first try.

Only issue I'm having now is I can't figure out how to get the proper driver for my video card....it;s a NVIDIA GeForce 630....I tried the "NVIDIA" driver that popped up...it made the graphics worse. It seems to work well other wise.....EXCEPT the software updater....seems to be some sort of glitch in the uploader....the screen gets all scrambled. 

THANK YOU! for the help!

---

### Post by Bucky Ball on 2012-11-09
Great news! Over the first hurdle and the learning curve has commenced! Please post new threads  in the appropriate sub-forums about these new issues with descriptive titles and as much info as you can get together.

Post a link to them here if you like and you might be able to kick them off that way. ;)

PS: Did you go for 12.10 or 12.04 LTS? I'd stick with 12.04 for the moment; smoother ride for a newcomer, until you know the ropes a little better. More stable.

PPS: Hint: Updating straight after install is pretty rule-of-thumb and solving the update issue may solve the graphics driver issue as you may just need to update/upgrade the Nvidia driver. Is that the one in 'Additional Drivers'? Have a look in there once you've solved the graphics, or now to make sure that is enabled if it's there. 

In the new post, include the output of this in a terminal:
```

sudo apt-get update

```You will get an error with a clue as to why it is crashing with any luck.

---

### Post by ToMang07 on 2012-11-09
> **Bucky Ball said:**
> Great news! Over the first hurdle and the learning curve has commenced! Please post new threads  in the appropriate sub-forums about these new issues with descriptive titles and as much info as you can get together.

Post a link to them here if you like and you might be able to kick them off that way. ;)

PS: Did you go for 12.10 or 12.04 LTS? I'd stick with 12.04 for the moment; smoother ride for a newcomer, until you know the ropes a little better. More stable.

PPS: Hint: Updating straight after install is pretty rule-of-thumb and solving the update issue may solve the graphics driver issue as you may just need to update/upgrade the Nvidia driver. Is that the one in 'Additional Drivers'? Have a look in there once you've solved the graphics, or now to make sure that is enabled if it's there. 

In the new post, include the output of this in a terminal:
```

sudo apt-get update

```You will get an error with a clue as to why it is crashing with any luck.
I did end up keeping 12.10 since I had it downloaded and already had a little experience using it.  It is very clean looking. 

As far as graphics drivers, I'll have to do some more research on that one. Right now it is using the one it loaded as default: "Using X.Org X Server Nouveau Display Driver from xserver-xorg-video-nouveau (Open Source.)" I'll attach a picture so you can see them. 

I did update everything, it said it was up to date. I put that coed in the terminal......no clue what that did tho, lol, this is the resulting readout: 

I entered that code into the terminal, not sure what that did, but here is a copy of the results:

> Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg [933 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [9,347 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [695 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [2,661 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [34.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources [14 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources [26.3 kB]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources [695 B] 
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources [8,010 B] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [8,343 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages [67.6 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1,151 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [34.6 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages [28.9 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [1,151 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages [67.6 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [8,394 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages [14 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,394 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages [29.3 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [1,394 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US  
Fetched 433 kB in 6s (71.1 kB/s)                                               
Reading package lists... Done


Thanks again for the help.

---

### Post by oldfred on 2012-11-09
I have an older nVidia but had to install kernel headers to get the proprietary nVidia driver to install correctly. There is also a choice of nVidia drivers.

To see what is available.
May want nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.

apt-cache search nvidia-sett*

I actually used 
nvidia-settings-updates 

[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

---

### Post by Bucky Ball on 2012-11-09
+1. As fred says, looks from the screenshot like you need to install the proprietary driver to get it working correctly.

---

### Post by ToMang07 on 2012-11-09
> **Bucky Ball said:**
> +1. As fred says, looks from the screenshot like you need to install the proprietary driver to get it working correctly.

I tried that...it made it worse. The dock disappeared and wouldn't come back until I reset the driver and restarted the computer, lol

---

### Post by ToMang07 on 2012-11-09
> **oldfred said:**
> I have an older nVidia but had to install kernel headers to get the proprietary nVidia driver to install correctly. There is also a choice of nVidia drivers.

To see what is available.
May want nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.

apt-cache search nvidia-sett*

I actually used 
nvidia-settings-updates 

[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

I should add the actual card is made by Gigabyte, but it has a Nvidia chipset on it. (Gigabyte GEforce GT 630) I can't find a linux driver anywhere for it, the manufacturer only lists windows OS drivers. 

[http://www.gigabyte.us/products/product-page.aspx?pid=4217#dl](http://www.gigabyte.us/products/product-page.aspx?pid=4217#dl)

I haven't had time to crawl the graphics part of the forum.... I probably will this weekend.

---

### Post by Bucky Ball on 2012-11-10
I found this driver for you graphics instantly:

[http://www.geforce.com/drivers/results/51453](http://www.geforce.com/drivers/results/51453)

---

