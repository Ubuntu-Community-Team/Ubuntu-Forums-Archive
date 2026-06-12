---
title: "acpi_fakekey doesn't work on Lucid"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by realn on 2010-07-09
Hello everybody,

I was using xbindkeys and acpi_fakekey for doing all sorts of nice shortcuts. Unfortunately, acpi_fakekey doesn't work any longer on LL.
 Can someone tell me if she/he had the same problem and how she/he sorted it out ?

 thanks a bunch

---

### Post by realn on 2010-07-09
I just realized that /etc/acpi/voldownbtn.sh  /etc/acpi/volupbtn.sh don't work any longer.
On the other hand, /etc/acpi/hibernate.sh works OK.
The problems occur on a thinkpad X200s and they don't occur on ubuntu KK on the same machine.

---

### Post by realn on 2010-07-12
I had a problem with hibernate, too. It seemed to have inconsistent behaviour - sometimes it worked, sometimes it didn't. I looked around a little bit, I realized that my swap size was bigger than my swap partition - because of the "compcache" thing. I disabled it.
 Now - hibernate consistently DOESN'T WORK. It seems that acpi is somehow broken on Lucid - just a reminder, I use a thinkpad X200s.
 PLEASE, can someone help ?
 Suspend works ok, I can even lauch with with Fn+F4. Well, sort of OK, because my screen is locked after wake up from suspend, even if I set it to NOT lock after suspend.

---

### Post by lechien73 on 2010-07-12
Have you taken a look at ThinkWiki, which covers how to get special ThinkPad keys to work, and which modules are required? Some information is general to Ubuntu, but some is Lucid-specific.

The wiki can be found here: [http://uri.tl/a](http://uri.tl/a)

---

### Post by realn on 2010-07-12
Thank you for your answer. I will take a look. 
Anyway, I have no problem whatsoever with the special keys. I try to put into hibernation my laptop by launching the script /etc/acpi/hibernate.sh from a terminal, so no special keys involved. acpi_fakekey, too, is not a Thinkpad specific feature, it should work on all machines.
 I am afraid that some of the problems arise from the fact that hal has been removed (although I have a very vague idea what hal is) and I am MUCH afraid that I will have to downgrade to Ubuntu HH (the most stable release I tested so far - it's running on my server and it has uptime of months on it).
 Thanks again, I would appreciate any help.

---

### Post by lechien73 on 2010-07-12
I think the problem may not be to do with acpi per se, but the ThinkPad's implementation of acpi. The ThinkWiki site seems to list special modules (thinkpad_acpi) that need to be installed.

HAL is the Hardware Abstraction Layer - providing an interface between the physical hardware and the software. In 10.04 the functionality of HAL has been merged into udev.

---

### Post by realn on 2010-07-12
Yes, that's exactly how I see it, too.

 Still, I have the module up and running

lsmod | grep think
thinkpad_acpi          68083  1
led_class               2864  2 iwlcore,thinkpad_acpi
nvram                   6171  1 thinkpad_acpi
snd                    54148  19 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device

Also, I managed to hibernate using the uswsusp tools, namely s2disk.
So, this thing of fakekey is really bugging me. I was using it for doing all sorts of stuff. Plus the hibernation thing which seems broken.

---

### Post by realn on 2010-07-20
Solved - fallback to Kubuntu Hardy Heron waiting for a real LTS release.

---

