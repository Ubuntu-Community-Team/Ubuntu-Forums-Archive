---
title: "16LTS suddenly need to turn off Secure Boot"
date: 2016-11-05
forum: Installation &amp; Upgrades
---

### Post by FerryGnu on 2016-11-05
This has been driving me nuts all this week as I have decided to abandon windows. I installed 16-LTS on Acer laptop i5, 6G, 256-SSD, UEFI and Secure boot enabled with defaults all set in the UEFI etc. Started setting it up and all works fine. Shut down and cold-starts all good. Wine working amazingly well with a few of my own windows programs.

Just now, I needed to get some stuff off the old windows SSD and I had to swap it in and run windows 8.1 to create a file of the stuff.

I swapped the Ubuntu SSD back in and got the "security ... blocked" error. I tried going into the UEFI and resetting the defaults. Restart and same again. Finally turned off Secure Boot and here I am. :)

So, what did windows change and how can I change it back again to enable Secure Boot to run with 16LTS?

Thanks

---

### Post by ubfan1 on 2016-11-05
Either the /EFI/Boot/bootx64.efi got rewritten (from shimx64,efi to grubx64.efi), and/or the nvram entry booting ubuntu got rewritten from /EFI/ubuntu/shimx64.efi to /EFI/ubuntu/grubx64.efi.  Take a look and fix the first case by copying the shimx64.efi back to the bootx64.efi.  Fix the second case with efibootmgr.

---

### Post by FerryGnu on 2016-11-05
Thanks, but I think you think I know more than I do. :)

Total newbie to Ubuntu/Linux. Can you please point me at some instructions on how to go about these things?

using File Manager I found the efi folder in boot but it will not let me in. 

Using Term and logged in as su and no boot64.efi visible. Will give it a try. Back soon -- I hope.

---

### Post by ubfan1 on 2016-11-05
Take a look at thread [https://ubuntuforums.org/showthread.php?t=2342322](https://ubuntuforums.org/showthread.php?t=2342322)  Sounds just like your problem.  Oldfred has provided some links to examine.  That boot64,efi was a typeo I hope, the location/name is on the EFI System partition  /EFI/Boot/bootx64.efi.  Check the size against /EFI/ubuntu/shimx64.efi, they should be the same.  Also, a copy of grubx64.efi should be in the same directory /EFI/Boot, and also a grub.cfg file in /EFI/ubuntu.  These bootloaders are optional, but are frequently used as a fallback when the first selection fails (like if grubx64.efi is attempted instead of shimx64.efi with secure boot on).  If the fallback also fails, then the second boot selection is tried.  The fallback is a good idea, because I have had my "ubuntu" selection get changed from shim to grub, and that sort of change I cannot blame on Windows.

---

### Post by FerryGnu on 2016-11-06
> **ubfan1 said:**
> Take a look at thread

Thanks, will do. I trashed the entire installation messing with stuff I don't understand. Oooops. All good. I have reinstalled 16LTS and am back at were I was yesterday so it is all working again OK with Secure Boot.

I will check that link and save the URL as I may have to swap in the windows SSD again at some time.

---

### Post by oldfred on 2016-11-06
When you disconnect a drive, UEFI forgets all entries related to that drive or that drive's ESP - efi system partition. The GUID it uses to find the ESP is gone.
Most auto find the Windows UEFI boot entry in the ESP, some auto find the fallback/backup entry in /EFI/Boot/bootx64.efi, but few find all folders and .efi files for booting.

You may just have needed to use efibootmgr to add a new Ubuntu entry using shimx64.efi.
Boot-Repair can also indirectly do that with the advanced option of a total reinstall of grub in UEFI mode. If booted in Secure boot mode grub will then add a new UEFI boot entry using shimx64.efi.

And Acer has its unique requirement to set "trust". Not sure if then you have to redo that, or does your system not need that?
       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

Some threads also mention that Acer needs to have newest UEFI/BIOS from Acer to work. If your system works then I assume you have done that or system has newest UEFI already.

---

### Post by FerryGnu on 2016-11-08
Thanks, had to swap back the windows SSD again today. Now back to no Secure Boot. But before doing that I copied the EFI Directory. Now comparing the saved and the current all of the files are the same with the same date of yesterday when I first installed Ubuntu -- again. 

```

grub.cfg 126-bytes  Nov-7
grubx64.efi 958.6-kb  Nov-7
MokManager.efi 1.3-mb  Nov-7
shimx64.efi 1.3-mb  Nov-7

```

Using OldFred's 
sudo efibootmgr -v
I get
```

BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000
Boot0000* HDD:     HD(1,800,100000,c03f6c6a-a2eb-4e65-9cd4-ab4e22019548)File(\EFI\ubuntu\grubx64.efi)RC
Boot0002* SanDisk SDSSDHP256G                 BIOS(2,500,00)................-.o.......o.A.o........................................

```

Hindsight being what it is I didn't think to run OldFred's sudo efibootmgr -v BEFORE swapping in windows so have nothing to compare it with.

How can I change "\grubx64.efi" to "\shimx64.efi"? OldFred mentioned it needs to boot "shim..."

---

### Post by ubfan1 on 2016-11-08
You can run efibootmgr -h to get the help, or the manual pages with  man efibootmgr.  Instead of changing the 0000 entry loader name with the -l switch, I'd just add a new one (-c ), then set the loader ( -l) and the name (-L), and if necessary, change the bootorder with -o.  That way you always have a working (without secure boot enabled) entry, and a fallback if something happens to the shim entry in the future.

---

### Post by FerryGnu on 2016-11-09
Thanks, but I am a total newbie with Ubuntu. I had already checked "man efibootmgr" as Old Fred opined in his other thread and know I don't know enough to attempt the suggestions in your latest reply.

If you check the outcome of my previous post #3, I went off to do stuff and trashed the entire install and had to start again. I do not want to spend another ten hours installing, configuring, adding programs, etc again by messing with stuff I think I understand. :D

I am sure you are correct in creating a new entry, but I need a working computer and messing with that process at this stage is just too risky.

The help and manual are way too complex for a first-timer. So, Rather than mash up the boot system  again, could someone please just give me single command example to change the filename being used.

---

### Post by FerryGnu on 2016-11-09
OK, problem solved.
Found a post from a guy having a similar problem and it can be handled totally in the UEFI settings.

Turn on and tap-tap-tap [F2] to enter UEFI settings
[Right-arrow] to "Security"
Set Supervisor password if not already set and the options below will become blue and selectable.
[Down-arrow] to "Select a UEFI file as trusted to execute"
"HDD1" [Enter]
"<EFI>" [Enter]
It shows three options 
[Down-arrow] to ubuntu
"<.>"
"<..>"
"ubuntu" [Enter]
It shows available files
"shimx64.efi"
"grubx64.efi"
"MokManager.efi"
[Down-arrow] to "shimx64.efi" [Enter]
It asks for a description so I entered "Shim" [Enter]
"Yes" [Enter]
[Down-arrow] to "grubx64.efi" [Enter]
It asks for a description so I entered "Grub" [Enter]
"Yes" [Enter]
I don't know anything about MokManager so did not add it.
[F10]
"Save and reboot" [Enter]
System reboots and starts OK WITH Secure boot ENABLED.

Now guys, THAT's how you describe a process to a newbie! Everyone has to start somewhere and taking the time to explain stuff in simple steps goes a loooong way towards getting more people using Linux and helping them get away from windows. Most would have reverted to windows at this point, so please be more patient and specific with a process. 

**efibootmgr -v now shows...**
```

BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0001
Boot0000* HDD:     HD(1,800,100000,c03f6c6a-a2eb-4e65-9cd4-ab4e22019548)File(\EFI\ubuntu\grubx64.efi)RC
Boot0001* Shim    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(1,800,100000,c03f6c6a-a2eb-4e65-9cd4-ab4e22019548)File(\EFI\ubuntu\shimx64.efi)A01 ..
Boot0002* Grub    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(1,800,100000,c03f6c6a-a2eb-4e65-9cd4-ab4e22019548)File(\EFI\ubuntu\grubx64.efi)A01 ..

```

AND, I didn't have to wade through an hour of cryptic and very technical help files and one-line replies.

---

### Post by oldfred on 2016-11-09
Glad you got it solved.
Acer is one with the unique requirement for enabling trust. But it is better than many others that are just difficult, will not let you boot ubuntu entry at all,  and need other work arounds.

You should not need MokManager. 
I do not use secure boot at all for now. But all Secure boot systems use the same key as Windows. If someday that key is lost and Windows changes its key, you may then need mokmanager to manage keys.

---

### Post by FerryGnu on 2016-11-11
@oldfred:
Thanks for  that info, I wasn't aware it was an Acer only thing but it sure was a safe way to do it all for a newbie. I have been programming before there was even an IBM-PC, but never on any Linux based stuff. I was happy messing with Assembler/C/Fortran/Pascal etc but always on the MS-DOS and later, windows platform. The "Linux-way," is a giant leap or maybe I am just so damned old it seems like it. :D

I wanted to use the Secure Boot just because it was there. It bugged me so I needed to keep at it, even though I know the pitfalls of using it and minimal risks of NOT using with Ubuntu. I just lucked out with the laptop being an Acer I guess. Thanks for all the stuff you have posted, but it is too sparse for newbies from a different world. I understand that a lot of reading is needed to get up to speed with Linux, and I will do that, but I just needed to get things going and opted for the "do-this, now do that" approach. Your postings were helpful, but too technically assuming. 

To get more people over to Linux/Ubuntu stuff has to be simple at the start. I keep seeing way too many posts here that have responses like "man dash" etc and while that is good advice to an older hand, to a newbie trying to leave the windows world, it is absolutely no use. Pages of Manual stuff makes no more sense than this well meaning, but zero actual help post.
[https://ubuntuforums.org/showthread.php?t=2342323&p=13567623#post13567623](https://ubuntuforums.org/showthread.php?t=2342323&p=13567623#post13567623)

In it, I don't know what the Path to the files might be or how many lines to use in the terminal, or if I can combine some or all of the options on a single sudo line. Anyway, moot, but thanks to all that tried to help. Canonical needs to make moving to windows much easier if they want that crown.

---

### Post by oldfred on 2016-11-11
Glad it worked.

And yes, I do assume some level of knowledge.

But now I am just as lost as you. 
Comcast will only let me use Windows to watch my DVD recordings.
I shut Windows XP down years ago, and now with Windows 10 am totally lost. 
Screen examples do not match, it seems every Windows version even of 10 has settings in different places.
Rarely do any solutions on line post a command line way to resolve issues.
But once I get to lower level screen, I would swear it is the same as my old XP.

---

