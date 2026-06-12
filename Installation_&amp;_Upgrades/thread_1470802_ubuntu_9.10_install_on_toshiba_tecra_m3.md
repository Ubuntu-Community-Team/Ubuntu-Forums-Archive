---
title: "ubuntu 9.10 install on toshiba tecra m3"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2010-05-03
hello all,

i have a toshiba tecra m3 that i have recently built into a multi boot system that originally had xp on and now it has a dual boot grub to boot to ubuntu if required, basically my end game is to have a triple boot system to allow me to run solaris too. but thats the next stage.
at present i cant get the wifi working on the m3 even though i have the wifi switched on and enabled i have entered the ssid and wep key but no avail any ideas?
i will continue to look into it, if there is any known issues with it please let me know

thanks

---

### Post by petebarchetta on 2010-05-03
Does the wireless have to be enabled during install for it to be seen? Just trying to rule out the obvious before I have to get down to command line. I have been used to the older releases and this one has thrown me. Any suggestions would be great, it's gotta be something simple I'm missing

thanks all

---

### Post by petebarchetta on 2010-05-05
eth0 is now operational, hence posting this, but eth1 (the ipw2200) wireless stack is still on the blink. i have done a lsmod and it is listed:
 lsmod
Module                  Size  Used by
usb_storage            52544  0 
bridge                 47952  0 
stp                     2272  1 bridge
binfmt_misc             8356  1 
bnep                   12060  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 36808  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
yenta_socket           24200  1 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         11644  1 yenta_socket
sdhci_pci               7100  0 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_infineon            8200  0 
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci                  17472  1 sdhci_pci
ppdev                   6688  0 
soundcore               7264  1 snd
joydev                 10272  0 
led_class               4096  1 sdhci
tpm                    15680  1 tpm_infineon
iptable_filter          3100  0 
ipw2200               140292  0 
parport_pc             31940  1 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
btusb                  11856  0 
libipw                 43148  1 ipw2200
lib80211                6432  2 ipw2200,libipw
psmouse                56180  0 
serio_raw               5280  0 
tpm_bios                6268  1 tpm
toshiba_acpi           10744  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 
video                  19380  0 
output                  2780  1 video
intel_agp              27484  0 
agpgart                34988  1 intel_agp

but there is no module alongside it suggesting its not active, any ideas guys?

---

### Post by petebarchetta on 2010-06-05
Issue now resolved, installed lucid lynx on the m3 and all modules running a'ok. It seems Lts versions are more compatible with the tecra series than the interim releases, setup for triple boot xp/lucid /solaris 10

I now have a fleet of 3 ubuntu machines:
tecra 550cdt - dapper 6.06 
tecra 8000 - hardy 8.04 
tecra m3 - lucid 10.04
tech ain't dead yet!!!

---

