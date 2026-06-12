---
title: "trouble upgrading 10.04 to10.10 with nvidia"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by fritzman on 2011-04-10
I'm really disappointed with the difficulties upgrading from 10.04 to 10.10.  Attempting to do the upgrade from the running installation of 10.04 results with an error, "An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report."
My system information;
$ uname -a
Linux uglybox 2.6.32-31-generic #60-Ubuntu SMP Thu Mar 17 22:15:39 UTC 2011 x86_64 GNU/Linux
$ sudo lspci
[sudo] password for al: 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
$ sudo lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
vboxnetadp              5636  0 
vboxnetflt             19227  0 
vboxdrv              1817576  2 vboxnetadp,vboxnetflt
xt_limit                2180  6 
xt_tcpudp               2667  17 
ipt_LOG                 5370  8 
ipt_MASQUERADE          1863  0 
xt_DSCP                 2277  5 
ipt_REJECT              2384  1 
nf_conntrack_irc        4429  0 
nf_conntrack_ftp        7126  0 
xt_state                1490  6 
snd_hda_codec_realtek   279072  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
iptable_nat             5219  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   6375  0 
nf_conntrack_ipv4      12980  9 iptable_nat,nf_nat
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usblp                  12407  0 
ses                     6683  0 
enclosure               8649  1 ses
joydev                 11104  0 
nf_conntrack           73966  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
iptable_mangle          3315  1 
iptable_filter          2791  1 
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               22461  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71251  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             29958  1 
psmouse                64576  0 
edac_core              45423  0 
serio_raw               4918  0 
edac_mce_amd            9278  0 
nvidia               8097254  30 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41116  0 
hid                    83600  1 usbhid
usb_storage            50377  0 
sata_nv                23714  5 
pata_amd               11962  0 
ahci                   37870  0 
pata_jmicron            2747  0 
forcedeth              55624  0
I am using NVIDIA accelerated graphics driver (version current)

So, I tried a clean install, somewhat annoyed that I still had to tab immediately to get to the options screen, do F6, and scroll down to 'nomodeset' in order for the installer to even run without a black screen.  I did manage to get it installed, or so I thought, but in order to even boot, I had to add "nomodeset" to the boot parameters.  Then, after the welcome screen and I have logged in, the screen locks with a message that it can't find some file or other.  And there it sits.... worthless!!
I've googled myself silly looking for answers, and now I'm here.  Does anyone have any ideas?  (As an aside, I sure hope the next LTS has these issues resolved before then.  I've been singing the praises of Ubuntu and its ease of installation till now.  This wrestling match would drive away the average Windows convert.)
Thanks for any help.
owa

---

### Post by Dutch70 on 2011-04-10
I done a quick google search for "E:Error, pkgProblemResolver" and it looks like there are several bug reports on this issue. 
[[COLOR="Red"]https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652")
[[COLOR="Red"]http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a9c154003ade45d3[/COLOR]]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a9c154003ade45d3")

Just to name a couple...Hope that helps until someone with more knowledge in that area responds.

As far as the problems your having with having to choose nomodeset and all of that. I wouldn't look for anything to change with the next LTS version. AFAIK you may want to take that complaint to nvidia, since I believe they are the only ones that can change it. 
I would really like to know more about that myself. I did find this though...
[[COLOR="RoyalBlue"]http://www.nuxified.org/blog/nvidia_dares_to_say_no[/COLOR]]("http://www.nuxified.org/blog/nvidia_dares_to_say_no")

Wish someone else would chime in on that subject.

---

