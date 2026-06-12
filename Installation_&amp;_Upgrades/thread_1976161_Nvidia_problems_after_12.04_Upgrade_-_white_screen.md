---
title: "Nvidia problems after 12.04 Upgrade - white screen after boot"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by keithwwalker on 2012-05-08
This problem is solved, go to this thread for details of the updated nVidia driver:
[http://ubuntuforums.org/showthread.php?t=1977972]("http://ubuntuforums.org/showthread.php?t=1977972")
Beware, that the Ubuntu update packager seems to remove the nVidia driver settings at this time, so update at your own risk!
For instructions on the nVidia problem refer to the above mentioned thread, for the Grub1.5 to 2.0 issue read on, thanks!
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I did the automatic upgrade from 11.10 to 12.04 and when the pc rebooted the GRUB 1.5 menu did not update to 12.04.

I am running a dual boot system with the other partition running winxp.

Anyway, in GRUB I select 11.10 (doesn't matter which version), and 12.10 boots up.

Problem is the colors are washed out so much that I can barely see the sign in screen and the top bar.

After I log in, I briefly see my old wallpaper (but not my desktop icons), then a white screen pops up and I can not see ANYTHING on the screen.

I can ctrl-alt-f1 to get into the terminal, and that is barely legible (but something).

Can anyone advise or link to one of these two possible solutions?

Is there a way to do a complete new 12.04 installation on the ubuntu partition without wiping the data on the winxp or ubuntu partition (I have almost 15 years of my data on that partition)?  If I use a CD, it tells me that I will delete everything.  Further, trying to boot on the CD is not working anymore.

Alternatively, it seems there is a layer over the screen, can this be disabled somehow, or how can I install the updates for a previous nvidia version or a fix?

This is extremely frustrating, never had a problem like this, 11.10 ran perfect.

---

### Post by bogan on 2012-05-08
Hi!, **keithwalker,**

You Posted: > Alternatively, it seems there is a layer over the screen, can this be  disabled somehow, or how can I install the updates for a previous nvidia  version or a fix? I think the 'invisibility' problem is a matter of the default Themes not being compatible with Gnome3, or vica versa. See my thread:[http://ubuntuforums.org/showthread.php?t=1966094](http://ubuntuforums.org/showthread.php?t=1966094) 
Though your description seems a bit more complex than just that.

Do your Launcher Icons show up in Ubuntu 3D or gnome classic?

What video card do you have, and is there an integrated GPU as well?

I would suggest, instead of installing a previous nvidia driver, that you install the latest version 295.49: if you have an internet connection ```
sudo nvidia-installer -f
```will un-install the present driver and download and substitute 295.49.

You have to run it from a text terminal without the x-server running. 'Ctrl_Alt+F1' and login at the tty prompt. If you come from a GUI started terminal you will need to enter ```
sudo service lightdm stop 
```and enter 'Ctrl_Alt+F1' or F2 & login again at the tty, before entering the 'nvidia-installer -f' code.

Afterwards reboot.

Post here if you need more info.

Chao!, **bogan**.

---

### Post by thatsmyboy on 2012-05-08
It seems like I'm having a similar issue with my install from Lucid. > **thatsmyboy said:**
> Just did a "fresh" install of Precise (12.04) over a lucid LTS box. I'm not sure which driver I'm using , so information to locate that would be welcome. as it stands I'm stuck looking at the desktop and navigating from there to applications - more likely clicking a document to launch the associated app. 

---

### Post by bogan on 2012-05-08
Hi!, **thatsmyboy,**

If you have an nvidia gpu card, from a terminal run:```
 cat /sys/module/nvidia/version
``` or, if you have an Internet connection ```
sudo nvidia-installer --latest
```You Posted:>  I'm stuck looking at the desktop and navigating from there to applicationsWhich sounds as if you are running Gnome or Gnome Classic, but it is not obvious to me what the problem is you want help to solve, unless you are still running Lucid or have a 'White on White' Theme problem.

Please Post details of your computer, especially video card.

Also please clarify to what point your system boots, do you get a GUI Login screen, with the Unity Launcher and topbar Icons after login, or do you have the Applications Menu header top left, or both?

Chao!, **bogan**.

---

### Post by keithwwalker on 2012-05-08
Thank you for the response Bogan.
I am using Gnome Classic.
My pc is a VCG-V620G all in one pc (desktop with pc built into back of lcd panel with laptop gpu)
The gpu is a NVIDIA GeForce FX Go 5700.

The GUI launcher is legible, but the colors are off.
After login, the launcher icons do not show up, but I see a 'white shadow' where the launcher bar should be.
The topbar is barely legible.
The desktop screen seems to have a white layer atop it, but even before that loads after login, you can not see any desktop icons.

I will try your advice and report back, thanks!

Well I tried the 
```
sudo nvidia-installer -f
```
it said 'command not found'

Will now try
```
sudo nvidia-installer --latest
```

kww

---

### Post by keithwwalker on 2012-05-09
My screen now renders correctly.  I upgraded the nvidia driver with this command:

```
sudo apt-get install nvidia-current
```

The current nvidia driver 295.40 loaded.
There was some weird text flying by indicating that some packages weren't loaded in.

Anyway, cut to the chase and the driver loaded in.  I would say that this episode is **solved**, but the driver only offers two resolutions at this time:
800x600
1024x768

Unfortunately, my resolution is 1280 x 768, but I will get by.

When I find the resolution solution, I will post that and change the thread to solved.

My upgrade build didn't complete, as GRUB 1.5 doesn't show 12.04 options as loading (still shows 11.10 and XP), even though I am clearly on 12.04.  I will search or start another thread for that problem though.

Thanks again!

---

### Post by bogan on 2012-05-09
Hi!, **keithwalker,**

This is a bit weird! The nvidia-current 295.40 driver is the bugged one all the fuss is about, but in anycase it does not support your video card!!

The driver you want is v173.14.30, listed in Synaptic Package Manager as "nvidia-73"; you can install it from there, or, probably better still from Nvidia Driver Downloads under "GeForce>5 FX series.

You may need to remove the existing driver and purge it, if the nvidia install does not do so; then reinstall.

However, If it ain't broke, don't Fix it.

If the nvidia-installer cmd was not found, that means there was no nvidia driver properly installed, at the time.

Edit: As for the incomplete install, grub1.5 is ancient you should have grub2, which shows in the grub boot menu title as Grub 1.99!

I suggest you run:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -a
sudo apt-get autoremove
```If that does not fix it you will need to remove grub1.5 and install grub 2, but that is more complex.

Chao!,** bogan**.

---

### Post by checkmateuk on 2012-05-09
Hi, I'm having problems with this white screen issue too.
If I install the 'latest' Nvidia driver (v295.40) I get offered a maximum screen resolution of 1024x768 (I want 1280x1024)
However, attempts to install the v173.14.30 driver just throw up the message:
> The following packages have unmet dependencies:

nvidia-173: Depends: x11-common (>= 1:7.0.0) but 1:7.6+12ubuntu1 is to be installed
            Depends: xorg-video-abi-10 but it is not going to be installed
            Depends: xserver-xorg-core (>= 2:1.8.99.905-1ubuntu3) but 2:1.11.4-0ubuntu10.2 is to be installed

I hear the v295.49 might solve some issues, but as a newbie I have no idea how to get this version!

---

### Post by bogan on 2012-05-09
Hi!, **checkmateuk**,

Download the 295.49 driver from nvidia.com /Driver downloads and run the file from a text terminal. but be sure it is the right version for your video card, it is not for FX series cards.

Check out MAFoElffen's Step-by-Step Trouble shooter in the Sticky of  'Installations & Upgrades': Post #1. There is a full Index in Post  #2.
[http://ubuntuforums.org/showthread.p...43535&page=101]("http://ubuntuforums.org/showthread.php?t=1743535&page=101")

The instructions you want are in Post #280 about page 71.

Chao!, **bogan**.

---

### Post by checkmateuk on 2012-05-09
Hi Bogan, many thanks for your prompt reply! Let me clarify:

I do indeed have an FX series card - it's a GeForce FX 5700. With the clean Ubuntu 12.04 install I get the 'White Screen of Death'. I have to select 2D mode to run anything, but it's painfully slow.

With installation of the v295.40 (aka. 'Latest') driver I get everything successfully working, except my screen is no longer detected (Displays calls it 'Laptop') and I'm left with a maximum selectable resolution of 1024x768.

When I attempt to install the recommended driver for my series of graphics card (v173.14.30) I get the message mentioned in my post below.

So if I can't install the older driver and the new one isn't supposed to be compatible with an ageing FX5700, what are my options?

I have downloaded the v294.49 driver, but when I install it I have to apparently use the 
sudo service lightdm stop
command but when I do, everything shuts off and I'm left with a black screen with a little bit of text at the top about 'checking battery state' or something to that effect with a flashing cursor underneath. Am I supposed to know how to log back in from that point as I haven't seen it explained anywhere!

EDIT: I managed to install the 294.49 driver, but this resulted in the same resolution problem (except this time my max selectable was 800x600!). How can I get the 173.x driver installed despite the 'unmet dependencies'?

---

### Post by Pablo Pablovski on 2012-05-09
The 295.49 driver is now available from the *precise-proposed* repository. 

I was running 295.33 on my kubuntu precise install, and now it's happily running 295.49. No issues so far (10 mins!).

---

### Post by checkmateuk on 2012-05-09
Okay, after a few hours of forum research (what fun!) I see what the issue is now. NVIDIA drivers 96 and 173 series are not compatible with X.org in Ubuntu 12.04. Luckily, Nvidia have confirmed they're working on an update to the 173 series, which is the one I need. So it's just a case of waiting for the update!

---

### Post by keithwwalker on 2012-05-09
Bogan

I recall a previous resolution problem with a previous upgrade concerning the nvidia resolutions.

Unfortunately, I do not recall the solution at the time, but it was probably an install of a legacy nvidia driver from the nvidia site.

fwiw, nvidia lists the following legacy drivers for linux:
[unix drivers]("http://www.nvidia.com/object/unix.html")

fyi, I started upgrading to GRUB2 last night.

I used the guide here:
[GRUB2]("https://help.ubuntu.com/community/Grub2")

Everything was working well, so I then put this command into the terminal:
```
sudo upgrade-from-grub-legacy
```

I did not run the following command right afterwards (now I wish I had):
```
rm -f /boot/grub/menu.lst*
```

upon reboot, I was expecting to see the GRUB2 menu and the initialization for GRUB1.5 still came up, followed immediately by the dreaded error 15.

GRUB2 is definitely installed, it worked through the chainloader, just now have to figure out how to purge the rest of the GRUB1.5 elements.

more later...

> **bogan said:**
> Hi!, **keithwalker,**

This is a bit weird! The nvidia-current 295.40 driver is the bugged one all the fuss is about, but in anycase it does not support your video card!!

The driver you want is v173.14.30, listed in Synaptic Package Manager as "nvidia-73"; you can install it from there, or, probably better still from Nvidia Driver Downloads under "GeForce>5 FX series.

You may need to remove the existing driver and purge it, if the nvidia install does not do so; then reinstall.

However, If it ain't broke, don't Fix it.

If the nvidia-installer cmd was not found, that means there was no nvidia driver properly installed, at the time.

Edit: As for the incomplete install, grub1.5 is ancient you should have grub2, which shows in the grub boot menu title as Grub 1.99!

I suggest you run:```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -a
sudo apt-get autoremove
```If that does not fix it you will need to remove grub1.5 and install grub 2, but that is more complex.

Chao!,** bogan**.

---

### Post by bogan on 2012-05-10
Hi!, checkmateuk,

You Posted: 
> I have downloaded the v294.49 driver, but when I install it I have to apparently use the 'sudo service lightdm stop' command but when I do, everything shuts off and I'm left with a black  screen with a little bit of text at the top about 'checking battery  state' or something to that effect with a flashing cursor underneath. Am  I supposed to know how to log back in from that point as I haven't seen  it explained anywhere!That is because you are still in the Graphics mode [Ctrl+Alt+F7] but you have closed the Manager; so press 'Ctrl+Alt+F1' or F2-F6 and you will get a tty [Text Terminal] log-in prompt.

There do whatever you need to do and then press 'Ctrl+Alt+F7' to return to graphics mode, or reboot.

You can download the 173.xx driver from nvidia.com>Driver Downloads either by using the search function or selecting "beta & older drivers", though the 'latest' version is dated AUG 2010. [See the comment above about its incompatibility with 12.04 Xorg!]

Chao!, **bogan**.

---

### Post by keithwwalker on 2012-05-11
Well I solved my Grub problem with [Rescatux]("http://www.supergrubdisk.org/rescatux/")
You insert it like you would a live boot disk cd, but it has a graphical interface which makes restoring your GRUB2 booter almost idiot proof!

When I booted my disc, it too gave a 'grayed' out screen, but there was enough legibility for me to select the proper buttons to restore the GRUB2 program.

Now the only remaining task is to restore my full screen resolution.  I will try the nvidia drivers mentioned earlier in the thread.

Thanks for the help!
kw

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by m0dcm on 2012-06-20
I'm also having the grey screen issue with a cutout where Unity should be, and it's not displaying any open windows from either a LiveCD or fresh install.
My PC is a Sony Vaio VGC-V2M with the GeForceFX 5700 on board GPU.

Has anyone got the current 173 driver running correctly? I'd love to get Ubuntu 12.04LTS installed on this machine.

Cheers....

---

### Post by keithwwalker on 2012-10-29
Instructions on how to load the driver here:
[http://ubuntuforums.org/showpost.php?p=11951878&postcount=13]("http://ubuntuforums.org/showpost.php?p=11951878&postcount=13")
However, when I do automated updates, the driver is booted, and you have to load it manually again....  Wish Nvidia and Ubuntu dealt with this better.

> **m0dcm said:**
> I'm also having the grey screen issue with a cutout where Unity should be, and it's not displaying any open windows from either a LiveCD or fresh install.
My PC is a Sony Vaio VGC-V2M with the GeForceFX 5700 on board GPU.

Has anyone got the current 173 driver running correctly? I'd love to get Ubuntu 12.04LTS installed on this machine.

Cheers....

---

