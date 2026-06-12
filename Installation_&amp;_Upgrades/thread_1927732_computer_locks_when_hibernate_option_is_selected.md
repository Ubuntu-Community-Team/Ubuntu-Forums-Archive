---
title: "computer locks when hibernate option is selected"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by thed0ctor on 2012-02-18
Hello,

I'm running Ubuntu 11.10 x64

I recently followed [this guide]("https://help.ubuntu.com/community/SwapFaq") to add a swap partition and enable hibernation. There is now a hibernation option but when I click it, it simply locks the screen. Sleep works fine but the hibernation option just locks the computer...

Any help would be appreciated!

---

### Post by thed0ctor on 2012-02-18
-bump-

---

### Post by thed0ctor on 2012-02-19
-bump-

---

### Post by thed0ctor on 2012-02-23
-bump-

Anyone?

---

### Post by matt_symes on 2012-02-23
Hi

Open up a terminal and post the results of these commands back here.

```
swapon -s
```

```
sudo blkid
```

```
tail -n100 /var/log/pm-suspend.log
```

That will do for a start. If no one else looks at this i may have to look at this tomorrow. It's late here.

Kind regards

---

### Post by thed0ctor on 2012-02-23
Here it is!

thedoctor@ubuntu:~$ swapon -s

```
        Filename                Type        Size    Used    Priority
        /dev/sda1                               partition    6291796    89620    -1
```thedoctor@ubuntu:~$ sudo blkid

```
        /dev/sda1: UUID="a4479a5b-955e-4c63-b822-cb16fdc6513d" TYPE="swap" 
        /dev/sda3: UUID="9f1db6c9-7654-4fef-94cc-668e1206367c" TYPE="ext4" 
```thedoctor@ubuntu:~$ tail -n100 /var/log/pm-suspend.log


```
        /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

        /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

        /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
        stop: Unknown instance: 

        /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

        /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

        /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
        Kernel modesetting video driver detected, not using quirks.

        /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

        /usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
        Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

        /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
        Thu Feb 23 20:37:14 EST 2012: performing suspend
        KMS graphics driver is in use, skipping quirks.
        Thu Feb 23 22:12:37 EST 2012: Awake.
        Thu Feb 23 22:12:37 EST 2012: Running hooks for resume
        Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

        /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

        /usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
        Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

        /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

        /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

        /dev/sda:
         setting Advanced Power Management level to 0x80 (128)
         APM_level    = 128

        /dev/sda:
         setting Advanced Power Management level to 0x80 (128)
         APM_level    = 128

        /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

        /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

        /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

        /usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
        Reloaded unloaded modules.

        /usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
        Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

        /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
        Having NetworkManager wake interfaces back up...Failed.

        /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

        /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
        Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

        /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
        Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

        /etc/pm/sleep.d/10_grub-common resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
        Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> 
        /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

        /usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

        /usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
        Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

        /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
        Thu Feb 23 22:12:40 EST 2012: Finished.
```Also I may note that my current installation was from a Wubi to Partition migration. Windows was on my computer and has been completely removed. This isn't a fresh install. I also know you can't hibernate without a hibernation file in Wubi and, being new to Linux distros, I thought perhaps after converting my Wubi installation to a normal one maybe some configuration files were never copied or something.

The guide I used [for Wubi is here]("http://ubuntuforums.org/showthread.php?t=1519354"), did the option without swap. Then used [this guide]("https://help.ubuntu.com/community/SwapFaq") for creating a swap partition.

---

### Post by bcbc on 2012-02-24
Please give the output of:
```
free -m
cat /etc/fstab | grep swap
cat /etc/initramfs-tools/conf.d/resume

```

---

### Post by matt_symes on 2012-02-24
Hi

Follow bcbc commands as they will tell us what should be setup as your swap in initramfs.

Your log file /var/log/pm-suspend.log is only showing attempts at suspending and we need to see one for hibernation, so could you type this command

```
echo "" | sudo tee /var/log/pm-suspend.log
```

Try to hibernate again and then post that log file back.

```
cat /var/log/pm-suspend.log
```

Kind regards

---

### Post by thed0ctor on 2012-02-24
Alright.

thedoctor@ubuntu:~$ free -m
```

                     total       used       free     shared    buffers     cached
        Mem:          3761       3364        397          0         31       1398
        -/+ buffers/cache:       1934       1826
        Swap:         6144        104       6039
```thedoctor@ubuntu:~$ cat /etc/fstab | grep swap
```

        UUID=a4479a5b-955e-4c63-b822-cb16fdc6513d    none    swap    sw    0    0

```thedoctor@ubuntu:~$ cat /etc/initramfs-tools/conf.d/resume
```

        resume=UUID=a4479a5b-955e-4c63-b822-cb16fdc6513d

```thedoctor@ubuntu:~$ echo "" | sudo tee /var/log/pm-suspend.log


After this I tried to hibernate. The computer just locked and I logged back in and entered this command as suggested:

thedoctor@ubuntu:~$ cat /var/log/pm-suspend.log
```

        Initial commandline parameters: 
        Fri Feb 24 12:10:02 EST 2012: Running hooks for hibernate.
        Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
        Linux ubuntu 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
        Module                  Size  Used by
        ipheth                 13563  0 
        nls_iso8859_1          12713  0 
        nls_cp437              16991  0 
        vfat                   17585  0 
        fat                    61475  1 vfat
        usb_storage            57901  0 
        uas                    18027  0 
        vmnet                  55617  10 
        vsock                  52475  0 
        vmci                   86575  1 vsock
        vmmon                  89424  0 
        pci_stub               12622  1 
        vboxpci                23200  0 
        vboxnetadp             13382  0 
        vboxnetflt             23441  0 
        parport_pc             36962  0 
        ppdev                  17113  0 
        lp                     17799  0 
        parport                46562  3 parport_pc,ppdev,lp
        vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
        bnep                   18436  2 
        kvm_intel              61643  0 
        rfcomm                 47946  0 
        kvm                   383773  1 kvm_intel
        bluetooth             166112  10 bnep,rfcomm
        binfmt_misc            17540  1 
        snd_hda_codec_hdmi     32040  1 
        snd_hda_codec_idt      70553  1 
        wl                   2568210  0 
        lib80211               14991  1 wl
        bcma                   20219  0 
        arc4                   12529  2 
        joydev                 17693  0 
        uvcvideo               72711  0 
        videodev               92992  1 uvcvideo
        v4l2_compat_ioctl32    17083  1 videodev
        wacom                  37975  0 
        snd_hda_intel          33390  4 
        snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
        snd_hwdep              13668  1 snd_hda_codec
        snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
        snd_seq_midi           13324  0 
        snd_rawmidi            30547  1 snd_seq_midi
        snd_seq_midi_event     14899  1 snd_seq_midi
        snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
        snd_timer              29991  2 snd_pcm,snd_seq
        snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
        snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
        psmouse                73882  0 
        intel_ips              18089  0 
        serio_raw              13166  0 
        brcmsmac              631693  0 
        brcmutil               17837  1 brcmsmac
        mac80211              462046  1 brcmsmac
        cfg80211              199630  2 brcmsmac,mac80211
        crc_ccitt              12667  1 brcmsmac
        soundcore              12680  1 snd
        snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
        i915                  571221  4 
        mei                    41480  0 
        drm_kms_helper         42558  1 i915
        drm                   236290  5 i915,drm_kms_helper
        i2c_algo_bit           13423  1 i915
        hp_accel               21880  0 
        lis3lv02d              19888  1 hp_accel
        input_polldev          13896  1 lis3lv02d
        video                  19412  1 i915
        hp_wmi                 18092  0 
        wmi                    19256  1 hp_wmi
        sparse_keymap          13890  1 hp_wmi
        usbhid                 47198  0 
        hid                    95463  1 usbhid
        ahci                   26002  2 
        libahci                26861  1 ahci
        r8169                  52788  0 
                     total       used       free     shared    buffers     cached
        Mem:       3851824    3488000     363824          0      33320    1452408
        -/+ buffers/cache:    2002272    1849552
        Swap:      6291796     107496    6184300

        /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
        Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> 
        /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
        Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

        /etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
        Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

        /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
        Having NetworkManager put all interaces to sleep...Failed.

        /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
        Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

        /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
        stop: Unknown instance: 

        /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
        Kernel modesetting video driver detected, not using quirks.

        /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

        /usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
        Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

        /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
        Fri Feb 24 12:10:03 EST 2012: performing hibernate
        s2disk: Could not stat the resume device file. Reason: No such file or directory
        Fri Feb 24 12:10:03 EST 2012: Awake.
        Fri Feb 24 12:10:03 EST 2012: Running hooks for thaw
        Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

        /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

        /usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

        /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

        /usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

        /dev/sda:
         setting Advanced Power Management level to 0xfe (254)
         APM_level    = 254

        /dev/sda:
         setting Advanced Power Management level to 0xfe (254)
         APM_level    = 254

        /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

        /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

        /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

        /usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
        Reloaded unloaded modules.

        /usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
        Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

        /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
        Having NetworkManager wake interfaces back up...Failed.

        /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

        /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
        Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

        /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
        Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

        /etc/pm/sleep.d/10_grub-common thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
        Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> Welcome to PulseAudio! Use "help" for usage information.
        >>> >>> 
        /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

        /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

        /usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
        Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

        /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
        Fri Feb 24 12:10:05 EST 2012: Finished.
```

---

### Post by thed0ctor on 2012-02-26
-bump-

---

### Post by bcbc on 2012-02-27
Sorry I was hoping matt_symes would reply ;)

I noticed this:
```
        Fri Feb 24 12:10:03 EST 2012: performing hibernate
        s2disk: Could not stat the resume device file. Reason: No such file or directory
        Fri Feb 24 12:10:03 EST 2012: Awake.
```

So that's the issue... but what the cause is I can't say. I searched a bit but there wasn't anything conclusive. I'm not sure what to suggest other than to double check everything, rerun 'update-initramfs -u'. ??

PS I just reviewed that swap guide you used and you shouldn't need to modify /etc/default/grub to hibernate. It's not necessary. I doubt that is the cause of the problem though.

---

### Post by bcbc on 2012-02-27
One thing I noticed is that your "resume=UUID=xxx" has a lower case "resume". Mine is "RESUME=UUID=xxx". The guide also had a lower case "resume" but I'd try changing it anyway and rerun:
```
sudo update-initramfs -u
```

Here's mine:
```
bcbc@ubuntu:~$ cat /etc/initramfs-tools/conf.d/resume 
RESUME=UUID=57c5fd7a-7b3d-43e9-9c1e-c59024a26992
```

---

### Post by matt_symes on 2012-02-28
Hi

> s2disk: Could not stat the resume device file. Reason: No such file or directory

I have to agree with bcbc. That error message looks ominous.

Just to eliminate some thing else though.

> /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
        Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
        Having NetworkManager put all interaces to sleep...Failed.


Disable your network interfaces before hibernating.

```
sudo /etc/init.d/networking stop
```

Then try to hibernate. I don't think it will fix the problem but it will eliminate your network interfaces as a potential cause of the problem.

Post back on the outcome.

To re-enable the interfaces

```
sudo /etc/init.d/networking start
```

Kind regards

---

### Post by thed0ctor on 2012-03-09
I tried changing the "resume" to capital RESUME and nothing changed. I also checked multiple times to make sure I did the tutorial correctly. I disabled the networking interface and still no go =/. Not sure how to fix this. Any ideas on how to remedy the error on not finding the file?

---

### Post by matt_symes on 2012-03-09
Hi

You did rebuild initramfs ? It looks like it does  not like the UUID in initramfs.

```
sudo update-initramfs -u
```

The above will update the latest initramfs image.

It may be worth having a look inside your initramfs file. Change the name of the initramfs (in bold) file to your current one.

```
gzip -dc /boot/**initrd.img-3.2.0-14-generic**  | cpio -idv  conf/conf.d/resume
``` 

You can find the name of your iniramfs by looking in /boot

```
ls /boot/initrd.img*
```

Post back results of this file.

```
cat conf/conf.d/resume
```

Then you can delete the extracted file.

And finally post the output of this command.

```
sudo blkid
```

Kind regards

---

### Post by thed0ctor on 2012-03-09
When I queried the name I received:


```
thedoctor@ubuntu:~$ ls /boot/initrd.img*
/boot/initrd.img-3.0.0-12-generic  /boot/initrd.img-3.0.0-15-generic
/boot/initrd.img-3.0.0-14-generic  /boot/initrd.img-3.0.0-16-generic
```

There are two, which one should I pick? Or post back both independently?

---

### Post by matt_symes on 2012-03-09
Hi

> **thed0ctor said:**
> When I queried the name I received:


```
thedoctor@ubuntu:~$ ls /boot/initrd.img*
/boot/initrd.img-3.0.0-12-generic  /boot/initrd.img-3.0.0-15-generic
/boot/initrd.img-3.0.0-14-generic  /boot/initrd.img-3.0.0-16-generic
```

There are two, which one should I pick? Or post back both independently?

Pick the bottom  right one. It's newest. (There are actually 4 of them ;) )

Kind regards

---

### Post by Toz on 2012-03-09
According to the instructions, you were asked (optionally) to make a change to your grub command line by adding a resume= parameter. If you did make that change, double-check that it is correct.
```
cat /proc/cmdline
```

---

### Post by matt_symes on 2012-03-09
Hi

> **Toz said:**
> According to the instructions, you were asked (optionally) to make a change to your grub command line by adding a resume= parameter. If you did make that change, double-check that it is correct.
```
cat /proc/cmdline
```

This is a good call and something i totally missed while scanning through that howto. 

I think a kernel command line parameter would take priority over what is in initramfs.

Kind regards

---

### Post by thed0ctor on 2012-03-09
In response to **Toz**

Assuming you're talking about the "Making the swap partition work for hibernate (optional)" section on the part about the UUID=... I double checked and here is the first half of the file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="RESUME=UUID=a4479a5b-955e-4c63-b822-cb16fdc6513d"
```

The UUID is correct according to gparted. When I first did the tutorial I copied and pasted it from gparted to avoid typos. Now, I then ran the command (cat /proc/cmdline) you said to ensure it was correct. This is what I achieved:
```


thedoctor@ubuntu:/$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=9f1db6c9-7654-4fef-94cc-668e1206367c ro RESUME=UUID=a4479a5b-955e-4c63-b822-cb16fdc6513d quiet splash vt.handoff=7

```

I'm honestly not sure about what this is suppose to look like, however the UUID is correct. 

In response to **matt_symes:**

Yes I did rebuild "initramfs" by typing ```
sudo update-initramfs -u
```

I typed what you said and received:
```

thedoctor@ubuntu:/$ ls /boot/initrd.img*
/boot/initrd.img-3.0.0-12-generic  /boot/initrd.img-3.0.0-15-generic
/boot/initrd.img-3.0.0-14-generic  /boot/initrd.img-3.0.0-16-generic
thedoctor@ubuntu:/$ gzip -dc /boot/initrd.img-3.0.0-16-generic  | cpio -idv  conf/conf.d/resume
cpio: no se puede crear el directorio `conf': Permiso denegado
cpio: conf/conf.d/resume: No se puede open: No existe el archivo o el directorio
conf/conf.d/resume
75106 bloques
thedoctor@ubuntu:/$ sudo gzip -dc /boot/initrd.img-3.0.0-16-generic  | cpio -idv  conf/conf.d/resume
cpio: no se puede crear el directorio `conf': Permiso denegado
cpio: conf/conf.d/resume: No se puede open: No existe el archivo o el directorio
conf/conf.d/resume
75106 bloques
thedoctor@ubuntu:/$ 

```

Pardon that my computer is in Spanish. It says "could not create the directory 'conf' permission denied," and then "Could not open the file or directory conf/conf.d/resume, 75106 blocks"

I stopped after that because I hit this error. Let me know what to do. If it helps I can change the language of my system back to English.

Thanks for the help thus far!

---

### Post by Toz on 2012-03-09
I'm not sure, but I think that the parameter is case sensitive. Try changing the line:
> GRUB_CMDLINE_LINUX="RESUME=UUID=a4479a5b-955e-4c63-b822-cb16fdc6513d"
...to read
```
GRUB_CMDLINE_LINUX="resume=UUID=a4479a5b-955e-4c63-b822-cb16fdc6513d"
```

Make sure you run:
```
sudo update-grub
```
...afterwards.

---

### Post by thed0ctor on 2012-03-10
Still just locks the screen..

---

### Post by bcbc on 2012-03-10
You don't need to modify GRUB_CMDLINE_LINUX to hibernate. I've never added it and it works fine without it.

I'd suggest removing it completely as another thing to try. I mentioned this in an earlier post (and I still don't think it's likely the issue), but might as well rule it out.

---

### Post by thed0ctor on 2012-03-10
I removed the line and still have the same result.

---

### Post by matt_symes on 2012-03-10
Hi

> Pardon that my computer is in Spanish. It says "could not create the directory 'conf' permission denied," and then "Could not open the file or directory conf/conf.d/resume, 75106 blocks"

> thedoctor@ubuntu**:/$** sudo gzip -dc /boot/initrd.img-3.0.0-16-generic  | cpio -idv  conf/conf.d/resume

You need to be in your home directory. You have run the command in your root directory and this is why you are getting permission denyed.

As an example, here's mine.

```
matthew@matthew-Aspire-7540:/sys$ cd
matthew@matthew-Aspire-7540:~$ pwd
/home/matthew
matthew@matthew-Aspire-7540:~$ ls /boot/init*
/boot/initrd.img-3.2.0-14-generic  /boot/initrd.img-3.2.0-15-generic
matthew@matthew-Aspire-7540:~$ sudo gzip -dc /boot/initrd.img-3.2.0-15-generic  | cpio -idv  conf/conf.d/resume
[sudo] password for matthew: 
conf/conf.d/resume
109626 blocks
matthew@matthew-Aspire-7540:~$ cat conf/conf.d/resume 
RESUME=UUID=1250f01e-19a4-4c40-bd50-b65af5dad42b
matthew@matthew-Aspire-7540:~$ 
```

Kind regards.

---

### Post by matt_symes on 2012-03-10
Hi

All your disk-by-uuid entries are correct ?

What's the output of

```
ls -l /dev/disk/by-uuid/
```

Kind regards

---

### Post by thed0ctor on 2012-03-10
I ran the commands from the home directory and was successful. Here are the results:

```
thedoctor@ubuntu:~$ ls /boot/init*
/boot/initrd.img-3.0.0-12-generic  /boot/initrd.img-3.0.0-15-generic
/boot/initrd.img-3.0.0-14-generic  /boot/initrd.img-3.0.0-16-generic
thedoctor@ubuntu:~$ sudo gzip -dc /boot/initrd.img-3.0.0-16-generic | cpio -idv conf/conf.d/resume
[sudo] password for thedoctor: 
conf/conf.d/resume
75106 bloques
thedoctor@ubuntu:~$ cat conf/conf.d/resume
resume=UUID=a4479a5b-955e-4c63-b822-cb16fdc6513d
thedoctor@ubuntu:~$ sudo blkid
/dev/sda1: UUID="a4479a5b-955e-4c63-b822-cb16fdc6513d" TYPE="swap" 
/dev/sda3: UUID="9f1db6c9-7654-4fef-94cc-668e1206367c" TYPE="ext4"
```

For the disk-by-uuid I have:

```

thedoctor@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2012-03-09 22:11 9f1db6c9-7654-4fef-94cc-668e1206367c -> ../../sda3
lrwxrwxrwx 1 root root 10 2012-03-09 22:11 a4479a5b-955e-4c63-b822-cb16fdc6513d -> ../../sda1
thedoctor@ubuntu:~$ 


```

I'm still new to this linux but the uuid strings are correct for both partitions.

---

### Post by matt_symes on 2012-03-11
Hi

I have to say i am a bit stumped by this at the moment. I will continue to scratch my head for you and i will also re-read the entire thread to make sure i have not missed something.

Anybody else have any ideas ?

Is it due to the WUBI to partition conversion ? I don't know much about WUBI.

Kind regards

---

### Post by Toz on 2012-03-11
This one sure is a head scratcher. 

On a long shot, did you install or are you using uswsusp:
```
apt-cache policy uswsusp
```
When I see s2disk, I usually think uswsusp, and not the kernel-based suspend/hibernate functions.

On the off-chance that it is installed, you may want to try uninstalling it (make sure pm-utils is installed).

---

### Post by bcbc on 2012-03-11
matt_symes, 
it's not related to Wubi or the migration. Wubi installs *can* actually hibernate: [http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html](http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html)

The migration script sets up hibernation automatically if a swap partition is provided, but in this case the swap partition was not provided.

---

### Post by matt_symes on 2012-03-11
Hi

> **bcbc said:**
> matt_symes, 
it's not related to Wubi or the migration. Wubi installs *can* actually hibernate: [http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html](http://ubuntu-with-wubi.blogspot.com/2011/01/swap-and-hibernation.html)

The migration script sets up hibernation automatically if a swap partition is provided, but in this case the swap partition was not provided.

Thanks for that information. I have never used Wubi and know next to nothing about it so i had no idea.

Kind regards

---

### Post by thed0ctor on 2012-03-12
> **Toz said:**
> This one sure is a head scratcher. 

On a long shot, did you install or are you using uswsusp:
```
apt-cache policy uswsusp
```
When I see s2disk, I usually think uswsusp, and not the kernel-based suspend/hibernate functions.

On the off-chance that it is installed, you may want to try uninstalling it (make sure pm-utils is installed).

I checked and both were installed. Uninstalled uswsusp and then restarted the computer. Then I tried to hibernate and it looked like it was going to but then when I powered it back on, it's like I turned the computer off. I opened some programs and things and then "hibernated" and none of the programs were up once I logged back on.

So now it appears to either be hibernating and not saving anything or just shutting down.

When it "hibernates" it doesn't prompt me about closing any programs or anything like shutting down does. I also don't get any Ubuntu loading bars or anything just a black screen like you'd expect.

Any ideas?

---

### Post by matt_symes on 2012-03-13
Hi

Good call Toz. I'm glad you joined this thread. I have seen some of your others on suspend and hibernate issues.

Try posting the logs again after hibernating.

```
tail -n 40 /var/log/pm-suspend.log
```

```
grep -i "PM:" /var/log/syslog | tail -n50
```

Kind regards

---

### Post by Toz on 2012-03-13
Hey Matt. Nothing like a good mystery to keep the brain cells firing.

@thed0ctor, I believe you need to also update your initramfs after installing/uninstalling uswsusp:
```
sudo update-initramfs -u
```

The logs that Matt ask for may also yeild some clues.

---

### Post by thed0ctor on 2012-03-14
Hey guys. I want to thank you soooo much for helping me with this issue. I ended up doing a fresh install of Ubuntu which gave me a swap partition. Everything is working after that. Thanks again for your help it's much appreciated glad to be part of the forums.

---

