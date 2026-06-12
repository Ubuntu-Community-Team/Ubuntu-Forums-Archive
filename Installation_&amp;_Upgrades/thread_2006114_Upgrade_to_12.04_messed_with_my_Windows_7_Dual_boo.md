---
title: "Upgrade to 12.04 messed with my Windows 7 Dual boot."
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by wdoubleyouesss on 2012-06-18
[http://paste.ubuntu.com/1048241/](http://paste.ubuntu.com/1048241/)

Hello,

Long time reader first time poster. 
I was dual booting Ubuntu 11.10 for a long time and everything was going great. Then I upgraded to 12.04, and then I could no longer boot into Windows 7. I still have the boot selection however when I choose Windows 7, the windows emblem comes into view, nice and shiny, but it just stays in that boot screen. Nothing happens. No errors, nothing. I have tried all kinds of things using boot repair in Ubuntu but no luck. I have to shut my computer off and reboot into Linux which is working great thankfully. I hope that the latest boot help from boot repair will provide enough information to solve this problem!

If any one can help me out with this dual boot issue I would greatly appreciate it!

Thanks in advance!

---

### Post by Arand on 2012-06-18
The bootinfo you posted shows some stuff from a Wubi intall, are you currently using Wubi or are you using the Ubuntu install on sda7, rather?

---

### Post by wdoubleyouesss on 2012-06-18
> **Arand said:**
> The bootinfo you posted shows some stuff from a Wubi intall, are you currently using Wubi or are you using the Ubuntu install on sda7, rather?

Yeah, I downloaded Wubi before I began dual booting from separate partitions. I thought I removed Wubi before I did the install of 11.10 but I guess not. How do I go about fixing this issue/ how is this causing the problem?

Thanks for the quick reply!

---

### Post by wilee-nilee on 2012-06-18
Try running in ubuntu.
```
sudo update-grub
```

---

### Post by wdoubleyouesss on 2012-06-18
I have updated grub and even used the boot repair to purge grub then did the re-install. Still no luck. I can try that again though. 

Thanks!

---

### Post by wilee-nilee on 2012-06-18
Personally I don't think the boot-repair tool will fix this, windows seems to need a chkdsk probably.

Does windows show as normal or of even loaded in gparted in ubuntu?

---

### Post by Arand on 2012-06-18
> 
=> Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

This bit looks very odd to me, Normally GRUB would be in the MBR, but in your case it seems like it goes
syslinux -> GRUB -> win/ubu

Does syslinux boot the Compaq diagnostics partition? If that is the case, and you want to keep that for some reason, don't install GRUB to sda.

To get GRUB in sda, which is the standard setup, you'd use:
```
sudo dpkg-reconfigure grub-pc
```
from Ubuntu, setting "sda" as a device where GRUB is to be installed.

HOWEVER, I'm not sure anything done from Ubuntu will fix windows' booting...
What you could try, if that is the case, is running ntfsfix from Ubuntu for force windows into performing CHKDSK on boot:
> ntfsfix  is  a  utility  that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2

```-> reboot into windows.

Otherwise, you may have to get hold of a windows boot/repair disk, use that to fix windows boot, and then use an Ubuntu liveCD to reinstall GRUB on top (since the windows bootfix removes grub in the process).

---

### Post by wdoubleyouesss on 2012-06-18
Hello,

Thanks for the detailed reply and all of your help! However, I am not too well versed in the lingo and also I really don't understand what you mean by 
[quote]"Does syslinux boot the Compaq diagnostics partition? If that is the case, and you want to keep that for some reason, don't install GRUB to sda."[quote]
That being said, do you think that I can jump straight to the chkdsk step? using the codes that you provided previously? And from there, resort to using a windows boot/repair disk?

Thanks!

---

### Post by Arand on 2012-06-18
> **wdoubleyouesss said:**
> Hello,

Thanks for the detailed reply and all of your help! However, I am not too well versed in the lingo and also I really don't understand what you mean by
> "Does syslinux boot the Compaq diagnostics partition? If that is the case, and you want to keep that for some reason, don't install GRUB to sda."
Well, if the syslinux bootloader came preinstalled with the computer it may be that it makes it possible to boot into some manufacturer diagnostics system, but if that is not the case or if you don't care about the diagnostics system (I'm guessing you don't), there should be no harm in installing GRUB over it.

> 
That being said, do you think that I can jump straight to the chkdsk step? using the codes that you provided previously? And from there, resort to using a windows boot/repair disk?

Thanks!Yes

---

### Post by wdoubleyouesss on 2012-06-18
> **Arand said:**
> Well, if the syslinux bootloader came preinstalled with the computer it may be that it makes it possible to boot into some manufacturer diagnostics system, but if that is not the case or if you don't care about the diagnostics system (I'm guessing you don't), there should be no harm in installing GRUB over it.

Yes

This did not work unfortunately :(

Should I try putting grub in sda? Or leave that be?

I can get a hold of the  windows boot/repair disk, and then use an Ubuntu liveCD to reinstall GRUB on top, I assume that that is not too complicated once I start doing it?

Thanks for the help.

---

### Post by darkod on 2012-06-19
I think part of your problem is that you had (or still have) grub installed onto the boot partition, sda5. Not sure if you had this in the previous install on purpose, or it ended up there by mistake.

In any case it's much simpler to use grub2 on the MBR. I wouldn't worry too much about the Syslinux bootloader on the MBR since the Compaq restore partition has it's own boot files on sda3 that grub2 is capable of booting.

So, simply boot with the ubuntu 12.04 cd in live mode, open terminal and install grub2 to the MBR of /dev/sda:
```
sudo mount /dev/sda7 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

Restart without the cd and see if you get a working grub2 menu. At first, maybe not all of the entries will work, but you can sort that out later. For example, you have win7 boot files on both sda1 and sda2, and they should be on one or another partition, but not on both.

This looks a little bit messed up and not only because of the ubuntu upgrade. Step by step you will sort it out.

If the above grub2 commands don't work, try running them again but this time modify the last one into:
```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by YannBuntu on 2012-06-19
Hello

> **wdoubleyouesss said:**
> I was dual booting Ubuntu 11.10 for a long time and everything was going great. Then I upgraded to 12.04, and then I could no longer boot into Windows 7. I still have the boot selection however when I choose Windows 7, the windows emblem comes into view, nice and shiny, but it just stays in that boot screen. Nothing happens. No errors, nothing.

Looks like a regression of GRUB2, you should first create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)
(when done, please indicate its URL so that we can follow it)

---

### Post by wdoubleyouesss on 2012-06-19
> **YannBuntu said:**
>  please indicate its URL so that we can follow it)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1015171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1015171)

Hope this helps!

---

### Post by YannBuntu on 2012-06-19
thanks

---

### Post by YannBuntu on 2012-06-21
@wdoubleyouesss: let's talk about your "update manager" problem here. What is the output of "sudo apt-get update" ?

---

### Post by wdoubleyouesss on 2012-06-21
> **YannBuntu said:**
> @wdoubleyouesss: let's talk about your "update manager" problem here. What is the output of "sudo apt-get update" ?

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease         
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                       
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]       
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                                      
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                              
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                                               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                           
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                                   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [20.7 kB]                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex             
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [6,150 B]                                              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]                                              
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [63.9 kB]                                                   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]                                               
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [15.1 kB]                                               
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,155 B]                                                  
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [65.9 kB]                                                    
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]                                                 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [15.3 kB]                                             
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                         
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]                     
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US                                                                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                                                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                                                     
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                                             
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]                                                                          
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]                                                                     
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB]                                                                      
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB]                                                                      
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]                                                                           
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]                                                                      
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]                                                                       
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                                                  
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [113 kB]                                                                           
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]                                                                    
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [25.8 kB]                                                                      
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]                                                                    
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [287 kB]                                                                    
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [2,417 B]                                                             
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [74.1 kB]                                                               
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [1,825 B]                                                             
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [289 kB]                                                                     
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]                                                              
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [74.6 kB]                                                                
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,049 B]                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                                          
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [1,346 B]                                                                        
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                                                     
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [6,873 B]                                                                    
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]                                                                  
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [929 B]                                                                   
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]                                                              
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [6,114 B]                                                             
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [996 B]                                                             
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [929 B]                                                                    
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                               
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [6,117 B]                                                              
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]                                                              
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex [71 B]                                                                  
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [71 B]                                                            
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]                                                            
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex [72 B]                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                                            
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en [731 B]                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                        
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [4,352 B]                                                             
Fetched 19.8 MB in 1min 19s (249 kB/s)                                                                                                              
Reading package lists... Done


Is this what you are looking for?

Sorry for the PPA confusion, it eventually downloaded. I don't know why it was acting funny. But the Update Manager seems to be working fine now.

Thanks

---

### Post by YannBuntu on 2012-06-21
> **wdoubleyouesss said:**
> the Update Manager seems to be working fine now.

ok, perfect :)

---

