---
title: "No sound but card installed ?!?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Useruntu on 2006-06-02
I just upgraded from 5.10 to 6.06 and audio doesn't work. I'm able to reproduce files (equalizer works, too) but there is no sound. I controlled volume and modules. Everything seems ok. Where is the problem?
Thanks

---

### Post by John.Michael.Kane on 2006-06-02
Your going to have to list your Machince spec's including soundcard is it onboard or discreet.

---

### Post by Useruntu on 2006-06-03
The sound card is on-board, the module is snd-via82xx and it is loaded. It works well till Breezy. I don't know if it can help but I noticed that if I open gnome-alsamixer the name of the mixer is "Analog Devices AD1980". I'm not sure but the name of the mixer before dapper was different, maybe this is the problem?
Thanks

> 

@ubuntu:~$ cat /proc/asound/cards
0 [V8237          ]: VIA8237 - VIA 8237
                     VIA 8237 with AD1980 at 0xc800, irq 201



@ubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
  




---

### Post by sefs on 2006-06-03
I have the same problem.

I can see via lspci and lsmod that its there.

It was working intially then it suddenly stopped working right after I followed some instructions on how to get firestarter to run under dapper.  I tried to undo those steps but no cigar.

However if i were to log in as one of the other users on the machine ... the sound plays perfectly...just not on the main ubuntu account.

If i double click on the speaker which has a red x next too it...i get a no volume control gstreamer plugins... error message.

I disabled the card in the bios, and installed a sblive card i had laying around in an extra pci slot.

Again the card is recognised but no sound.

Any help is appreciated to get this sorted out.

Specs K8MM-V mother board from MSI with a via vt8237 (AC97) sound card

lspci :
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890  South]
0000:00:09.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:09.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a )
0000:00:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev  0a)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Co ntroller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/ K8T890 South]
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Mod el 64/Model 64 Pro] (rev 15)

```

lsmod:
```

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
af_packet              22920  0
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ipv6                  265600  15
ndiswrapper           183952  0
dm_mod                 58936  1
md_mod                 72532  0
sb_lib                 48452  0
uart401                11716  1 sb_lib
sound                  80940  2 sb_lib,uart401
lp                     11844  0
rsrc_nonstatic         13440  0
pcmcia_core            42640  1 rsrc_nonstatic
tsdev                   8000  0
floppy                 62148  0
pcspkr                  2180  0
serio_raw               7300  0
psmouse                36228  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
nvidia               3921884  12
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rtc                    13492  0
snd_emu10k1           117156  1 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         92704  1 snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
via_rhine              23940  0
i2c_viapro              8980  0
mii                     5888  1 via_rhine
i2c_core               21904  2 i2c_acpi_ec,i2c_viapro
snd_pcm                89864  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10632  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
snd                    55268  13 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
emu10k1_gp              3840  0
soundcore              10208  3 sb_lib,sound,snd
gameport               15496  2 emu10k1_gp
amd64_agp              12356  1
agpgart                34888  2 nvidia,amd64_agp
evdev                   9856  1
ext3                  135688  2
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
ehci_hcd               32008  0
ohci_hcd               21892  0
usbcore               129668  5 ndiswrapper,uhci_hcd,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  5
via82cxxx               9988  0 [permanent]
generic                 5124  0
sata_via                8964  0
libata                 78992  1 sata_via
scsi_mod              139496  1 libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

---

### Post by rejser on 2006-06-03
Same here, after upgrade it won't work anymore. Had the same after upgrade to breezy from hoary. There is a breezy thread that maybe holds the answer somewhere. I will continue to look

---

### Post by Useruntu on 2006-06-03
[QUOTE=sefs]
However if i were to log in as one of the other users on the machine ... the sound plays perfectly...just not on the main ubuntu account.
[/QUOTE]

On my PC doesn't work with any account :( 
Did you try to check the permission of the main account? The user has to be in audio group.
Bye

---

### Post by mpierce on 2006-06-03
First thing, I'd do is to check /etc/group and make sure I'm part of the audio group. Same thing happened to me while upgrading my wife's machine. She wasn't part of the group anymore. Log out & back in.

---

### Post by Useruntu on 2006-06-03
[QUOTE=mpierce]First thing, I'd do is to check /etc/group and make sure I'm part of the audio group. Same thing happened to me while upgrading my wife's machine. She wasn't part of the group anymore. Log out & back in.[/QUOTE]

In my case I'm in audio group, but the thing really strange is that I get no errors ?!? Every programm seems to work: xmms, amarok, etc... play the songs, equalizer works but there is no sound. It seems that the sound is directed to the wrong place but where?
I'm googling but without luck :( Another hint?
Thanks to all

---

### Post by hippyjim on 2006-06-03
Me too - Amarok even gives me its pretty equalisers , but nothing comes out of the speakers. I have the sound engine on autodetect - I'm gonna try different ones and if I get it working i'll let you know.

---

### Post by hippyjim on 2006-06-03
Ok, so now I can't get Amarok to open at all. I even put all my settings back to how they were - and Amarok tries to open but just dies. Tried to open it in a console but I didn't even get an error message. In the end I gave up and just used CTRL-C to quit it.

God help me if my wife finds out she can't play her hard rockin' sounds!

---

### Post by oimon on 2006-06-03
i had a similar problem which was simply that the master volume channel was turned off by the dapper upgrade.
Un-mute the master channel using the "m" key in alsamixer.
More details here
[http://ubuntuforums.org/showthread.php?p=1086230#post1086230](http://ubuntuforums.org/showthread.php?p=1086230#post1086230)

---

### Post by sefs on 2006-06-03
Useruntu & mpierce you were bang on the ball ... I went into the user manager applet and look at the priviliages of the main account and all of them were unchecked except one.  And I know is that I didnt do it.  So somehow they came unset.  I wonder how. 

Thanks fellas!!!

---

### Post by Useruntu on 2006-06-04
[QUOTE=Useruntu]I just upgraded from 5.10 to 6.06 and audio doesn't work. I'm able to reproduce files (equalizer works, too) but there is no sound. I controlled volume and modules. Everything seems ok. Where is the problem?
Thanks[/QUOTE]

Don't tell me I have to reinstall Dapper!!!](*,)  Does anybody know to solve the problem above? :-k 
Thanks :D

---

### Post by Useruntu on 2006-06-04
[QUOTE=Useruntu]Don't tell me I have to reinstall Dapper!!!](*,)  Does anybody know to solve the problem above? :-k 
Thanks :D[/QUOTE]

I installed another soundcard in the system and it works. But why the other doesn't? Is there a specific problem with the via on-board soundcard?
Someone know a good tutorial that explain which file to check in case of audio problems?
Cheers

---

### Post by JcZndeR on 2006-07-03
ahh....!! i have the exact same problem as Useruntu, altho i havent yet tried another sound card
i have only had ubuntu 4 a few weeks and ignored the problem for a while cuz i failed in finding a solution.. but i can only live without sound for so long..
has anyone found a solution??
when i play files they seem 2 go perfectly well except 4 the fact that when i turn on my speakers nothing comes out..
the volume meter shows nothin as well.. so it has 2 b a software problem. i already checked the speakers anyways
no other forums seemed 2 have a solution 4 this either...
so far this is the most annoying problem wit ubuntu, next 2 the fact that i haven't yet successfully updated my kernel..

a fix, anyone?? :(

---

