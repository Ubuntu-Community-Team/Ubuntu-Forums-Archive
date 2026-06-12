---
title: "Linux not for my desktop"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by arunim on 2011-02-28
It has been 4-5 yrs I have been using Linux Distros like **OpenSuSE, Fedora, Ubuntu, Gentoo, Linspire, LinuxMint, LG3D, Open Solaris** on different coputers(my own computer and my friends) but Dont know why none of the latest Distros run on my computer. The last time a distro ran was **Ubuntu 8.04 desktop 32 bit edition**.... but the 64bit version didnt run though I have a **AMD 64bit** processor:confused:.

even the live CDs wont work... I had top install Linux mint to use it. but m not able to run the latest versions of it.

My Desktop Specs are:

AMD Athlon 64 1.8 GHz
512 MB DDR RAM 400GHz
Seagate 80GB HDD
VIA/S3G  UniChrome PRo IGP VGA=64 Mb

My computer successfully ran the beta versions of  Windows 7 and Windows Vista and I am Currently using Windows XP but want to switch to a linux. but sadly m not able to.:(

My latest issue is with the Ubuntu Netbook Remix. I downloaded it and copied it to my pendrive as instructed in the website using Universal USB installer. and  When I started to boot... It Didnt run the live cd showing lots of error. I then tried installing it. It got installed in 15 mins and the system was on in another 15secs giving me a hope that I can now use linux on my system but sadly.... when I move my mouse on the left side bar the whole desktop starts reloading and there is no text beside any Icons....even the date and time arent there. there are just sum unsymmetrical symbols. there was a similer problem with Kubuntu the desktop of kubuntu didnt start or when it started it just keeps on reloading. 

Pls help... I am very depressed .... btw....pls temme how to repair a pendrive so that it is readable by windows. cause the universa usb installer made it unusable other than installing.... pls help.... ****

---

### Post by zenwalker on 2011-02-28
Have you tried slackware based distros such as zenwalk? I am not sure if the problem do get resolved. But worth trying i believe.

---

### Post by NightwishFan on 2011-02-28
Sure I shall aid you. For one, be very very strict whatever ISO you download is 100% correct. The issues you describe seem like it may be due to a bad download or burn. To learn how to check md5sums (valid for most distros) go here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

To get help burning isos this is useful, though I bet you know this well enough. A good tip is to always burn at the slowest speed.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

If you are familiar with Linux you might want to try Debian instead of Ubuntu, though I recommend both:
[http://www.debian.org/](http://www.debian.org/)

As for the issues with the netbook remix. I think this is due to your graphics card being unsupported. The netbook remix requires valid 3d acceleration to work. Try the standard desktop edition (or Debian).

---

### Post by arunim on 2011-02-28
> **zenwalker said:**
> Have you tried slackware based distros such as zenwalk? I am not sure if the problem do get resolved. But worth trying i believe.

Have tried it but I wanted sumthing more better than slackware. I want to use it as my primary OS. even the latest Pinguy Os didnt work.

---

### Post by arunim on 2011-02-28
> **NightwishFan said:**
> 
As for the issues with the netbook remix. I think this is due to your graphics card being unsupported. The netbook remix requires valid 3d acceleration to work. Try the standard desktop edition (or Debian).

I write the isos in a re writable DVD at a 2X speed.

I am seeing the links u gave. Btw isnt the unity interface for older PCs.

Pls temme how to recover my pendrive so that it is readable in windows.

---

### Post by NightwishFan on 2011-02-28
> Btw isnt the unity interface for older PCs.

It is fairly lightweight but requires solid 3d acceleration. The new Unity in Ubuntu 11.04 (this april) will be better in that regard.

> Pls temme how to recover my pendrive so that it is readable in windows.

Simply format it as FAT32. You can do this in Ubuntu by right clicking the drive on the desktop and formatting. In Windows, right click on "My Computer" hit "Manage" Then find the disk partitioner. Be careful you format the flash drive and not your hard drive.

---

### Post by brallan on 2011-02-28
> **arunim said:**
> VIA/S3G  UniChrome PRo IGP VGA=64 Mb

This: [S3 UniChrome] Worst card (brand) you can use with Linux, as the S3 vendor hardly supports Linux. Try with the latest version of Ubuntu and see if the S3 driver (newer), corrects the error.

 
here is a recent thread of someone with the same video card:
[http://ubuntuforums.org/showthread.php?t=1695554](http://ubuntuforums.org/showthread.php?t=1695554)

> **arunim said:**
> My latest issue is with the Ubuntu Netbook Remix

why are you using the netbook remix? (the remix is for netbooks with very small screen-size) If you are installing on a desktop box, pick the version that more people have, then when you run into errors, it's more likely that someone else will have found the same error (and a solution.)

> **arunim said:**
>  I downloaded it and copied it to my pendrive as instructed in the website using Universal USB installer. and  When I started to boot... It Didnt run the live cd showing lots of error. I then tried installing it.

Better not to install the remix (or any other distro) if you cannot get it to work on live.

> **arunim said:**
>   there is no text beside any Icons....even the date and time arent there. there are just sum unsymmetrical symbols. there was a similer problem with Kubuntu the desktop of kubuntu didnt start or when it started it just keeps on reloading. 

you might repair the install. but I bet it's simpler just to download  another version of the liveCD and try to get it working before  installing. it sounds like less work if you are new to linux. Any good  reason you can't download (or torrent-download) one of the following and  try it out?

[ubuntu 10.10]("http://www.ubuntu.com/desktop/get-ubuntu/download")
[ubuntu alpha daily build]("http://cdimage.ubuntu.com/daily-live/current/") ?

to repair your install: It might be a problem with video, or a unicode problem, or that you have to install language support.

try getting out of gnome to a terminal.

there are 6 terminal and a gnome-interface. f1 - f6 are terminals, f7 is xwindows (gnome)

To get to a terminal: press control + alt + F1 but before doing it you should know that to get back you will need to press  control + alt + F7.

once at a terminal, and if you indeed can see text, you can try the following:

sudo apt-get update
sudo apt-get upgrade

see if that helps.

---

### Post by amsterdamharu on 2011-02-28
> VIA/S3G....
Oh brallan you beat me to it.

Instead of going beta release you could try xorg edgers though, the packages for video are beta release but the rest of your install can be stables and gives you only the video problem to deal with first.

---

### Post by arunim on 2011-03-02
I m now using it in safe graphics mode... M searching the net....could you all help me in finding the driver for my graphics card

---

