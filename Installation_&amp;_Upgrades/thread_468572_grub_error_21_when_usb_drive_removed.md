---
title: "grub error 21 when usb drive removed"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by newtimes on 2007-06-09
i loaded fiesty fawn on a usb external drive and now the only way to get back vista is to have usb drive plugged in
and go thru grub to boot vista. how can i put my internal HDD back the way it was.
without the external drive plugged in all i get is grub error 21

thanks in advance:(

---

### Post by RaZoR-x11 on 2007-06-09
Hey,   What have you done?, did you have vista installed on the main hd, Then installed Ubuntu onto an extenal hd?  You might need to change the grub setting's etc.

---

### Post by newtimes on 2007-06-09
thats exactly what i did.  how can i fix it now?

---

### Post by RaZoR-x11 on 2007-06-09
That's Ubuntu and grub for you, Well i would say use a different version off grub or reinstall it, Should fix it.

---

### Post by newtimes on 2007-06-09
so just reinstall 7.04 again?

---

### Post by RaZoR-x11 on 2007-06-09
No, not install it all again, what i would do is have ya main Harddisk partitioned like. windows 49%, Linux 49%, 2%Swap,  Then use the external hard disk as a back-up or just for mp3', file storage, documents.  As Ubuntu can read/write to windows partitions (aka fat/ntfs) you can see, use all the files in vista to.

---

### Post by newtimes on 2007-06-09
thats the problem the internal HDD belongs to my job so thats why i needed ubuntu on a external.
now i just want to undo the mess before monday

---

### Post by RaZoR-x11 on 2007-06-09
Ohh, So you want windows vista to boot normally? without grub loading up?

---

### Post by newtimes on 2007-06-09
right!  i didint think about removing the internal HD before instal or did i think about ubuntu putting grub on the internal

---

### Post by newtimes on 2007-06-09
so how can i fix it?

---

### Post by RaZoR-x11 on 2007-06-09
.

---

### Post by RaZoR-x11 on 2007-06-09
Well, GRUB is the default boot loader on the system now, the window's boot loader has bin over written, you should off used the boot menu at the pc start on mine it is f11, then select the USB, and presto, 

```

1. Boot up Windows Vista, and right click on Start (the Vista orb)-> All Programs -> Accessories -> Command Prompt, and select Run as Adminstrator. Either enter your password if needed or just press continue.    
2. In the command prompt, type in bcdedit /enum active and press Enter.    
3. Locate the sections titled "Windows Legacy OS Loader". Note the identifier (all of them if there is more than one matching section); my identifier was {ntldr}. If the problem is the same as mine, the device property should be currently set to unknown.
4. Use the command bcdedit /set (ID) device boot to change unknown to boot, that is, the partition that is active and is booting from. By default, Vista does not change the which partition boots, so if your XP partition is set as active, it will add the new booting code to that. Therefore assuming your XP partition is set as the active (boot) partition, the above command will be correct. Apply the above command for each identifier, replacing (ID) with the identifieritself, including the curly braces. Press Enter after each one - it should report that the operation was completed successfully.    
5. Rerun the command in step 2 to check that the changes were applied correctly.
6. Test!

```

 Hope this helps.

---

### Post by newtimes on 2007-06-09
this what i have 



Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>bcdedit /enum

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {7fdd6ac6-70be-11db-ba26-a0b016378059}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows Vista
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {572bcd55-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {7fdd6ac6-70be-11db-ba26-a0b016378059}
nx                      OptIn

C:\Windows\system32>

---

### Post by koshari on 2007-06-09
basicly what you want to do is boot the usb installation from the bios and rewrite the windows mbr as what you are trying to acheive isnt possable if you are going to be removing the usb drive.

basicly the master boot record on the perminant drive i nthe notebook is being asked to execute stuff on the removable drive at boot time (and this is what your error means, grub is installed in the linux boot/grub directory.

the little bit of code at the beginning of the perminant drive is merely a pointer or shortcut .

so in this order its prolly the best thing to do if you want to keep the option of booting linux.

1- install grubs root and boot files on the usb removable drive, 

2- repair the windows mbr to boot windows

3- change bios boot device to usb to boot linux.

possably another alternative may be to make a little ext2 partition and install grub on that with an entry to boot a kernel of sda2 or whatever linux sees your usb drive as. however this is simply a variation of previous posts suggesting having linux installed on the perminant drive also, 

the only advantage is you would smply have /boot mounted on the perm drive and the rest on your removable, i havnt done anything like and its likely to be quite technical but it is feasable.

---

### Post by RaZoR-x11 on 2007-06-09
Or, just go to this site and all will be fine :D buga that lol. [HTML]http://supergrub.forjamari.linex.org/?section=home[/HTML]

---

### Post by confused57 on 2007-06-09
I have no idea if this actually works or not, but thought I'd provide you with the reply in this thread:
[http://ubuntuforums.org/showpost.php?p=2802713&postcount=8](http://ubuntuforums.org/showpost.php?p=2802713&postcount=8)

---

### Post by newtimes on 2007-06-09
at this point im only interested in fixing the companys computer and i will load ubuntu on old puter.

---

### Post by RaZoR-x11 on 2007-06-09
Just go to this site download it, burn it, run it, and then restore the mbr for windows, and it will all be as good as new.


[HTML]http://supergrub.forjamari.linex.org/?section=home[/HTML]

---

### Post by newtimes on 2007-06-09
thanks guy i will try it.  and post back

---

### Post by newtimes on 2007-06-09
got this when trying mbr fix

C:\Windows\system32>MbrFix /drive 0 fixmbr /vista
'MbrFix' is not recognized as an internal or external command,
operable program or batch file.

---

### Post by confused57 on 2007-06-09
I tried to download the MbrFix.exe, but looks like the download mirror is down...here's a guide for using it:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Also, at the link to download the file, be sure to read the usage with installing Vista's mbr:
[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

As with any beta software, this is use at your own risk for installing Vista's mbr...I can't vouch for it since  I don't use Vista.  Do you know anyone you could borrow a Vista installation Disk from?

---

### Post by newtimes on 2007-06-09
I got MBRfix to work like a charm here is how I did it.  download the above mentioned MBRfix and extract it to desktop.

then run command prompt as admin

then type

**cd C:\Users\Chris\Desktop\mbrfix**    (change chris to your name etc.)

and you should get this

[B]C:\Users\Chris\Desktop\mbrfix>MbrFix /drive 0 fixmbr /vista
You are about to Fix MBR,
are you sure (Y/N)?  [/B]

then just type Y and reboot!  and Bam ! finnaly after 3 freakin hours of hair pulling and cussing its done...


Hope this with the above posts helps someone else get here faster than I did

Cheers

---

### Post by confused57 on 2007-06-09
Glad it worked...thanks for posting the alternate way that you executed the MbrFix.exe...Herman's instructions were to extract the MbrFix.exe from the downloaded zip file & paste the .exe to the root of C:...I believe  extracting to the Desktop might be easier...then cd to the desktop in the command prompt.

---

### Post by newtimes on 2007-06-11
also was able to use the USB drive after all.

after uninstalling grub as said above I ejected the internal drive and re installed fiesty fawn to the USB drive form the Ubuntu CD then I re inserted the internal drive and now have dual boot using F12 at start up
so I can choose vista or ubuntu.   Thanks again guys.

---

### Post by alexnb185 on 2007-06-15
Hey I have the exact same problem, luckily it was an old laptop running windows nt, however, i still need it to work, because ... it isn't mine haha but ya my bios is set to boot normal but idk how to fix the error, if anyone knows anything email me

AlexnBryan[at]gmail[dot][com]

---

### Post by mikesmithv on 2008-03-11
I am in the same situation where I can boot via grub into Ubuntu off my removable USB disk but get error 21 when the USB disk is off or unplugged.  I noticed this thread is old and I wonder if there is any new developments on this front.  I can reinstall Ubuntu with my HD disconnected, reconnect it, and then use Dell's F12 option to choose the boot device but would hate to destroy my Ubuntu I worked so hard on (dual head monitors, etc - everything works!).  Ideally I would like grub to be on my fixed HD (obviously), is there any way to change that now?  It would be great if during the install Ubuntu detected it was about to put grub on a removable disk but maybe that's not easily detectable.  I am using 7.10

---

### Post by confused57 on 2008-03-11
> **mikesmithv said:**
> I am in the same situation where I can boot via grub into Ubuntu off my removable USB disk but get error 21 when the USB disk is off or unplugged.  I noticed this thread is old and I wonder if there is any new developments on this front.  I can reinstall Ubuntu with my HD disconnected, reconnect it, and then use Dell's F12 option to choose the boot device but would hate to destroy my Ubuntu I worked so hard on (dual head monitors, etc - everything works!).  Ideally I would like grub to be on my fixed HD (obviously), is there any way to change that now?  It would be great if during the install Ubuntu detected it was about to put grub on a removable disk but maybe that's not easily detectable.  I am using 7.10
First thing you need to do is repair(overwrite grub) your internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Super Grub Disk is an easy way or a Windows install cd(not a recovery disk)

Then use the Ubuntu live cd to install grub's IPL(Initial Program Loader) to the external drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
something like:
root (hd1,x)
setup (hd1)

Then boot first to your external drive, you should get a grub menu...you'll need to highlight your first Ubuntu entry, press "e" to edit, then highlight the line with root, press "e" again, change (hd1,x) to (hd0,x), press "enter" then "b" to boot...x means leave this value as it already is.  This change is temporary, but can be made permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
be sure to change the line with groot to (hd0,0)...leave the # in front of groot.

---

### Post by mikesmithv on 2008-03-11
Thankyou confused57, it worked EXACTLY as you said.  After all that careful typing there was much rejoicing seeing that Ubuntu startup screen.

---

### Post by confused57 on 2008-03-11
> **mikesmithv said:**
> Thankyou confused57, it worked EXACTLY as you said.  After all that careful typing there was much rejoicing seeing that Ubuntu startup screen.
You're welcome, glad it worked.  

See I made a typo on changing groot...change it to (hd0,0), if Ubuntu is on the first partition of the external drive.

---

### Post by mikesmithv on 2008-03-13
As it turns out, I love this setup.  It's perfect for someone with a laptop transitioning off Windows.  I also changed the (hd0,0) to (hd1,0) in grub for the Windows menu, basically reversing every hd1 to hd0 and every hd0 to hd1.  Then I changed to boot order in my BIOS setup so it looks for the USB disk first when doing the normal boot sequence.  Now all I have to do is turn on my computer - if the USB disk is plugged in in I get Linux (via grub), otherwise Windows.  My "normal" situation is with the USB disk plugged in so I get the standard grub menu to choose Windows if I change my mind, but when I'm on the road I have the standard Windows boot.  Perfect!

---

