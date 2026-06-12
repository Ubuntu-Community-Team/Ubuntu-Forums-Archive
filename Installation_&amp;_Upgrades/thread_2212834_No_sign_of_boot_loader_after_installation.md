---
title: "No sign of boot loader after installation"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by fangorn2 on 2014-03-23
Hello.

I tried to install Windows 7 and Ubuntu, in this order, but something went wrong after the Ubuntu installation.
After rebooting the machine, the message 'Out of Range' on black background appears on the screen, with no sign of any boot loader. This message should have something to do with the screen resolution...

I tried to use Boot Repair. I actually used Boot repair twice, the first time using the 'recommended repair' without results. 
You can find the first BootInfo summary at: [http://paste.ubuntu.com/7141099](http://paste.ubuntu.com/7141099)
The second time I changed, in advanced options, 'the OS to boot by default'. I was able to recover at least Windows. 
The second BootInfo summary is at: [http://paste.ubuntu.com/7141166](http://paste.ubuntu.com/7141166).

Therefore, now I am able to boot Windows but unable to boot Ubuntu. There is no trace of Grub. The machine loads Windows directly, after 5/7 seconds of the message 'Out of Range'.

Before installing Windows, and therefore Ubuntu, I partitioned my hd with GParted. This is how my partition table looks like:

- /dev/sda1: 70 Gb ntfs primary partition for Windows
- 73 Gb extended partition 
  /dev/sda5: 3 Gb logical partition for Swap
  /dev/sda6: 70 Gb logical partition for root (/)
- /dev/sda3: 90 Gb ntfs primary partition for documents

I am also unable to check whether the Ubuntu installation was succesful or not.
I am ready to use Gparted again, erase everything and start anew if necessary. I don't care about windows because is freshly installed and I do not have any data to save. I would like to know if any of you have any idea about how can I procede.

Many thanks in advance.

---

### Post by kc1di on 2014-03-23
Hi fangorn2,
And welcome to Ubuntu.

Grub is there but it's not able to render the video mode that being used.  it boots to windows because you must have that set as the default.  here's what to do to fix it or at least a work around.

boot up when you get the window saying out of range. hit the down arrow on your keyboard and hit enter see if that brings up Ubuntu.
if it does great.  If not try two down arrows and try again.  if it still does not work, try the up arrow once if not, try it twice. once you find where ubuntu is and it boots. 

The go to a terminal and type the following command:
```
sudo gedit
```
When gedit come up open this file ```
/etc/default/grub
```

when that file comes up scroll down to the line that looks like this:

```
#GRUB_GFXMODE=640x480
```

Change it so it looks like this:

```
GRUB_GFXMODE=1024x768
```

now save the file and close gedit and return to the terminal and type this command:
```
sudo update-grub
```

Then reboot you should now see a grub menu.  

(Note: in the above command you will need to enter your password when asked)
good luck.

---

### Post by fangorn2 on 2014-03-23
Hello Kc1di,

I hit the down arrow once and twice. In both cases I got Windows.
Hitting the up arrow once and twice brings up a terminal software called 'Memtest86 v4.20'.
Ubuntu started loading after hitting three times the up arrow, but something goes wrong and the 'recovery menu' appears. If from the list of choices I choose 'resume -> Resume normal boot', the following warning appears: 'Warning: Fake initctl called, doing nothing'.

---

### Post by kc1di on 2014-03-23
what choices did the recovery menu offer besides resume?
you may be getting a recovery menu with three up arrows, try four.
let me know what happens.

---

### Post by fangorn2 on 2014-03-23
If I hit the up arrow four times the screen remains black with a blinking cursor at the top left corner. To restart the machine I have to use the ctrl + alt + del combination. Before restarting I receive a list of 'Warning: Fake initctl called, doing nothing'.

The options of the Recovery Menu I get when I hit three times the up arrow are:

resume                 [Resume normal boot]
clean [Try to make free space]
dpkg                    [Repair broken packages]
failsafeX [              Run in failsafe graphic mode]
fsck                    [Check all file systems]
grub [                   Update grub bootloader]
network               [Enable networking]
root [Drop to root shell prompt]
system-summary [  System summary]

---

### Post by kc1di on 2014-03-23
Try the failsafex mode, see what happens.

---

### Post by fangorn2 on 2014-03-24
I tried the failsafeX mode but nothing happened. It goes back to the Recovery Menu.
These are the passages:

First message:
'Continuing will mount your / filesystem in read/write mode and mount any other filesystem defined in etc/fstab. Do you wish to continue?'

If I choose 'yes' the following warning appears:
'The system is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself'

Clicking 'ok' brings up this menu:
'Run in low graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to consol login'

If I choose 'run in low-graphics mode for just one session' a window appears: 'stand by one minute while the display restarts'.
I click ok and the Recovery Menu comes back.

---

### Post by kc1di on 2014-03-24
At this point I think your best bet would be a re install of Ubuntu.

---

### Post by fangorn2 on 2014-03-24
I already tried to reinstall it.
I noticed that after the first and the second installation the machine did not reboot but I had to do it myself manually. The screen was black.

I chose Ubuntu 12.04 LTS desktop 64bit. I have 3 Gb of RAM.
Do I have to change my partition table configuration? Ubuntu is installed and would be installed in an extended partition. This should be all right, as far as I know. The last BootRepair bootinfo is: [http://paste.ubuntu.com/7141166/](http://paste.ubuntu.com/7141166/)

I think something should be changed to get a different result.
I will try to download Ubuntu again and make a new installation dvd.

---

### Post by kc1di on 2014-03-24
give us some information on the machine,
make model ram you gave, video card

Also when you do the new download check the MD5sum make sure you got a good download.
you can get information on that [here]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by fangorn2 on 2014-03-24
I am making progress.
I could not check the DVD integrity because I was not able to load the menu while booting from the dvd.
So I downloaded again Ubuntu iso image, tested the file with winMD5Sum and made another bootable dvd. This time I was able to verify the new dvd integrity: everything was fine. So I used the new dvd to reinstall Ubuntu. I still had to cope with the 'Out of Range' welcoming message after the reboot.

I managed to load Ubuntu in safe mode. Once Ubuntu was loaded, I followed your instructions in the first of your messages, restarted the machine and now any time I make a restart I can see these options from Grub:

Ubuntu, with Linux 3.11.0-15-generic
Ubuntu, with Linux 3.11.0-15-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sdb1)
Windows Vista (loader) (on /dev/sdb2)

Windows Vista was the OS installed in my external hard drive, retrieved from an old notebook. I do not need the last two options.
Anyway what is important is that I am able to load Windows 7, and Ubuntu in recovery mode (option 2). I am still unable to load the default option, that is Ubuntu (option 1). When I try to load Ubuntu, the login windows appears for seconds. During this time I cannot move the mouse pointer nor insert my login details. Then the screen gets black and I have to reboot manually.

I am able to load Ubuntu if I choose 'resume [Resume normal boot]' from the recovery mode menu.

If it can be of any help, here is some information about my machine:

Mainboard: Asus M2N-MX SE
Chipset: nVidia GeForce 6100V
Processor: AMD Athlon 64 X2 5000+ @ 2600MHz
Physical memory: 3072 MB DDR2-SDRAM
Video card: NVIDIA GeForce 6150SE nForce 430
Audio card: ASUSTeK Computer nForce 430 (MCP61) High Definition Audio
Network card: NVIDIA nForce Networking Controller
Hard disk: 250 GB

---

### Post by oldfred on 2014-03-24
I have a bit newer nVidia card and have to use nomodeset in grub menu until I install the proprietary nVidia drivers.
Use e on grub menu for edit, scroll to linux line and replace quiet splash with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I am not sure your card is new enough for the current nVidia driver. But there are two different versions for older cards. Be sure to install correct version or else it can be a big issue. With nVidia you cannot install a correct driver over an incorrect one, but must thoroughly houseclean incorrect version(s).

Also only install from repository. Other options of ppa or direct from nVidia are much more advanced and rarely required.

 [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
      [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
           
 nVidia versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by fangorn2 on 2014-03-24
Thanks oldfred.
I edited the grub menu with 'e'. I was able to boot with ctrl+x. Once Ubuntu was loaded I permanently edited the file /etc/default/grub changing the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

into this:

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

I also found useful this thread: [http://ubuntuforums.org/showthread.php?t=1542883](http://ubuntuforums.org/showthread.php?t=1542883)

Now I think I have to look for the right nVidia driver. I will follow your links for this. This search I think does not pertain to this thread.

The last question I would like to ask is how to remove the boot options related to Windows Vista.
If I have understood, I should edit the file /boot/grub/grub.cfg, removing or commenting (adding a #) the start of the lines which refers to Windows Vista.

These lines for each option look like:

menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd1,msos1)'
search --no-floppy --fs-uuid  --set=root 13670***********
chainloader +1
}

Is this correct? I would remove them.
Is there anything else, any other file to edit?

---

### Post by kc1di on 2014-03-24
You need to install nvidia-304 driver. you have he same video card that I'm using on this machine. the 304 driver works well for me.
you can install it from the software center search for nvidia-304  or by typing in the terminal :
```
sudo apt-get install nvidia-304
```

remember to reboot after installing. 
good luck

---

### Post by oldfred on 2014-03-24
Once you install correct nVidia driver you must remove nomodeset.

You are not supposed to edit grub.cfg. It is auto regenerated on updates or anytime you change any grub settings and run sudo update-grub.

Best to turn off os-prober. If you need any boot stanza for Windows 7, you can just copy the one you want into 40_custom. If you add another system then turn os-prober back on.

Copy Windows boot stanza:
 gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Turn off os-prober to not create Vista (or any) entries automatically.

        In /etc/default/grub I added this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by fangorn2 on 2014-03-24
Many thanks, the nvidia-304 driver works well for me too :p

Shall I have to copy to 40_custom all the stanzas I want to keep, or only that for Windows 7?
/boot/grub/grub.cfg has stanzas for each of these options:

Ubuntu, with Linux 3.11.0-15-generic
Ubuntu, with Linux 3.11.0-15-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sdb1)
Windows Vista (loader) (on /dev/sdb2)

I want to remove the last two options.
Apart from turning off os-prober, shall I have to copy to 40_custom the stanzas also for the Memory test entries?
I suppose I do not have to include in 40_custom the stanzas for Ubuntu.

---

### Post by oldfred on 2014-03-24
You just need Windows 7. 

The os-prober looks for all other installs on your system whether Windows or other Linux.
There are multiple scripts and each adds part of the boot stanza from the scripts, adding options from grub settings and appending in boot stanzas from 40_custom.

If for any reason you wanted to boot Windows first, you can copy 40_custom to 06_custom and add Windows boot stanza to that. Then it will always be first in boot menu as that script would be before the standard ones. 

Grub runs script that are executable and have two digits and an underscore in the scripts folder.

 Configuring the Boot Menu in Ubuntu - Boot Order in grub
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)
      
 Ubuntu Community Documentation site
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by fangorn2 on 2014-03-25
Made it. Now everything works fine.

Many thanks to both of you Kc1di and oldfred for your help.
See you somewhere in ubuntuforums :)

---

### Post by kc1di on 2014-03-25
Glad it's all sorted for you :) 
Enjoy.

---

