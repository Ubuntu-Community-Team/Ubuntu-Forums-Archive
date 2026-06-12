---
title: "Karmic freezes and I don't know how to diagnose..."
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zaomaster on 2009-05-14
So it's happened a couple of times over the last day or so. I'll be working on my laptop and then everything freezes, screen stays lit, and the scroll and caps lock lights start flashing in unison. If I knew where to look I'd give more information or post a bug report, but I'm not even sure where to start.

thanks for any help.

oh, and after the last time that it did it, there were drive errors on my home partition that I had to manually fix with fsck, for what it's worth.

---

### Post by Saint Angeles on 2009-05-14
prolly because karmic is pre pre pre alpha right now. they DO say "try at your own risk"...


i'm not trying to be rude at all... just stating that it may be impossible to diagnose whats wrong at this stage.

---

### Post by zaomaster on 2009-05-14
> **Saint Angeles said:**
> prolly because karmic is pre pre pre alpha right now. they DO say "try at your own risk"...


i'm not trying to be rude at all... just stating that it may be impossible to diagnose whats wrong at this stage.

This is true and I understand the nature of a pre-alpha release. I'm fine with it breaking, that's why I offer myself as a guinea pig. I was simply trolling to see if this is a singular case on my part or if others had experienced this issue. Because if it's simply something on my machine and not repeated by others then maybe a clean reinstall might fix whatever borked, if not, then it's an issue the devs, bless their hearts, should look into.

Thanks for the word, and I understand your point. It's just not helpful.

---

### Post by taavikko on 2009-05-14
Try kerneloops for reporting issues.

If you have any closed source drivers in use, disable them to research more.
Also, dmesg logs may reveal something.

---

### Post by zaomaster on 2009-05-14
> **taavikko said:**
> Try kerneloops for reporting issues.

If you have any closed source drivers in use, disable them to research more.
Also, dmesg logs may reveal something.

Ok,

*Closed source drivers*: none

*Kerneloops*: found several log files, all showing the same text.
[INDENT]```
Kernel failure message 1:
BUG: unable to handle kernel paging request at 9e116c54
IP: [<c01a1d71>] put_page+0x11/0x100
*pde = 00000000 
Oops: 0000 [#1] SMP 
last sysfs file: /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
Modules linked in: sha1_generic ppp_mppe ppp_async crc_ccitt rt2500pci rt2x00pci rt2x00lib input_polldev mac80211 cfg80211 eeprom_93cx6 aes_i586 aes_generic binfmt_misc radeon drm vboxnetflt vboxdrv lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss arc4 ecb snd_pcm snd_seq_dummy snd_seq_oss ppdev snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq thinkpad_acpi led_class snd_timer snd_seq_device nvram video output parport_pc snd parport psmouse serio_raw soundcore snd_page_alloc intel_agp shpchp agpgart e100 mii vesafb fbcon tileblit font bitblit softcursor [last unloaded: eeprom_93cx6]

Pid: 5632, comm: phy0 Not tainted (2.6.30-5-generic #6-Ubuntu) 236683U
EIP: 0060:[<c01a1d71>] EFLAGS: 00010296 CPU: 0
EIP is at put_page+0x11/0x100
EAX: 9e116c54 EBX: 9e116c54 ECX: f72ae0c1 EDX: f72ae9e0
ESI: f1573100 EDI: 00000000 EBP: f157df10 ESP: f157defc
 DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Process phy0 (pid: 5632, ti=f157c000 task=f40abe30 task.ti=f157c000)
Stack:
 00000000 00000000 00000001 f1573100 00000000 f157df20 c0459947 f1573100
 f88a9e9f f157df2c c04594d2 f1573100 f157df40 c04595cb f1573100 f1573120
 f6941180 f157df54 f88a9e9f f1573120 f38d9b80 f38d9d8c f157df70 f88a9fb1
Call Trace:
 [<c0459947>] ? skb_release_data+0x87/0xa0
 [<f88a9e9f>] ? ieee80211_sta_rx_queued_mgmt+0x5f/0x110 [mac80211]
 [<c04594d2>] ? __kfree_skb+0x12/0x90
 [<c04595cb>] ? kfree_skb+0x3b/0x80
 [<f88a9e9f>] ? ieee80211_sta_rx_queued_mgmt+0x5f/0x110 [mac80211]
 [<f88a9fb1>] ? ieee80211_sta_work+0x61/0x1c0 [mac80211]
 [<c014b88e>] ? run_workqueue+0x6e/0x140
 [<f88a9f50>] ? ieee80211_sta_work+0x0/0x1c0 [mac80211]
 [<c014b9e8>] ? worker_thread+0x88/0xf0
 [<c014f8e0>] ? autoremove_wake_function+0x0/0x40
 [<c014b960>] ? worker_thread+0x0/0xf0
 [<c014f586>] ? kthread+0x46/0x80
 [<c014f540>] ? kthread+0x0/0x80
 [<c0103f57>] ? kernel_thread_helper+0x7/0x10
Code: fe ff ff 3e 80 23 fb eb dc 90 55 b8 30 24 1a c0 89 e5 e8 33 a8 fa ff 5d c3 90 55 89 e5 83 ec 14 89 5d f4 89 c3 89 75 f8 89 7d fc <66> f7 00 00 c0 0f 85 cc 00 00 00 3e ff 48 04 0f 94 c0 84 c0 74 
EIP: [<c01a1d71>] put_page+0x11/0x100 SS:ESP 0068:f157defc
CR2: 000000009e116c54
---[ end trace d63765705eb71466 ]---
```[/INDENT]

*Dmesg*: nothing really of note.

Maybe if someone could help me decipher the kerneloops log?

Thanks again for the help.

---

### Post by taavikko on 2009-05-14
> **zaomaster said:**
> Ok,
Maybe if someone could help me decipher the kerneloops log?

Thanks again for the help.

Please report bug using
```
ubuntu-bug linux
```
And attach kerneloops log files to that one.

---

### Post by olskar on 2009-05-14
Does it freeze if you disable networking too?

---

### Post by 23meg on 2009-05-14
> **zaomaster said:**
> So it's happened a couple of times over the last day or so. I'll be working on my laptop and then everything freezes, screen stays lit, and the scroll and caps lock lights start flashing in unison. If I knew where to look I'd give more information or post a bug report, but I'm not even sure where to start.

thanks for any help.

oh, and after the last time that it did it, there were drive errors on my home partition that I had to manually fix with fsck, for what it's worth.

This can help:

[https://wiki.ubuntu.com/DebuggingSystemCrash](https://wiki.ubuntu.com/DebuggingSystemCrash)

---

### Post by zaomaster on 2009-05-14
Thanks for this guys. I've posted to launchpad with attached kerneloops log and output from ubuntu-bug linux. We'll see if it's anything.

---

### Post by Starks on 2009-05-14
The newer 2.6.30 kernels, namely -4  and -5 are causing this.

---

### Post by zaomaster on 2009-05-15
> **olskar said:**
> Does it freeze if you disable networking too?
You know, I've noticed that it does seem to happen when there's something going on with the wifi... hmm.

---

