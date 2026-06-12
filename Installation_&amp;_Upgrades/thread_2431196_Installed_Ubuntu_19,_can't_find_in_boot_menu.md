---
title: "Installed Ubuntu 19, can't find in boot menu"
date: 2019-11-13
forum: Installation &amp; Upgrades
---

### Post by dudekulowski on 2019-11-13
I'm trying to dual boot ubuntu and windows 10.

Have already googled this a bit:

[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

The thread above mentions [COLOR=#000000]"Select an UEFI file as trusted for executing:" press ENTER
[/COLOR]I don't have such a feature in my BIOS.

BIOS name:
Brand	American Megatrends Inc.
Version	R02-A1
Date	9/01/2017

Tried installing the boot-repair tool but it gave an error (booted up ubuntu on a usb).

Acer motherboard (Acer Aspire GX-781(KBL) (U3E1))

---

### Post by yancek on 2019-11-13
You have an Acer and they require on newer (UEFI) machines that you set trust in the BIOS firmware before you can install any OS other than windows.  In order to do this, you first need to set a Supervisor password in the BIOS firmware.  Did you read the Ubuntu documentation on dual booting with windows 10, link below?

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Go back to the boot repair page and look at the 2nd option near the top of the page, using the ppa option .  You should be able to do this while booted into the Ubuntu install usb.  After doing this, there is no reason why you would reboot, just run boot repair and select ONLY the option to Create BootInfo Summary and post the link you get when it finishes here to get help.

---

### Post by oldfred on 2019-11-13
Other users with an Acer and how they set trust.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust, never lose password:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by dudekulowski on 2019-11-13
Using the code snippets at this site:
[HTML]https://help.ubuntu.com/community/Boot-Repair[/HTML]

```
[COLOR=#333333][FONT=UbuntuMono]sudo add-apt-repository ppa:yannubuntu/boot-repair
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo apt-get update [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo apt-get install -y boot-repair && boot-repair[/FONT][/COLOR]
```

I'm getting this error message when trying to run boot repair
```
sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I went back into the BIOS to check:
I have a supervisor password
Secure boot is enabled.

---

### Post by yancek on 2019-11-13
After you set the supervisor password, did you look for some option to set 'trust'.  I don't have an Acer so no way to check, might try an online search specifically for that.

Not sure why you are getting the error with boot repair.  Are you using the Ubuntu install DVD/USB to do this?

---

### Post by dudekulowski on 2019-11-14
> **yancek said:**
> After you set the supervisor password, did you look for some option to set 'trust'.  I don't have an Acer so no way to check, might try an online search specifically for that.


Yes, but I couldn't find anything. I'm guessing my issue is somewhat similar to the one this person had:
[https://ubuntuforums.org/showthread.php?t=2412341](https://ubuntuforums.org/showthread.php?t=2412341)

> **yancek said:**
> Not sure why you are getting the error with boot repair. Are you using the Ubuntu install DVD/USB to do this?
I used the same USB i used to install Ubuntu.

I also updated my BIOS in case that would change anything. It didn't.

---

### Post by oldfred on 2019-11-14
You say Ubuntu 19, what exact version are you installing?
Boot-Repair should work with any current version of Ubuntu, but does not work on EOL - end of life versions.

After you update UEFI, it often sets many of the settings you changed back to defaults. Have you reset those settings?

Post this from live installer:
sudo efibootmgr -v

---

### Post by dudekulowski on 2019-11-15
Update:
I got Ubuntu to work, it now starts up automatically on boot

Used this to get it working (typed in windows cmd):
```
bcedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
```

My BIOS/UEFI still looks the same and ubuntu isn't seen there as an option even if it does boot up if I touch nothing.

[B]Problem is:
[/B]Now I can't boot to Windows. 
I get to the Grub screen, where the options are (about):
Ubuntu
Advanced Ubuntu
Windows Boot Manager
Windows Boot Manager 2
System check 

If I select Ubuntu, it boots without a hitch.

Both the Windows Boot Manager selections, however, only make the screen blink. Nothing else happens. If I want to boot anywhere, I have to boot into Ubuntu.

Any way I could fix this?

Here's the code output from ```
sudo efibootmgr -v
```:

```
BootCurrent: 0001Timeout: 1 seconds
BootOrder: 0001,0002,0000
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* UEFI: ST1000DM003-1CH162, Partition 2    PciRoot(0x0)/Pci(0x17,0x0)/Sata(2,65535,0)/HD(2,GPT,b0d051fc-50f0-4da1-8636-e9d3dffdfd50,0x200000,0xb4000)..BO



```

---

### Post by yancek on 2019-11-15
I've never used the bcdedit command you posted so I'm not sure what it is supposed to do but, looking at the efibootmgr output, it appears to be pointing to the Ubuntu efi files in the entry for Windows Boot Manager.

> Boot0001* Windows Boot Manager    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.. 

Have you run sudo update-grub since making this change?  If not, try that and post back what happens on reboot.

---

### Post by oldfred on 2019-11-15
Years ago when UEFI was new we used to use a setting like that. But it caused issue and we have other better work arounds.

If you use the Windows setting, Windows updates will overwrite it and you cannot boot Ubuntu.
And grub only boots working Windows. So if Windows turn fast start up back on with an update or needs chkdsk, you have no way to boot Ubuntu.

Now the most common work around is to use the fallback or hard drive boot entry in UEFI to be for Ubuntu.
Examples in link in my signature.

---

### Post by dudekulowski on 2019-11-16
Thanks for the help @oldfred, but... you have a lot of info in that thread. I don't know which part it is that I should be looking at.[URL="https://paste.ubuntu.com/p/b8qP3Pfjcd/"]

https://paste.ubuntu.com/p/b8qP3Pfjcd/[/URL]

Posted the summary from boot repair

@yancek I did that, but didn't make any changes from what I can see

---

### Post by oldfred on 2019-11-16
Is this an Acer?
Then you need to set "trust" from within UEFI. See post #3.

Also many need UEFI update from Acer, especially if trust option missing.

---

### Post by dudekulowski on 2019-11-16
It is an Acer. But I simply cannot find any trust option from within the UEFI.
I've tested setting a supervisor password, turning secure boot off and on, and so on.

I have also updated my UEFI to the newest, from Acers support site.

Right now I'd love to get access to windows again. 

But the only thing that is working (from grub) is ubuntu. If I try selecting windows boot loader and pressing enter, the screen just flickers quickly, but nothing else happens.

---

### Post by jeremy31 on 2019-11-16
I see some strange things in that boot repair info, you have 2 drives each with their own EFI System Partition.  Post results for ```
efibootmgr -v; sudo ls -R /boot/efi
```

---

### Post by dudekulowski on 2019-11-16
> **jeremy31 said:**
> I see some strange things in that boot repair info, you have 2 drives each with their own EFI System Partition.  Post results for ```
efibootmgr -v; sudo ls -R /boot/efi
```

efibootmgr -v results in:
```
BootCurrent: 0001Timeout: 1 seconds
BootOrder: 0001,0002,0000
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* UEFI: ST1000DM003-1CH162, Partition 2    PciRoot(0x0)/Pci(0x17,0x0)/Sata(2,65535,0)/HD(2,GPT,b0d051fc-50f0-4da1-8636-e9d3dffdfd50,0x200000,0xb4000)..BO

```

sudo ls -R /boot/efi results in:
```
/boot/efi:
boot-repair  EFI


/boot/efi/boot-repair:
log


/boot/efi/boot-repair/log:
20191116_074711


/boot/efi/boot-repair/log/20191116_074711:
boot-repair.log  sda   sda3  sdb   sdb2  sdb5  sdb7
RESULTS.txt     sda1  sda4  sdb1  sdb4  sdb6  sdb9


/boot/efi/boot-repair/log/20191116_074711/sda:
partition_table.dmp


/boot/efi/boot-repair/log/20191116_074711/sda1:


/boot/efi/boot-repair/log/20191116_074711/sda3:


/boot/efi/boot-repair/log/20191116_074711/sda4:


/boot/efi/boot-repair/log/20191116_074711/sdb:
partition_table.dmp


/boot/efi/boot-repair/log/20191116_074711/sdb1:


/boot/efi/boot-repair/log/20191116_074711/sdb2:


/boot/efi/boot-repair/log/20191116_074711/sdb4:


/boot/efi/boot-repair/log/20191116_074711/sdb5:


/boot/efi/boot-repair/log/20191116_074711/sdb6:


/boot/efi/boot-repair/log/20191116_074711/sdb7:
grubenv


/boot/efi/boot-repair/log/20191116_074711/sdb9:


/boot/efi/EFI:
Boot  Microsoft  OEM  ubuntu


/boot/efi/EFI/Boot:
bootx64.efi  fbx64.efi    mmx64.efi


/boot/efi/EFI/Microsoft:
Boot  Recovery


/boot/efi/EFI/Microsoft/Boot:
BCD          en-GB  kd_02_10df.dll  lt-LT      sl-SI
BCD.LOG       en-US  kd_02_10ec.dll  lv-LV      sr-Latn-CS
BCD.LOG1      es-ES  kd_02_1137.dll  memtest.efi  sr-Latn-RS
BCD.LOG2      es-MX  kd_02_14e4.dll  nb-NO      sv-SE
bg-BG          et-EE  kd_02_15b3.dll  nl-NL      tr-TR
bootmgfw.efi  fi-FI  kd_02_1969.dll  pl-PL      uk-UA
bootmgr.efi   Fonts  kd_02_19a2.dll  pt-BR      updaterevokesipolicy.p7b
BOOTSTAT.DAT  fr-CA  kd_02_1af4.dll  pt-PT      winsipolicy.p7b
boot.stl      fr-FR  kd_02_8086.dll  qps-ploc      zh-CN
cs-CZ          hr-HR  kd_07_1415.dll  Resources      zh-HK
da-DK          hu-HU  kd_0C_8086.dll  ro-RO      zh-TW
de-DE          it-IT  kdstub.dll      ru-RU
el-GR          ja-JP  ko-KR         sk-SK


/boot/efi/EFI/Microsoft/Boot/bg-BG:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/cs-CZ:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/da-DK:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/de-DE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/el-GR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/en-GB:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/en-US:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/es-ES:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/es-MX:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/et-EE:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/fi-FI:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/Fonts:
chs_boot.ttf  malgun_boot.ttf    msjh_boot.ttf    segmono_boot.ttf
cht_boot.ttf  malgunn_boot.ttf    msjhn_boot.ttf    segoen_slboot.ttf
jpn_boot.ttf  meiryo_boot.ttf    msyh_boot.ttf    segoe_slboot.ttf
kor_boot.ttf  meiryon_boot.ttf    msyhn_boot.ttf    wgl4_boot.ttf


/boot/efi/EFI/Microsoft/Boot/fr-CA:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/fr-FR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/hr-HR:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/hu-HU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/it-IT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/ja-JP:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/ko-KR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/lt-LT:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/lv-LV:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/nb-NO:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/nl-NL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/pl-PL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/pt-BR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/pt-PT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/qps-ploc:
memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/Resources:
bootres.dll  da-DK  en-US  fi-FI  nb-NO  sv-SE


/boot/efi/EFI/Microsoft/Boot/Resources/da-DK:
bootres.dll.mui


/boot/efi/EFI/Microsoft/Boot/Resources/en-US:
bootres.dll.mui


/boot/efi/EFI/Microsoft/Boot/Resources/fi-FI:
bootres.dll.mui


/boot/efi/EFI/Microsoft/Boot/Resources/nb-NO:
bootres.dll.mui


/boot/efi/EFI/Microsoft/Boot/Resources/sv-SE:
bootres.dll.mui


/boot/efi/EFI/Microsoft/Boot/ro-RO:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/ru-RU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/sk-SK:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/sl-SI:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/sr-Latn-CS:
memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/sr-Latn-RS:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/sv-SE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/tr-TR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/uk-UA:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/Microsoft/Boot/zh-CN:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/zh-HK:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Boot/zh-TW:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/Microsoft/Recovery:
BCD  BCD.LOG  BCD.LOG1    BCD.LOG2


/boot/efi/EFI/OEM:
Boot  Recovery


/boot/efi/EFI/OEM/Boot:
BCD          da-DK  fr-CA         kd_02_15b3.dll  memtest.efi  sk-SK
BCD.LOG       de-DE  fr-FR         kd_02_1969.dll  nb-NO      sl-SI
BCD.LOG1      el-GR  hr-HR         kd_02_19a2.dll  nl-NL      sr-Latn-CS
BCD.LOG2      en-GB  hu-HU         kd_02_8086.dll  pl-PL      sr-Latn-RS
bg-BG          en-US  it-IT         kd_07_1415.dll  pt-BR      sv-SE
bootmgfw.efi  es-ES  ja-JP         kd_0C_8086.dll  pt-PT      tr-TR
bootmgr.efi   es-MX  kd_02_10df.dll  kdstub.dll      qps-ploc      uk-UA
BOOTSTAT.DAT  et-EE  kd_02_10ec.dll  ko-KR         Resources      zh-CN
boot.stl      fi-FI  kd_02_1137.dll  lt-LT         ro-RO      zh-HK
cs-CZ          Fonts  kd_02_14e4.dll  lv-LV         ru-RU      zh-TW


/boot/efi/EFI/OEM/Boot/bg-BG:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/cs-CZ:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/da-DK:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/de-DE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/el-GR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/en-GB:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/en-US:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/es-ES:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/es-MX:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/et-EE:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/fi-FI:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/Fonts:
chs_boot.ttf  malgun_boot.ttf    msjh_boot.ttf    segmono_boot.ttf
cht_boot.ttf  malgunn_boot.ttf    msjhn_boot.ttf    segoen_slboot.ttf
jpn_boot.ttf  meiryo_boot.ttf    msyh_boot.ttf    segoe_slboot.ttf
kor_boot.ttf  meiryon_boot.ttf    msyhn_boot.ttf    wgl4_boot.ttf


/boot/efi/EFI/OEM/Boot/fr-CA:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/fr-FR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/hr-HR:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/hu-HU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/it-IT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/ja-JP:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/ko-KR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/lt-LT:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/lv-LV:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/nb-NO:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/nl-NL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/pl-PL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/pt-BR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/pt-PT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/qps-ploc:
memtest.efi.mui


/boot/efi/EFI/OEM/Boot/Resources:
bootres.dll  da-DK  en-US  fi-FI  nb-NO  sv-SE


/boot/efi/EFI/OEM/Boot/Resources/da-DK:
bootres.dll.mui


/boot/efi/EFI/OEM/Boot/Resources/en-US:
bootres.dll.mui


/boot/efi/EFI/OEM/Boot/Resources/fi-FI:
bootres.dll.mui


/boot/efi/EFI/OEM/Boot/Resources/nb-NO:
bootres.dll.mui


/boot/efi/EFI/OEM/Boot/Resources/sv-SE:
bootres.dll.mui


/boot/efi/EFI/OEM/Boot/ro-RO:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/ru-RU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/sk-SK:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/sl-SI:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/sr-Latn-CS:
memtest.efi.mui


/boot/efi/EFI/OEM/Boot/sr-Latn-RS:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/sv-SE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/tr-TR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/uk-UA:
bootmgfw.efi.mui  bootmgr.efi.mui


/boot/efi/EFI/OEM/Boot/zh-CN:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/zh-HK:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Boot/zh-TW:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui


/boot/efi/EFI/OEM/Recovery:
BCD  BCD.LOG  BCD.LOG1    BCD.LOG2


/boot/efi/EFI/ubuntu:
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

```

---

### Post by oldfred on 2019-11-16
It is ok to have two ESP, as long as on different drives.

You have to have UEFI Secure boot on with UEFI password (never forget password or reset when done).
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---

### Post by dudekulowski on 2019-11-16
My BIOS seems to differ from those linked.

Compare this
[https://i.imgur.com/E0KuZeK.jpg](https://i.imgur.com/E0KuZeK.jpg)

to this (screenshot of bios, found in post oldfred linked)
[http://www.bernaerts-nicolas.fr/images/technoblog/acer-ao1-431/ubuntu-aceraspireone431-uefi-menu.jpg](http://www.bernaerts-nicolas.fr/images/technoblog/acer-ao1-431/ubuntu-aceraspireone431-uefi-menu.jpg)

I don't really care too much about being able to boot into linux. 
However, I *need* to be able to boot into windows. I can start this process from scratch once I get there. 

Seeing as I managed to make my PC boot into only linux using one command, surely there's a way to revert it as well?

---

### Post by jeremy31 on 2019-11-16
How did you edit the windows entry?
```
Boot0001* Windows Boot Manager    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
```
Is what you have but it should show /File(\EFI\Microsoft\Boot\bootmgfw.efi)

---

### Post by dudekulowski on 2019-11-16
I followed this guide:
[https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

And I think it's this command that did it:

bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi

Thats only my guess though

So if i could somehow access the same thing or use the same program, I could revert changes just by doing

bcdedit /set "{bootmgr}" path \EFI\Microsoft\Boot\bootmgfw.efi

...or?

---

### Post by jeremy31 on 2019-11-16
The efibootmgr program might be able to fix
try ```
sudo efibootmgr -c  -L "Windows Boot Test" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
```
Then see if it shows in the results for [code]efibootmgr -v[/code

---

### Post by dudekulowski on 2019-11-16
> **jeremy31 said:**
> The efibootmgr program might be able to fix
try ```
sudo efibootmgr -c  -L "Windows Boot Test" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
```
Then see if it shows in the results for ```
efibootmgr -v[/code

Did the above, here's the output:

[code]
matt@matt-Aspire-GX-781:~$ sudo efibootmgr -c -L "Windows Boot Test" -l "\EFI\Microsoft\Boot\bootmgfw.efi"
[sudo] password for matt: 

BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0003,0001,0002,0000
Boot0000  ubuntu
Boot0001* Windows Boot Manager
Boot0002* UEFI: ST1000DM003-1CH162, Partition 2
Boot0003* Windows Boot Test

matt@matt-Aspire-GX-781:~$ efibootmgr -v

BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0003,0001,0002,0000
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* UEFI: ST1000DM003-1CH162, Partition 2    PciRoot(0x0)/Pci(0x17,0x0)/Sata(2,65535,0)/HD(2,GPT,b0d051fc-50f0-4da1-8636-e9d3dffdfd50,0x200000,0xb4000)..BO
Boot0003* Windows Boot Test    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)



```

---

### Post by jeremy31 on 2019-11-16
Now lets try ```
sudo efibootmgr -n 0003
```
Reboot and see if you end up in Windows

---

### Post by oldfred on 2019-11-16
Does Windows Boot test boot Windows?

The ubuntu entry is not a full UEFI boot entry .

You can use efibootngr to create an ubuntu entry.
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/sda -p 1

Then see if in UEFI entries it shows and boot order can be set.

I might delete old ubuntu entry also

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). With Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by dudekulowski on 2019-11-16
> **jeremy31 said:**
> Now lets try ```
sudo efibootmgr -n 0003
```
Reboot and see if you end up in Windows

I get an error, saying the boot method is not enabled in BIOS settings

"Selected boot device is disabled in BIOS setup"

But again, when I do go to BIOS I can't find anything where I could 'enable' these ...whatever they are. Boot methods?

---

### Post by jeremy31 on 2019-11-16
Look in the Boot Option tab in BIOS setting, see if it is set to UEFI only also

---

### Post by dudekulowski on 2019-11-16
Here's what I'm looking at in the boot menu
[https://i.imgur.com/8TvYAhv.jpg](https://i.imgur.com/8TvYAhv.jpg)

[https://i.imgur.com/7TLC3NL.jpg](https://i.imgur.com/7TLC3NL.jpg)

When you click on 'hard disk drive priority' -> You see 2 options (1st & 2nd boot device: Windows boot manager or 'UEFI: ST1000DM003-1..' (Booting this leads to windows auto repair tool, but you don't get anywhere from there)

---

### Post by jeremy31 on 2019-11-16
On this screen [https://imgur.com/8TvYAhv](https://imgur.com/8TvYAhv)
There is an option for F7 load user defined????
What is the full text?

---

### Post by dudekulowski on 2019-11-16
F7: Load user-defined defaults

---

### Post by jeremy31 on 2019-11-16
What is in the Authentication tab in BIOS?  And what shows if you press F12 at boot?

---

### Post by dudekulowski on 2019-11-16
**F12 shows:**

[COLOR=#000000]I get to the Grub screen, where the options are (about):[/COLOR]
[COLOR=#000000]Ubuntu[/COLOR]
[COLOR=#000000]Advanced Ubuntu[/COLOR]
[COLOR=#000000]Windows Boot Manager[/COLOR]
[COLOR=#000000]Windows Boot Manager 2[/COLOR]
[COLOR=#000000]System check[/COLOR]

[COLOR=#000000]If I select Ubuntu, it boots without a hitch.[/COLOR]

[COLOR=#000000]Both the Windows Boot Manager selections, however, only make the screen blink. Nothing else happens. If I want to boot anywhere, I have to boot into [B]Ubuntu.

Authentification Tab

[/B][/COLOR][https://imgur.com/a/xxGcDol](https://imgur.com/a/xxGcDol)

Note: If I enable secure boot, I'm getting the red error when starting the computer. I think this has to do with me updating the BIOS and somehow the keys mismatching. But I'm not the expert here so hey ho...

---

### Post by jeremy31 on 2019-11-16
Does the Secure Boot mode [custom] give any options?  I would suspect that setting would allow booting to an EFI file

---

### Post by dudekulowski on 2019-11-16
Custom adds the 2 bottom rows
If you choose the other option "Standard" these 2 bottom rows disappear

---

### Post by jeremy31 on 2019-11-16
Reboot and at the grub menu, press c for command line, then try this
```
insmod part_gpt
insmod chain
set root=(hd0,gpt1)
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
boot
```

---

### Post by dudekulowski on 2019-11-16
set root=(hd0,gpt1) 
returns the error:
Error: disk `hd0,gpt1`not found

Tried added spaces, didnt make a difference

---

### Post by oldfred on 2019-11-16
With UEFI secure boot on, & admin password set have you checked every entry in all your UEFI screens that have sub-menus to see what is there?

---

### Post by jeremy31 on 2019-11-16
> **dudekulowski said:**
> set root=(hd0,gpt1) 
returns the error:
Error: disk `hd0,gpt1`not found

Tried added spaces, didnt make a difference

In the grub command line, try the ls command to see what is available, it might be
```
set root=(hd1,gpt1)
```

---

### Post by dudekulowski on 2019-11-16
Yes, I've checked all of them multiple times. Didn't find anything that would be relevant to this (according to me that is)

---

### Post by dudekulowski on 2019-11-16
ls
->

(proc) (hd0) (hd1) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) (hd2) (hd2,gpt9) (hd2,gpt8) (hd2,gpt7) (hd2,gpt6) (hd2,gpt5) (hd2,gpt4) (hd2,gpt3) (hd2,gpt2) (hd2,gpt1)

---

### Post by jeremy31 on 2019-11-16
```
insmod part_gpt
insmod chain
set root=(hd1,gpt1)
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
boot
```

hd0 might be optical drive

---

### Post by dudekulowski on 2019-11-16
When i enter this code, what is supposed to happen?

When writing boot and hitting ENTER, is it supposed to immediately boot whatever has been set? or am I supposed to reboot, and only then will this code be implemented?

As it is now, I write what you stated (no errors), but nothing happens after i write the last line, boot.

---

### Post by jeremy31 on 2019-11-16
After typing the last command I would expect it to try booting Windows.  Unfortunately I am out of any other ideas at this time unless using set root=(hd2,gpt1) might be a working replacement

---

### Post by oldfred on 2019-11-16
The only other thing I have seen and am not sure why it works is rEFInd. 
I do use rEFInd on an old tiny flash drive that now had no other use as an emergency boot drive. It seems to automatically find all my installs, but I do not have Windows.
But some have posted that systems that do not want to boot may work with rEFInd.

[https://forums.linuxmint.com/viewtopic.php?t=254948](https://forums.linuxmint.com/viewtopic.php?t=254948)
[https://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html](https://gnu-linux.org/how-to-permanently-add-linux-entry-in-uefi-menu.html)
Alternative efi boot manager for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) &
[https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions](https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions)

---

### Post by dudekulowski on 2019-11-17
**Captain's log 17th of November. Morale low. Mutiny is feared.**

Tried installing the above mentioend rEFInd. I accidentally mounted it on my windows boot manager partition.

Now I get "Reboot and select proper boot device or insert boot media in selected device and press a key", unless I have the refind usb (mounted it succesfully from another computer) stick in. 
With that, I find the linux boot. 

The Windows boot goes into auto repair mode -> error. I have like 6 different boots to choose from though, haven't tried them all.

efibootmgr -v returns:
```

BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0001,0002,0000,0003,0004
Boot0000  ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager	HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* UEFI: ST1000DM003-1CH162, Partition 2	PciRoot(0x0)/Pci(0x17,0x0)/Sata(2,65535,0)/HD(2,GPT,b0d051fc-50f0-4da1-8636-e9d3dffdfd50,0x200000,0xb4000)..BO
Boot0003  Windows Boot Test	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004  rEFInd Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0005* UEFI: SanDisk, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(19,0)/HD(1,GPT,c271db03-317d-44ed-aad3-1a7c34d614c7,0x800,0x305f)..BO



```

SO.

**What I'd like to know now is:**

#1. How do I unf**k this situation I made by accidentally mounting refind on sda1 aka windows boot aka the partition that booted ubuntu even though it says windows boot?

#2. How do I get back into Windows?

[I]Sidenote: I'm starting to accept the situation. There's nothing of vital importance in my windows system anyway, only thing are my games that won't work on linux. But games are a time-waste.

Only thing is I installed Ubuntu on this old and slow harddrive I salvaged from a broken computer. I have a 250 GB SSD, which is used by Windows. But right now it's just sitting there.

And the SSD <-> HDD difference in speed is noticeable.[/I]

---

### Post by dudekulowski on 2019-11-17
Here's a list of the 6 different boot options rEFInd gives on startup, and what they do:

1. Boot Microsoft EFI boot from SYSTEM                                                  ---> Windows recovery tool, all tools there return some form of error.
2. Boot EFI\Boot\bootx64.efi.efi from recovery image                                ---> Runs a shell that does something ([https://i.imgur.com/t2V1vtk.jpg](https://i.imgur.com/t2V1vtk.jpg)). Haven't let it run simply because I've no idea what its doing.
3. Boot boot\cdboot_noprompt.efi from recovery image                             ---> Returns a 'no mapping returned' error
4. Boot boot\cdboot from recovery image                                                   ---> "Press any key to boot from CD or DVD" (dont have one)
5. Boot fallback boot loader from recovery image                                       ---> Here it starts the same windows recovery tool as in option 1, but here it gives me a new option of performing a full factory reset, deleting all my information and so on. 
                                                                                                                           That option is starting to sound quite tempting.
6. Boot Ubuntu (boot\vmlinuz-5.3.0-23-generic from 19gb ext4 volume)   ---> Boots successfully (but slowly) to ubuntu.

---

### Post by yancek on 2019-11-17
At the end of the boot repair script. you will see the following:

> Please do not forget to make your BIOS boot on sdb2/efi/.../grub*.efi file!

If you have not done so already, try going into the BIOS firmware and changing the boot priority to boot from the entries on sdb, the 1TB drive.

> Boot0001* Windows Boot Manager 

The output of efibootmgr in your last post shows the above.  If you go to the end of that line, you will see that it is pointing to the ubuntu\grubx64.efi rather than the correct windows entry.  That's because you used the bcdedit command to change it, post 8.  In post 20, there is a command suggested to change it.  Did you run this and get the same result, not windows boot?  That entry in efibootmgr is different and doesn't show the path, not sure if that's a problem.  If you look at the output of efibootmgr, you will see that it does not show the entries from the EFI partition on sdb2.  Not sure why that is the case.  Might try the boot repair suggestion of booting from that drive from the BIOS.

---

### Post by dudekulowski on 2019-11-17
This is the current result of efibootmgr -v

BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0007,0006,0005,0001,0002,0000,0003,0004
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* Windows Boot Manager    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* UEFI: ST1000DM003-1CH162, Partition 2    PciRoot(0x0)/Pci(0x17,0x0)/Sata(2,65535,0)/HD(2,GPT,b0d051fc-50f0-4da1-8636-e9d3dffdfd50,0x200000,0xb4000)..BO
Boot0003  Windows Boot Test    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0004  rEFInd Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0005* UEFI: SanDisk, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(19,0)/HD(1,GPT,c271db03-317d-44ed-aad3-1a7c34d614c7,0x800,0x305f)..BO
Boot0006* Windows Boot Test    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
Boot0007* Windows Boot Manager    HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)


The command in post 20 just creates more boots as seen above. I'll go check if there are 8 boots to choose from now in the rEFInd menu. (Edit: nope still the same 6)

It goes into recovery mode (none of the options there work) if i make boot priority -> the 1TB drive

---

### Post by oldfred on 2019-11-17
This is not a valid Windows entry, it was an old work around to boot Ubuntu on systems that would only boot Windows.
Boot0001* Windows Boot Manager HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\[COLOR=#ff0000]grubx64.efi[/COLOR])WINDOWS

This should be a valid Windows boot loader, but those systems that boot by description will only use "Windows Boot Manager" entry.
Boot0006* Windows Boot Test HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\Microsoft\Boot\[COLOR=#ff0000]bootmgfw.efi[/COLOR])

This should also be valid but duplicate description of 0001, but the one we want to keep as correct description and file.
Boot0007* Windows Boot Manager HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\Microsoft\Boot\[COLOR=#ff0000]bootmgfw.efi[/COLOR])

This is not a typical UEFI boot, not sure but either BIOS boot or just a place holder. When drive is disconnected, UEFI forgets entry and reverts to this type.
Boot0000 ubuntu VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)

I suggest full clean up of old entries & add a correct Ubuntu entry.
I believe rEFInd uses the fallback or /EFI/Boot/bootx64.efi as its boot loader. Full reinstall of grub puts a copy of shimx64.efi as bootx64.efi. And Windows normally has a copy of its bootmgfw.efi  as a copy when it is first installed.

I would remove 0000,0001, 0003 & 0006
Old Ubuntu, incorrect Windows, and ones with test in description.
 
We want a good Ubuntu, good Windows (0007), refind (0007) and fallback (0005) 

To delete (also in post #23):
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). With Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

Add new Ubuntu UEFI entry:
sudo efibootmgr -c -w -L ubuntu -l "\EFI\ubuntu\shimx64.efi"  -d /dev/sda -p 1
The -d & -p are optional if installing to sda1, as that is default. But if installing to ESP in any other partition or any other drive they are required.

Then post entries you have and see what rEFInd does.

---

### Post by dudekulowski on 2019-11-17
Entries after the cleaning up:

BootCurrent: 0007
Timeout: 1 seconds
BootOrder: 0000,0007,0002,0004
Boot0000* ubuntu	HD(1,GPT,3eb99d51-cc22-47b6-bc8b-96b71e2fb71e,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* UEFI: ST1000DM003-1CH162, Partition 2	PciRoot(0x0)/Pci(0x17,0x0)/Sata(2,65535,0)/HD(2,GPT,b0d051fc-50f0-4da1-8636-e9d3dffdfd50,0x200000,0xb4000)..BO
Boot0004  rEFInd Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0007* UEFI: SanDisk, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(19,0)/HD(1,GPT,c271db03-317d-44ed-aad3-1a7c34d614c7,0x800,0x305f)..BO

---

### Post by dudekulowski on 2019-11-17
rEFInd still shows the exact same entries detailed in post #44

---

### Post by oldfred on 2019-11-17
You are not showing Windows entry? It was 0007.

New Windows UEFI entry - assumes default sda1  
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

I do not really know if rEFInd looks for UEFI entries or folders in ESP?
If folders it should have found both ubuntu at /EFI/ubuntu and Windows at  /EFI/Microsoft in ESP.

---

### Post by dudekulowski on 2019-11-17
Here's what my refind looks like:

[https://i.imgur.com/FU1pi9O.jpg](https://i.imgur.com/FU1pi9O.jpg)

Also, in the bios that new uefi entry (that you mentioned in the above post) got added into the bios as windows boot manager. When I select it, however, the system gives the error ''[COLOR=#000000]Reboot and select proper boot device or insert boot media in selected device and press a key"[/COLOR]

---

### Post by oldfred on 2019-11-17
That should be a good UEFI Windows boot entry. Were you selecting direct from UEFI, or from rEFInd?

Some systems key on description and it must be "Windows Boot Manager". 
Others like Acer want you to set trust, but the Windows entry should always work. Any others need trust. Not sure then how rEFInd works around that.
Every UEFI we have seen always works with the Windows entry, if formatted correctly.

Error is from UEFI, so setting is not UEFI, or UEFI with Secure Boot. Windows should boot with either. 
Often better to have UEFI Secure boot off, but to change "trust" in Acer Secure boot has to be on.

---

