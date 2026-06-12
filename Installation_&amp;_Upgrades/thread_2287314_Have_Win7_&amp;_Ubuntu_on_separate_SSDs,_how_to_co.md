---
title: "Have Win7 &amp; Ubuntu on separate SSDs, how to config bootup so I can load one I want?"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by PsychedelicWonders on 2015-07-18
Ok so I have Win7 & Ubuntu, each on their own SSD.

I have them both hooked up right now, but it only booted up the windows SSD, it didn't prompt me to to choose between either Win7 or Ubuntu?

So how do I configure it to prompt me upon bootup to pick which OS I want to use at the time?

Also, when I just have the Ubuntu SSD hooked up, when it boots up I get a menu with the following options:

Ubuntu
Advanced Options for Ubuntu
Memory Test
Memory Test (serial console)

What is this menu for & how do I get rid of it from bootup & replaced by just a Win7 or Ubuntu option choice?

---

### Post by ubfan1 on 2015-07-18
If you switch the two SSDs on the ports they are using, do you get the Ubuntu menu?  If so, run Ubuntu and then run sudo update-grub to pick up the Windows boot.  Getting rid of the other menu items may be done by taking the execute permission off the appropriate file in /etc/grub.d (identified as a section in the comments of the /boot/grub/grub.cfg file).  Keep a copy of the original if you have to remove a section of any of the files, then run update-grub again.

---

### Post by Bashing-om on 2015-07-18
PsychedelicWonders; Hello;

Another thought too ^^ :
> 
Ok so I have Win7 & Ubuntu, each on their own SSD.

How about switching boot drives in bios when required to -only- boot Windows.

If one has Windows' boot code installed to the drive containing Windows and untouched by ubuntu, then can always boot that drive by selecting it in bios.
With ubuntu's boot code installed to ubunu's drive, and grub updated to pick up the Windows' installation on the other hard drive, will have the option to boot either operating system when in grub the hard drive containing ubuntu is set as the boot priority.

[INDENT][INDENT]best of both worlds
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-18
Are both systems installed in UEFI boot mode or both systems installed in BIOS boot mode?
Only if both systems are same boot mode can you boot from grub menu as UEFI & BIOS are not compatible. You can only boot from UEFI/BIOS to switch boot modes.

---

### Post by PsychedelicWonders on 2015-07-18
Ok so I ran sudo update-grub and had this come up, I haven't rebooted to test it yet, but does it look right?:

```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
done


```

> **Bashing-om said:**
> PsychedelicWonders; Hello;

Another thought too ^^ :

How about switching boot drives in bios when required to -only- boot Windows.

If one has Windows' boot code installed to the drive containing Windows and untouched by ubuntu, then can always boot that drive by selecting it in bios.
With ubuntu's boot code installed to ubunu's drive, and grub updated to pick up the Windows' installation on the other hard drive, will have the option to boot either operating system when in grub the hard drive containing ubuntu is set as the boot priority.
[INDENT][INDENT]best of both worlds
[/INDENT]
[/INDENT]


I'm not sure, I'll check to see if I can switch bios boot, but I would really prefer to have bios boot to a menu to make me choose which OS I want to use since I'll be jumping back & forth for a while until I'm really used to Ubuntu.  

So how would I go about doing that?  Is it already done now that I did the sudo update-grub?  (going to reboot and test it out after I post this)

> **oldfred said:**
> Are both systems installed in UEFI boot mode or both systems installed in BIOS boot mode?
Only if both systems are same boot mode can you boot from grub menu as UEFI & BIOS are not compatible. You can only boot from UEFI/BIOS to switch boot modes.

I'm not sure, how do I tell if they are both installed in UEFI or BIOS mode?  I have an older Asus P5k mobo, so I'm not sure if I even have UEFI, I've only seen/worked with BIOS from what I can figure out?

---

### Post by Bashing-om on 2015-07-18
PsychedelicWonders; Hey ;

Yepper:
> 
but I would really prefer to have bios boot to a menu to make me choose which OS I want to use since I'll be jumping back & forth for a while until I'm really used to Ubuntu. 

So how would I go about doing that? Is it already done now that I did the sudo update-grub?


Should now be a done deal; per:
> 
Found Windows 7 (loader) on /dev/sdb1


So, reboot with 'sda' continuing as the 1st boot priority and you should have the option now whether to boot ubuntu or Windows.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by PsychedelicWonders on 2015-07-18
Ok yes, I think everything is good, I have the GRUB menu pulling up now with the Windows 7 Loader option at the bottom of the list:

[ATTACH=CONFIG]263273[/ATTACH]

So that looks right, that is the only version that GRUB is going to visually look like right?

So now that I have them both available for my choice upon bootup, how do I go about getting rid of the Advanced Ubuntu Settings & Memtest options out of the GRUB menu?

What benefit would I have in keeping the Advanced Ubuntu Settings options on the GRUB menu list?  I'd really just like it as clean as possible with either just Ubuntu or Win7

---

### Post by oldfred on 2015-07-18
If an older motherboard, it probably is BIOS. All Windows 8 systems are UEFI. Only a few Windows 7 systems later in production may be UEFI hardware, but Windows was still in BIOS mode.

Each of those grub entries is a script in 
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

If primarily using Windows you may want it first in menu.
You can edit 40_custom with your own entries, but those are last. Or copy 40_custom to 06_custom and copy the Windows boot stanza into that. Grub processes scripts in number order, and then Windows will be first. Then turn off os-prober, so it does not automatically keep adding a new Windows entry last.

In terminal:

 sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
       
 sudo chmod a+x /etc/grub.d/06_custom
    sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup

 gedit /boot/grub/grub.cfg
# copy Windows boot stanza from above to below, do not remove any existing text.
sudo nano /etc/grub.d/06_custom
sudo update-grub

If you can then boot new entry without issue, turn off os-prober.
      
  turn off executeable bit, You can do the same for 20_memtest86+ if you do not want that entry.
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by PsychedelicWonders on 2015-07-18
Ok yes it's just bios then, it's an older Asus P5k-E board.

I honestly want to start using Ubuntu as much as possible/as primary OS - as long as I can get rid of this freezing/lockup it's doing every few minutes, it's beyond frustrating.

So out of those two links you posted for making a Grub2 menu (which I assume the 2 just means a customized one) what are the differences between the two links?  Should I just follow either one or do they each do something different of the other?

The first one seems to allow background images, which is pretty cool considering the stock dark purple/black is kind of blah... might as well dress it up if I can.  So in that case should I just stick with the first walk-thru?

Is your terminal code just cliff notes of either one of those walk-thrus, or would that be in addition to one of the walk-thrus?

Sorry I'm basically new to Ubuntu as it's been 5 or 6 years since I used it last and forgot everything lol.

---

### Post by oldfred on 2015-07-18
If you just want to change menu, the specific commands I posted will do that.
But the links are for more info, explanation, and detail of many changes you can do.

---

### Post by PsychedelicWonders on 2015-07-18
So trying to give grub a background picture from one of those walktrhoughs that say this:

[h=3]Setting up a Grub background picture[/h] You need to move 1 picture that is the same size as your screen resolution to **/boot/grub/** e.g. **sudo cp rain.jpg /boot/grub/**. 
 If you change the picture be sure and remove the previous one because it looks for the first one it finds. 
 To remove the picture you would enter **sudo rm /boot/grub/rain.jpg**. 
 
If the picture is listed when you enter **sudo update-grub** but, does not show up at boot time, try another picture. 
 It is because of the existance of the picture that grub uses the font colors in **/etc/grub.d/05_debian_theme**.

```
johnnyscience@SpaceStation:~$ sudo cp thematrix.jpg /boot/grub/
[sudo] password for johnnyscience: 
cp: cannot stat &#8216;thematrix.jpg&#8217;: No such file or directory
johnnyscience@SpaceStation:~$ 

```

What am I doing wrong?

---

### Post by PsychedelicWonders on 2015-07-18
```
johnnyscience@SpaceStation:~$ sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
[sudo] password for johnnyscience: 
johnnyscience@SpaceStation:~$ sudo chmod a+x /etc/grub.d/06_custom
johnnyscience@SpaceStation:~$ sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
johnnyscience@SpaceStation:~$ 

```

Man I don't know how anyone figures this stuff out without help, I have no clue what I'm doing, it doesn't seem to be running the code right does it?  I've tried multiple times and made sure my password was correct

---

### Post by tokyobadger on 2015-07-19
the cp command is relative you get the error message because you're not in the same location as the file when you execute the command - you have 2 options:
1) navigate to the directory with the desired picture eg cd /home/johnnyscience/Pictures (assuming that Pictures is where you have the image file you want) then execute the cp commands as above
2) from wherever you currently are specify the full path to the image file eg sudo cp /home/johnnyscience/Pictures/thematrix.jpg /boot/grub/ 

The linked walkthrough shows sudo chmod +x /etc/grub.d/06_custom - you have the flags a+x - any reason?

---

### Post by oldfred on 2015-07-19
If you get no error message it worked. That is a good thing.

If copy did not work and you try to edit 06_custom, nano will create a new file, which you do not want. As you have to have the couple of lines at the top of 40_custom. 

Path is full path so can be run from anywhere. If in a location and you want to copy from there you do not have to have full path on the from location. 

You can always check. I often also have Nautilus or file browser open also and can drill down to that location to see what files are where. Or open another terminal and change to new location.

I do not know where I picked up a+x. But that actually converts all users to allow execute which probably is not correct. Only root when grub is running updates with sudo should need or have execute bit set. My list does show +x for all users.

```
fred@trusy-ar:~$ cd /etc/grub.d
fred@trusy-ar:/etc/grub.d$ ls -l
total 80
-rwxr-xr-x 1 root root  9424 Jun 26 06:16 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   724 Jul  6 16:30 40_custom
-rwxr-xr-x 1 root root   638 Dec  6  2014 40_custom~
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README

```

After running command the 30_os-prober has no execute bits set:
```
 sudo chmod a-x /etc/grub.d/30_os-prober
 ls -l /etc/grub.d
-rw-r--r-- 1 root root 11692 May 15  2014 30_os-prober

```
If your command worked you will  also have a 06_custom with execute bit set (the x ).

I have not turned off os-prober in this install.

---

### Post by tokyobadger on 2015-07-19
@oldfred: I missed what you posted and went straight to your links - wasn't nitpicking, just rt#m ;-)

---

### Post by oldfred on 2015-07-19
@tokyobadger
No problem. Oldfred has regularly posted something not quite right (he blames the old in oldfred, or those fingers that like to mistype :) ). And it always is good that another user reviews posts to clarify or correct information.

---

### Post by efflandt on 2015-07-20
Note that something you might run into rarely is Win7 updates that do not work unless Windows boots itself from its own mbr. But so far it was only a Win7 service pack update years ago and one more recent update in the past year. If you run into that you could set your BIOS to temporarily boot your Windows drive first. Then after the update is successful, switch back to booting your Ubuntu drive.

It is probably not a problem booting Windows from sdb in a pinch, as long as that is set as the boot drive in BIOS at the time. But Linux is less particular about where it boots from, so that is why I usually leave Windows drive as sda and boot grub from sdb. On my desktop I have Win7 and Ubuntu 14.04 on sda (with standard DOS/Win mbr) and normally boot everything from grub on sdb (SSD w/small Ubuntu 12.04 system for emergencies, which I should update one of these days). If for some reason I have an issue with the SSD I can set sda as the boot drive and either boot Windows with the boot flag where it normally expects it or can unset that and set the boot flag to sda4 where I installed 14.04's grub.

On my laptop similarly sda is Win7 with its standard mbr and I normally boot sdb (mSATA SSD) which has 14.04 with its grub on its mbr. But I can simply switch the boot drive in BIOS from sdb to sda if a Win7 update requires booting from its mbr.

---

