---
title: "Screen Flicker: Intel Mobile 4 Series Chipset Integrated Graphics"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sloosley on 2010-04-14
I'm on an Asus UL20A with the Intel chipset. Since Beta 1, my screen periodically flickers -- a violent flicker, if you will; a harsh jolt or jerk. 

Is there a way to fix this? Should I be using an Intel Driver, rather than the default driver that comes with Lucid?

Thanks,
-steve.

---

### Post by bofphile on 2010-04-15
I think the problem you describe is the same as mine on my Thinkpad T500 (Intel 4500MHD). And it has already been reported on launchpad: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/538648") and also here: [http://bugs.freedesktop.org/show_bug.cgi?id=27589]("http://bugs.freedesktop.org/show_bug.cgi?id=27589")

Apparently the workaround is to add "i915.powersave=0" to the kernel command line in grub. But this increase power consumption.

I hope a fix will be found before the release of Lucid.

---

### Post by jochem on 2010-04-15
I had this with my acer timeline 1810tz, same chipset.
It's removed since alpha3 or beta1 or so.

I did use the workaround of bofphile, but the bug is fixed for me now.

---

### Post by sloosley on 2010-04-15
Thank you for showing me the work around. I too hope this us resolved before the final release. 

Thank you for your help.

---

### Post by bobnutfield on 2010-04-16
Hello,

An issue I am having may or may not be related.  I have an old laptop with a P4 and intel 82845G integrated graphics.  I originally had Fedora on it, but every third or fourth reboot resulted in booting to a black screen.  Normal boot was taking place in the background as sound and wireless light worked, just no screen.

I reinstalled with Lucid as I thought this may have been a Fedora issue, but it is now happening with Ubuntu as well.  Both installs used the i915 driver natively during the install.  

I formerly had Slackware installed and had the same issue, so I used the vesa driver and it never happened using that driver.  But the issue started with the initial boot sequence:  the screen would have background light, flicker, then go to a black screen (no background light).  I was under the impression that the graphics driver in the kernel didn't kick in until late in the boot sequence and if that is true then this cannot be a related issue.

It may be a failing hardware issue, but I recently replaced the hard drive (which had a six year old installation of Windows), but with the former Windows installation on the other drive it never occurred.

Anyone have any opinions?

---

### Post by bofphile on 2010-04-16
Apparently the Intel 845G chipset has some problems with different version of Ubuntu, this is what I found: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/425251]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/425251")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399821]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399821")

I hope this helps you.

---

### Post by bobnutfield on 2010-04-16
> **bofphile said:**
> Apparently the Intel 845G chipset has some problems with different version of Ubuntu, this is what I found: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/425251]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/425251")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399821]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/399821")

I hope this helps you.

Wow, thanks bofphile.  I have been searching for something like this, but until you posted I had not found this information.  This explains a lot.  Apparently, this chipset was not even supported in Jaunty, improved in Karmic, and sporadic in Lucid.  Many people have difficulty with many Intel chipsets, and many of them get improvements with disabling KMS with "nomodset".

I will try that, but I have been away from getting inside Ubuntu for a while and I have to first get to grips with Grub2 to figure out how to add "nomodset" to the kernel boot.

Thank you for your post.

---

### Post by Yasawas on 2010-04-18
For something so minor this is utterly infuriating. Can someone advise which file I add the "i915.powersave=0" entry to please?

---

### Post by sloosley on 2010-04-18
What confuses me to no end is that I'm running a current chip set, the Intel Mobile 4! Why doesn't Lucid support the current Intel chipset? 

Most who get traction from nomodset are running old hardware. Why nomodset for new hardware? 

And I agree: This is really annoying!

---

### Post by zevans on 2010-04-18
> **sloosley said:**
> What confuses me to no end is that I'm running a current chip set, the Intel Mobile 4! Why doesn't Lucid support the current Intel chipset? 

Most who get traction from nomodset are running old hardware. Why nomodset for new hardware? 

And I agree: This is really annoying!

What's doubly annoying is we went through all this with Karmic. These problems keep either coming out TOO LATE in the testing cycle or are discovered early and somehow left on the shelf. Canonical should know by now that problems with laptop chipsets mean instant and widespread bad press. Why does this keep happening?

Yes, the kernel stack for DRI is a nightmare, but it was all fixed in Karmic, why is it back in Lucid?

I expect your specific problem is something to do with the major upheavals in the Intel stack over the last year. You could try running the xorg-edgers stuff - I've run karmic with it for over a year now and it's been fine for quite some time - it's only in my Lucid testing partition I've got weird thing happening in X.

---

### Post by sloosley on 2010-04-18
This is a newbie question: Should I look for an [Intel driver]("http://edc.intel.com/Software/Downloads/IEGD/#overview")?

Or, should I rely on the developers to adapt the Intel driver(s) to their distro? (This seems more logical, at least to a rookie.)

---

### Post by RAOF on 2010-04-19
> **Yasawas said:**
> For something so minor this is utterly infuriating. Can someone advise which file I add the "i915.powersave=0" entry to please?
Any file in /etc/modprobe.d.  This should work:
```

echo "i915.powersave=0" | sudo tee /etc/modprobe.d/i915-disable-powersave.conf
sudo update-initramfs -u

```

---

### Post by sloosley on 2010-04-19
After disabling "nomodset" in grub, my notebook fan runs much much more frequently than before. 

So, looks like we have two evils to choose from (1) a periodically flickering screen; or (2) a noisy fan. Ahh!

---

### Post by zevans on 2010-04-20
> **sloosley said:**
> 
So, looks like we have two evils to choose from (1) a periodically flickering screen; or (2) a noisy fan. Ahh!

Well, I suppose less powersaving equals more heat. But, interesting comparison: Have you run a flavour of Windows on same notebook, and how was the fan then?

---

### Post by bobnutfield on 2010-04-20
I finally gave up on trying to use Ubuntu Lucid on my P4 laptop with Intel graphics and installed Slackware.  Networking was difficult to get going, but it runs.  I have been running at least one Ubuntu on my machines since 2006.  I am growing tired of the direction Ubuntu is taking and Karmic that is on my desktop may be the last Ubuntu that I use.

---

### Post by pressureman on 2010-04-20
I've been running the Lucid alpha/beta for a while, and I'm pretty sure this problem only occurred with kernel packages 2.6.32-16 and later. It certainly wasn't a problem when I first installed a Lucid alpha.

I'm using a Thinkpad T500.

---

### Post by kevin01123 on 2010-04-21
Same problem here. Specs:

```
uname -a: Linux kevin-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
lspci -knn: 00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
lspci -knn: 	Kernel driver in use: agpgart-intel
lspci -knn: 	Kernel modules: intel-agp
lspci -knn: 00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
lspci -knn: 	Kernel driver in use: pcieport
lspci -knn: 	Kernel modules: shpchp
lspci -knn: 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
lspci -knn: 	Kernel driver in use: i915
lspci -knn: 	Kernel modules: i915
lspci -knn: 00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
lspci -knn: 00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
lspci -knn: 	Kernel driver in use: ehci_hcd
lspci -knn: 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
lspci -knn: 	Kernel driver in use: HDA Intel
lspci -knn: 	Kernel modules: snd-hda-intel
lspci -knn: 00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
lspci -knn: 	Kernel driver in use: pcieport
lspci -knn: 	Kernel modules: shpchp
lspci -knn: 00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
lspci -knn: 	Kernel driver in use: pcieport
lspci -knn: 	Kernel modules: shpchp
lspci -knn: 00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
lspci -knn: 	Kernel driver in use: pcieport
lspci -knn: 	Kernel modules: shpchp
lspci -knn: 00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
lspci -knn: 	Kernel driver in use: pcieport
lspci -knn: 	Kernel modules: shpchp
lspci -knn: 00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
lspci -knn: 	Kernel driver in use: pcieport
lspci -knn: 	Kernel modules: shpchp
lspci -knn: 00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
lspci -knn: 	Kernel driver in use: ehci_hcd
lspci -knn: 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
lspci -knn: 00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
lspci -knn: 	Kernel modules: iTCO_wdt
lspci -knn: 00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
lspci -knn: 	Kernel driver in use: ahci
lspci -knn: 	Kernel modules: ahci
lspci -knn: 00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
lspci -knn: 	Kernel modules: i2c-i801
lspci -knn: 02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
lspci -knn: 	Kernel driver in use: sky2
lspci -knn: 	Kernel modules: sky2
lspci -knn: 03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
lspci -knn: 	Kernel driver in use: iwlagn
lspci -knn: 	Kernel modules: iwlagn
lsmod: Module                  Size  Used by
lsmod: cryptd                  8116  0 
lsmod: aes_x86_64              7912  365 
lsmod: aes_generic            27607  1 aes_x86_64
lsmod: binfmt_misc             7960  1 
lsmod: ppdev                   6375  0 
lsmod: joydev                 11072  0 
lsmod: dm_crypt               13043  0 
lsmod: snd_hda_codec_realtek   278890  1 
lsmod: snd_hda_intel          25645  2 
lsmod: snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
lsmod: snd_hwdep               6924  1 snd_hda_codec
lsmod: snd_pcm_oss            41394  0 
lsmod: snd_mixer_oss          16299  1 snd_pcm_oss
lsmod: arc4                    1473  2 
lsmod: snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
lsmod: snd_seq_dummy           1782  0 
lsmod: snd_seq_oss            31219  0 
lsmod: snd_seq_midi            5829  0 
lsmod: snd_rawmidi            23388  1 snd_seq_midi
lsmod: snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
lsmod: snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lsmod: iwlagn                121577  0 
lsmod: snd_timer              23553  2 snd_pcm,snd_seq
lsmod: snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lsmod: iwlcore               124955  1 iwlagn
lsmod: uvcvideo               62403  0 
lsmod: videodev               40486  1 uvcvideo
lsmod: v4l1_compat            15495  2 uvcvideo,videodev
lsmod: v4l2_compat_ioctl32    12020  1 videodev
lsmod: snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lsmod: psmouse                64608  0 
lsmod: serio_raw               4918  0 
lsmod: acer_wmi               15829  0 
lsmod: led_class               3732  2 iwlcore,acer_wmi
lsmod: mac80211              238128  2 iwlagn,iwlcore
lsmod: cfg80211              148386  3 iwlagn,iwlcore,mac80211
lsmod: soundcore               8052  1 snd
lsmod: snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lsmod: lp                      9336  0 
lsmod: parport                37160  2 ppdev,lp
lsmod: fbcon                  39270  71 
lsmod: tileblit                2487  1 fbcon
lsmod: font                    8053  1 fbcon
lsmod: bitblit                 5811  1 fbcon
lsmod: softcursor              1565  1 bitblit
lsmod: vga16fb                12757  0 
lsmod: vgastate                9857  1 vga16fb
lsmod: usb_storage            49833  0 
lsmod: i915                  317872  3 
lsmod: drm_kms_helper         30742  1 i915
lsmod: drm                   198770  4 i915,drm_kms_helper
lsmod: i2c_algo_bit            6024  1 i915
lsmod: video                  20623  1 i915
lsmod: output                  2503  1 video
lsmod: sky2                   48803  0 
lsmod: ahci                   37646  4 
lsmod: intel_agp              29225  2 i915
df: Filesystem           1K-blocks      Used Available Use% Mounted on
df: /dev/sda5              7688360   3457208   3840600  48% /
df: none                   1986820       308   1986512   1% /dev
df: none                   1994040       200   1993840   1% /dev/shm
df: none                   1994040        84   1993956   1% /var/run
df: none                   1994040         0   1994040   0% /var/lock
df: none                   1994040         0   1994040   0% /lib/init/rw
df: /dev/sda3               182331     45163    127440  27% /boot
df: /dev/sda7            141197168  23867080 110157636  18% /home
df: /home/kevin/.Private 141197168  23867080 110157636  18% /home/kevin
free:              total       used       free     shared    buffers     cached
free: Mem:       3988084    1106984    2881100          0      54316     594428
free: -/+ buffers/cache:     458240    3529844
free: Swap:      5858296          0    5858296
/proc/cmdline: BOOT_IMAGE=/vmlinuz-2.6.32-21-generic root=UUID=5ae7d953-1f35-4a72-92fc-63d2c6dd1f64 ro quiet splash
/proc/cpuinfo: processor	: 0
/proc/cpuinfo: vendor_id	: GenuineIntel
/proc/cpuinfo: cpu family	: 6
/proc/cpuinfo: model		: 23
/proc/cpuinfo: model name	: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
/proc/cpuinfo: stepping	: 10
/proc/cpuinfo: cpu MHz		: 2000.000
/proc/cpuinfo: cache size	: 2048 KB
/proc/cpuinfo: physical id	: 0
/proc/cpuinfo: siblings	: 2
/proc/cpuinfo: core id		: 0
/proc/cpuinfo: cpu cores	: 2
/proc/cpuinfo: apicid		: 0
/proc/cpuinfo: initial apicid	: 0
/proc/cpuinfo: fpu		: yes
/proc/cpuinfo: fpu_exception	: yes
/proc/cpuinfo: cpuid level	: 13
/proc/cpuinfo: wp		: yes
/proc/cpuinfo: flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm
/proc/cpuinfo: bogomips	: 3990.03
/proc/cpuinfo: clflush size	: 64
/proc/cpuinfo: cache_alignment	: 64
/proc/cpuinfo: address sizes	: 36 bits physical, 48 bits virtual
/proc/cpuinfo: power management:
/proc/cpuinfo: 
/proc/cpuinfo: processor	: 1
/proc/cpuinfo: vendor_id	: GenuineIntel
/proc/cpuinfo: cpu family	: 6
/proc/cpuinfo: model		: 23
/proc/cpuinfo: model name	: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
/proc/cpuinfo: stepping	: 10
/proc/cpuinfo: cpu MHz		: 1200.000
/proc/cpuinfo: cache size	: 2048 KB
/proc/cpuinfo: physical id	: 0
/proc/cpuinfo: siblings	: 2
/proc/cpuinfo: core id		: 1
/proc/cpuinfo: cpu cores	: 2
/proc/cpuinfo: apicid		: 1
/proc/cpuinfo: initial apicid	: 1
/proc/cpuinfo: fpu		: yes
/proc/cpuinfo: fpu_exception	: yes
/proc/cpuinfo: cpuid level	: 13
/proc/cpuinfo: wp		: yes
/proc/cpuinfo: flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm
/proc/cpuinfo: bogomips	: 3990.02
/proc/cpuinfo: clflush size	: 64
/proc/cpuinfo: cache_alignment	: 64
/proc/cpuinfo: address sizes	: 36 bits physical, 48 bits virtual
/proc/cpuinfo: power management:
/proc/cpuinfo: 
/proc/ioports: 0000-001f : dma1
/proc/ioports: 0020-0021 : pic1
/proc/ioports: 0040-0043 : timer0
/proc/ioports: 0050-0053 : timer1
/proc/ioports: 0060-0060 : keyboard
/proc/ioports: 0064-0064 : keyboard
/proc/ioports: 0070-0077 : rtc0
/proc/ioports: 0080-008f : dma page reg
/proc/ioports: 00a0-00a1 : pic2
/proc/ioports: 00c0-00df : dma2
/proc/ioports: 00f0-00ff : fpu
/proc/ioports: 03c0-03df : vga+
/proc/ioports: 0400-047f : pnp 00:07
/proc/ioports:   0400-0403 : ACPI PM1a_EVT_BLK
/proc/ioports:   0404-0405 : ACPI PM1a_CNT_BLK
/proc/ioports:   0408-040b : ACPI PM_TMR
/proc/ioports:   0410-0415 : ACPI CPU throttle
/proc/ioports:   0420-042f : ACPI GPE0_BLK
/proc/ioports:   0450-0450 : ACPI PM2_CNT_BLK
/proc/ioports: 0480-048f : pnp 00:07
/proc/ioports: 0cf8-0cff : PCI conf1
/proc/ioports: 1180-11ff : pnp 00:07
/proc/ioports: 1200-120f : pnp 00:07
/proc/ioports: 1800-1807 : 0000:00:02.0
/proc/ioports: 1808-180b : 0000:00:1f.2
/proc/ioports:   1808-180b : ahci
/proc/ioports: 180c-180f : 0000:00:1f.2
/proc/ioports:   180c-180f : ahci
/proc/ioports: 1810-1817 : 0000:00:1f.2
/proc/ioports:   1810-1817 : ahci
/proc/ioports: 1818-181f : 0000:00:1f.2
/proc/ioports:   1818-181f : ahci
/proc/ioports: 1820-183f : 0000:00:1a.0
/proc/ioports:   1820-183f : uhci_hcd
/proc/ioports: 1840-185f : 0000:00:1a.1
/proc/ioports:   1840-185f : uhci_hcd
/proc/ioports: 1860-187f : 0000:00:1a.2
/proc/ioports:   1860-187f : uhci_hcd
/proc/ioports: 1880-189f : 0000:00:1d.0
/proc/ioports:   1880-189f : uhci_hcd
/proc/ioports: 18a0-18bf : 0000:00:1d.1
/proc/ioports:   18a0-18bf : uhci_hcd
/proc/ioports: 18c0-18df : 0000:00:1d.2
/proc/ioports:   18c0-18df : uhci_hcd
/proc/ioports: 18e0-18ff : 0000:00:1f.2
/proc/ioports:   18e0-18ff : ahci
/proc/ioports: 1c00-1c1f : 0000:00:1f.3
/proc/ioports: 2000-2fff : PCI Bus 0000:02
/proc/ioports:   2000-20ff : 0000:02:00.0
/proc/ioports:     2000-20ff : sky2
/proc/ioports: 3000-3fff : PCI Bus 0000:05
/proc/ioports: 4000-4fff : PCI Bus 0000:08
/proc/ioports: 5000-5fff : PCI Bus 0000:01
/proc/ioports: 6000-6fff : PCI Bus 0000:03
/proc/ioports: 7000-7fff : PCI Bus 0000:04
/proc/ioports: fe00-fe00 : pnp 00:07
/proc/ioports: ffff-ffff : pnp 00:07
/proc/ioports:   ffff-ffff : pnp 00:07
/proc/iomem: 00000000-0000ffff : reserved
/proc/iomem: 00010000-0009d3ff : System RAM
/proc/iomem: 0009d400-0009ffff : reserved
/proc/iomem: 000d2000-000d3fff : reserved
/proc/iomem: 000e4000-000fffff : reserved
/proc/iomem: 00100000-bb6a0fff : System RAM
/proc/iomem:   01000000-01548476 : Kernel code
/proc/iomem:   01548477-018305cf : Kernel data
/proc/iomem:   01919000-01a29e63 : Kernel bss
/proc/iomem: bb6a1000-bb6a6fff : reserved
/proc/iomem: bb6a7000-bb7bbfff : System RAM
/proc/iomem: bb7bc000-bb80efff : reserved
/proc/iomem: bb80f000-bb907fff : System RAM
/proc/iomem: bb908000-bbb0efff : reserved
/proc/iomem: bbb0f000-bbb18fff : System RAM
/proc/iomem: bbb19000-bbb1efff : reserved
/proc/iomem: bbb1f000-bbb63fff : System RAM
/proc/iomem: bbb64000-bbb9efff : ACPI Non-volatile Storage
/proc/iomem: bbb9f000-bbbe1fff : System RAM
/proc/iomem: bbbe2000-bbbfefff : ACPI Tables
/proc/iomem: bbbff000-bbbfffff : System RAM
/proc/iomem: bbc00000-bbffffff : RAM buffer
/proc/iomem: bc000000-bc1fffff : PCI Bus 0000:01
/proc/iomem: bc200000-bc3fffff : PCI Bus 0000:01
/proc/iomem: bc400000-bc5fffff : PCI Bus 0000:02
/proc/iomem:   bc400000-bc41ffff : 0000:02:00.0
/proc/iomem: bc600000-bc7fffff : PCI Bus 0000:03
/proc/iomem: bc800000-bc9fffff : PCI Bus 0000:04
/proc/iomem: bca00000-bcbfffff : PCI Bus 0000:04
/proc/iomem: bcc00000-bcc000ff : 0000:00:1f.3
/proc/iomem: bcc01000-bcc01fff : Intel Flush Page
/proc/iomem: d0000000-dfffffff : 0000:00:02.0
/proc/iomem: e0000000-efffffff : PCI MMCONFIG 0 [00-ff]
/proc/iomem:   e0000000-efffffff : pnp 00:09
/proc/iomem: f0000000-f1ffffff : PCI Bus 0000:05
/proc/iomem: f2000000-f3ffffff : PCI Bus 0000:08
/proc/iomem: f4000000-f5ffffff : PCI Bus 0000:05
/proc/iomem: f6000000-f7ffffff : PCI Bus 0000:08
/proc/iomem: f8000000-f83fffff : 0000:00:02.0
/proc/iomem: f8400000-f84fffff : 0000:00:02.1
/proc/iomem: f8500000-f85fffff : PCI Bus 0000:02
/proc/iomem:   f8500000-f8503fff : 0000:02:00.0
/proc/iomem:     f8500000-f8503fff : sky2
/proc/iomem: f8600000-f86fffff : PCI Bus 0000:03
/proc/iomem:   f8600000-f8601fff : 0000:03:00.0
/proc/iomem:     f8600000-f8601fff : iwlagn
/proc/iomem: f8900000-f8903fff : 0000:00:1b.0
/proc/iomem:   f8900000-f8903fff : ICH HD audio
/proc/iomem: f8904000-f89047ff : 0000:00:1f.2
/proc/iomem:   f8904000-f89047ff : ahci
/proc/iomem: f8904800-f8904bff : 0000:00:1a.7
/proc/iomem:   f8904800-f8904bff : ehci_hcd
/proc/iomem: f8904c00-f8904fff : 0000:00:1d.7
/proc/iomem:   f8904c00-f8904fff : ehci_hcd
/proc/iomem: fec00000-fec00fff : IOAPIC 0
/proc/iomem: fed00000-fed003ff : HPET 0
/proc/iomem:   fed00000-fed003ff : pnp 00:05
/proc/iomem: fed10000-fed13fff : pnp 00:09
/proc/iomem: fed18000-fed18fff : pnp 00:09
/proc/iomem: fed19000-fed19fff : pnp 00:09
/proc/iomem: fed1c000-fed1ffff : pnp 00:09
/proc/iomem: fed20000-fed3ffff : pnp 00:09
/proc/iomem: fee00000-fee00fff : Local APIC
/proc/iomem: 100000000-13fffffff : System RAM
/proc/interrupts:            CPU0       CPU1       
/proc/interrupts:   0:      46272      42792   IO-APIC-edge      timer
/proc/interrupts:   1:       4867          3   IO-APIC-edge      i8042
/proc/interrupts:   8:          1          0   IO-APIC-edge      rtc0
/proc/interrupts:   9:       1873        252   IO-APIC-fasteoi   acpi
/proc/interrupts:  12:         61      60884   IO-APIC-edge      i8042
/proc/interrupts:  17:          0          0   IO-APIC-fasteoi   uhci_hcd:usb7
/proc/interrupts:  18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb8
/proc/interrupts:  20:         59      10518   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb3, uhci_hcd:usb4, uhci_hcd:usb5
/proc/interrupts:  21:        301        596   IO-APIC-fasteoi   HDA Intel
/proc/interrupts:  23:          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
/proc/interrupts:  30:          1          0   PCI-MSI-edge      sky2@pci:0000:02:00.0
/proc/interrupts:  31:      20850       1664   PCI-MSI-edge      ahci
/proc/interrupts:  32:      15100         40   PCI-MSI-edge      i915
/proc/interrupts:  33:      40416      38814   PCI-MSI-edge      iwlagn
/proc/interrupts: NMI:          0          0   Non-maskable interrupts
/proc/interrupts: LOC:      37975      19462   Local timer interrupts
/proc/interrupts: SPU:          0          0   Spurious interrupts
/proc/interrupts: PMI:          0          0   Performance monitoring interrupts
/proc/interrupts: PND:          0          0   Performance pending work
/proc/interrupts: RES:       3716       3123   Rescheduling interrupts
/proc/interrupts: CAL:         44         98   Function call interrupts
/proc/interrupts: TLB:       2494       1892   TLB shootdowns
/proc/interrupts: TRM:          0          0   Thermal event interrupts
/proc/interrupts: THR:          0          0   Threshold APIC interrupts
/proc/interrupts: MCE:          0          0   Machine check exceptions
/proc/interrupts: MCP:          3          3   Machine check polls
/proc/interrupts: ERR:          1
/proc/interrupts: MIS:          0
/proc/meminfo: MemTotal:        3988084 kB
/proc/meminfo: MemFree:         2880984 kB
/proc/meminfo: Buffers:           54316 kB
/proc/meminfo: Cached:           594428 kB
/proc/meminfo: SwapCached:            0 kB
/proc/meminfo: Active:           632756 kB
/proc/meminfo: Inactive:         276804 kB
/proc/meminfo: Active(anon):     446332 kB
/proc/meminfo: Inactive(anon):       16 kB
/proc/meminfo: Active(file):     186424 kB
/proc/meminfo: Inactive(file):   276788 kB
/proc/meminfo: Unevictable:           0 kB
/proc/meminfo: Mlocked:               0 kB
/proc/meminfo: SwapTotal:       5858296 kB
/proc/meminfo: SwapFree:        5858296 kB
/proc/meminfo: Dirty:               620 kB
/proc/meminfo: Writeback:             0 kB
/proc/meminfo: AnonPages:        260832 kB
/proc/meminfo: Mapped:            84404 kB
/proc/meminfo: Shmem:            185540 kB
/proc/meminfo: Slab:              55608 kB
/proc/meminfo: SReclaimable:      33088 kB
/proc/meminfo: SUnreclaim:        22520 kB
/proc/meminfo: KernelStack:        2232 kB
/proc/meminfo: PageTables:        19636 kB
/proc/meminfo: NFS_Unstable:          0 kB
/proc/meminfo: Bounce:                0 kB
/proc/meminfo: WritebackTmp:          0 kB
/proc/meminfo: CommitLimit:     7852336 kB
/proc/meminfo: Committed_AS:     977492 kB
/proc/meminfo: VmallocTotal:   34359738367 kB
/proc/meminfo: VmallocUsed:      569576 kB
/proc/meminfo: VmallocChunk:   34359092728 kB
/proc/meminfo: HardwareCorrupted:     0 kB
/proc/meminfo: HugePages_Total:       0
/proc/meminfo: HugePages_Free:        0
/proc/meminfo: HugePages_Rsvd:        0
/proc/meminfo: HugePages_Surp:        0
/proc/meminfo: Hugepagesize:       2048 kB
/proc/meminfo: DirectMap4k:       10240 kB
/proc/meminfo: DirectMap2M:     4114432 kB
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0005 Version=0000
/proc/bus/input/devices: N: Name="Lid Switch"
/proc/bus/input/devices: P: Phys=PNP0C0D/button/input0
/proc/bus/input/devices: S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=event0 
/proc/bus/input/devices: B: EV=21
/proc/bus/input/devices: B: SW=1
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0003 Version=0000
/proc/bus/input/devices: N: Name="Sleep Button"
/proc/bus/input/devices: P: Phys=PNP0C0E/button/input0
/proc/bus/input/devices: S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event1 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=4000 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0001 Version=0000
/proc/bus/input/devices: N: Name="Power Button"
/proc/bus/input/devices: P: Phys=LNXPWRBN/button/input0
/proc/bus/input/devices: S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event2 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=10000000000000 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0017 Vendor=0001 Product=0001 Version=0100
/proc/bus/input/devices: N: Name="Macintosh mouse button emulation"
/proc/bus/input/devices: P: Phys=
/proc/bus/input/devices: S: Sysfs=/devices/virtual/input/input3
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse0 event3 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=70000 0 0 0 0
/proc/bus/input/devices: B: REL=3
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
/proc/bus/input/devices: N: Name="AT Translated Set 2 keyboard"
/proc/bus/input/devices: P: Phys=isa0060/serio0/input0
/proc/bus/input/devices: S: Sysfs=/devices/platform/i8042/serio0/input/input4
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event4 
/proc/bus/input/devices: B: EV=120013
/proc/bus/input/devices: B: KEY=10000 c020000000000 0 0 700f02000003 3803078f830f401 febfffdfffefffff ffffffffffffffff
/proc/bus/input/devices: B: MSC=10
/proc/bus/input/devices: B: LED=7
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0006 Version=0000
/proc/bus/input/devices: N: Name="Video Bus"
/proc/bus/input/devices: P: Phys=LNXVIDEO/video/input0
/proc/bus/input/devices: S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event5 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=3f000b00000000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0003 Vendor=064e Product=a103 Version=0100
/proc/bus/input/devices: N: Name="Acer Crystal Eye webcam"
/proc/bus/input/devices: P: Phys=usb-0000:00:1a.7-3/button
/proc/bus/input/devices: S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input6
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event6 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=100000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0001 Vendor=10ec Product=0268 Version=0001
/proc/bus/input/devices: N: Name="HDA Digital PCBeep"
/proc/bus/input/devices: P: Phys=card0/codec#0/beep0
/proc/bus/input/devices: S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input7
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event7 
/proc/bus/input/devices: B: EV=40001
/proc/bus/input/devices: B: SND=6
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
/proc/bus/input/devices: N: Name="SynPS/2 Synaptics TouchPad"
/proc/bus/input/devices: P: Phys=isa0060/serio1/input0
/proc/bus/input/devices: S: Sysfs=/devices/platform/i8042/serio1/input/input8
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse1 event8 
/proc/bus/input/devices: B: EV=b
/proc/bus/input/devices: B: KEY=420 7000f 0 0 0 0
/proc/bus/input/devices: B: ABS=11000003
/proc/bus/input/devices: 
dmidecode: # dmidecode 2.9
dmidecode: SMBIOS 2.5 present.
dmidecode: 45 structures occupying 1821 bytes.
dmidecode: Table at 0xBBAC0000.
dmidecode: 
dmidecode: Handle 0x0000, DMI type 0, 24 bytes
dmidecode: BIOS Information
dmidecode: 	Vendor: Phoenix Technologies LTD
dmidecode: 	Version: V1.10          
dmidecode: 	Release Date: 12/04/2008
dmidecode: 	Address: 0xE5D00
dmidecode: 	Runtime Size: 107264 bytes
dmidecode: 	ROM Size: 2048 kB
dmidecode: 	Characteristics:
dmidecode: 		ISA is supported
dmidecode: 		PCI is supported
dmidecode: 		PC Card (PCMCIA) is supported
dmidecode: 		PNP is supported
dmidecode: 		BIOS is upgradeable
dmidecode: 		BIOS shadowing is allowed
dmidecode: 		ESCD support is available
dmidecode: 		Boot from CD is supported
dmidecode: 		ACPI is supported
dmidecode: 		USB legacy is supported
dmidecode: 		AGP is supported
dmidecode: 		BIOS boot specification is supported
dmidecode: 		Targeted content distribution is supported
dmidecode: 
dmidecode: Handle 0x0001, DMI type 1, 27 bytes
dmidecode: System Information
dmidecode: 	Manufacturer: Acer           
dmidecode: 	Product Name: Aspire 5735                    
dmidecode: 	Version: 0100           
dmidecode: 	Serial Number: LXAU50X2218492BF2D2000        
dmidecode: 	UUID: CEE8AD80-C381-11DD-AB12-9A92BCE85B05
dmidecode: 	Wake-up Type: Power Switch
dmidecode: 	SKU Number: Not Specified
dmidecode: 	Family: Not Specified
dmidecode: 
dmidecode: Handle 0x0002, DMI type 2, 8 bytes
dmidecode: Base Board Information
dmidecode: 	Manufacturer: Acer           
dmidecode: 	Product Name: CathedralPeak                  
dmidecode: 	Version: Rev            
dmidecode: 	Serial Number: LXAU50X2218492BF2D2000        
dmidecode: 
dmidecode: Handle 0x0003, DMI type 3, 17 bytes
dmidecode: Chassis Information
dmidecode: 	Manufacturer: Acer           
dmidecode: 	Type: Notebook
dmidecode: 	Lock: Not Present
dmidecode: 	Version: N/A            
dmidecode: 	Serial Number: None           
dmidecode: 	Asset Tag:                                 
dmidecode: 	Boot-up State: Safe
dmidecode: 	Power Supply State: Safe
dmidecode: 	Thermal State: Safe
dmidecode: 	Security Status: None
dmidecode: 	OEM Information: 0x00001234
dmidecode: 
dmidecode: Handle 0x0004, DMI type 4, 40 bytes
dmidecode: Processor Information
dmidecode: 	Socket Designation: U2E1
dmidecode: 	Type: Central Processor
dmidecode: 	Family: <OUT OF SPEC>
dmidecode: 	Manufacturer: Intel
dmidecode: 	ID: 7A 06 01 00 FF FB EB BF
dmidecode: 	Version: CPU Version
dmidecode: 	Voltage: 3.3 V
dmidecode: 	External Clock: 200 MHz
dmidecode: 	Max Speed: 2000 MHz
dmidecode: 	Current Speed: 2000 MHz
dmidecode: 	Status: Populated, Enabled
dmidecode: 	Upgrade: ZIF Socket
dmidecode: 	L1 Cache Handle: 0x0005
dmidecode: 	L2 Cache Handle: 0x0006
dmidecode: 	L3 Cache Handle: Not Provided
dmidecode: 	Serial Number: Not Specified
dmidecode: 	Asset Tag: Not Specified
dmidecode: 	Part Number: Not Specified
dmidecode: 	Core Count: 2
dmidecode: 	Core Enabled: 2
dmidecode: 	Thread Count: 2
dmidecode: 	Characteristics:
dmidecode: 		64-bit capable
dmidecode: 
dmidecode: Handle 0x0005, DMI type 7, 19 bytes
dmidecode: Cache Information
dmidecode: 	Socket Designation: L1 Cache
dmidecode: 	Configuration: Enabled, Socketed, Level 1
dmidecode: 	Operational Mode: Write Back
dmidecode: 	Location: Internal
dmidecode: 	Installed Size: 64 KB
dmidecode: 	Maximum Size: 64 KB
dmidecode: 	Supported SRAM Types:
dmidecode: 		Burst
dmidecode: 		Pipeline Burst
dmidecode: 		Asynchronous
dmidecode: 	Installed SRAM Type: Asynchronous
dmidecode: 	Speed: Unknown
dmidecode: 	Error Correction Type: Unknown
dmidecode: 	System Type: Unknown
dmidecode: 	Associativity: Unknown
dmidecode: 
dmidecode: Handle 0x0006, DMI type 7, 19 bytes
dmidecode: Cache Information
dmidecode: 	Socket Designation: L2 Cache
dmidecode: 	Configuration: Enabled, Socketed, Level 2
dmidecode: 	Operational Mode: Write Back
dmidecode: 	Location: Internal
dmidecode: 	Installed Size: 2048 KB
dmidecode: 	Maximum Size: 4096 KB
dmidecode: 	Supported SRAM Types:
dmidecode: 		Burst
dmidecode: 		Pipeline Burst
dmidecode: 		Asynchronous
dmidecode: 	Installed SRAM Type: Burst
dmidecode: 	Speed: Unknown
dmidecode: 	Error Correction Type: Unknown
dmidecode: 	System Type: Unknown
dmidecode: 	Associativity: Unknown
dmidecode: 
dmidecode: Handle 0x0007, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: J19
dmidecode: 	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
dmidecode: 	External Reference Designator: COM 1
dmidecode: 	External Connector Type: DB-9 male
dmidecode: 	Port Type: Serial Port 16550A Compatible
dmidecode: 
dmidecode: Handle 0x0008, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: J1A1
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: Keyboard
dmidecode: 	External Connector Type: Circular DIN-8 male
dmidecode: 	Port Type: Keyboard Port
dmidecode: 
dmidecode: Handle 0x0009, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: J1A1
dmidecode: 	Internal Connector Type: None
dmidecode: 	External Reference Designator: PS/2 Mouse
dmidecode: 	External Connector Type: Circular DIN-8 male
dmidecode: 	Port Type: Mouse Port
dmidecode: 
dmidecode: Handle 0x000A, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PEG Slot J6B2
dmidecode: 	Type: 32-bit PCI Express
dmidecode: 	Current Usage: Available
dmidecode: 	Length: Long
dmidecode: 	ID: 6
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 
dmidecode: Handle 0x000B, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI Express Slot J6B1
dmidecode: 	Type: 32-bit PCI Express
dmidecode: 	Current Usage: In Use
dmidecode: 	Length: Long
dmidecode: 	ID: 7
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 
dmidecode: Handle 0x000C, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI Express Slot J6D1
dmidecode: 	Type: 32-bit PCI Express
dmidecode: 	Current Usage: In Use
dmidecode: 	Length: Long
dmidecode: 	ID: 8
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 
dmidecode: Handle 0x000D, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI Express Slot J8B3
dmidecode: 	Type: 32-bit PCI Express
dmidecode: 	Current Usage: Available
dmidecode: 	Length: Long
dmidecode: 	ID: 9
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 
dmidecode: Handle 0x000E, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI Express Slot J8D1
dmidecode: 	Type: 32-bit PCI Express
dmidecode: 	Current Usage: Available
dmidecode: 	Length: Long
dmidecode: 	ID: 10
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 
dmidecode: Handle 0x000F, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI Express Slot J7B1
dmidecode: 	Type: 32-bit PCI Express
dmidecode: 	Current Usage: Available
dmidecode: 	Length: Long
dmidecode: 	ID: 11
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 
dmidecode: Handle 0x0010, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI Express Slot 6
dmidecode: 	Type: 32-bit PCI Express
dmidecode: 	Current Usage: Available
dmidecode: 	Length: Long
dmidecode: 	ID: 10
dmidecode: 	Characteristics:
dmidecode: 		5.0 V is provided
dmidecode: 		3.3 V is provided
dmidecode: 
dmidecode: Handle 0x0011, DMI type 10, 6 bytes
dmidecode: On Board Device Information
dmidecode: 	Type: Sound
dmidecode: 	Status: Disabled
dmidecode: 	Description: HD-Audio
dmidecode: 
dmidecode: Handle 0x0012, DMI type 11, 5 bytes
dmidecode: OEM Strings
dmidecode: 	String 1: This is the Intel Cantiga
dmidecode: 	String 2: Chipset CRB Platform
dmidecode: 
dmidecode: Handle 0x0013, DMI type 12, 5 bytes
dmidecode: System Configuration Options
dmidecode: 	Option 1: Jumper settings can be described here.
dmidecode: 
dmidecode: Handle 0x0014, DMI type 15, 29 bytes
dmidecode: System Event Log
dmidecode: 	Area Length: 16 bytes
dmidecode: 	Header Start Offset: 0x0000
dmidecode: 	Header Length: 16 bytes
dmidecode: 	Data Start Offset: 0x0010
dmidecode: 	Access Method: General-purpose non-volatile data functions
dmidecode: 	Access Address: 0x0000
dmidecode: 	Status: Valid, Not Full
dmidecode: 	Change Token: 0x00000001
dmidecode: 	Header Format: Type 1
dmidecode: 	Supported Log Type Descriptors: 3
dmidecode: 	Descriptor 1: POST error
dmidecode: 	Data Format 1: POST results bitmap
dmidecode: 	Descriptor 2: Single-bit ECC memory error
dmidecode: 	Data Format 2: Multiple-event
dmidecode: 	Descriptor 3: Multi-bit ECC memory error
dmidecode: 	Data Format 3: Multiple-event
dmidecode: 
dmidecode: Handle 0x0015, DMI type 16, 15 bytes
dmidecode: Physical Memory Array
dmidecode: 	Location: System Board Or Motherboard
dmidecode: 	Use: System Memory
dmidecode: 	Error Correction Type: None
dmidecode: 	Maximum Capacity: 4 GB
dmidecode: 	Error Information Handle: Not Provided
dmidecode: 	Number Of Devices: 2
dmidecode: 
dmidecode: Handle 0x0016, DMI type 17, 27 bytes
dmidecode: Memory Device
dmidecode: 	Array Handle: 0x0015
dmidecode: 	Error Information Handle: No Error
dmidecode: 	Total Width: 64 bits
dmidecode: 	Data Width: 64 bits
dmidecode: 	Size: 2048 MB
dmidecode: 	Form Factor: SODIMM
dmidecode: 	Set: 1
dmidecode: 	Locator: M1
dmidecode: 	Bank Locator: Bank 0
dmidecode: 	Type: DDR2
dmidecode: 	Type Detail: Synchronous
dmidecode: 	Speed: 667 MHz (1.5 ns)
dmidecode: 	Manufacturer: Mfg 0
dmidecode: 	Serial Number: 1234-B0
dmidecode: 	Asset Tag: Not Specified
dmidecode: 	Part Number: SODIMM000
dmidecode: 
dmidecode: Handle 0x0017, DMI type 17, 27 bytes
dmidecode: Memory Device
dmidecode: 	Array Handle: 0x0015
dmidecode: 	Error Information Handle: No Error
dmidecode: 	Total Width: 64 bits
dmidecode: 	Data Width: 64 bits
dmidecode: 	Size: 2048 MB
dmidecode: 	Form Factor: SODIMM
dmidecode: 	Set: 1
dmidecode: 	Locator: M2
dmidecode: 	Bank Locator: Bank 1
dmidecode: 	Type: DDR2
dmidecode: 	Type Detail: Synchronous
dmidecode: 	Speed: 667 MHz (1.5 ns)
dmidecode: 	Manufacturer: Mfg 1
dmidecode: 	Serial Number: 1234-B1
dmidecode: 	Asset Tag: Not Specified
dmidecode: 	Part Number: SODIMM001
dmidecode: 
dmidecode: Handle 0x0018, DMI type 18, 23 bytes
dmidecode: 32-bit Memory Error Information
dmidecode: 	Type: OK
dmidecode: 	Granularity: Unknown
dmidecode: 	Operation: Unknown
dmidecode: 	Vendor Syndrome: Unknown
dmidecode: 	Memory Array Address: Unknown
dmidecode: 	Device Address: Unknown
dmidecode: 	Resolution: Unknown
dmidecode: 
dmidecode: Handle 0x0019, DMI type 18, 23 bytes
dmidecode: 32-bit Memory Error Information
dmidecode: 	Type: OK
dmidecode: 	Granularity: Unknown
dmidecode: 	Operation: Unknown
dmidecode: 	Vendor Syndrome: Unknown
dmidecode: 	Memory Array Address: Unknown
dmidecode: 	Device Address: Unknown
dmidecode: 	Resolution: Unknown
dmidecode: 
dmidecode: Handle 0x001A, DMI type 19, 15 bytes
dmidecode: Memory Array Mapped Address
dmidecode: 	Starting Address: 0x00000000000
dmidecode: 	Ending Address: 0x000FFFFFFFF
dmidecode: 	Range Size: 4 GB
dmidecode: 	Physical Array Handle: 0x0015
dmidecode: 	Partition Width: 0
dmidecode: 
dmidecode: Handle 0x001B, DMI type 20, 19 bytes
dmidecode: Memory Device Mapped Address
dmidecode: 	Starting Address: 0x00000000000
dmidecode: 	Ending Address: 0x0007FFFFFFF
dmidecode: 	Range Size: 2 GB
dmidecode: 	Physical Device Handle: 0x0016
dmidecode: 	Memory Array Mapped Address Handle: 0x001A
dmidecode: 	Partition Row Position: Unknown
dmidecode: 	Interleave Position: Unknown
dmidecode: 	Interleaved Data Depth: Unknown
dmidecode: 
dmidecode: Handle 0x001C, DMI type 20, 19 bytes
dmidecode: Memory Device Mapped Address
dmidecode: 	Starting Address: 0x00080000000
dmidecode: 	Ending Address: 0x000FFFFFFFF
dmidecode: 	Range Size: 2 GB
dmidecode: 	Physical Device Handle: 0x0017
dmidecode: 	Memory Array Mapped Address Handle: 0x001A
dmidecode: 	Partition Row Position: Unknown
dmidecode: 	Interleave Position: Unknown
dmidecode: 	Interleaved Data Depth: Unknown
dmidecode: 
dmidecode: Handle 0x001D, DMI type 22, 26 bytes
dmidecode: Portable Battery
dmidecode: 	Location: Rear
dmidecode: 	Manufacturer: Intel Corporation
dmidecode: 	Name: Intel Corporation
dmidecode: 	Chemistry: Lithium Ion
dmidecode: 	Design Capacity: 1000 mWh
dmidecode: 	Design Voltage: 19 mV
dmidecode: 	SBDS Version: BATT_1234
dmidecode: 	Maximum Error: 100%
dmidecode: 	SBDS Serial Number: 0001
dmidecode: 	SBDS Manufacture Date: 1980-00-01
dmidecode: 	OEM-specific Information: 0x00000000
dmidecode: 
dmidecode: Handle 0x001E, DMI type 23, 13 bytes
dmidecode: System Reset
dmidecode: 	Status: Enabled
dmidecode: 	Watchdog Timer: Present
dmidecode: 	Boot Option: Do Not Reboot
dmidecode: 	Boot Option On Limit: Do Not Reboot
dmidecode: 	Reset Count: Unknown
dmidecode: 	Reset Limit: Unknown
dmidecode: 	Timer Interval: Unknown
dmidecode: 	Timeout: Unknown
dmidecode: 
dmidecode: Handle 0x001F, DMI type 24, 5 bytes
dmidecode: Hardware Security
dmidecode: 	Power-On Password Status: Disabled
dmidecode: 	Keyboard Password Status: Unknown
dmidecode: 	Administrator Password Status: Disabled
dmidecode: 	Front Panel Reset Status: Unknown
dmidecode: 
dmidecode: Handle 0x0020, DMI type 25, 9 bytes
dmidecode: 	System Power Controls
dmidecode: 	Next Scheduled Power-on: 12-31 23:59:59
dmidecode: 
dmidecode: Handle 0x0021, DMI type 26, 20 bytes
dmidecode: Voltage Probe
dmidecode: 	Description: Voltage Probe
dmidecode: 	Location: Processor
dmidecode: 	Status: OK
dmidecode: 	Maximum Value: Unknown
dmidecode: 	Minimum Value: Unknown
dmidecode: 	Resolution: Unknown
dmidecode: 	Tolerance: Unknown
dmidecode: 	Accuracy: Unknown
dmidecode: 	OEM-specific Information: 0x00000000
dmidecode: 
dmidecode: Handle 0x0022, DMI type 27, 12 bytes
dmidecode: Cooling Device
dmidecode: 	Temperature Probe Handle: 0x0023
dmidecode: 	Type: Fan
dmidecode: 	Status: OK
dmidecode: 	OEM-specific Information: 0x00000000
dmidecode: 
dmidecode: Handle 0x0023, DMI type 28, 20 bytes
dmidecode: Temperature Probe
dmidecode: 	Description: Temperature Probe
dmidecode: 	Location: Processor
dmidecode: 	Status: OK
dmidecode: 	Maximum Value: Unknown
dmidecode: 	Minimum Value Unknown
dmidecode: 	Resolution: Unknown
dmidecode: 	Tolerance: Unknown
dmidecode: 	Accuracy: Unknown
dmidecode: 	OEM-specific Information: 0x00000000
dmidecode: 
dmidecode: Handle 0x0024, DMI type 29, 20 bytes
dmidecode: Electrical Current Probe
dmidecode: 	Description: Electrical Current Probe
dmidecode: 	Location: Processor
dmidecode: 	Status: OK
dmidecode: 	Maximum Value: Unknown
dmidecode: 	Minimum Value: Unknown
dmidecode: 	Resolution: Unknown
dmidecode: 	Tolerance: Unknown
dmidecode: 	Accuracy: Unknown
dmidecode: 	OEM-specific Information: 0x00000000
dmidecode: 
dmidecode: Handle 0x0025, DMI type 30, 6 bytes
dmidecode: Out-of-band Remote Access
dmidecode: 	Manufacturer Name: Intel
dmidecode: 	Inbound Connection: Disabled
dmidecode: 	Outbound Connection: Enabled
dmidecode: 
dmidecode: Handle 0x0026, DMI type 32, 20 bytes
dmidecode: System Boot Information
dmidecode: 	Status: No errors detected
dmidecode: 
dmidecode: Handle 0x0027, DMI type 39, 22 bytes
dmidecode: System Power Supply
dmidecode: 	Power Unit Group: 1
dmidecode: 	Location: To Be Defined By O.E.M
dmidecode: 	Name: To Be Defined By O.E.M
dmidecode: 	Manufacturer: To Be Defined By O.E.M
dmidecode: 	Serial Number: To Be Defined By O.E.M
dmidecode: 	Asset Tag: To Be Defined By O.E.M
dmidecode: 	Model Part Number: To Be Defined By O.E.M
dmidecode: 	Revision: 2.50
dmidecode: 	Max Power Capacity: Unknown
dmidecode: 	Status: Present, Unknown
dmidecode: 	Type: Unknown
dmidecode: 	Input Voltage Range Switching: Unknown
dmidecode: 	Plugged: Yes
dmidecode: 	Hot Replaceable: No
dmidecode: 	Input Voltage Probe Handle: 0x0021
dmidecode: 	Cooling Device Handle: 0x0022
dmidecode: 	Input Current Probe Handle: 0x0024
dmidecode: 
dmidecode: Handle 0x0028, DMI type 129, 8 bytes
dmidecode: OEM-specific Type
dmidecode: 	Header and Data:
dmidecode: 		81 08 28 00 01 01 02 01
dmidecode: 	Strings:
dmidecode: 		Intel_ASF
dmidecode: 		Intel_ASF_001
dmidecode: 
dmidecode: Handle 0x0029, DMI type 136, 6 bytes
dmidecode: OEM-specific Type
dmidecode: 	Header and Data:
dmidecode: 		88 06 29 00 FF FF
dmidecode: 
dmidecode: Handle 0x002A, DMI type 150, 14 bytes
dmidecode: OEM-specific Type
dmidecode: 	Header and Data:
dmidecode: 		96 0E 2A 00 01 01 00 00 00 00 00 00 00 00
dmidecode: 	Strings:
dmidecode: 		ABSOLUTE(PHOENIX) CLM
dmidecode: 
dmidecode: Handle 0x002B, DMI type 200, 7 bytes
dmidecode: OEM-specific Type
dmidecode: 	Header and Data:
dmidecode: 		C8 07 2B 00 01 02 03
dmidecode: 	Strings:
dmidecode: 		17C0
dmidecode: 		             
dmidecode: 		0001
dmidecode: 
dmidecode: Handle 0x002C, DMI type 127, 4 bytes
dmidecode: End Of Table
dmidecode: 
```

---

### Post by NightwishFan on 2010-04-21
Try adding i915.powersave=0 to your boot options.

---

