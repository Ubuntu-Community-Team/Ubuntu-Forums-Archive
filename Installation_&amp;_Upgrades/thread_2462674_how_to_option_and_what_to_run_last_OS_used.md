---
title: "how to option and what to run last OS used?"
date: 2021-05-25
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-05-25
First item in grub menu  
 is  
 * ubuntu
then normal grub options follows.
 
 
 The system** then  executes *ubuntu  **( name / function?) 
( UEFI ?) 
not grub ! 


 which  makes  using saving last working OS in grub configuration
  , in mutiboot system, worthless.
 
 
 Is there a hack for that ?

---

### Post by grahammechanical on 2021-05-25
I do not understand what you are taking about. First of all when the Grub menu appears Grub has already been activated (executed?). The menu is a list of boot options and the first option on the menu is the default boot option. It loads after about 10 seconds. Selecting another boot option does not put that OS option at the top of the Grub boot menu. That is not the way that Grub is designed to work.

If the alternative OS is another Linux distribution we can put that OS at the top of the Grub boot menu by loading into that OS and running

```
sudo update-grub
sudo grub-install /dev/sd?
```

Where the question mark is the drive letter of the drive the alternative OS is installed on. By doing this we are effectively putting the OS we are running from in charge of the Grub menu and that OS becomes the default OS to load.

Are you using some utility that is supposed to put the last used OS at  the top of the Grub boot menu? Or, are you talking about the boot  options of your machine's UEFI settings utility? None of this is clear from your post. If you are dual booting between Windows 10 and Ubuntu you should tell us. 

I am not familiar with UEFI settings as I have a BIOS motherboard. And I do not know of any way to put the last used working OS at the top of the grub configuration except by the method I have explained above. What are you using and what are you expecting it to do?

Regards

---

### Post by oldfred on 2021-05-25
UEFI boots Ubuntu/grub using shimx64.efi. Shim is for Secure boot, but also boots with it off. I have Secure boot off.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for fred:  
BootCurrent: 0018 [/FONT]
[FONT=monospace]QUOTETimeout: 1 seconds 
BootOrder: [COLOR=#ff0000]0018[/COLOR],0002,0005,001F,0020,001A,0021,0022 
Boot0002* focal HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\FOCAL\SHIMX64.EFI) 
Boot0005* focal_a       HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\FOCAL_A\SHI
MX64.EFI) 
[COLOR=#ff0000]Boot0018* ubuntu[/COLOR]        HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File([COLOR=#ff0000]\EFI\UBUNTU\SHI
MX64.EFI[/COLOR])

Then from /EFI/ubuntu/grub.cfg which is a configfile to load the full grub.cfg in your install.
And then you see the full grub menu to boot all installed systems. If only one system, it just default boots it.



[/FONT]
```

---

### Post by anneranch on 2021-05-25
I do not understand what you are taking about.

Next time ask for clarification before you spend your time replying.

---

### Post by anneranch on 2021-05-25
> **oldfred said:**
> UEFI boots Ubuntu/grub using shimx64.efi. Shim is for Secure boot, but also boots with it off. I have Secure boot off.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for fred:  
BootCurrent: 0018 [/FONT]
[FONT=monospace]QUOTETimeout: 1 seconds 
BootOrder: [COLOR=#ff0000]0018[/COLOR],0002,0005,001F,0020,001A,0021,0022 
Boot0002* focal HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\FOCAL\SHIMX64.EFI) 
Boot0005* focal_a       HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\FOCAL_A\SHI
MX64.EFI) 
[COLOR=#ff0000]Boot0018* ubuntu[/COLOR]        HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File([COLOR=#ff0000]\EFI\UBUNTU\SHI
MX64.EFI[/COLOR])

Then from /EFI/ubuntu/grub.cfg which is a configfile to load the full grub.cfg in your install.
And then you see the full grub menu to boot all installed systems. If only one system, it just default boots it.



[/FONT]
```

OK , now tell me how this correlates to "grub" ?

And how do it  tells me "/dev/???" of the actual OS ?
Is this a list of EFI   partitions?  I do not have that many....

And it still does not  answer the question 

how to **option ****efibootmgr to save current OS and reboot to it next time **- as optioned in grub which is bypassed by  "*ubuntu" entry in grub menu. 

Please note 

[B]Boot0000* ubuntu   

and 
[/B]
**[B]* ubuntu  **
[/B]

is the first entry in my grub menu 

as * indicates  - it will get selected next boot  time which puts me back to 
**efibootmgr  which could be  changed to "EFI"  winch does not tell me the device ! **


In short
Ubuntu boot process goes this way 

read firmware (UEFI)  
using efibootmgr  (??) 
select "boot order" default (??) 
*ubuntu   (??) 
which need to be decoded to find the device...

and according to UEFI  doc when *ubuntu fails to load OS grub ( !)  will go to next item on grub menu list.
BUT UEFI  firmware itself has SAME  behavior - if *ubuntu fails it gores to next UEFI option...

That seem to be to redundant and really hard to verify without screwing things up. 


In short 
**at present I have ONE really working OS and I like to be able to load  it automatically on power up AND on "reboot". **


qe@qe-desktop:~$ sudo efibootmgr -v 
[sudo] password for qe:  
BootCurrent: 0000 
Timeout: 3 seconds 
BootOrder: 0000,0003,0004,0005,0006,0007,0008,0009,0002 
Boot0000* ubuntu    HD(1,GPT,7149cebc-a872-4fa7-bf45-e75ea1672895,0xffff,0xefff1)/File(\EFI\ubuntu\shimx64.efi) 
Boot0002  USB     BBS(USB,,0x0)..GO..NO........].e.M. .B.a.y. .R.e.a.d.e.r. .1...0.0....................A...................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO..NO........e.e.M. .B.a.y. .R.e.a.d.e.r. .1...0.1....................A...........................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO..NO........e.e.M. .B.a.y. .R.e.a.d.e.r. .1...0.2....................A...........................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO..NO........e.e.M. .B.a.y. .R.e.a.d.e.r. .1...0.3....................A...........................................$..Gd-.;.A..MQ..L.9.2.0.3.1.1.1........BO..NO........u.S.e.a.g.a.t.e. .B.U.P. .U.l.t.r.a. .T.o.u.c.h. .0.0.0.4....................A.........................................6..Gd-.;.A..MQ..L.0.0.0.0.0.0.0.0.N.A.B.1.3.3.H.H........BO..NO{.......Y.S.e.a.g.a.t.e....................A.............................&..Gd-.;.A..MQ..L.N.A.8.3.3.B.D.C........BO 
Boot0003* UEFI: Seagate BUP Ultra Touch 0004    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/USB(4,0)/USB(6,0)/HD(10,GPT,66537b42-4255-4eef-886f-7f0d54024f1f,0x803c8000,0x39fbc000)..BO 
Boot0004* UEFI: Seagate BUP Ultra Touch 0004    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/USB(4,0)/USB(6,0)/HD(12,GPT,eaa6938b-2fda-41b8-a307-6eaa95e594e4,0xba384000,0x3a98000)..BO 
Boot0005* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(12,GPT,edc8d0de-ae79-422d-80df-25f487993547,0x6dd9f800,0xd206800)..BO 
Boot0006* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(15,GPT,131a1c2e-0252-4fee-ba59-61731b3e5837,0x80852000,0xc350000)..BO 
Boot0007* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(16,GPT,dd77e4d5-c8fb-43a8-9e5f-439556ee8ee4,0x8cba2000,0x7b64000)..BO 
Boot0008* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(17,GPT,daeea54e-8f34-4f47-b6a8-74e5043e9e24,0x94706000,0x4e2f800)..BO 
Boot0009* UEFI: Seagate    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(19,GPT,ad233d75-450e-424f-99d4-7347b20efd49,0xaba2d800,0x3d1f2800)..BO 
qe@qe-desktop:~$

---

### Post by oldfred on 2021-05-25
You show UEFI boot of 0000 as first option. And it boots using 7149cebc-a872-4fa7-bf45-e75ea1672895 as GUID/partUUID to find an ESP - efi system partition. It uses shimx64.efi which is part of grub boot loader for Secure boot whether Secure boot is on or not.

You can see which partition is the ESP being used by looking at the partUUID from this.
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"


And which install is the install grub UEFI is  booting, this is only 3 lines showing UUID & drive,partition of the install you are booting:
cat /boot/efi/EFI/ubuntu/grub.cfg

Then grub in your default install will add other operating systems to its menu. 

All that should be automatic.
But some vendors like HP, Sony, do not recognize efibootmgr boot order changes and change boot order back to Windows.
The only way to change boot order with those systems is to go into UEFI menu and on boot tab change boot order. Some also need UEFI update for it to work.

If grub is not booting Ubuntu by default that is another issue with your install. If you get grub menu, it is booting, but then have other issues like missing nVidia driver, file corruption or other issues that have to be investigated.

---

### Post by anneranch on 2021-05-25
> **grahammechanical said:**
> I do not understand what you are taking about. First of all when the Grub menu appears Grub has already been activated (executed?). The menu is a list of boot options and the first option on the menu is the default boot option. It loads after about 10 seconds. Selecting another boot option does not put that OS option at the top of the Grub boot menu. That is not the way that Grub is designed to work.

If the alternative OS is another Linux distribution we can put that OS at the top of the Grub boot menu by loading into that OS and running

```
sudo update-grub
sudo grub-install /dev/sd?
```

Where the question mark is the drive letter of the drive the alternative OS is installed on. By doing this we are effectively putting the OS we are running from in charge of the Grub menu and that OS becomes the default OS to load.

Are you using some utility that is supposed to put the last used OS at  the top of the Grub boot menu? Or, are you talking about the boot  options of your machine's UEFI settings utility? None of this is clear from your post. If you are dual booting between Windows 10 and Ubuntu you should tell us. 

I am not familiar with UEFI settings as I have a BIOS motherboard. And I do not know of any way to put the last used working OS at the top of the grub configuration except by the method I have explained above. What are you using and what are you expecting it to do?

Regards

Doing 

sudo grub-install /dev/sdf7 



removed majority of entries in  my grub menu 

I run grub *ubuntu default few times as a test.
Always loaded sdf7.
Problem solved/

I did not pursue this any further - my main objective is not to monkey with OS , I need to write code. 
I suspect  the non working  OS were removed , I'll know next time I run update-grub.
Thanks

---

### Post by ubfan1 on 2021-05-25
Don't confuse the EFI boot menu with the grub menu.  EFI boots a bootloader (grub, shim, windows/bootmgfw, etc. from its nvram) or a device with a default bootloader (no nvram needed). the "ubuntu" entry in both are just titles, they bear no relationship to each other.  From the grub menu, type "E" to edit, (instruction at bottom of page) and the entire boot paragraph will appear, using meaningful UUIDs and partition numbers (they match output of blkid).  the efibootmgr disk identification is a bit more arcane, te HD(2,GPT might be sdb, but the non-UUID/non-PARTID is buried in gparts' detailed partition information="Partition unique GUID".

Grub has the capability of selecting a "saved" entry to boot.  Rather than reordering the /etc/grub.d files which generate the grub.cfg, you can set the /etc/default/grub variable GRUB_DEFAULT to "saved", then in /boot/grub/grubenv, set the saved_entry=3  or whatever number on the initial menu (not the submenus).  I use that on one machine to select Windows as the default OS to boot.  
There is another variable, GRUB_SAVEDEFAULT, (used in conjunction with GRUB_DEFAULT) which if set to "true" might be just what you want, the last grub selection is written back out to the grubenv file, and used upon reboot.  I've never done that, see the details from the command: info -f grub -n 'Simple configuration'

If your machine vendor does not follow the UEFI standard, and resets a grub/shim default selection back to a Windows boot, you can bypass that by making a device boot the default -- grub-install puts shim/grub into the default /EFI/Boot/bootx64.efi location, and using that usually avoids the vendor resets.

---

