---
title: "Black Screen"
date: 2014-03-12
forum: Installation &amp; Upgrades
---

### Post by pitiburi on 2014-03-12
Hi, after the last update my computer does the following:

It starts normally, goes to the OS screen, where i choose Ubuntu (I have W7 also).
Then, it shows the purple screen, and then at the very instant in which it draws the ubuntu logo, it goes completely black, not even backlight, it seems without power (the screen). It is working though, because you can hear later the drums for when it draws the box asking you to log in.

I run Ubuntu 12.04

My PC is an ASUS X72D, with
Processor: AMD Phenom II N830
Graphics: ATI Mobility Radeon HD 5470 1GB DDR3

Please, I can't make it work with what I read froom the other threads, so if you think you can help me, I am all ears, I have some important stuff there.

Thanks

---

### Post by Mark Phelps on 2014-03-12
Recommend you read through the linked thread: [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

... and ... first try setting nomodeset and see if that gives you a desktop.

If that doesn't work, where the instructions talk about "quiet splash", remove the work "quiet".  When you continue with the boot, you should see some progress messages to the screen.

---

### Post by pitiburi on 2014-03-12
So, after many hours trying everything from that thread and some related ones, i was not able to get any combination working.
I am able, anyway, with some of the tweaking, to see the progress messages before it goes black, and what may be related is the line
"Starting load graphics fallback devices ------ failed"

It's not related to the brightness.

I tried with kernels as back as 2.6.38-13-generic, and the changes related with nomodeset and acpi_osi= and acpi_osi="Linux", but nothing worked.

The other thing is that when i choose ubuntu but having the shift key I end up in the screen for choosing the kernel, before getting there i can see a couple lines, one of which reads
blahblahblah error: "prefix" is not set.
Maybe that's related.

Anyway, remember this computer works perfectly with W7 so the hardware seems to be ok.

Any ideas, pointers, anything? This is incredibly frustrating, time consuming, and heartbreaking.

---

### Post by nibal on 2014-03-13
> **pitiburi said:**
> So, after many hours trying everything from that thread and some related ones, i was not able to get any combination working.
I am able, anyway, with some of the tweaking, to see the progress messages before it goes black, and what may be related is the line
"Starting load graphics fallback devices ------ failed"

It's not related to the brightness.

I tried with kernels as back as 2.6.38-13-generic, and the changes related with nomodeset and acpi_osi= and acpi_osi="Linux", but nothing worked.

The other thing is that when i choose ubuntu but having the shift key I end up in the screen for choosing the kernel, before getting there i can see a couple lines, one of which reads
blahblahblah error: "prefix" is not set.
Maybe that's related.

Anyway, remember this computer works perfectly with W7 so the hardware seems to be ok.

Any ideas, pointers, anything? This is incredibly frustrating, time consuming, and heartbreaking.

Don't go back, before you get an idea of what's wrong. Can you boot from the live CD? If yes, choose try Ubuntu. Open a terminal and type:

```


lsmod


```

You should get your graphics card driver from there. You can also mount your root partition:

```


sudo mount <root partition> /mnt
sudo mount --bind -t proc /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
chroot /mnt


```

Go and get the boot errors from your installation. Post them here.

HTH,
Nikos

---

### Post by pitiburi on 2014-03-13
Well, booting rom the LiveCD and running lsmod spits this:

> Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40302  1 
dm_crypt               23111  0 
arc4                   12573  2 
uvcvideo               82247  0 
ath9k                 161996  0 
videobuf2_core         40815  1 uvcvideo
videodev              138562  2 uvcvideo,videobuf2_core
mac80211              619465  1 ath9k
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hda_codec_hdmi     41736  1 
ath9k_common           13859  1 ath9k
snd_hda_codec_realtek    56448  1 
snd_seq_midi           13324  0 
ath9k_hw              457667  2 ath9k,ath9k_common
snd_hda_intel          53038  5 
joydev                 17613  0 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_rawmidi            30416  1 snd_seq_midi
psmouse               104093  0 
ath                    24123  3 ath9k,ath9k_common,ath9k_hw
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13613  1 snd_hda_codec
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
cfg80211              499466  3 ath9k,mac80211,ath
dm_multipath           27401  0 
scsi_dh                14873  1 dm_multipath
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             14114  0 
edac_core              62944  0 
edac_mce_amd           22792  0 
snd_timer              29989  2 snd_seq,snd_pcm
k10temp                13173  0 
serio_raw              13413  0 
i2c_piix4              22299  0 
snd                     73753  21  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_seq_midi,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
asus_laptop            28954  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
mac_hid                13253  0 
bnep                   24107  2 
parport_pc             32866  0 
soundcore              12680  1 snd
ppdev                  17711  0 
rfcomm                 74718  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
bluetooth             391726  10 bnep,rfcomm
parport                42466  3 parport_pc,ppdev,lp
squashfs               48026  1 
overlayfs              28370  1 
nls_iso8859_1          12713  1 
dm_raid45              78160  0 
dm_mirror              22307  0 
dm_region_hash         20961  1 dm_mirror
dm_log                 18527  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 857513  0 
raid6_pq               97812  1 btrfs
xor                    21411  2 dm_raid45,btrfs
zlib_deflate           27139  1 btrfs
hid_generic            12548  0 
usbhid                 53329  0 
hid                   106315  2 hid_generic,usbhid
usb_storage            66567  2 
radeon               1447330  3 
ttm                    84837  1 radeon
drm_kms_helper         53237  1 radeon
drm                   306660  5 radeon,ttm,drm_kms_helper
ahci                   30063  3 
i2c_algo_bit           13564  1 radeon
libahci                32118  1 ahci
atl1c                  47001  0 
video                  19574  0 



I have no idea on how am I supposed to find what there. As I said, I have an ATI Mobility Radeon HD5470.

Is there on that output any clue of what is going on?

And you aske me to post the boot errors from my installation. Anyone willing to explain me how to do that?

Thanks.

---

### Post by nibal on 2014-03-13
> **pitiburi said:**
> Well, booting rom the LiveCD and running lsmod spits this:



I have no idea on how am I supposed to find what there. As I said, I have an ATI Mobility Radeon HD5470.

Is there on that output any clue of what is going on?


Well, in the output you look for anything that resembles your card. For example the module for your video card is "radeon.ko". Assuming that your live CD is
booting without any problems, then you should pass this module to your kernel when booting. You have to modify your grub.cfg for that.

> 

And you aske me to post the boot errors from my installation. Anyone willing to explain me how to do that?

Thanks.

I did describe the procedure in my previous post. Read it. Then you can find your boot logs under /mnt/var/log (or /var/log if you are in chroot environment)

---

### Post by pitiburi on 2014-03-13
> Well, in the output you look for anything that resembles your card. For example the module for your video card is "radeon.ko". Assuming that your live CD is
booting without any problems, then you should pass this module to your kernel when booting. You have to modify your grub.cfg for that.

I can see the "radeon" string on many places in that list, how am I supposed to know which one is the module of my video card??
Plus, I have no idea what to do with that "module".

I confirm, the live CD is booting without problem, but once there it can see the W7 disk (or partition, or however it's called) but not the ubuntu disk. Which, btw, I don't know how to call/look for/mount.

About modifying my grub.cfg, it would help to know where to find it, and specially to know what do I have to edit there. And saying "You should pass this module to your kernel when booting" is supposing I have proficiency doing that, when I don't even know what it *means*.

I really appreciate the will to help from anyone, but for me to do something I have to be told what to do, and not what is the problem in a language i cannot decode. I am frustrated, my computer decided to stop working in Ubuntu and I have very important data there.

> I did describe the procedure in my previous post. Read it. Then you can find your boot logs under /mnt/var/log (or /var/log if you are in chroot environment)

Please could you point me to the part where you describe the procedure??????? I feel treated like a stupid, and I might well be one, but I cannot find there a procedure....
I read your previous post. I might be reeeeally stupid, because with the knowledge I have I can not find anywhere clear indications of a procedure. You tell me to type lsmode, and "You should get your graphics card driver from there" (how? how?????). Then, I get to know I can also, if I want, mount my root partition! (hurra! Got no idea what is that or what to do it for, but thanks!). And at the end, you said "Go and get the boot errors from your installation.". A clear explanation of the procedure to follow to achieve that, of course.

Please, I REALLY need help.

> Don't go back, before you get an idea of what's wrong. Can you boot from  the live CD? If yes, choose try Ubuntu. Open a terminal and type:

 	Code:
 	lsmod 
You should get your graphics card driver from there. You can also mount your root partition:

 	Code:
 	sudo mount <root partition> /mnt
sudo mount --bind -t proc /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
chroot /mnt 
Go and get the boot errors from your installation. Post them here.

HTH,
Nikos

---

### Post by nibal on 2014-03-14
> **pitiburi said:**
> I can see the "radeon" string on many places in that list, how am I supposed to know which one is the module of my video card??
Plus, I have no idea what to do with that "module".

Well, you see it in many places because many other modules (video mostly) depend on it, and you see the dependencies. :)

> 
I confirm, the live CD is booting without problem, but once there it can see the W7 disk (or partition, or however it's called) but not the ubuntu disk. Which, btw, I don't know how to call/look for/mount.


Live CD is booting? That's great news. You will have to work from the live CD to recover your installation.
Please post what you see from your W7 partition. It will help finding your Ubuntu one.

/mnt is just a directory from the live CD filesystem. If you type "ls /" you should see it. BTW, that was the procedure I was referring to:

```


sudo mount <root partition> /mnt
.
.
.

```

> 
About modifying my grub.cfg, it would help to know where to find it, and specially to know what do I have to edit there. And saying "You should pass this module to your kernel when booting" is supposing I have proficiency doing that, when I don't even know what it *means*.

I really appreciate the will to help from anyone, but for me to do something I have to be told what to do, and not what is the problem in a language i cannot decode. I am frustrated, my computer decided to stop working in Ubuntu and I have very important data there.


Hang in there. We will sort this out. You mean your Ubuntu was working fine and suddenly you got black screens? How come?

> 

Please could you point me to the part where you describe the procedure??????? I feel treated like a stupid, and I might well be one, but I cannot find there a procedure....
I read your previous post. I might be reeeeally stupid, because with the knowledge I have I can not find anywhere clear indications of a procedure. You tell me to type lsmode, and "You should get your graphics card driver from there" (how? how?????). Then, I get to know I can also, if I want, mount my root partition! (hurra! Got no idea what is that or what to do it for, but thanks!). And at the end, you said "Go and get the boot errors from your installation.". A clear explanation of the procedure to follow to achieve that, of course.


Not stupid, just newbie. All of us started like that. Just make an effort to invest a bit and learn about Linux when you get up and running. And feel free to google for things you don't understand. Man pages are also a very good source. Try "man lsmod" and then compare it to my responses about it.

Now, you first need to boot with the live CD and find your Ubuntu disks. To do that post what you see from your windows disks.

---

