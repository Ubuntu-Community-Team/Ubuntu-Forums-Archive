---
title: "&quot;Gave up waiting for root device&quot; &amp; &quot;configured for UDMA/66...&quot; message"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by blitzter47 on 2010-08-10
I have an old computer with old hard drives made before 2000:
Motherboard : AOpen AX34 Pentium III 1Ghz
Hard drives : 13 GB QUANTUM FIREBALL CX13.0A + 20 GB Seagate ST320414A + 13 GB FUJITSU MPC3064AT.

_**[FONT=Arial Black][SIZE=4]The problem[/SIZE][/FONT]**_

The first time I start booting Ubuntu, I got the message saying "Gave up waiting for root device ...". I searched about it on the Net and found a popular "alternative" to get rid of the shell message by adding **[SIZE=3]rootdelay=90 or 120[/SIZE]**... For me, I put[SIZE=3] **rootdelay=126**[/SIZE] exactly according to the verbose message while booting, after GRUB menu, or in **dmesg** log in terminal command just below :
[SIZE=3]_**T**__**ake care to look at the bold sections and underlined ones.**_[/SIZE]
> ```
dmesg
```[   32.816074] [SIZE=1]ata1: lost interrupt (Status 0x58)
[   32.820021] ata1: drained 32768 bytes to clear DRQ.
[   32.856542] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   32.856614] ata1.01: failed command: READ DMA
[   32.856687] ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[   32.856691]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   32.856841] ata1.01: status: { DRDY }
[   32.856938] ata1: soft resetting link[/SIZE]
[   33.044521] ata1.00: configured for UDMA/66[B]
[   33.060285] ata1.01: configured for UDMA/66[/B]
[SIZE=2]_My comment : The kernel seems to try booting the system hard drive __(ata1.01 : which is used to boot Ubuntu)__ in UDMA/66 Mode_[/SIZE]

[SIZE=1] [   33.060353] ata1.01: device reported invalid CHS sector 0
[   33.060428] ata1: EH complete
[   63.816066] ata1: lost interrupt (Status 0x58)
[   63.820021] ata1: drained 32768 bytes to clear DRQ.
[   63.856524] ata1.01: limiting speed to UDMA/44:PIO4
[   63.856590] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   63.856660] ata1.01: failed command: READ DMA
[   63.856733] ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[   63.856737]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   63.856886] ata1.01: status: { DRDY }
[   63.856975] ata1: soft resetting link[/SIZE]

[   64.044489] ata1.00: configured for UDMA/66[B]
[   64.060285] ata1.01: configured for UDMA/44[/B]
[SIZE=2]_My comment : Now, the kernel seems to try booting the system hard drive __(ata1.01 : which is used to boot Ubuntu)__ in UDMA/44 Mode_[/SIZE]

[SIZE=1][   64.060350] ata1.01: device reported invalid CHS sector 0
[   64.060423] ata1: EH complete
[   94.816062] ata1: lost interrupt (Status 0x58)
[   94.820022] ata1: drained 32768 bytes to clear DRQ.
[   94.856514] ata1.01: limiting speed to UDMA/33:PIO4
[   94.856580] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   94.856648] ata1.01: failed command: READ DMA
[   94.856720] ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[   94.856724]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   94.856874] ata1.01: status: { DRDY }
[   94.856960] ata1: soft resetting link
[   95.044523] ata1.00: configured for UDMA/66
[   95.060285] ata1.01: configured for UDMA/33
[   95.060350] ata1.01: device reported invalid CHS sector 0
[   95.060421] ata1: EH complete
[  125.816067] ata1: lost interrupt (Status 0x58)
[  125.820020] ata1: drained 32768 bytes to clear DRQ.
[  125.856521] ata1.01: limiting speed to PIO4
[  125.856586] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  125.856655] ata1.01: failed command: READ DMA
[  125.856728] ata1.01: cmd c8/00:08:00:00:00/00:00:00:00:00/f0 tag 0 dma 4096 in
[  125.856732]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  125.856882] ata1.01: status: { DRDY }
[  125.856970] ata1: soft resetting link[/SIZE]

[  126.044487] ata1.00: configured for UDMA/66[B]
[ [SIZE=3] 126[/SIZE].060284] ata1.01: configured for PIO4[/B]
[SIZE=2]_My comment : After the 126th seconds while booting, the kernel detected FINALLY that the system hard drive __(ata1.01 : which is used to boot Ubuntu)__ can support as best as PIO4 mode only_.[/SIZE]

[SIZE=1][  126.060349] ata1.01: device reported invalid CHS sector 0
[  126.060420] ata1: EH complete
[  126.070024]  sdb1 sdb2
[  126.070519] sd 0:0:0:0: [sda] Attached SCSI disk[/SIZE]
**[****[SIZE=3]126[/SIZE]**[B] .070993] sda: detected capacity change from 0 to 13020069888
[[/B]**[SIZE=3]126[/SIZE]**[B] .071357] sdb: detected capacity change from 0 to 20020396032
[[/B]**[SIZE=3]126[/SIZE]**[B] .072682] sda: detected capacity change from 0 to 13020069888
[/B][  126.073138] sd 0:0:1:0: [sdb] Attached SCSI disk
**[  [SIZE=3]126[/SIZE].088848] sdb: detected capacity change from 0 to 20020396032**
_[SIZE=2]My comment : At the end of the 126th seconds, the kernel is adjusting itself to the PIO4 mode of the Ubuntu system hard drive, and Ubuntu starts loading! That's why I put [/SIZE]**[SIZE=3]rootdelay=126[/SIZE]**._[U][FONT=Arial Black][SIZE=4][B]The real solution for me

[/B][/SIZE][/FONT][/U]As I can see, I think the kernel go through all possible UDMA modes before getting the right mode for my hard drive. So after a long research about this issue on the Net and about the kernel, here's the solution for me to avoid the delay and load Ubuntu immediately, with "**libata.force=1:pio4**" to force the kernel to go directly to PIO4 mode (the appropriate mode for me) without passing by UDMA modes.

I tested it by pressing "e" key at GRUB menu startup after highlighted "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic" in the menu.
and added "**libata.force=1:pio4**" at the end of "kernel" line as below
> title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        0a6411bd-3776-4186-bc4a-8d63e2d1eb5f
_kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=0a6411bd-3776-4186-bc4a-8d63e2d1eb5f ro rootdelay=126 **libata.force=1:pio4**_
initrd        /boot/initrd.img-2.6.32-24-genericThen I booted with this parameter ("Ctrl + b" or "b") and not only the shell should disappeared but the time delay waiting for the device also. If it works, go to the next section to see how to make this permanent.

I suppose who has a SATA hard drive may try "**libata.force=1:sata**" or "**libata.force=1:1.5Gbps**" or "**libata.force=1:3.0Gbps**" or a combination of them, separated with comma like **libata.force=1:sata,1.5Gbps**". More info about libata.force at the end of this post.

_[FONT=Arial Black]**[SIZE=4]To make this permanent (if the solution works)[/SIZE]**[/FONT]_

_[SIZE=3]For GRUB 1[/SIZE]_
In terminal: edit /boot/grub/menu.lst
```
sudo gedit /boot/grub/menu.lst
```[U][SIZE=3]
...or for GRUB 2:[/SIZE][/U]
```
sudo gedit /boot/grub/grub.cfg
```and add "**libata.force=1:pio4**" in text editor like above, where "pio4" is the supported mode of your hard drive, according to the kernel parameters at the end of this post.
_[SIZE=3]Another way for GRUB 2 (little more steps):[/SIZE]_
To edit /etc/default/grub file in text editor, type in terminal
```
sudo gedit /etc/default/grub
```then find, in the 9th line of the opened file, **GRUB_CMDLINE_LINUX_DEFAULT** Then change the content in quotes in the following way:
```
GRUB_CMDLINE_LINUX_DEFAULT=**"libata.force=1:pio4 quiet splash"**
```then run **sudo update-grub** in the terminal.

Hope that will help.

_[SIZE=3] Info about libata.force=... :[/SIZE]_
> 
1195**_        libata.force=_**    [LIBATA] Force configurations.  The format is comma
1196                separated list of "[ID:]VAL" where ID is
1197                PORT[.DEVICE].  PORT and DEVICE are decimal numbers
1198                matching port, link or device.  Basically, it matches
1199                the ATA ID string printed on console by libata.  If
1200                the whole ID part is omitted, the last PORT and DEVICE
1201                values are used.  If ID hasn't been specified yet, the
1202                configuration applies to all ports, links and devices.
1203    
1204                If only DEVICE is omitted, the parameter applies to
1205                the port and all links and devices behind it.  DEVICE
1206                number of 0 either selects the first device or the
1207                first fan-out link behind PMP device.  It does not
1208                select the host link.  DEVICE number of 15 selects the
1209                host link and device attached to it.
1210    
1211                The VAL specifies the configuration to force.  As long
1212                as there's no ambiguity shortcut notation is allowed.
1213                For example, both 1.5 and 1.5G would work for 1.5Gbps.
1214                The following configurations can be forced.
1215    
1216                * Cable type: **40c, 80c, short40c, unk, ign or sata**.
1217                  Any ID with matching PORT is used.
1218    
1219                * SATA link speed limit: **1.5Gbps or 3.0Gbps**.
1220    
1221                * Transfer mode: **pio[0-7], mwdma[0-4] and udma[0-7]**.
1222                  **udma[/][16,25,33,44,66,100,133]** notation is also
1223                  allowed.

sources :
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)


---

### Post by NexaYa on 2011-05-12
> **chtnh said:**
> I have an old computer with old hard drives made before 2000:
Motherboard : AOpen AX34 Pentium III 1Ghz
Hard drives : 13 GB QUANTUM FIREBALL CX13.0A + 20 GB Seagate ST320414A + 13 GB FUJITSU MPC3064AT.

_**[FONT=Arial Black][SIZE=4]The problem[/SIZE][/FONT]**_

The first time I start booting Ubuntu, I got the message saying "Gave up waiting for root device ...". I searched about it on the Net and found a popular "alternative" to get rid of the shell message by adding **[SIZE=3]rootdelay=90 or 120[/SIZE]**... For me, I put[SIZE=3] **rootdelay=126**[/SIZE] exactly according to the verbose message while booting, after GRUB menu, or in **dmesg** log in terminal command just below :
[SIZE=3]_**T**__**ake care to look at the bold sections and underlined ones.**_[/SIZE]
[U][FONT=Arial Black][SIZE=4][B]The real solution for me

[/B][/SIZE][/FONT][/U]As I can see, I think the kernel go through all possible UDMA modes before getting the right mode for my hard drive. So after a long research about this issue on the Net and about the kernel, here's the solution for me to avoid the delay and load Ubuntu immediately, with "**libata.force=1:pio4**" to force the kernel to go directly to PIO4 mode (the appropriate mode for me) without passing by UDMA modes.

I tested it by pressing "e" key at GRUB menu startup after highlighted "Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic" in the menu.
and added "**libata.force=1:pio4**" at the end of "kernel" line as below
Then I booted with this parameter ("Ctrl + b" or "b") and not only the shell should disappeared but the time delay waiting for the device also. If it works, go to the next section to see how to make this permanent.

I suppose who has a SATA hard drive may try "**libata.force=1:sata**" or "**libata.force=1:1.5Gbps**" or "**libata.force=1:3.0Gbps**" or a combination of them, separated with comma like **libata.force=1:sata,1.5Gbps**". More info about libata.force at the end of this post.

_[FONT=Arial Black]**[SIZE=4]To make this permanent (if the solution works)[/SIZE]**[/FONT]_

In terminal:
```
sudo gedit /boot/grub/menu.lst
```or for GRUB 2:
```
sudo gedit /boot/grub/grub.cfg
```and add "**libata.force=1:pio4**" in text editor like above, where "pio4" is the supported mode of your hard drive, according to the kernel parameters at the end of this post.

Hope that will help.

Info about libata.force=... :
Thanks a lot!!!

---

### Post by JeremyT on 2011-11-11
Wowza! That worked. Thank you so very much, chtnh! You are awesome!

However, would it be better to place the parameter in /etc/default/grub because when update-grub is run, the /boot/grub/grub.cfg file is written over, isn't it?

So, change the **GRUB_CMDLINE_LINUX_DEFAULT** value to include the **libata.force=1:pio4** line

example:
```
GRUB_CMDLINE_LINUX_DEFAULT="libata.force=1:pio4 quiet splash"
```

---

### Post by blitzter47 on 2011-11-12
@JeremyT

Yes, you can edit /etc/default/grub as sudo (e.g. with gedit) in the way you said :
```
GRUB_CMDLINE_LINUX_DEFAULT="libata.force=1:pio4 quiet splash"
```
then run **update-grub** in the terminal.

Usually, the way you suggested or mine gives the same result as /boot/grub/grub.cfg file is edited in both manipulations.

But people seem to say that editing /etc/default/grub then **update-grub** (for GRUB 2) is safer and avoids _risks_ for linux misreading the grub file.

---

### Post by jsa36 on 2011-11-24
I just now registered on the forum just to say thank you.  I am completely new to Ubuntu and Linux as I am trying to resurrect an old desktop for my kids to use.

With a little tweaking, your post fixed my problem booting.  At first I wasn't able to boot at all, but adding the rootdelay solved that.

I still had issues with the boot taking so long and the libata.force wasn't helping.

Finally, I noticed that in dmesg ata1 (my hard drive) wasn't the problem, it was ata2 (my cd/dvd drive) that took so long to finally configure for pio4.  So I took a guess and made the slight change to "**libata.force=2**:pio4" to the line in /etc/default/grub and it worked like a charm.

So again, thank you for sharing your knowledge and solving my issue.

---

