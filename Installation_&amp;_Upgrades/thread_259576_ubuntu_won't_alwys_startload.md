---
title: "ubuntu won't alwys start/load"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by Fingerlakes_Dave on 2006-09-17
Hello All.

  New to ubuntu and linux.  I had no problems with the live cd loading, everything appeared to work fine, so I installed.

 Partition 1: C:\Windows XP Pro SR2, ntfs, 30gb Partition 2: Linux swap, 6gb Partition 3: linux ext 3, ubuntu, 30gb

 I can only get ubuntu to load every 3 to 4 tries.  Shows up fine in grub.  I was able to update everything during one of the times I had it loaded.  I now show 2 kernels.  Same issue with either.

 >> Issue: All lines show OK on boot.  At login screen usb wireless mouse is dead.  Repeating sound (drum?) that is usually one beat now repeats endlessly.  ](*,) 
  If I try to load the desktop, it will load, and the "theme sound" starts.  First note repeats endlessly. (Best I can do to describe it. ](*,) 

  Got me swing'n.  Standard lines in grub.  If I try to delete
"options", saved default loads, so no go.

  When I **_CAN_** get ubuntu to load consistently, it looks like an OS I would be very happy with.

Hardware:
 AMD Athlox XP 2800+, LanParty II mb by DFI, 1gb Corsair memory, dual channel, nVidia GeForce FX5600 AGP video, WD 80gb SATA drive - 3 partitions, Logitech Cordless Mouseman Optical mouse, Creative Audigy 2 sound card, others....

  ANY help appreciated. :confused: 

Dave

---

### Post by Fingerlakes_Dave on 2006-09-18
New info: 50% success.  
 If I load ubuntu from cold start, it may load.
 
 If I load from rescue (by typing exit), it may load.

 ANY help appreciated!:confused:

---

### Post by hearnden on 2006-09-18
So does Ubuntu work fine except for the repeating sound?  Or does it crash 50% of the time, and the other 50% of the time it works except for the repeating sound?

With the USB wireless mouse, does unplugging and replugging the USB have any effect?  With my wireless mouse (Logitech), it also crashes X on startup until I unplug/replug it.

As for the repeating sound, perhaps it's a sound driver issue?

When you get it to load, can you copy and paste the output from opening a terminal and typing 'dmesg | tail', 'aplay -l' (that's a lowercase L), and 'lsmod | grep snd'?

---

### Post by Fingerlakes_Dave on 2006-09-18
> **hearnden said:**
> So does Ubuntu work fine except for the repeating sound?  Or does it crash 50% of the time, and the other 50% of the time it works except for the repeating sound?

  Actually no.  If you get to the login with the repeated sound, and you get the desktop to load after 5-10 minutes, no mouse therefore, no navigation.

>  With the USB wireless mouse, does unplugging and replugging the USB have any effect?  With my wireless mouse (Logitech), it also crashes X on startup until I unplug/replug it.

  Unplugging and replugging the mouse hasn't worked so far.  Mine is also a Logitech. 
  
> 
As for the repeating sound, perhaps it's a sound driver issue? 

  OK. I'd by that.  Now the question is, what's the fix?  Or is it a USB or mouse driver issue?????

>  When you get it to load, can you copy and paste the output from opening a terminal and typing 'dmesg | tail', 'aplay -l' (that's a lowercase L), and 'lsmod | grep snd'?

  I suppose.  I just don't understand what the commands even are yet.

  This the main reason Linux won't take off and beat Windows XP.
My worst Windows install, also a driver issue, I could figure out in about 20 minutes.

  I'm into hours on this.  Any average user wouldn't bother.  And I'm almost at that point myself..... *sigh*  :(

---

### Post by Lord Illidan on 2006-09-18
> **Fingerlakes_Dave said:**
> 
  I'm into hours on this.  Any average user wouldn't bother.  And I'm almost at that point myself..... *sigh*  :(

I sympathise with you... however make an effort. You don't know much about this because Linux is all new to you...I was in that position once..try again.

---

### Post by hearnden on 2006-09-18
If you get to the desktop, you can hit Alt+F2 to execute a command.  Try 'gnome-terminal', and that should bring up a terminal window.  In that window you can try out the commands:

```

dmesg | tail
aplay -l
lsmod | grep snd

```

The first one, is two commands. 'dmesg' prints out kernel log messages, and '| tail' prints out just the last 25 lines.  The second command, 'aplay -l', lists the detected sound devices.  The last one is again two commands.  'lsmod' lists the loaded kernel modules, and '| grep snd' prints out only lines that contain the text 'snd'.  The sound-related kernel modules often have 'snd' in their name.  The reason I'm suggesting them is #1 is often a good starting point to search for error messages, #2 is to see if your sound hardware is getting detected, and #3 is to look at what sound-related kernel modules are getting loaded.  For illustrative purposes, the output I get from these commands is:

```

hearnden@connie:~$ dmesg | tail
[17179641.696000] Bluetooth: HCI device and connection manager initialized
[17179641.696000] Bluetooth: HCI socket layer initialized
[17179641.720000] Bluetooth: L2CAP ver 2.8
[17179641.720000] Bluetooth: L2CAP socket layer initialized
[17179641.748000] Bluetooth: RFCOMM socket layer initialized
[17179641.748000] Bluetooth: RFCOMM TTY layer initialized
[17179641.748000] Bluetooth: RFCOMM ver 1.7
[17179659.576000] eth1: no IPv6 routers present
[17188215.584000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[17188448.716000] usb 5-6: USB disconnect, address 3

```

```

hearnden@connie:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

hearnden@connie:~$ lsmod | grep snd
snd_hda_intel          20468  2
snd_hda_codec         163088  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

```

If it is a sound driver issue, you can try looking at this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

