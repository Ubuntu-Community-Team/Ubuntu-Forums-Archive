---
title: "Big upgrade problem"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by binbash on 2006-09-29
hi all , 

here is my story.Last night ,cos of my fault ,i deleted my 3 years old gentoo system(rm -rf s.ucks : )) )I hav problems with dvd writer (hardware problem) and i installed kubuntu (hoary)..Everything was fine till upgrading to dapper..Now latest kernel is broken (Now Im using the kernel whick comes with hoary.2.6.12) but wireless , sound card are broken , there are lots of problems.i tried to install a new kernel but on system start that gives fatal error occured bla bla too.


I hav to fix the wireless cos its 50x faster than this.


deneme@ubuntu:~$ sudo modprobe ipw2200 
deneme@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.       >>This is what m usin now

sit0      no wireless extensions.

Soundcard : 

root@ubuntu:/home/deneme# /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'... 

lsmod : 

```

ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
ipv6                  217408  6
snd_pcm_oss            46368  0
snd_pcm                78344  1 snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_mixer_oss          16128  1 snd_pcm_oss
snd                    48644  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9184  1 snd
agpgart                32328  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
ppdev                   9092  0
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
rtc                    11832  0
pcmcia                 24584  2
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
af_packet              20232  2
dm_mod                 50364  1
md                     40656  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  1 sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  3 ppdev,parport_pc,lp
ext3                  116104  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  3
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
ata_piix                9476  0
ahci                   11268  4
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  5 sr_mod,sbp2,sd_mod,ahci,libata
piix                    9476  1
ide_core              125268  3 ide_cd,ide_generic,piix
unix                   24624  331
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```


I dont want to compile the kernel , and i am new to ubuntu (i can only install kubuntu cos its the only OS cd i have :D )

---

