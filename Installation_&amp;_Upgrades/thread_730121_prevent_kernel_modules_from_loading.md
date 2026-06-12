---
title: "prevent kernel modules from loading"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-03-20
[http://ubuntuforums.org/showthread.php?t=31031](http://ubuntuforums.org/showthread.php?t=31031)
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)
[http://ubuntuforums.org/showthread.php?t=44071](http://ubuntuforums.org/showthread.php?t=44071)

None of the above worked.

As can be seen below, some modules are not required. I can remove them with rmmod however they are loaded again at boot. For example, I have disabled the parallel port in the BIOS yet the system wishes to insist on loading the module.

Ideas please?

Thanks


[/code]
ppdev                  14088  0
parport_pc             41640  0
lp                     17736  0
parport                44684  3 ppdev,parport_pc,lp
button                 12192  0
ac                     10376  0
battery                15496  0
ipv6                  286048  10
snd_hda_intel          23708  0
snd_hda_codec         184192  1 snd_hda_intel
snd_pcm_oss            48672  0
snd_mixer_oss          21888  1 snd_pcm_oss
snd_pcm                89096  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              29192  1 snd_pcm
snd                    65256  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              15392  1 snd
snd_page_alloc         15504  2 snd_hda_intel,snd_pcm
ext2                   70416  2
mbcache                14216  1 ext2
dm_snapshot            20664  0
dm_mirror              25216  0
dm_mod                 62800  2 dm_snapshot,dm_mirror
loop                   20112  0
psmouse                44432  0
floppy                 67112  0
pcspkr                  7808  0
tsdev                  13056  0
xfs                   485192  3
ide_generic             5760  0 [permanent]
usbhid                 45088  0
ide_cd                 45088  0
cdrom                  40488  1 ide_cd
ide_disk               20608  7
8139too                33408  0
via82cxxx              13444  0 [permanent]
8139cp                 29440  0
mii                    10368  2 8139too,8139cp
generic                10500  0 [permanent]
ide_core              147584  5 ide_generic,ide_cd,ide_disk,via82cxxx,generic
ehci_hcd               36104  0
uhci_hcd               28696  0
thermal                20240  0
processor              38248  1 thermal
fan                     9864  0
[/code]

---

### Post by dannyboy79 on 2008-03-20
you put them in the /etc/modprobe.d/blacklist file. There should already be some modules in there so format the new modules you don't want loaded at startup the same way.

ie
blacklist eepro100

good luck

PS I didn't bother checking out the links so if this is something you have already tried I apologize for wasting your time.

---

### Post by keratos on 2008-03-20
sorry but this does not work. 

one of the above links also refer to this proposal and as stated they (the "solutions" are ineffective. the modules still load at boot despite the fact they are not needed and I can "rmmod" them after boot with no problem or warning.

anyone else please, thank you.

---

### Post by keratos on 2008-03-20
bump ..

just read your "P.S" note.

you didnt waste my time...all responses and suggestions kindly received.

---

