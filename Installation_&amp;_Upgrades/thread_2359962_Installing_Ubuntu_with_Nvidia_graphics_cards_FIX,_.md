---
title: "Installing Ubuntu with Nvidia graphics cards FIX, long way that I found"
date: 2017-04-30
forum: Installation &amp; Upgrades
---

### Post by devynandalex2525 on 2017-04-30
Hey guys, I was having a lot of trouble installing Ubuntu on my desktop and laptop, both have Nvidia graphics cards, my desktop a 970, and my laptop a 1050, and I finally figured out how to do it and I thought I would share my experience to help anyone experiencing the same issue, Since I figured this out on my own and never found any real fixes online and in the forums. 

I got a fresh ISO from the downloads page, both of 16.04 and 17.04 Both of them no matter what I tried wouldn't get past Grub, and I tried all the boot parameters. It would either go to a black screen with a bunch of pink and green artifacting, or it would go to a black screen with a blinking cursor. or just a black screen with nothing. I couldn't get to the live boot on my desktop at all, and I could on my laptop, but when I tried installing it, it would crash and give me a bunch of errors. and the install ubuntu would never come up. 

I was about to call it quits, but decided the last thing I would try is getting the net install ISO. I put it on my flash drive and I got to work. 

I'm going to start with my laptop because I ran into a couple issues that I think those with dells might run into. it is important to note that this will only work if you have an active internet connection, I personally used a raspberry pi as a usb Ethernet device, and that was connected to wifi. Okay, so, I booted up and went to the installer and it actually booted straight in with the default boot parameters. I'm not going to go into detail on how to install it from there, but I just went through the regular routine install, but when it came time to select the packages. 

[SIZE=5][I][B]This is important!!!!!!
[SIZE=1][SIZE=3]Do not select anything other than the basic install! Do not select any of the Ubuntu desktops. just a basic command line install
[/SIZE][/SIZE][/B][/I][SIZE=2]Now after I had it installed I ran into 2 issues. The first issue is I got some sort of fdisk error which was easily bypassed by doing CTRL+ALT+F2. I logged in and ran into my second issue. The network wasn't connecting.

I had to find out my network device name, So I did [I][B]sudo ip a

[/B][/I]I found the network device name that should be something like [/SIZE][/SIZE]enp0s3 for ethernet and wlp2s0 for wireless. 
[SIZE=5][SIZE=2]I went into the network interfaces by going [I][B]sudo nano /etc/network/interfaces
[/B][/I][/SIZE][/SIZE][SIZE=5][SIZE=2]I added the lines

***auto ***[/SIZE][/SIZE][I][B]enp0s3
allow-hotplug enp0s3
[SIZE=5][SIZE=2]Iface [/SIZE][/SIZE]enp0s3 inet dhcp

[/B][/I]I then saved the file with CTRL+X. and I started the interface with [I][B]ifconfig enp0s3 up
[/B][/I]after a reboot the network worked great. For wireless you have to do a few extra steps, But I'm not going to go into detail.

I then installed my desired desktop, for me I just played it safe and went with unity, but any of them should be fine. I used [I][B]sudo apt-get install ubuntu-destop 
[/B][/I]**It's important to NOT shut down or reboot after this is complete!!** If you do it'll just boot up with the default driver and you will be in the same boat as you were before you installed. [SIZE=2]Now it's time for the most important part, installing the Nvidia drivers.

You'll want to add the repository, [I][B]sudo add-apt-repository ppa:graphics-drivers/ppa
[/B][/I]Then you want to update your Repo list, [I][B]sudo apt-get update
[/B][/I]Then you will want to list out all the available nvidia packages ***sudo apt-cache search nvidia***.
At the time of installation the latest nvidia driver is 381. So do ***sudo apt-get install nvidia-381***

Now it's okay to reboot, it should boot straight into the desktop, and your drivers should be installed and set to default.
You are good to go. it's important to let you know that the network issue I had may have been unique due to the usb Ethernet device, but it's still an issue I ran into so I thought i would mention it. 

These dang Nvidia drivers have been an issue for me for a long time. and lately it's been such an issue I switched to fedora for about a year. But I needed to come back. I love the community here.

 
This is my first time posting on the Ubuntu forums, though I've been a long time ubuntu user of 9 years. so take it easy on me!
Thanks everyone![/SIZE]

---

