---
title: "Help... upgrade to 19.10 almost finished - power outage"
date: 2019-10-23
forum: Installation &amp; Upgrades
---

### Post by bierdo69 on 2019-10-23
I was running 19.9 (Disco Dingo) and decided to upgrade to 19.10, 
I followed all the options and was going well, I was almost finished and I had a power outage.
On restart it won't fully go into 19.10, it starts (goes through some stuff) and then just stops and stays on a blank screen with a cursor showing "-" at the top left of the screen.

When I try to start it or go into recovery mode, I only get 19.10 options (which I would like to finish upgrading).
As 19.10 won't start, I thought upgrading from my old Ubuntu might work, but I don't know how to access this, to finish the upgrade...
I'm worried after all of this I might lose files on my desktop etc... (yes I should have backed up ...)

Can anyone help me ...

---

### Post by crip720 on 2019-10-23
Do you happen to still have the installer USB, any recent one should do?

---

### Post by rbmorse on 2019-10-23
The 19.10 dailies are being posted, so you could grab the latest one of those and make a live install flash media (or DVD) from that.

---

### Post by bierdo69 on 2019-10-23
No USB installer as I did it all online ...

Cool I'll look for the 19.10 dailies, what ever they are.
I ALWAYS use Ubuntu and I have for years, I've never had an issue.
    So from the dailies can I continue the installation?
    I don't want to loose my desktop folders/files and personal etc...

---

### Post by bierdo69 on 2019-10-24
By the way, thank you for your help.
I haven't found a solution yet, but thanks. 
:-)

---

### Post by westie457 on 2019-10-24
This might work.

Boot the system into recovery mode, at the on screen menu select 'Root Prompt'

In here run 'dpkg --configure -a' to fix the not quite installed packages.
This command is optional : 'apt install -f' #not sure if this will work in the root prompt without internet access
Reboot to 'hopefully' normal system, open a terminal and run ```
sudo apt install -f
sudo apt update
sudo apt upgrade
```

All being well you should have a usable system.

---

### Post by Impavidus on 2019-10-24
Before you run any other commands at the root shell, you may have to remount the file system in read-write mode:```
mount -rw -o remount /
```

---

### Post by bierdo69 on 2019-10-26
Thanks for the help, westie457 and Impavidus,
I followed all your suggestions and it seemed to help.
After running 
mount -rw -o remount /
and
run 'dpkg --configure -a' 

It allowed me to login like normal and then up comes:
"Oh no! Something has gone wrong"
...
"Log Out"

So the Ubuntu system still has problems and doesn't want to run, 
I can't get into the Terminal to run the Code or maybe there's another solution?
HELP ...

I'll restart it and see if this helps?
And if I can, I'll run the Code in the Terminal ...

---

### Post by bierdo69 on 2019-10-26
Restarting doesn't fix it.
As I'm running two screens, the main screen is blocked by the error code.
The second has the rest of the desktop, so I could right click and run a terminal from desktop? ...

Thanks to help from the two people just before, I was able to copy most of my desktop, just in case ... but if I can, I'd like to do this and keep them as they are,  if I can ...

Any suggestions or help?
It fully boots up and my desktop is intact, but I have that error message (that blocks the main screen)
asking me to logout and restart... which I have done MANY times ...
HELP ...

---

### Post by uRock on 2019-10-26
Ctrl+Alt+T will open a terminal window. Ctrl+Alt+F1 will drop you to a non-GUI command line.

---

### Post by bierdo69 on 2019-10-27
I used Ctrl T and tried to run 
sudo apt install -f
sudo apt update
sudo apt upgrade

but it told me i had to run
sudo dpkg --configure -a
again
Which I did, but it eventually froze
So I had to try a restart and it then took me into:
"grub rescue>"
What do I do now?

---

### Post by bierdo69 on 2019-10-27
it says on restart:

error: symbol 'grub_file_filters' not found.
Entering rescue mode...
grub rescue>

I don't know what to enter ... HELP me please ...

---

### Post by zimbuf on 2019-10-27
At this point, I think it is best to create a new Ubuntu installation medium  (if you don't have one already) and reinstall. The following steps should guide you through recovery via graphical means:

Phase 1 - Recovery:


[LIST=1]
[*]Boot from the USB/CD/DVD. 
[*]From there select "Try Ubuntu without installing" 
[*]IF YOUR PERSONAL FILES EXCEED WHAT FITS ON A THUMB DRIVE:
[LIST=1]
[*]Open GParted. 
[*]Shrink your existing / partition by about 20 GB (it'll be the biggest ext4 one). 
[*]Create a new partition of 20GB as ext4. 
[*]Save your changes and once GParted has finished writing the drive, open Nautilus and navigate to "Other Locations". Click on the volume that was your original / to mount it. 
[*]Then re-open nautilus and click the volume that is the new 20GB drive. 
[*]Go through the drive and copy over any files that you wish to keep to the 20GB share. (Your personal files will be in /home/<your username>) 
[/LIST]
  
[*]IF YOUR PERSONAL FILES DO NOT EXCEED WHAT FITS ON A THUMB DRIVE:
[LIST=1]
[*]Open Nautilus and go to "Other Locations" 
[*]Click the largest drive to mount it 
[*]Plug in your other USB drive (Ubuntu will auto detect it) 
[*]Open a second Nautilus window to open the other USB drive 
[*]Go through the drive and copy over and files that you wish to keep to the USB drive (Your personal files will be in /home/<your username>) 
[/LIST]
  
[*]Once done, go ahead and select the "power off" option from Ubuntu's toolbar (Ubuntu will take care of unmounting the drives). 
[/LIST]

Phase 2 - Reinstallation


[LIST=1]
[*]Boot from the Ubuntu LiveCD/USB/DVD 
[*]Select "Install Ubuntu" 
[*]IF COPYING DATA FROM THE DISK:
[LIST=1]
[*]Proceed through installation as usual, but select to manually partition the disks 
[*]Delete all partitions except for (Windows partitions, Mac partitions if you have them), the 20GB share, linux swap and your efi partition 
[*]Create a 5GB ext4 partition mounted at /boot 
[*]Create a new ext4 partition that takes up most of the space. Have it mount as / 
[*]Format the linux swap partition 
[*]Do not touch the 20GB share 
[*]Proceed with installation 
[*]On boot of the installed system, open Nautilus 
[*]Go to "Other Locations" and select your 20GB share. 
[*]Copy stuff over 
[*]Alternatively you can modify /etc/fstab to permanently mount the 20GB share in the future if you want. Or, you can download GParted from the repository and delete it altogether (after unmounting via Nautilus) 
[/LIST]
  
[*]IF COPYING DATA FROM THUMB DRIVE:
[LIST=1]
[*]Proceed with installation as normal. 
[*]On boot of the installed system, insert your thumb drive 
[*]Copy files over 
[/LIST]
   
[/LIST]

---

### Post by bierdo69 on 2019-10-27
I'll try that if I have to, I would prefer to keep all my files and just do it online rather than having to copy onto and use a USB.
Is there no command I can just enter into "grub rescue>" that will get me out of this situation?
Just looking for an easy solution ...

---

### Post by bierdo69 on 2019-10-27
As I have my computer partitioned, to UBUNTU and a percentage to WINDOWS to for when I have to use it. 
So I don't want to lose everything ... and I've been trying for the last few days to find a solution to this ...
I like UBUNTU a lot ... that's why I have been using it for a while now ... as never before have I had a problem ...
HELP

---

### Post by bierdo69 on 2019-10-27
Thanks zimbuf,
All sorted now, a bit more complicated than I wanted.
I lost a few, but thankfully not too many files, I should have backups?
If I don't, I don't, oh well ...
Thank you.

---

