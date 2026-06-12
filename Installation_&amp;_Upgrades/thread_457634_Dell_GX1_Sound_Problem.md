---
title: "Dell GX1 Sound Problem"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by shawnwheeler on 2007-05-28
I have a GX1 that I just installed umbuntu on.  The sound card is not recognized.  When I click on the speaker it tells me I need a gstreaming plugin.  What do I find this and how do I know which one I should use?

Thanks in advance

Shawn

---

### Post by handydan918 on 2007-05-29
Open a terminal and type "lspci" (without the quotes). Also type "lsmod". Copy and paste the output to this forum and someone might be able to help you. 
"lspci gives a list of the PCI devices. lsmod gives a list of the loaded modules, including drivers.This info is needed before any diagnosis can be done.

---

### Post by tnseditor on 2007-05-29
Try this.... I just did this yesturday on a GX1

Run terminal: Click: Applications/Accessories/Terminal
In terminal type:

    sudo gedit /etc/modules

enter your password

append line to end of modules file:

    snd-cs4236

save and reboot system.

---

### Post by shawnwheeler on 2007-05-29
This is what the two commands gave me.  The other post didn't show me what you told me I am looking for.  I am new to this so I could have done it wrong.  

Thanks in advance. 

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)
shawn@shawn-desktop:~$ 
________________________________________________________________________
LSMOD
shawn@shawn-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
apm                    22752  1 
ppdev                  10116  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
snd_opl3_lib           11520  0 
snd_hwdep               9988  1 snd_opl3_lib
snd_cs4231_lib         26112  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_cs4231_lib,snd_pcm_oss
snd_page_alloc         10888  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart         9472  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device          9100  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ns558                   5760  0 
gameport               16520  2 ns558
parport_pc             36388  1 
soundcore               8672  1 snd
pcspkr                  4224  0 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
serio_raw               7940  0 
i2c_piix4               9740  0 
intel_agp              25244  1 
i2c_core               22656  1 i2c_piix4
agpgart                35400  1 intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  1 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
floppy                 59524  0 
3c59x                  46632  0 
mii                     6528  1 3c59x
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
piix                   11140  0 [permanent]
generic                 5124  0 [permanent]
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
shawn@shawn-desktop:~$

---

### Post by tnseditor on 2007-05-29
Please let me know how far you can go with this.  Run terminal: Click: Applications/Accessories/Terminal
In terminal type:

    sudo gedit /etc/modules

Can you open the terminal?  If you copy and pasted the above command, does anything show up?  
Does your computer have Crystal audio?

---

### Post by tnseditor on 2007-05-29
Here's something else you may want to try if the above suggestion doesn't work:

*This is from another thread

How to activate Crystal CS4236B Audio on Optiplex GX1:

> At the Desktop, open Applications> Accessories> Terminal
> At the flashing cursor, type: sudo gedit
> Type your system password
> In gedit, click on the "Open" icon
> Double-click "File System" from the lefthand sidebar
> Double-click the "etc" folder
> Scroll down past the folders to the "modules" file, and open it
> On the line after the last entry, type:

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

> Click the "Save" icon, and Quit the program. Reboot.
> Go to System> Preferences> Sound
> "CS4236B" should appear in the Default sound card field
> Make sure "Enable sound server startup" is unchecked
> Go to Applications> Sound and Video> Volume Control
> Make sure the volume level is up in both Playback and Capture
> Open CD Player or Sound Juicer and test for audio from a music cd

---

### Post by shawnwheeler on 2007-05-29
After some messing around I got the sound to work.    The command  snd-cs4236 made the sound work but it took the screen resolution back to 800 x 600.    So I moved the command to a new location.   This is the way it currently looks.

fuse
snd-cs4236
lp

I have sound and the screen resolution is back to 1024 x 768.   I should start a new post but I will toss it out here anyway.   Without the command, I had a nice looking 800 x 600 at 61 htz display.  But it wouldn't go any higher.  Now I have 1024 x 768 at 85 htz.  I know 85 is to high and would like to drop it.  It doens't give me the option. 

Thanks again for you help.

---

