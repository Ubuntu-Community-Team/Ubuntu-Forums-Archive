---
title: "Cant install Ubuntu 7.10"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by ComputersXP on 2008-03-30
Right , i recived my Ubuntu 7.10 CD's 1x X86 and 1 x X64 

and when i goto install X86 or X64 they will both sat on a black screen 

it will load the kernal etc but before it gets to the desktop it will sit at a black screen the X64 Version Powers Down my moniter aswel but the X86 Version dont 

Remember this is just booting the live CD 

I would like to try this 

System Spec : 

Amd Athlon X64 X2 Dual Core 5600+ 
4GB XMS2 Ram 
8800GT PCI-E 
ECS KN3 - SLI 2

---

### Post by Miller12 on 2008-03-30
I believe it is your graphics card, nvidia 8800GT. It is trying to use the generic Vesa driver. Try the safe graphics mode but I wouldn't count on that working either.

I had problems with my 7600GT  and could never get the Live CD to work. I had to use the alternate CD and do an install. I then used Envy to get the graphics card to work properly.

---

### Post by ComputersXP on 2008-03-30
Yeh i tried Graphic's Safe Mod and it still didnt load 

Were can i get the Alternative CD from for 7.10 ? 

Would you mind explaining what Envy is m8 ? 

From a bit of research envy is the NVidia Manager 


is this  CD i need 
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fubuntu.virginmedia.com%2Freleases%2F&debug=&download-button=%3CIMG+alt%3Ddownload+src%3D%22%2Fthemes%2Fubuntu07%2Fimages%2Fbutton-download-new.png%22%3E+Start+Download&alternatecd=alternate](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=http%3A%2F%2Fubuntu.virginmedia.com%2Freleases%2F&debug=&download-button=%3CIMG+alt%3Ddownload+src%3D%22%2Fthemes%2Fubuntu07%2Fimages%2Fbutton-download-new.png%22%3E+Start+Download&alternatecd=alternate)

---

### Post by Miller12 on 2008-03-30
The alternate CD can be downloaded here: [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

near the bottom of the page there is a check box for the alternate cd. This is a text based installer. Someone may have a better answer for you as to why you are getting the blank screen though so maybe just wait a bit.

This is from the Envy website: [website]("http://www.albertomilone.com/nvidia_scripts1.html")

"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you

It will get the latest driver for your graphics card and then configure the xorg.conf file which handles the x window system.

---

### Post by ComputersXP on 2008-03-30
Yeh im downloading it now ..

BTW .

How long would shipping take if i ordered a Ubuntu Metal Key Fog Today ?

---

### Post by ComputersXP on 2008-03-30
How would  i set my partitions out 

For Swap etc 

The Drive is 160GB

---

### Post by forestpixie on 2008-03-30
Are you dual booting or just booting buntu - 

I'd do 
/ - 10Gb
/home - 149Gb
swap 1Gb

but swap depends on a number of factors - how much RAM you have, do you hibernate, what you're doing with the pc - memory intensive apps are liklely to need more swap.

---

### Post by ComputersXP on 2008-03-30
i set 

/ as 130gb 
and 30gb swap 

if i need to format n do it again .. then i will 

but should be o.k

---

### Post by pasmeh on 2008-03-30
You shouldnt have to re-install, it will still work fine, just that you are sort of wasting that 30GB, iv got pretty much the same setup as you but mines an 8800GTS and my system runs fine on: 

swap / 2GB
etc / 490GB

Note, i never really had much luck running 7.10 with my video card, just changed over to Hardy 8.04 and everything is working much more smoothly.

---

### Post by ComputersXP on 2008-03-30
i cant seem to find the 8.04 install cd .. maybe ill wait until its realased so i can get my free cd of it

---

### Post by forestpixie on 2008-03-30
Hardy is here - but bear in mind it's a beta - 

[https://wiki.ubuntu.com/HardyHeron/Beta#head-8845f7d03a79ba22bbc3993ed0ffc8395651a9a0](https://wiki.ubuntu.com/HardyHeron/Beta#head-8845f7d03a79ba22bbc3993ed0ffc8395651a9a0)
as has been said 30Gb of swap is a waste :)

To use all your 4Gb of RAM and any swap you specify you will need to get 64bit

---

### Post by pasmeh on 2008-03-30
[http://mirror.internode.on.net/pub/ubuntu/releases/8.04/](http://mirror.internode.on.net/pub/ubuntu/releases/8.04/)

heres a link for all the Alternate Releases, there not live CD's but they all work fine. If your based in Australia then your speeds should be pretty fast.

---

### Post by ComputersXP on 2008-03-30
im having to reinstall due to grub not working properly and ill set swap to 4gb .. and then it will be fine i hope ..

---

### Post by ComputersXP on 2008-03-30
Right , 

All installled got Nvidia drivers installed Via envy 

but i aint got no sound even tho it says installed it wont output sound out my speakers

---

### Post by bondboy8 on 2008-03-30
How would you go about reinstalling Ubuntu.  I think i am having the same problem I installed with the alt CD but it was corrupt so i deleted that partition filled with the corrupt data and tried to create a new partition from the free space to install Ubuntu on.  This left me with to swap partitions each about a gig which i thought was weird.  Now GRUB works and XP will boot fine but Ubuntu goes to a black screen after the loading bar.  Is this a graphics card problem that I can fix or should I reinstall Ubuntu again

---

### Post by ComputersXP on 2008-03-30
This is wat i did 

boot into Vista or XP 

Delete the ubuntu parition 

recreate partitionss

reinstall ubuntu

---

### Post by ComputersXP on 2008-03-30
More of my problems here 

[http://ubuntuforums.org/showthread.php?p=4616324#post4616324](http://ubuntuforums.org/showthread.php?p=4616324#post4616324)

---

### Post by bondboy8 on 2008-03-31
How do u delete the partition in XP or would it just be easier to use the partition editor in the Ubuntu installer

---

