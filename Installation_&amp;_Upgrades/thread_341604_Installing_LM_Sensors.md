---
title: "Installing LM Sensors"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by ejrives on 2007-01-18
Hi all....Im new to  Ubuntu here. For the last few years I have only messed with redhat and decided to change and see what the Debian based OS can do and I have to say that I rather enjoy it . Anyways I am having a heck of a time to get LM sensors installed correctly and below I have pasted the output of what I did and the results that are showing up. I have checked the LM sensors  forums first but was unable to see anyone that was having the same issues as me. I am really at a loss here  and am unsure as to why this isn't working. If there is anymore information needed from me please let me know.Thanks is advance and I hope to hear from someone.

[COLOR="Red"]
erives@VRTDB1:~$ sudo apt-get install lm-sensors[/COLOR]
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  sensord read-edid
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 491kB of archives.
After unpacking 1507kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main lm-sensors 1:2.10.0-7ubuntu3 [491kB
]
Fetched 491kB in 4s (122kB/s)      
Selecting previously deselected package lm-sensors.
(Reading database ... 88277 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a2.10.0-7ubuntu3_i386.deb) ...
Setting up lm-sensors (2.10.0-7ubuntu3) ...

Creating config file /etc/sensors.conf with new version

[COLOR="Red"]erives@VRTDB1:~$ vi mkdev.sh
erives@VRTDB1:~$ chmod  700  mkdev.sh 
chmod: changing permissions of `mkdev.sh': Operation not permitted
erives@VRTDB1:~$ sudo chmod 700  mkdev.sh 
erives@VRTDB1:~$ sudo ./mkdev.s[/COLOR]h 
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
  
[COLOR="Red"]erives@VRTDB1:~$ sudo sensors-detect [/COLOR]
# sensors-detect revision 1.413 (2006/01/19 20:28:00)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
[COLOR="Red"] Do you want to probe now? (YES/no): y[/COLOR]
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 00:1f.3: Intel 82801DB ICH4
Probe succesfully concluded.

We will now try to load each adapter module in turn.
[COLOR="Red"]Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y[/COLOR]
Module loaded succesfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.[COLOR="Red"]
 i2c-dev is not loaded. Do you want to load it now? (YES/no): y[/COLOR]
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: SMBus I801 adapter at 1860
[COLOR="Red"]Do you want to scan it? (YES/no/selectively): y[/COLOR]
Client found at address 0x30
Client found at address 0x50
Probing for `SPD EEPROM'... Success!
    (confidence 8, driver `eeprom')
Probing for `DDC monitor'... Failed!
Probing for `Maxim MAX6900'... Failed!
Client found at address 0x51
Probing for `SPD EEPROM'... Success!
    (confidence 8, driver `eeprom')
Client found at address 0x69

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

[COLOR="Red"]Do you want to scan the ISA bus? (YES/no): y[/COLOR]
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8712F'
  Trying address 0x0290... Failed!
Probing for `ITE IT8705F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.
[COLOR="Red"]
Do you want to scan for Super I/O sensors? (YES/no): y[/COLOR]
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0xea11)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0xea11)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0xea11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `Nat. Semi. PC87591 Super IO'
  Failed! (0xea)
Probing for `Nat. Semi. PC87371 Super IO'
  Failed! (0xea)
Probing for `Nat. Semi. PC97371 Super IO'
  Failed! (0xea)
Probing for `Nat. Semi. PC8739x Super IO'
  Success... (no hardware monitoring capabilities)
Probing for `Nat. Semi. PC8741x Super IO'
  Failed! (0xea)
Probing for `Nat. Semi. PCPC87427 Super IO'
  Failed! (0xea)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (0xea)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
  Failed! (0xea)
Probing for `SMSC 47M14x Super IO Fan Sensors'
  Failed! (0xea)
Probing for `SMSC 47M15x/192/997 Super IO Fan Sensors'
  Failed! (0xea)
Probing for `SMSC 47S42x Super IO Fan Sensors'
  Failed! (0xea)
Probing for `SMSC 47S45x Super IO Fan Sensors'
  Failed! (0xea)
Probing for `SMSC 47M172 Super IO'
  Failed! (0xea)
Probing for `SMSC LPC47B397-NC Super IO'
  Failed! (0xea)
Probing for `SMSC SCH5307-NS Super IO'
  Failed! (0xea)
Probing for `VT1211 Super IO Sensors'
  Failed! (0xea)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0xea)
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0xea)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0xea)
Probing for `Winbond W83687THF Super IO Sensors'
  Failed! (0xea)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0xea)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0xea)
Probing for `Winbond W83L517D Super IO'
  Failed! (0xea)
Probing for `Fintek F71805F/FG Super IO Sensors'
  Failed! (0xea11)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (0xea11)
[COLOR="Red"]
Do you want to scan for secondary Super I/O sensors? (YES/no): y[/COLOR]
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue: 

[COLOR="Red"]Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 1860'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `SPD EEPROM' (confidence: 8)
  * Bus `SMBus I801 adapter at 1860'
    Busdriver `i2c-i801', I2C address 0x51
    Chip `SPD EEPROM' (confidence: 8)[/COLOR]


I will now generate the commands needed to load the I2C modules.

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# I2C chip drivers
eeprom
#----cut here----

[COLOR="Red"]Do you want to add these lines to /etc/modules automatically? (yes/NO)y[/COLOR]
[COLOR="Red"]erives@VRTDB1:~$ sudo /etc/init.d/module-init-tools[/COLOR]
 * Loading manual drivers...                                                    
                                      [ ok ] 
[COLOR="Red"]erives@VRTDB1:~$ sudo sensors -s[/COLOR]
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
erives@VRTDB1:~$

---

### Post by jjross on 2007-01-18
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by ejrives on 2007-01-18
That is nearly identical to the process that I have followed..I just find it odd that there are multiple articles on how to install this correctly with everyones way just slightly different. Any other suggestions???????

---

### Post by jjross on 2007-01-18
I think you really need to run the script  described in the first part of the How To, I have used this process on two different computers and it works great.

---

### Post by ejrives on 2007-01-18
I have ran that as well....One question though.. from the looks of the script I should be able to run that anywhere...right? If you see in the original post you can see what the script  as well...also here is the output from lsmod. I also see that the directories that script created were static...is that correct.??


Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
i915                   21632  2 
drm                    74644  3 i915
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ipv6                  272288  8 
af_packet              24584  4 
eeprom                  8208  0 
i2c_i801                9868  0 
i2c_core               23424  3 i2c_ec,eeprom,i2c_i801
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
lp                     12964  0 
joydev                 11200  0 
tsdev                   9152  0 
ipw2200               115652  0 
pcmcia                 40380  0 
r1000                  17792  0 
ieee80211              35272  1 ipw2200
ieee80211_crypt         7552  1 ieee80211
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
usbhid                 45152  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
serio_raw               8452  0 
yenta_socket           28812  2 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
r8169                  32136  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
psmouse                41352  0 
evdev                  11392  2 
pcspkr                  4352  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
hw_random               7320  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
erives@VRTDB1:~$

---

### Post by jjross on 2007-01-18
Well, you have gone beyond my abilities to offer any help, one question though, does your motherboard support this?  some dont.
Good luck with this and dont give up, there are a lot of really talented people here on the forum and some one will probably be able to help with this

---

### Post by ejrives on 2007-01-19
Thanks for the help I appreciate it. As far as the motherboard goes ;honetly I am not sure what kind it is . I cannot found any info on it at all and according to my devices it is unknown. Does anyone have a panasonic toghbook at all and verified that this is working? Secondly from looking at other forums if you have a mobo that isnt supported the sesors-detect command would tell me that I have a chip that is unsupported..Is that correct as well? Thanks

---

