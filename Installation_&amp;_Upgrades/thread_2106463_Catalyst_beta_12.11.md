---
title: "Catalyst beta 12.11"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by Dobly on 2013-01-19
After installing the latest Ubuntu yesterday, today it was time to install some proper drivers for the ATI HD6000 type graphics card. 

I followed to the letter the instructions on this site.. 

[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL")

I used the instructions for the Manual install of the Catalyst 12.11 beta drivers. 
What a nightmare. 

After all of the steps I rebooted my pc. When I got back in, all I could see was the background image. No launcher, nothing. 

Pressing CTRL-ALT-T I could get a terminal up. I got into to the /etc/X11 folder in there was able to run...

sudo cp xorg.conf.original-0 xorg.conf

That original file name is close to what I remember it being called. 

After that I rebooted again and things went from bad to worse. 

I was presented with the standard desktop, with a dotted grid all over it and a login option on the left. However putting in my password, did not log me in. No amount of attempts would let me in. 

I was out of options.. I booted from the install DVD and selected the option to install over the existing install. 

That is running now but does any one have any idea what could have gone wrong? That wiki I linked to above seemed pretty thourough but fell way short in my case. I am bound to try this again once I get the install fixed. 

Anyone have a better tutorial on how to install these drivers?

---

### Post by Dobly on 2013-01-19
Well, after the reinstall (where it tried to reinstall over the existing install, keeping you files intact), I still can't get in. 
I get the little login option where my user name and password (100% correct) do not log me in. 

Also, get this. 

I was able to get to a desktop using the Guest option. But logged in like that sudo and su do not work. 

Looks like full reinstall for me. :(

---

### Post by westie457 on 2013-01-19
Hi reset your password using this guide.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

That will get sudo working for you.

Sorry no help from me installing 'catalyst' drivers.

---

### Post by Dobly on 2013-01-19
> **westie457 said:**
> Hi reset your password using this guide.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)



During the reinstall I was just asked to create my username and password. I am 100% positive I have the correct password. 

Or put it this way, the log in box I get tells me that if I enter the wrong password. When I put in the correct password it thinks for a couple of seconds, the screen blacks for a fraction of a second and I get the login box again. 

I'd really like to be able to get some stuff out of my home folder before I go the full reinstall.

---

### Post by Dobly on 2013-01-19
Enough is enough. I have bitten the bullet and opted for a full, hard drive wiping reinstall. I only had it install for a day so I only had on it, Updates, Steam, 1 x 2.5GB game and emails from the last day or so. 

I am a recent long term Win7 user and my first crack at Linux in years had me install Mint 14 about a month ago. It was my attempt to install the Catalyst drivers in there along with a few other problem with Mint that prompted me to dump it. I tried Fedora 18. Yuck. What a hassle that was. So i have come back to Ubuntu. If it's good enough for Valve, it's good enough for me. 

I only want a few things from my OS. 

1. Play 3d, hardware accelerated games.
2. Use Aftershot Pro and have it use OpenCL on my ATI Radeon video card.

Modest stuff for a PC in 2013, but wow, what a hassle getting something as common as video card drivers installed in a so called 'modern' OS.

---

### Post by Mark Phelps on 2013-01-19
> **Dobly said:**
> I only want a few things from my OS. 

1. Play 3d, hardware accelerated games.
2. Use Aftershot Pro and have it use OpenCL on my ATI Radeon video card.

Modest stuff for a PC in 2013, but wow, what a hassle getting something as common as video card drivers installed in a so called 'modern' OS.

If the 3D hardware accelerate games are Windows games, you are wanting too much.  Linux is not designed to run Windows games.  You would have to use Wine, and the results there very from good to really BAD, depending on the Windows app and version.

Aftershot Pro is a Corel product, and those are generally ONLY available for Windows.  I checked the WineHQ site, and that is not even listed -- but the other Corel products ARE listed and they are rated GARBAGE -- meaning, they will not work with Wine, no matter what you do.

As to video drivers, Ubuntu installs Radeon drivers by default -- so you already HAVE video drivers installed.  IF you did not, you would have a black screen with nothing else.

Looks like what you basically want is Ubuntu to be a perfect replacement for Windows -- which it is NOT.  If your goal is to keep using Windows stuff, then you need to stay with Windows -- that's where the Windows stuff works best.

---

### Post by Thee on 2013-01-19
Whats wrong with the ATI driver that comes with Ubuntu? It will work, why do you need the latest one?

---

### Post by The Spectre on 2013-01-19
Why are you trying to install BETA Drivers?

AMD Catalyst for Linux 13.1 (Final) was relesed on the 17th...
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

You also might want to try the Officially Supported Drivers that are listed in Software Sources on the Additional Drivers tab.
Or the ATI Driver that is listed in the Ubuntu Software Center.

---

### Post by Dobly on 2013-01-20
> **Mark Phelps said:**
> If the 3D hardware accelerate games are Windows games, you are wanting too much.  Linux is not designed to run Windows games.  You would have to use Wine, and the results there very from good to really BAD, depending on the Windows app and version.


I have not tried to run a 'Windows' game. Thus far I have installed Trine 2 (native) and Team Fortress. Also a native Linux app. 


> **Mark Phelps said:**
> 
Aftershot Pro is a Corel product, and those are generally ONLY available for Windows.  I checked the WineHQ site, and that is not even listed -- but the other Corel products ARE listed and they are rated GARBAGE -- meaning, they will not work with Wine, no matter what you do.

Aftershot pro from Corel has a native Linux version. Check it out here.

[http://www.corel.com/corel/product/index.jsp?pid=prod4670071&cid=catalog20038&segid=6000006&storeKey=us&languageCode=en]("http://www.corel.com/corel/product/index.jsp?pid=prod4670071&cid=catalog20038&segid=6000006&storeKey=us&languageCode=en")

It was the first Linux app I was more than happy to pay for. It rocks. Was based on a popular linux app called Bibble i do believe, but I'm no expert on it's history. The fact that it is a AAA supported Linux app is tops for the Linux platform me thinks. 

Worth mentining here in case you have not heard that Lightworks is coming to Linux too... Professional video / movie making software. 

Check it out. 

[http://www.lwks.com/]("http://www.lwks.com/")

> **Mark Phelps said:**
> 
As to video drivers, Ubuntu installs Radeon drivers by default -- so you already HAVE video drivers installed.  IF you did not, you would have a black screen with nothing else.


There are drivers and there are drivers. The ones installed by default, for whatever reason (that I don't understand), do not run any of the games I have installed above. I don't know why.  (Each added via the NATIVE linux Steam Client. 

> **Mark Phelps said:**
> 
Looks like what you basically want is Ubuntu to be a perfect replacement for Windows -- which it is NOT.  If your goal is to keep using Windows stuff, then you need to stay with Windows -- that's where the Windows stuff works best.

Then you have not read my post. I have not mentioned wine or Windows. I'm not interested in trying to run Windows software on Linux.  I just want to get a video card driver installed that will... 

1.. Run Linux native OpenGL 3d games..   
2.. Have an OpenCL api (< not a typo.. [OpenCL]("http://en.wikipedia.org/wiki/OpenCL")) for use by Aftershot Pro (and hopefully Lightworks).

---

### Post by Dobly on 2013-01-20
> **The Spectre said:**
> Why are you trying to install BETA Drivers?

AMD Catalyst for Linux 13.1 (Final) was relesed on the 17th...
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

You also might want to try the Officially Supported Drivers that are listed in Software Sources on the Additional Drivers tab.
Or the ATI Driver that is listed in the Ubuntu Software Center.

Well that is a great question.. I did not know the 13.1 (Final) drivers came out. To busy wrestling with the 12.11 beta drivers. D'oh!

I just need to decide now do i try the 13.1 drivers OR the ones in the Additional Drivers tab. 

My question is, what can I do to somehow take a snap shot of my setup before I did this? I am now typing this from my fresh install of 12.10.

---

### Post by The Spectre on 2013-01-20
> **Dobly said:**
> My question is, what can I do to somehow take a snap shot of my setup before I did this? I am now typing this from my fresh install of 12.10.

I use a program called Redo Backup & Recovery to create a Disk Images of my system before I do any major updates. (Or something that might FUBAR my system.)

[http://redobackup.org/](http://redobackup.org/)

I also use it to create Disk Images once a Week as my regular backup routine because you just never know when the unexpected might happen.

---

### Post by The Spectre on 2013-01-20
> **Dobly said:**
> I just need to decide now do i try the 13.1 drivers OR the ones in the Additional Drivers tab.

I would definitely try the AMD/ATI Drivers that are listed under the Additional Drivers Tab First because they are already there and the easiest to tryout.

Then if they do not give you the results that you are looking for then try the AMD/ATI Drivers that are listed in the Ubuntu Software Center.

Hopefully one of the options listed above will work for you.

---

### Post by Dobly on 2013-01-20
> **The Spectre said:**
> I use a program called Redo Backup & Recovery to create a Disk Images of my system before I do any major updates. (Or something that might FUBAR my system.)

[http://redobackup.org/](http://redobackup.org/)

I also use it to create Disk Images once a Week as my regular backup routine because you just never know when the unexpected might happen.

Thanks for the tip Spectre. 

I downloaded the [3.1 (Final)]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx") drivers. When I tried to install them I got an error with a missing fglrx or some such thing.. 

This I fixed by installing the linux-headers-generic

```
sudo apt-get install linux-headers-generic
```

Then voila, the 3.1 drives installed and after 5 weeks of my big move from Windows 7 to Mint 14, then Fedora 18 and now finally Ubuntu 12.10, I have proper 3d acceleration. 

Thanks everyone for your help and suggestions.

---

