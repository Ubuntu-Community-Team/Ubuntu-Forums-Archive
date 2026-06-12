---
title: "Asking for a little help ( Sound / Video )"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by maan84 on 2005-08-18
Hello, 

I recently installed Ubuntu 5.04 to try start using it for a while, and I like the look of it, but I'm totally new to Linux :)

I've been searching and looking for a bit, but there are a few things here that I can't get working: 

Can start with the resolution, I can't change it past 1024x768 @ 60Hz, and I searched a little and found a thread about it, but the solution provided there was the installation of the driver from ubuntuguide.org and I've done that, I even got that nvidia logo showing up at start, but I still can't change it in System - Preferences - Screen Resolution, I'm used to running 1600x1200 @75Hz. 

Secondly, I use to run WinXP and I have one partion on about 5.2GB and another on 30GB from the same HD a 36GB 10000rpm SATA drive. The 30GB one, I think it's called sda5? I'm not quite sure on that  Is NTFS file system, and I wanna be able to acces it from a typical file manager (Mount it?), and when I've searched, I've mostly found answers regarding fdisk etc which I'm used to running from DOS earlier years, don't know if that's the same but still, my point is I have a lot of music/video files etc on it that I wanna acces so I don't wanna reformat it or something  Oh and on the 5.2 one WinXP was which I deleted from the Ubuntu installed and created an ext3 one on 4.8 and a Swap with the rest.  

Third the sound don't work O_o It's a soundcard on the motherboard, and I ran that thing about gnome and sound in the ubuntuguide.org, still don't work, and Systems -> Preferences -> Multimedia Systems Selector , none of the esd etc work if I choose test. 

So any help with all of this I would so appriciate, and don't hesitate to ask for any more information needed, and easy answers since I'm new to this   ](*,) 

I just like to chat/music/video etc, oh and Gaim seems great  
Oh and I installed Fire Starter from the guide, and is there any way to make 
it start automatically when I logon? 

Thank you!  :-P

---

### Post by maan84 on 2005-08-19
I looked up some additional information regarding the sound, my motherboard is:

Intel Cherry Creek i915P 4DDR2-DIMM 4PCI 2PCIe SATA Audio LAN Socket775 ATX. 
Product link: [http://www.intel.com/design/motherbd/cy....htm?iid=ipp_browse+desktopbd_d915pcy&](http://www.intel.com/design/motherbd/cy....htm?iid=ipp_browse+desktopbd_d915pcy&) 

So the Audio would be Intel® High Definition Audio subsystem using the Realtek ALC860 audio codec. 

If this helps :O

---

### Post by crocco on 2005-08-19
I have the same issue regarding resolution options.  During install, I pushed enter when prompted to select resolution options.  This resulted in my only having three options, the best of which is 1024x768 @ 60Hz.  

How can I change my system for more options, in terms of resolution, after installation?  

Thanks in advace to the awesome tech help! \\:D/

---

### Post by AnythingBut on 2005-08-19
[QUOTE=maan84]
Can start with the resolution, I can't change it past 1024x768 @ 60Hz, and I searched a little and found a thread about it, but the solution provided there was the installation of the driver from ubuntuguide.org and I've done that, I even got that nvidia logo showing up at start, but I still can't change it in System - Preferences - Screen Resolution, I'm used to running 1600x1200 @75Hz. 
[/QUOTE]
There are a bunch of threads about screen resolution in the forums.  But this should get you started.  You are going to need to edit the /etc/X11/xorg.conf file.

In a terminal, backup the file first with
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Edit the file using
sudo nano /etc/X11/xorg.conf

Find the [COLOR=Blue]Section "Screen"[/COLOR] and make sure the sub section corresponding to your [COLOR=Blue]DefaultDepth[/COLOR] has the resolution you want.  For example,
```
Section "Screen"
        Identifier "Default Screen"
        Device     "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor    "P95f+-2"
        DefaultDepth     24
        SubSection "Display"
                Depth     16
                Modes    ""1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```
This would default to 1600x1200.  Be sure to read other threads on the topic in the forums.


[QUOTE=maan84]
Secondly, I use to run WinXP and I have one partion on about 5.2GB and another on 30GB from the same HD a 36GB 10000rpm SATA drive. The 30GB one, I think it's called sda5? I'm not quite sure on that  Is NTFS file system, and I wanna be able to acces it from a typical file manager (Mount it?), and when I've searched, I've mostly found answers regarding fdisk etc which I'm used to running from DOS earlier years, don't know if that's the same but still, my point is I have a lot of music/video files etc on it that I wanna acces so I don't wanna reformat it or something  Oh and on the 5.2 one WinXP was which I deleted from the Ubuntu installed and created an ext3 one on 4.8 and a Swap with the rest.  
[/QUOTE]
You can mount NTFS file systems in Linux.  It's usually a good idea to keep them read only.  Here's how:

Create a directory at which to mount the partition
sudo mkdir /mnt/ntfspartition

Mount the partition
sudo mount -t ntfs -o umask=0222 /dev/sda5 /mnt/ntfspartition

If this works out for you, you can make the mount occur at start up by adding a line to /etc/fstab

Edit fstab
sudo nano /etc/fstab

Add the line
/dev/sda5      /mnt/ntfspartition    ntfs    umask=0222      0       0

---

### Post by maan84 on 2005-08-19
Thank you very much for the detailed answer, I'm at work now, quit in about 1 hour, but I feel very excited about getting home and trying it out :)

I did some searches and it's a little worrying to see that it's pretty complicated to write to NTFS, since my partition with that filesystem is the "Storage" where I store all files that I download etc  :?   
 
Anyone have a suggestion on how I can solve the sound problem? I really love my music   \\:D/

---

### Post by AnythingBut on 2005-08-19
[QUOTE=maan84]
I did some searches and it's a little worrying to see that it's pretty complicated to write to NTFS, since my partition with that filesystem is the "Storage" where I store all files that I download etc  :?   
[/QUOTE]

I personally mount an NTFS volume as read only.  If you want write access and the ability to share the partion with windows, a VFAT partition might be the only answer.  But there's no easy way to convert NTFS to VFAT.  Sorry, I don't have a simple solution.
 
[QUOTE=maan84]
Anyone have a suggestion on how I can solve the sound problem? I really love my music   \\:D/[/QUOTE]

I'm not too familiar with sound, but I'll try to help.  Hopefully someone else will step in where my knowledge trails off.

Post the output of typing "lsmod | grep snd" in a terminal.  This will let us know if a modules (AKA driver) for your soundcard is loaded.

---

### Post by maan84 on 2005-08-19
Thank you for your reply. Mounting works yay :) Though I tried to open a .avi file with Totem and it complained about not being able to write to the disk =/ Though after driver installation (I think? lol), it complained about ALSA. Hmm  :-| 

I tried using "lsmod | grep snd" and when I execute it in the terminal nothing happens, just get back to command prompt, so I'm guess no sound driver is loaded?

I'm so new to all of this, I went to this page, [http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs)
And downloaded the linux driver, and then unpacked it and read the readme, and ran /install , but still sound don't seem to work  ](*,)

---

### Post by AnythingBut on 2005-08-20
Looks like the answer to your sound problem is here: 
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto) 

Let me know how it goes.

---

### Post by maan84 on 2005-08-21
[QUOTE=AnythingBut]Looks like the answer to your sound problem is here: 
[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto) 

Let me know how it goes.[/QUOTE]
 Thank you for finding that one, I tried it but I must've done something wrong, I downloaded all that it said from an FTP and ran the ./configure as it said, then on "make" it said must run configure first, and alternative 2 didn't work eaither it couldn't fint alsa-source package.

Heh so I kinda gave up, I went to my parents house and dug up some old soundcards and found a Soundblaster, and put that one in and now the sound works :) And I reinstalled Ubuntu and now I can run at resolution 1600x1200, but only at 60Hz =/ Don't know how to change to 75Hz? The monitor can run it, though in the System -> Prefrences -> Screen Resolution, there's only 60.

Thank you so much for your help :)
Now I gotta try getting codecs for divx/xvid etc, this will be a challenge:)

EDIT, all right can listen to mp3, play my dvds, and play mpeg/avi files :) 

I just wish I knew what I was doing while copying commands etc, I guess it'll come :P

EDIT#2, It's a little sad that x-vid playing in totem is a little laggy, and that xmms freezes whenever trying to play a mp3 (followed every step in the guide), so using "Music Player", works ok, but keeps gettin paranoid about the quality, but maybe something to do with the old soundcard, since I couldn't get the new one to run. And only using ESD works, if I choose something else in the "Multimedia System Selector", all I get is ALSA/OSS etc is busy when I try to play something, 

So if anyone reading this know something about improvement with anything, I'd be happy to try it out :)

---

### Post by Serzholino on 2005-12-07
Hi! In [https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto) written that for   BreezyBadger users sound must work out of the box. It's not true. My installation failed. Disabling hotplug helped me to complete installation, but there wasn't no sound. 

Then I downloaded latest alsa 1.10, installed it and  enabled hotplug there are some progress, but still no sound at all.
 
Now Kmix shows volume controls, but says that codec is Realtek 880, not 860. And alsamixer and alsactl still not working. Modules snd-hda-intel are loaded.

I've tried writing to alsa-user mailng list but haven't got any answer :(

---

### Post by Serzholino on 2005-12-08
For me helped Reateks version of alsa, grap it here [http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs#2004061Unix%20(Linux](http://www.realtek.com.tw/downloads/dlhd-2.aspx?lineid=2004052&famid=2004052&series=2004061&Software=True&title=HD%20Audio%20CODECs#2004061Unix%20(Linux))
Asla developers says that they are merging this version with upstream now in CVS

---

