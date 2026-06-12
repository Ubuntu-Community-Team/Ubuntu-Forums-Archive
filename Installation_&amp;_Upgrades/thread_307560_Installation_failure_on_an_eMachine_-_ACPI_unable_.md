---
title: "Installation failure on an eMachine - ACPI: unable to locate RSDP"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by george_in_the_d on 2006-11-26
Hello,

I have tried to install Xubunto 6.10 using the Xubuntu alternate install CD.  Actually, I have tried several disk images, and a common problem seems to be the following message after the Linux Kernel is loaded:

[17179569.184000] ACPI: unable to locate RSDP

After the language, location, and keyboard options are chosen, the detect hardware process gives me this screen:


>             [!!Detect and mount CD-ROM]
>
>Your installation CD-ROM couldn't be mounted. This probably means
>that the CD-ROM was not in the drive. If so you can insert and try 
>again.
>
>Try again to mount the CD-ROM?
>
> <Yes>                                                 <No>


Entering 'yes' gives the same results, so entering 'no' gives me this screen:


>                  [!!] Detect and mount CD-ROM
>                    Installation step failed
>An installation step failed. You can try to run the failing item
>again from the menu, or skip it and choose something else. The
>failing step is: Detect and mount CD-ROM
>
>                         <Continue>


So I enter 'continue' getting this screen:


>                  [?] Detect and mount CD-ROM
>
>Some PCMCIA hardware needs special resource configuration options in
>order to work, and can cause the computer to freeze otherwise. For
>example some Dell laptops need "exclude port 0x800-0x8ff" to be
>specified here. These options will be added to
>/etc/pcmcia/config.opts. See the installation manual or the PCMCIA
>HOWTO for more information.
>
>For most hardware, you do not need to specify anything here.
>
>PCMCIA resource range options:
>
>___________________________________________________________________
>
>
>                         <Continue>


I think that the problem is that after loading the linux kernel, the installation program cannot read my CD-ROM drive for some reason.  

For the record this computer I am attempting this on is an eMachine etower 400i2.  I have tried:
Xubunto 6.10 alternate install CD
Xubunto 6.10 desktop CD
Ubunto 6.10 desktop CD
Kubunto 6.06 desktop CD

The various desktop CD images do not walk through the selection process detailed above, but all give the message:

[17179569.184000] ACPI: unable to locate RSDP

(There will be a different number in the brackets with different install disks)  Then all have a problem mounting a filesystem.

Curiously, I have a Ubuntu 5.10 install CD which does not have this problem, but will load a functioning Ubuntu system, and I assume, would install it if I told it to.

So my question: Has anyone seen this problem?  Is my etower box the cause of the problem?  Since this is an older machine, I would prefer to try Xubuntu 6.10.  Do I need some  secret code to put in the PCMCIA resource range options?

George

---

