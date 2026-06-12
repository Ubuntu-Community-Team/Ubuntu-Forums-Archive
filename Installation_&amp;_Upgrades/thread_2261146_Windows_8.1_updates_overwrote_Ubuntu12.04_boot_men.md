---
title: "Windows 8.1 updates overwrote Ubuntu12.04 boot menu"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by Rich27 on 2015-01-16
Hi,

I tried to use install disk to run boot repair with it " the current session is in legacy mode..."

running email option

[http://paste.ubuntu.com/9763584](http://paste.ubuntu.com/9763584)

any ideas?

thanks
Rich

---

### Post by oldfred on 2015-01-16
Since Windows is in UEFI boot, you should only install and boot in UEFI mode.

It does look like you updated Ubuntu to boot in Legacy mode. Since UEFI and BIOS boot are not compatible, you can only dual boot from UEFI menu, or perhaps one time boot key. Some systems require you to manually turn on/off UEFI/BIOS boot settings in UEFI to match how you want to boot. Others will let you use one time boot key.

You cannot dual boot from grub menu unless other install(s) are in same boot mode either both UEFI or both BIOS. And Windows only boots from gpt partitioned drives with UEFI.

---

### Post by Rich27 on 2015-01-19
Thanks for the reply.

My fear is trashing the already installed U12.04. I will read your suggestions and try again.
Thanks
Rich27

---

### Post by oldfred on 2015-01-19
If hardware is UEFI and drive is gpt partitioned, Boot-Repair can convert a BIOS install to UEFI or vice-versa. It really is just what version of grub you have installed. grub-pc is for BIOS and grub-efi-amd64 is for UEFI.

---

### Post by Rich27 on 2015-01-23
oldFred,

I am getting closer.

Now I have to use BIOS to select to boot either win8 or Ubuntu 12.04. What is needed to clean up to get grub menu to choose win8 or Ubuntu. Would like to get all straightened out, before I upgrade to 14.04.

See [http://paste.ubuntu.com/9827302/](http://paste.ubuntu.com/9827302/)

Your help is appreciated.
Rich

---

### Post by oldfred on 2015-01-23
It looks like Ubuntu is now in UEFI boot mode.
Have you run this to see if it adds a grub menu entry for Windows?
sudo update-grub

Does ubuntu entry in UEFI work ok? Some vendors modify UEFI to only boot "Windows", so we have to do work arounds.

---

### Post by Rich27 on 2015-01-23
Rebooting after running boot-repair it fails to boot, I dont remember what exactly it said. I'm at work and this is my home machine.

However, choosing the boot device from BIOS, I have ubuntu (doesn't boot), Windows (does boot if chosen into windows) and lastly Ubuntu (again).

If I choose the Ubuntu (last choice) it does boot ubuntu 12.04 but windows wasn't part of a boot loader choice like it was prior to win8.1 upgrade.

I don't know why the 1st ubuntu choice in BIOS boot device menu doesn't work.

What is needed to clean up the boot device choices?

---

### Post by oldfred on 2015-01-23
If booting in UEFI mode:

 modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by Rich27 on 2015-01-24
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Adding boot menu entry for EFI firmware configuration
done

Doesnt look like it found and added windows.
 
modprobe efivars

SX2110G:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0002
Boot0000  Windows Boot Manager    HD(2,c8800,96000,d0c59313-8f1d-405f-9831-1682cbcfe519)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* ubuntu    HD(2,c8800,96000,d0c59313-8f1d-405f-9831-1682cbcfe519)File(\EFI\ubuntu\shimx64.efi)
Boot0002  ubuntu    HD(2,c8800,96000,d0c59313-8f1d-405f-9831-1682cbcfe519)File(\EFI\Ubuntu\grubx64.efi)

SX2110G:~$ ls /sys/firmware/efi/vars
AcerBootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c
AcerSystemHddHandle-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
AcpiGlobalVariable-af9ffd67-ec10-488a-9dfc-6cbf5ee22c2e
AfterFlashEnterUSBKey-55550001-0123-4567-89ab-cdef01234567
AmdAcpiVar-79941ecd-ed36-49d0-8124-e4c31ac75cd4
AmiAgesaSetup-840f6ac6-6f42-11d4-bce7-0080c73c8881
AMITSESetup-c811fa38-42c8-4579-a9bb-60e94eddfb34
Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootOptionSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c
BrandNum-4feffaa5-39be-4da1-a7e4-1656dd3e1cfb
CMOSClearCanNotBootToDevice-55550002-0123-4567-89ab-cdef01234567
ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
CpuS3Resume-30b98b95-dfa3-4501-a3ce-e38c186384a0
db-d719b2cb-3d3a-4596-a3bc-dad00e67656f
dbx-d719b2cb-3d3a-4596-a3bc-dad00e67656f
DefaultUefiDevOrder-0c923ca9-df73-4ac8-b6d2-98ddc30d99fc
del_var
DiskInfoByPort-8be4df61-93ca-11d2-aa0d-00e098032b8c
DmiArray-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar010001040-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar010001050-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar010001070-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar010001080-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar0100011a0-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar020002040-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar020002050-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar020002070-4b3082a3-80c6-4d7e-9cd0-583917265df1
DmiVar030003040-4b3082a3-80c6-4d7e-9cd0-583917265df1
DriverHealthCount-7459a7d4-6533-4480-bba7-79e25a4443c9
DriverHlthEnable-0885f288-418c-4be1-a6af-8bad61da08fe
EfiTime-9d0da369-540b-46f8-85a0-2b5f2c301e15
ErrOut-8be4df61-93ca-11d2-aa0d-00e098032b8c
ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
FixedBoot-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
FixedBootGroup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
FPDT_Variable-8be4df61-93ca-11d2-aa0d-00e098032b8c
FUB-1dd54778-f3ea-11e0-af9a-84914824019b
GNVS_PTR-0a602c5b-05a0-40c4-9181-edcd891d0013
HddGroupDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
HiiDB-1b838190-4625-4ead-abc9-cd5e6af18fe0
HobRomImage-dde1bc72-d45e-4209-ab85-14462d2f5074
KEK-8be4df61-93ca-11d2-aa0d-00e098032b8c
Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c
LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c
MemCeil.-8be4df61-93ca-11d2-aa0d-00e098032b8c
MemoryS3SaveNv-b1cfc482-4cb2-4cee-9b00-ce2579ec7186
MemoryS3SaveVol-0a51b41d-de21-43fe-be27-d6dbc9efd104
MemoryS3SaveVolLength-0a51b41d-de21-43fe-be27-d6dbc9efd104
MemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa
MonotonicCounter-8be4df61-93ca-11d2-aa0d-00e098032b8c
NBMemoryLength-490216c0-076a-44d3-a536-ace05c90e386
NB SSID-3470d772-49ba-4c28-a559-3f4dad8361ef
NetGroupDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
NetworkStackVar-d1405d16-7afc-4695-bb12-41459d3695a2
new_var
OAadder-8be4df61-93ca-11d2-aa0d-00e098032b8c
OddGroupDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
OsIndications-8be4df61-93ca-11d2-aa0d-00e098032b8c
OsIndicationsSupported-8be4df61-93ca-11d2-aa0d-00e098032b8c
PBRDevicePath-8be4df61-93ca-11d2-aa0d-00e098032b8c
PK-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c
PNP0501_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031
PNP0501_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031
PNP0510_0_NV-560bf58a-1e0d-4d7e-953f-2980a261e031
PNP0510_0_VV-560bf58a-1e0d-4d7e-953f-2980a261e031
PreviousMemoryTypeInformation-4c19049f-4137-4dd3-9c10-8b97a83ffdfa
PS2KB-3fcd4dc6-9fe4-40f4-98fe-b9b003caa010
RemGroupDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
RSCInfoAddresss-8be4df61-93ca-11d2-aa0d-00e098032b8c
S3SS-4bafc2b4-02dc-4104-b236-d6f1b98d9e84
SbNvramVar-393c4833-402f-4bd5-bf5a-1f5cd8681444
SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c
Setup-80e1202e-2697-4264-9cc9-80762c3e5863
SetupCpuFeatures-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
Setup-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
SetupMode-8be4df61-93ca-11d2-aa0d-00e098032b8c
SignatureSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c
SpdBypassData-8be4df61-93ca-11d2-aa0d-00e098032b8c
SpdBypassSerial-8be4df61-93ca-11d2-aa0d-00e098032b8c
StdDefaults-4599d26f-1a11-49b8-b91f-858745cff824
TcgInternalSyncFlag-f3ed95df-828e-41c7-bca0-16c41965a634
TimeData-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c
UmaSize-8be4df61-93ca-11d2-aa0d-00e098032b8c
UsbMassDevNum-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
UsbMassDevValid-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
USB_POINT-8be4df61-93ca-11d2-aa0d-00e098032b8c
UsbSupport-ec87d643-eba4-4bb5-a1e5-3f3e36b20da9
VgaMode-8be4df61-93ca-11d2-aa0d-00e098032b8c

---

### Post by oldfred on 2015-01-24
Is Windows hibernated or needing chkdsk?
Script usually shows those as issues. But run chkdsk and double check that fast boot or always on hibernation is off.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
powercfg /h off

    
Or you may just need the newer grub with 14.04 to work with the Windows 8.1 version?
What brand/model computer?

---

