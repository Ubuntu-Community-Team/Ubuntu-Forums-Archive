---
title: "Windows Vista kills sound in Gutsy"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by AngryAnimal on 2007-12-18
Fujitsu Siemens Laptop Esprimo v5505 Intel HDA Conexant Venice CX20549 ICH8 82801
Ubuntu Gutsy 7.10

```
$cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20549 (Venice)
```

I have been searching the forums to and get my sound card working for a couple of months .  I have read that sometimes the card works and othertimes it stops for no apparent reason?

I have experience the broken card, the working card, the headphone jack working and not working.  A complete missing sound card.  Anyway without writing a novel I eventually fixed my problems with various websites and links.

1) Perform a clean install from Live CD

2) Update all security updates

3) Visit Alsa-Project 
[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")
Download alsa-driver-1.0.15  alsa-lib-1.0.15  alsa-utils-1.0.15

4) Read the instructions on the below link
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

5) Use the above instructions but when installing the driver use

```
sudo ./configure --with-debug=basic
```
NOTE This will take a little longer

6) When you modify your modprobe

 ```
sudo nano /etc/modprobe.d/alsa-base
```

Make sure you add both these lines 
(my model should be laptop based on my above specs)

# options snd-hda-intel model=laptop
 options snd-hda-intel model=test

7) Reboot 
when using model=test there will be no sound at first  (this is normal)

8') Open a terminal and use
 ```
alsamixer
``` to unmute the external amp, adjust the PCM/Master sliders to get volume; one of the nodes also let me change the headphone sound but as this is in test mode the jack doesn't disable the laptop speakers

9) Once you've proven you have sound :-\"
Modify your modprobe but this time in an attempt for permanent fix

 ```
sudo nano /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=laptop
# options snd-hda-intel model=test

10) Reboot

This time you should have sound and an almighty gasp that you can use Ubuntu instead of Vista forever.:guitar:

10) Now boot up Vista, Logout in disgust with this vicious creation:evil:

11) Log back into Unbuntu - no sound ](*,)

12) Repeat 6,7&8 and then 9)

13) [-X NEVER EVER use Vista again.[-X



More Ramblings:

This might work for other laptops but the final model in the modprobe must be correct.

If like me you you did the normal sudo ./configure --with-cards=hda-intel and all was good and then it broke i.e. Making the AnimalAngry you could use to fix probably without reinstall on Ubuntu.

Vista seems to sought itself everytime: Perhaps the Alsa boys ought do the same.
(I'll be writing to them in due course)

---

### Post by gogan on 2008-01-10
This doesn't work for me on the same laptop with kubuntu 7.10, I 've got the following message

[   13.312000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   13.312000] snd_hda_intel: Unknown symbol snd_ctl_add
[   13.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   13.312000] snd_hda_intel: Unknown symbol snd_pcm_new
[   13.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   13.312000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   13.312000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   13.312000] snd_hda_intel: Unknown symbol snd_card_register
[   13.312000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   13.312000] snd_hda_intel: Unknown symbol snd_card_free
[   13.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   13.312000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   13.312000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   13.312000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   13.312000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   13.312000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   13.316000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   13.316000] snd_hda_intel: Unknown symbol snd_component_add
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   13.316000] snd_hda_intel: Unknown symbol snd_card_new
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   13.316000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   13.316000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   13.316000] snd_hda_intel: Unknown symbol snd_device_new
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   13.316000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   13.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   13.316000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step


I have this alsa-base

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
#jaime
#options snd-hda-intel model=test
options snd-hda-intel model=laptop

---

### Post by AngryAnimal on 2008-01-13
Not sure about kubuntu.  I haven't enough partitions free to give it a go; due to the vista installation.

If you have the same laptop why not just use ubuntu instead?  Your machine has more than enough power for the job and ubuntu has more stuff to play with.

---

