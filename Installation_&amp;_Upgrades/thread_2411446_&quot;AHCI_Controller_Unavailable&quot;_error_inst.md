---
title: "&quot;AHCI Controller Unavailable&quot; error installing Ubuntu 18.10"
date: 2019-01-30
forum: Installation &amp; Upgrades
---

### Post by daveface2 on 2019-01-30
I'm currently trying to install the latest version of Ubuntu on a custom build desktop PC. My intention is to dualboot with Windows (so I already have Win10 installed with space on my SSD for Ubuntu). However whenever I go to Try or Install Ubuntu, I'm getting boot errors.

At first I was getting the following:
```
nouveau 0000:01:00.0: bus: MMIO write of 8000140 FAULT at 10eb14 [IBUS]
ACPI BIOS Error (bug): Could not resolve [\_SB.PC10.SATA.SPT4._GTF.DSSP], AE_NOT_FOUND (20180531/psargs-330)
```

Looked up the first error code, apparently this is an issue with Nvidia drivers, so booting without graphics drivers (e.g. [this answer](https://askubuntu.com/questions/742237/installing-ubuntu-with-nouveau-error) fixed that particular one. But now I have the following error:

```
ahci 0000:03:00.0: AHCI controller unavailable!
```

The SATA Configuration in the BIOS is set to AHCI and there's nothing else obviously wrong (secure boot is disabled, Windows specific options are off, etc). My specs are:

MSI Mpower Z97 Motherboard (with latest 2016 bios)
Intel i7-4770k CPU
GTX 980 4gb GPU
Boot drive is Sandisk Ultra II SSD

Any ideas?

---

### Post by donkus on 2019-03-07
Were you able to solve this? I'm having a similar issue when installing.

---

### Post by wildmanne39 on 2019-03-07
Hello and welcome to the forum donkus please start your own thread so you can get the help you need instead of posting in someone else's thread.

Thanks

---

### Post by daveface2 on 2019-04-10
I mean, no one ever responded to my thread in the first place and the issue didn't get resolved - not unreasonable to bump a thread in that situation IMO.

> **donkus said:**
> Were you able to solve this? I'm having a similar issue when installing.

No, unfortunately I never got past this error. I read that it may be because I was installing 18.10 instead of 18.04LTS but honestly I just got tired of messing around with bootable USB's and gave up. Might give it another try with LTS and then upgrade, though I'm worried that will just brick my installation.

---

### Post by oldfred on 2019-04-10
Many (even new) SSD need firmware updates to work. Have you updated firmware?

Next older model, issues could be the same:
       Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725)

Some other MSI,possibly similar issues:
[https://ubuntuforums.org/showthread.php?t=2357641](https://ubuntuforums.org/showthread.php?t=2357641)

---

### Post by daveface2 on 2019-04-19
Alright, so I took another shot at this today, using the new 19.04 release.

First thing I did was update my SSD firmware using Sandisk's tool. It did need an update, so I'm now running the latest version. That said other reviews have said [the same SSD worked out the box for them on Ubuntu (albeit an older version)]("https://delightlylinux.wordpress.com/2016/01/06/the-sandisk-ultra-ii-ssd-and-linux/").

[IMG]https://i.imgur.com/Pub2W0c.jpg[/IMG]

Then I went back to my BIOS, disabled anything that I think might have been causing conflicts (Intel rapid start for SSD's, Windows 8.1/10 fast start features) and double-double-checked that my hard drive mode was set to AHCI:

[IMG]https://i.imgur.com/26HOB3p.jpg[/IMG]
I boot to the USB, 'Try Ubuntu (Safe Graphics)' (since trying without safe graphics, as before, causes a nouveau error that somehow isn't fixed yet?) - and there's the AHCI controller error again.

---

### Post by oldfred on 2019-04-19
Please attach screen shots.
Easy to do with Forum's advanced editor and the paperclip icon.

With nVidia you need nomodeset.
And now with 19.04 checking the install proprietary drivers should auto install a correct nVidia driver (not necessary the newest) where before you had to also boot install using nomodeset & then add nVidia driver yourself. 
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
    
       MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[URL="https://ubuntuforums.org/showthread.php?t=2390475"]https://ubuntuforums.org/showthread.php?t=2390475
      [/URL]
 MSI Tomahawk Z370 GTX 1070 TI [SOLVED] Grub error during install two NVMe drives
[https://ubuntuforums.org/showthread.php?t=2398599](https://ubuntuforums.org/showthread.php?t=2398599) 
    
Also needed acpi=off boot parameter:
[https://ubuntuforums.org/showthread.php?t=2371556](https://ubuntuforums.org/showthread.php?t=2371556)
[URL="https://ubuntuforums.org/showthread.php?t=2390475"]
[/URL]

---

### Post by daveface2 on 2019-04-19
I actually found the 'safe mode' graphics option seemed to bypass the need for 'nodemodeset' which I used previously, so the installed skipped straight to the AHCI error.


As mentioned in my first post, I'm running the [latest BIOS for my motherboard](https://www.msi.com/Motherboard/support/z97-mpower) (1.B, which appears as 1.11 in the setup screen). I tried using the ACPI=OFF parameter and the nomodeset so my boot looked like this:

[ATTACH=CONFIG]283061[/ATTACH]

Unfortunately:

[ATTACH=CONFIG]283062[/ATTACH]

---

### Post by oldfred on 2019-04-20
Do you have multiple USB devices plugged in, or a multi-port device?
It seems that is also an error.

It sure looks like UEFI is set for AHCI, so do not know why it is saying AHCI not available.

---

### Post by daveface2 on 2019-04-21
I suspect it's complaining about my Inateck USB expansion card, as the only USB hub I have connected is on my monitor which is usb3-3 (and it successfully detects that I have a Blue Microphone plugged into it). The only other USB ports not directly on the motherboard I/O are on my case, but one of them is being used for the bootable USB, so is clearly working fine.

Is there a way to get a more detailed log to diagnose the issue further, or is this as much detail as I can get?


**UPDATE: It's now working.**

[FONT=Verdana]I tried everything I could think of, including removing my USB expansion card, other hard drives, and extraneous USB devices. None of that worked.

What worked in the end was disabling my motherboard's external SATA controller (and enabling SATA hot plugging, but I doubt that was what fixed it), which was previously set to AHCI. Presumably Ubuntu was trying and failing to use this - I'm not sure why it would or why it was failing though.

[/FONT][ATTACH=CONFIG]283070[/ATTACH][FONT=Verdana]
[/FONT]

---

### Post by donbcilly on 2019-04-29
You know - FWIF - that AHCI Controller Unavailable error drove **me** crazy for a while.
It turned out that the problem had *nothing *to do with it.
It just happened to be the last line of the log that was printed on the screen.

In **my** case it wasn't booting (and having problems installing) because of my silly Intel video card.
I had to load the proper boot parameters for the card -with **e** at boot and then in the grub config - into the kernel and it started booting OK.

Just saying, the last error reported at boot...isn't always the cause of the boot failure.

---

### Post by macgyver27 on 2020-01-21
> **donbcilly said:**
> You know - FWIF - that AHCI Controller Unavailable error drove **me** crazy for a while.
It turned out that the problem had *nothing *to do with it.
It just happened to be the last line of the log that was printed on the screen.

In **my** case it wasn't booting (and having problems installing) because of my silly Intel video card.
I had to load the proper boot parameters for the card -with **e** at boot and then in the grub config - into the kernel and it started booting OK.

Just saying, the last error reported at boot...isn't always the cause of the boot failure.

Hello there.

I am facing the very same problem. I have bought this card to provide me with 8 additional SATAIII connectors: [COLOR=#666666][FONT=Arial][IO-PCE9215S-8I]("http://www.iocrest.com/en/product_details612.html").
[/FONT][/COLOR]
No problem if none disks are attached to it. Until I attach them card goes "crazy" - all leds starts blinking and system freezes at the end. Strange thing is I have dualboot with windows 10 and card works there flawlessly out of the box. Literally this problem has been driving me crazy for like a year.. I was using this card in my older build (i7-2600) and same thing - but it was "solveable" with parameter in the grub file "pci=nommconf" but this doesnt work with the current build (Ryzen 3950x, Gigabyte x570 AORUS Master).

I dont really get what you mean "[COLOR=#000000]had to load the proper boot parameters for the card -with [/COLOR][B]e at boot and then in the grub config"
[/B]
BTW: I have tried disabling SATA driver on the motherboard chipset with no effect on the problem.

Thnaks a lot, Michal

---

### Post by julius08x on 2020-04-21
Hi all,
this boot problem with the message "AHCI controller unavailable" is related to the Asmedia 1061 chipset which simply does not work with CD / DVD / BluRay players !!! (not ATAPI compatible)
Strangely on older versions of the kernel (those of Ubuntu 14.04 for example) there was no problem.
There are several solutions:
1- the simplest: connect your CD / DVD / BluRay drive to another SATA port not linked to the Asmedia 1061 (see the configuration of the ports in the manual for your motherboard)
2- see here => [https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208](https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208)
3- untested: deactivate the NCQ command by entering the command "libata.force=noncq" in your /etc/default/grub file and update grub (this solution may reduce the performance of other connected devices)

---

### Post by roboman6 on 2020-10-03
> **julius08x said:**
> Hi all,
this boot problem with the message "AHCI controller unavailable" is related to the Asmedia 1061 chipset which simply does not work with CD / DVD / BluRay players !!! (not ATAPI compatible)
Strangely on older versions of the kernel (those of Ubuntu 14.04 for example) there was no problem.
There are several solutions:
1- the simplest: connect your CD / DVD / BluRay drive to another SATA port not linked to the Asmedia 1061 (see the configuration of the ports in the manual for your motherboard)
2- see here => [https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208](https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208)
3- untested: deactivate the NCQ command by entering the command "libata.force=noncq" in your /etc/default/grub file and update grub (this solution may reduce the performance of other connected devices)


This was a headache for me for a long time.  I created this account just to thank you.

So thanks.

---

### Post by 3dresu on 2021-05-02
The solution of changing the DVD drive SATA plug *away *from the ASMedia ASM1061 motherboard connection also worked for me.
Motherboard:  ASRock Z77 Extreme 6

---

### Post by coffeecat on 2021-05-03
Back to sleep, ancient thread.

R.I.P.

---

