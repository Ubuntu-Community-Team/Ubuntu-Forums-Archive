---
title: "Asus P6T Deluxe V2: Kernel or BIOS bug?"
date: 2009-06-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-06-13
Evening, 

Running Karmic up-to-date ugraded from Jaunty.
Also did a BIOS update after upgrade.
```
sudo dmidecode --type bios
# dmidecode 2.9                          
SMBIOS 2.5 present.                      

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information                   
        Vendor: American Megatrends Inc.
        Version: 0504                   
        Release Date: 05/19/2009        
        Address: 0xF0000                
        Runtime Size: 64 kB             
        ROM Size: 2048 kB               
        Characteristics:                
                ISA is supported
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
        BIOS Revision: 8.15

Handle 0x003E, DMI type 13, 22 bytes
BIOS Language Information
        Installable Languages: 6
                en|US|iso8859-1
                zh|ZH|iso8859-1
                de|DE|iso8859-1
                cn|CN|iso8859-1
                fr|FR|iso8859-1
                ja|JP|unicode-1
        Currently Installed Language: en|US|iso8859-1


```

Now dmesg shows a ~30s pause after startup
Also tried LiveCD (Kubuntu Karmic Alpha2) which didn't make a difference.
```
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.30-9-generic root=UUID=4659a494-59da-42b4-9265-47661ea18c04 ro quiet splash                                                                        
[    0.000000] Initializing CPU#0                                                                         
[    0.000000] NR_IRQS:4352 nr_irqs:944                                                                   
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)                                      
[    0.000000] Fast TSC calibration using PIT                                                             
[    0.000000] Detected 2672.615 MHz processor.                                                           
[   34.111335] Console: colour VGA+ 80x25                                                                 
[   34.111337] console [tty0] enabled                                                                     
[   34.124433] allocated 62914560 bytes of page_cgroup                                                    
[   34.124435] please try cgroup_disable=memory option if you don't want                                  
[   34.124659] Checking aperture...                                                                       
[   34.130254] No AGP bridge found                                                                        
[   34.130290] Calgary: detecting Calgary via BIOS EBDA area                                              
[   34.130291] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
```
bootchart doesn't reveal anything suspicious, normal boot process.

There's this line in dmesg that got me wondering?
```
[   35.052336] ACPI Warning (tbutils-0246): Incorrect checksum in table [OEMB] - 80, should be 78 [20090320]
```

That caused me to google: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249)

And then I found this on my dsdt,
```
    Method (OSYS, 0, NotSerialized)
    {
        Store (0x10, Local0)
        If (CondRefOf (_OSI, Local1))
        {
            If (_OSI ("Windows 2000"))
            {
                Store (0x12, Local0)
            }

            If (_OSI ("Windows 2001"))
            {
                Store (0x13, Local0)
            }

            If (_OSI ("Windows 2001 SP1"))
            {
                Store (0x13, Local0)
            }

            If (_OSI ("Windows 2001 SP2"))
            {
                Store (0x13, Local0)
            }

            If (_OSI ("Windows 2001.1"))
            {
                Store (0x14, Local0)
            }

            If (_OSI ("Windows 2001.1 SP1"))
            {
                Store (0x14, Local0)
            }

            If (_OSI ("Windows 2006"))
            {
                Store (0x15, Local0)
            }
        }
        Else
        {
            If (MCTH (_OS, "Microsoft Windows NT"))
            {
                Store (0x12, Local0)
            }
            Else
            {
                If (MCTH (_OS, "Microsoft WindowsME: Millennium Edition"))
                {
                    Store (0x11, Local0)
                }

                If (MCTH (_OS, "Linux"))
                {
                    Store (One, Local0)
                }
            }
        }

        Return (Local0)
    }
```

Is everything okay? or is it time to have a panic attack?

---

### Post by autocrosser on 2009-06-13
I would reflash with your older BIOS & recheck---things look a bit fishy to me---There was an issue like this about a year ago--looks like Linux is getting the "shaft":(

You might also contact ASUS about this---maybe the BIOS developer made a "mistake".


*Additional*

Yes--I see you found the Foxconn "mistake"--there was quite a dust-up about that one---Foxconn made a public retraction after the problem was reported on SlashDot---If you don't get a answer--you know what to do...........

---

### Post by autocrosser on 2009-06-13
taavikko---take a look at the third post in this thread---I think you will get the idea........................

[http://ubuntuforums.org/showthread.php?t=871311](http://ubuntuforums.org/showthread.php?t=871311)

---

### Post by taavikko on 2009-06-13
Just downloaded two previous BIOS images to test if they suffer from the same flaw.

When I originally bought this motherboard it came with the 1st version available, due it's being a new model.
It didn't have this problem.

p.s I requested this thread to be moved to more appropriate subforum.

Will try to make this situation solved by Asus, if it really is an intentional...

---

### Post by autocrosser on 2009-06-13
> **taavikko said:**
> Just downloaded two previous BIOS images to test if they suffer from the same flaw.

When I originally bought this motherboard it came with the 1st version available, due it's being a new model.
It didn't have this problem.

p.s I requested this thread to be moved to more appropriate subforum.

Will try to make this situation solved by Asus, if it really is an intentional...


I just hope it's an oversight----& yes---this belongs in the Cafe....

---

### Post by taavikko on 2009-06-14
Error reported to Asus Forums.
[http://vip.asus.com/forum/view.aspx?id=20090614044621112&board_id=1&model=P6T+Deluxe+V2&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20090614044621112&board_id=1&model=P6T+Deluxe+V2&page=1&SLanguage=en-us)

Second post is IMO very funny.
I indeed tried to fill an form to be sended directly to devs, but the form crashes :popcorn:

---

### Post by autocrosser on 2009-06-14
I've heard that ASUS forums are a bit bad---but that is really bad......Hang in there......:D

---

### Post by taavikko on 2009-06-14
> **autocrosser said:**
> I've heard that ASUS forums are a bit bad---but that is really bad......Hang in there......:D

:) Got nothing better to do with my time, so "hanging on"

This issue get's more funnier since Asus claimed that "It's better with Windows"
[http://www.asus.co.uk/eeepc/1008HA/features.html](http://www.asus.co.uk/eeepc/1008HA/features.html)
Scroll down to the bottom, and check the link
[http://www.itsbetterwithwindows.com/](http://www.itsbetterwithwindows.com/)

---

### Post by taavikko on 2009-06-14
If anyone is running same motherboard with earlier BIOS versions could somebody send me the info from dsdt.dsl file obtained via
```
cat /sys/firmware/acpi/tables/DSDT > ~/dsdt.dat && iasl -d dsdt.dat
```

Line around 280
```
If (_OSI ("Windows 2000"))
            {
                Store (0x12, Local0)
            }

            If (_OSI ("Windows 2001"))
            {
                Store (0x13, Local0)
            }

            If (_OSI ("Windows 2001 SP1"))
            {
                Store (0x13, Local0)
            }

            If (_OSI ("Windows 2001 SP2"))
            {
                Store (0x13, Local0)
            }

            If (_OSI ("Windows 2001.1"))
            {
                Store (0x14, Local0)
            }

            If (_OSI ("Windows 2001.1 SP1"))
            {
                Store (0x14, Local0)
            }

            If (_OSI ("Windows 2006"))
            {
                Store (0x15, Local0)
            }
        }
        Else
        {
            If (MCTH (_OS, "Microsoft Windows NT"))
            {
                Store (0x12, Local0)
            }
            Else
            {
                If (MCTH (_OS, "Microsoft WindowsME: Millennium Edition"))
                {
                    Store (0x11, Local0)
                }

                If (MCTH (_OS, "Linux"))
                {
                    Store (One, Local0)
                }
            }
        }

        Return (Local0)
    }
```

Thanks, need it for educational purposes, to see if Asus really changed their BIOS... :(

---

### Post by taavikko on 2009-06-14
OK, downloaded every BIOS.rom from Asus and tested everyone
Used flashrom to downgrade the version (that may have caused some issues, but dunno)

entered to BIOS to verify that indeed were running earlier version.
Every BIOS version I tested resulted in same behaviour, 

dmesg messages are roughly the same as posted earlier.

Upgrading Grub didn't affect this stuation, since this issue was present before the grub-upgrade.

This leaves only "kernel" to be b0rked.
Will download and test jauntys latest kernel if that displays anything, since nothing was wrong with them.
Too bad I cant remember when this started exactly.

---

### Post by taavikko on 2009-06-14
> **taavikko said:**
> 
This leaves only "kernel" to be b0rked.
Will download and test jauntys latest kernel if that displays anything, since nothing was wrong with them.
Too bad I cant remember when this started exactly.

Yep, started system with older kernel
```
apt-cache policy linux-image-2.6.28-11-generic
linux-image-2.6.28-11-generic:
  Installed: 2.6.28-11.42
  Candidate: 2.6.28-11.42
  Version table:
 *** 2.6.28-11.42 0
        100 /var/lib/dpkg/status

```

System started just fine (apart that headers weren't installed so starting without xorg, cause nvidia module wasn't present., dmesg is normal
but ```
[    1.046001] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 80, should be 78 [20080926]
```
This was still present.

Time to "ubuntu-bug linux"

Reported as: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/386999](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/386999)

---

