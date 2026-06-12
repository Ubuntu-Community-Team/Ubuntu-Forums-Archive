---
title: "Updating to kernel 3.5.0-23, ubuntu won't boot up"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by avielmenter on 2013-02-18
I updated Ubuntu 12.10. The most updated version on my computer now uses kernel 3.5.0-23. However, when if I select that version to boot into at the GRUB, all I get is a black screen with a flashing white underscore at the top. It stays there indefinitely. I have to boot into an older version of the kernel (I think 3.5.0-17).

Why is this the case and how can I fix it?

---

### Post by oldfred on 2013-02-18
Welcome to the forums.

Do you have nVidia or other proprietary video? Often nomodeset required to boot.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
You should be able to press e on grub menu and replace quiet splash with nomodeset.

---

### Post by avielmenter on 2013-02-18
> **oldfred said:**
> Welcome to the forums.

Do you have nVidia or other proprietary video?
Yes, I have NVidia!
> 
 Often nomodeset required to boot.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
You should be able to press e on grub menu and replace quiet splash with nomodeset.

Thank you, I will try this shortly and report back.

---

### Post by avielmenter on 2013-02-18
Unfortunately, setting the nomodeset option did not work. I still have to boot up into kernel version 3.5.0-17

I want to make clear that I'm not using the Nouveau drivers, but rather NVidia's.

---

### Post by oldfred on 2013-02-18
With 12.10 I had to install Linux headers first to get nVidia to correctly install.

Do you have dual video? If so you may need bumblebee.

       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by avielmenter on 2013-02-18
I do have two video cards. I have already installed headers and upgraded my video card drivers. I had to to solve another error I was having previously, in which Ubuntu would boot up in low resolution and nothing related to Unity would display. My drivers are version 304.64

---

### Post by avielmenter on 2013-02-20
Bump. I did those things, I ensured everything was updated, I ensured that when I was updating and installing it installed for the updated kernel versions, and I still can't boot using the new kernels.

---

### Post by oldfred on 2013-02-20
Did you install headers.

If you installed nVidia from the nVidia site you actually have to reinstall with every kernel update as it is not automated. Better to use the Ubuntu provided versions.

---

### Post by avielmenter on 2013-02-20
> **oldfred said:**
> Did you install headers.

If you installed nVidia from the nVidia site you actually have to reinstall with every kernel update as it is not automated. Better to use the Ubuntu provided versions.

I installed the headers. I've ensured I have linux-headers-generic, linux-headers-3.5.0-17-generic, and linux-headers-3.5.0-23-generic. I'm fine reinstalling the headers. Does that mean I have to remove and replace them? Or if they're there already, is that enough? Or did you mean that I have to reinstall the drivers? Either way, just tell me the protocol.

I didn't install from the NVidia site, I installed via apt-get install nvidia-current. Those may be the same drivers. Do nouveau drivers provide the same 3D graphics support that the NVidia ones do? Because that's not the impression I get from the website. I am gaming on this computer.

---

### Post by oldfred on 2013-02-21
If you have the headers I would think it should be ok.

Ubuntu offers several versions of nVidia. If a gamer I might install the most current or experiment (less tested by Ubuntu). All the video drivers are being updated for gaming that is coming to Ubuntu, but it takes a while and you may need newest version with newest kernel and even like Windows new hardware to really run games well.

---

### Post by Styrmir Magnusson on 2013-02-22
I have the same problem, on a Laptop Lenovo U350. Sometimes is hangs on Ubuntu logo, sometimes it stops on black screen. It is a complete freeze, the capslock does not turn on or off so I can only restart by holding down power button.

---

### Post by pauldeveth on 2013-02-22
Hi

Same here after upgading after 3.5.0-22 generic kernel image ubuntu wont boot up anymore. It falls back to some half x start with onley two icons on the desktop without unity loading correct.

dropping back to 3.5.0-22 generic kernel everything goes on like nothing happened.

We a&#341;e three kernels versions further ans problem consists in the same error.

If there anything I can do to help you youre welcom

Greetz

Paul

---

### Post by oldfred on 2013-02-22
I might just try reinstalling headers to make sure they are install and reinstalling nVidia drivers from Ubuntu to make sure they are installed using the newest kernel headers.

I am not at my machine with nVidia, so I cannot test for a month or more.

---

### Post by avielmenter on 2013-02-23
I have decent hardware but if I can't game well on Ubuntu's NVidia drivers then the point is moot. Is there a way I can update to a new kernel while using NVidia's drivers, or is that not an option? Everything I've tried here so far hasn't worked.

---

### Post by Jedcurtis on 2013-02-24
In the OP you mention that you have two video cards.  That means (especially with an Nvidia card) that you have most likely, Optimus hybrid graphics.  This will most certainly require Bumblebee.

As oldfred mentioned with 'nomodeset' you could also try something like 'acpi=noirq' among many other options.  The blinking cursor issue sounds like a definite graphics card issue to me.

After fighting with nvidia's ominous Optimus graphics for laptops (now  installed in 90% of newly sold laptops) for over a year, I wrote my own  How To [here]("http://vsido.org/index.php/topic,32.msg109.html#msg109").   This was written with my distribution in mind (VSIDO) but as it is a  Debian based distro just like Ubuntu is, it should work for you.  A  couple of points for you to be aware of with Bumblebee.
1.  It is mainly designed with the idea of 'Powersavings' related to battery life.
2.  The Hybrid/Optimus Graphics "share" a GPU.  Bumblebee doesn't turn one off, then activate the other...  (confusing I know!)
The x-swat repositories don't work for me and is the reason for me  writing the How To which points to the (I think) official Debian  supported repositories at [http://suwako.nomanga.net](http://suwako.nomanga.net).  
Like I said, try to follow the How To at the above link.  I'd appreciate  any feedback you may have.  This just resulted in me getting my second  newly purchased laptop (Feb. 21st 2013) up and fully functional.  It is  an MSI GT60 with Nvidia's GTX 675M with 2Gb of GDDR5 ram.  The first  laptop was a Dell XPS 15z with the GeForce 540M.  Both were able to be  put in working order using the How To.
If you don't want to use the Suwako repo's, then feel free to continue  with the Ubuntu xswat repo's but following the How To at the above link.
I have made this work with 2 separate Linux distributions now.  Ubuntu, and VSIDO my current Linux distro.
Again, the How To is here; [http://vsido.org/index.php/topic,32.msg109.html#msg109](http://vsido.org/index.php/topic,32.msg109.html#msg109)

You should "***_once again_***" uninstall all Bumblebee related software before trying this.  Hopefully this will end your Optimus nightmare!

If you have any questions, don't hesitate to ask!  I just wish someone  had done this before me, so I wouldn't have had to go through this  nightmare myself.

---

### Post by avielmenter on 2013-02-24
Okay, so I already have Optimus or I need to install it? Note that I'm not on a laptop. Also, can I get bumblebee via "sudo apt-get install bumblebee" or is it somewhere? I know I'm asking a lot of questions but I can't of need to be handheld. What exactly do I need to do.

---

### Post by oldfred on 2013-02-24
I do not know the dual video thing. Some live with one or the other video and not try switching..

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)

    
       Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by Jedcurtis on 2013-02-24
If you are not using a laptop, the odds are highly unlikely that you have Optimus enabled hardware.  I've never heard of it being on anything other than a laptop.  That being said, I'm not the guru that oldfred is and you'll probably be better off following his sage advice.  This breaks my "Linux" heart to say, but I've not read anything good when it comes to my favorite OS working and playing well with others when it comes to dual video anything!
I've been a full time Linux user a long time and have never had an easy time getting hybrid graphics to work well.  That was my thinking as I read the OP where you mention 2 video cards.  I "assumed" you had a laptop, so my bad for making assumptions.
Probably the easiest thing you could do, would be to remove one of the cards if it isn't being used to save you the trouble of trying to get both to work simultaneously.  Not saying it can't be done, just never have myself.  Been chained to a laptop for years now, and haven't worked on a desktop in a long time.
Sorry if I steered you in the wrong direction.

---

### Post by oldfred on 2013-02-25
I assumed it was a laptop also. That has two different video. The on chip Intel and a nVidia chip and it switches between performance and power savings.

If you just have two nVidia cards then I would think it is just the nVidia driver. You may need some settings, but I have not followed that. I have seen some threads with dual monitors or dual video where they have to edit xorg. But I have not had to edit xorg for 4 or 5 years so again I do not know details.

---

