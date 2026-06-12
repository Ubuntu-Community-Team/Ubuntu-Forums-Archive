---
title: "No Windows Boot Manager after Installation &amp; Restart"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by HolgerBurghardt on 2012-10-06
Hello,

today I used the **W**indows-based **Ub**untu **I**nstaller (Wubi) as per [Ubuntu Documentation]("https://help.ubuntu.com/community/Wubi").

I get as far as *Completing the Ubuntu Setup Wizard* and *Reboot Now*. But after rebooting I don't get the Windows Boot Manager to finish the installation. I always get back to Windows XP which operates as if nothing had happened. Or to use another installation guide ([http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)), I get through 1 to 6 but 7 never comes, I'm just back to Win XP.

Please note that I don't want a clean install as for the time being I stick with Windows but want to try and use occasionnally some programs on Ubuntu (and do a little programming, maybe).

Anyone an idea what might have gone wrong?

My basic OS: Windows XP SP3
Wubi: downloaded yesterday from [here]("http://www.ubuntu.com/download/desktop/windows-installer")
Intended Ubuntu: Ubuntu Desktop 12.04 LTS

Thanks anyone reading and trying to help!

P.S. A small explanation of the difference between the Windows Boot Manager and the Windows (NT) Boot Loader (ntldr) would be appreciated.

---

### Post by bcbc on 2012-10-06
Check the "Time to display operating systems". It's probably at zero, when it should have been changed to 10.

Otherwise post the contents of your C:\boot.ini file.

To get there, right click, My Computer, Properties, Advanced, Startup & Recovery settings.

---

### Post by HolgerBurghardt on 2012-10-07
Thank you, after checking the boot.ini file I already found the source of my problem - now all I need is the way out.

Wubi (and you) assume that it is always the drive C that is the boot partition but in my case this isn't so.

```

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
```My PC boots from the drive G.

I guess change the timeout to 10 or 15 is step 1 of solving my problem. For step 2 I wonder whether simply copying the wubildr file to drive and change the drive in the boot.ini file would do the trick.

I'll try and come back to you...

---

### Post by HolgerBurghardt on 2012-10-07
Okay, no need to copy the wubildr file just changing timeout and the drive got my a major step farther.

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
G:\wubildr.mbr = "Ubuntu"

```I get to make the choice between Windows or Ubuntu.

But now it claims that the hal.dll file in the system32 (the Hardware Abstruction Layer DLL) can not be found. I looked and it is there.

My guess it's again linked to the drive?

---

### Post by critin on 2012-10-07
> **HolgerBurghardt said:**
> Okay, no need to copy the wubildr file just changing timeout and the drive got my a major step farther.

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
G:\wubildr.mbr = "Ubuntu"

```I get to make the choice between Windows or Ubuntu.

But now it claims that the **[COLOR=Red]hal.dll file in the system32[/COLOR] **(the Hardware Abstruction Layer DLL) can not be found. I looked and it is there.

**[COLOR=Red]My guess it's again linked to the drive[/COLOR]**?

> Wubi (and you) assume that it is always the drive C that is the **boot partition **but in my case this isn't so.Probably because C is the Windows default and the owner is the only one that knows for sure.   It's assumed the owner will know the correct drive.   The **C:\boot.ini file** isn't the same thing as the boot partition.

Speaking of drives.   Wubi is installed into the same drive and partition as Windows.  System32 that contains the hal.dll is in system32 which is in Windows.    Changing its drive on your own is a bad idea unless you know what you're doing.    It may not boot.

---

### Post by bcbc on 2012-10-07
> **HolgerBurghardt said:**
> Okay, no need to copy the wubildr file just changing timeout and the drive got my a major step farther.

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
G:\wubildr.mbr = "Ubuntu"

```I get to make the choice between Windows or Ubuntu.

But now it claims that the hal.dll file in the system32 (the Hardware Abstruction Layer DLL) can not be found. I looked and it is there.

My guess it's again linked to the drive?

You can get hal.dll errors if you make a mistake while editing the boot.ini. It doesn't mean there's a hal.dll problem. You just need to recheck the boot.ini and (if you used windows facilities to edit it) there should be a backup.

---

### Post by HolgerBurghardt on 2012-10-09
All I did was change the timeout (actually using the GUI found under My Computer, Properties, Advanced, Startup & Recovery settings, as per instruction) and eventually the URI to the wubildr.mbr as Wubi wrote the C drive instead of the G drive into the boot.ini (though it correctly installed Ubuntu on the G drive).

If I kept the C address I'd be back to square as I'd see nothing during the boot, if I use the G address I can perfectly boot into WinXP but not Ubuntu.

By now I have posted both versions of the boot.ini file and I don't see the error.

I guessed as much that my hal.dll is neither corrupted nor missing else I probably could not boot Windows.

@critin: I guess you've misunderstood me (or I misunderstand you). Neither way would be the first nor will be the last time. :P
The boot.ini and boot partition are not the same things (file vs partition - not even in the same category). But during the installation Wubi changed the boot.ini and added the line *C:\wubildr.mbr = "Ubuntu"* to my boot.ini despite installing to the G drive (which is my boot partition).

Maybe you have an idea of how to achieve what I need?

---

### Post by oldfred on 2012-10-09
Windows only boots from the primary NTFS partition with the boot flag.

Boot.ini must then relate to that partition, but is very sensitive to typos, line endings or even extra spaces. If you used a Linux editor to change boot.ini you may have changed the line endings.

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to cchoose windows format.


One of the main advantage of wubi is that you do not have to create separate partitions for Ubuntu.  If you were willing to use a separate partition then a full install may make more sense.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by HolgerBurghardt on 2012-10-10
I don't use any Linux tools as I don't get Ubuntu running - I'm still using Windows XP only. The hal.dll error appears only when I chose Ubuntu from the OS list but not when I chose Windows XP.

I did my edits using Windows own Notepad.

I did not create a partition but used the same one where Windows is installed on to install Ubuntu using Wubi. (Else I wouldn't have used Wubi...)

---

### Post by bcbc on 2012-10-10
It sounds like the bootmanager has an issue with "G:" - maybe something like this would work: 
```
multi(0)disk(0)rdisk(0)partition(1)\wubildr.mbr = "Ubuntu"
```
Caution: I haven't tried this so use at own risk. i.e. backup of boot.ini and a live CD or windows repair disk.

---

### Post by oldfred on 2012-10-10
@bcbc
I have seen only a few installs with wubi in a separate partition. Is wubildr.mbr really in c: even though the root.disk is in g: .  Your detailed boot.ini entry is in effect also referring to c: , so would not c: work?

---

### Post by HolgerBurghardt on 2012-10-10
@bcbc
Did you mean like that?
```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\wubildr.mbr = "Ubuntu"

```@oldfred
Wubi installed into the same partition as my windows.
wubildr.mbr had been placed in G: but there was a wubildr file in both G and C (i.e. some file named like that without extension and only half the size).

(I have since uninstalled the whole thing but I hope to get an idea to try it again.)

---

### Post by bcbc on 2012-10-10
> **oldfred said:**
> @bcbc
I have seen only a few installs with wubi in a separate partition. Is wubildr.mbr really in c: even though the root.disk is in g: .  Your detailed boot.ini entry is in effect also referring to c: , so would not c: work?

From what I understood, there is no C: drive, the windows main partition is G:. By referencing the partition directly, there is no need to reference the 'drive letter'. (That's what windows is doing when it boots).

If there was a C: drive (even if it's not the windows boot drive, I would instead recommend copying wubildr.mbr to it).

EDIT: okay so I see there is a C:, so instead just copy wubildr.mbr to the root of that. (I think both would work, but this is the easiest and safest)

---

### Post by HolgerBurghardt on 2012-10-10
Okay, thanks, I'll try that ASAP. ;)

---

### Post by HolgerBurghardt on 2012-10-10
Yes, indeed, copying wubildr.mbr to the root of drive C: is indeed working.

Preparing Ubuntu for first use just took an awfully long time and actually seemed to fall asleep. I broke it off and are reinstalling Wubi. Is it normal that it takes so much time?

---

### Post by bcbc on 2012-10-10
> **HolgerBurghardt said:**
> Yes, indeed, copying wubildr.mbr to the root of drive C: is indeed working.

Preparing Ubuntu for first use just took an awfully long time and actually seemed to fall asleep. I broke it off and are reinstalling Wubi. Is it normal that it takes so much time?

No, it's not normal. What are your computer specs: Brand/Model/Graphics card/Ram?

---

### Post by HolgerBurghardt on 2012-11-02
Thanks, bcbc, I finally decided to make a full install of Kubuntu so I consider this thread as solved as the initial problem as described has been solved, kinda!

Thanks to anyone else involved in trying to find a solution!

---

