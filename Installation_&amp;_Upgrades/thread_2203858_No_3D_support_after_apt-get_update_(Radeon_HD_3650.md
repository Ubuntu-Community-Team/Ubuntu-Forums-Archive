---
title: "No 3D support after apt-get update (Radeon HD 3650 on precise)"
date: 2014-02-05
forum: Installation &amp; Upgrades
---

### Post by launchpad-wijzijnhet on 2014-02-05
During a routine update yesterday I recieved a new fglrx package, as no reboot was required I continued to work on it.
When I started my system this evening, my second screen was not enabled anymore and 3D support was not available anymore in Unity.

After checking the logs, it seams that my videocard is not recognized anymore.
```

Feb  5 19:03:30 VGN-FW21Z kernel: [   32.255032] [fglrx] Maximum main memory to use for locked dma buffers: 3761 MBytes.
Feb  5 19:03:30 VGN-FW21Z kernel: [   32.255576] [fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
Feb  5 19:03:30 VGN-FW21Z kernel: [   32.255579] [fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
Feb  5 19:03:32 VGN-FW21Z kernel: [   33.753225] [fglrx] Maximum main memory to use for locked dma buffers: 3761 MBytes.
Feb  5 19:03:32 VGN-FW21Z kernel: [   33.753762] [fglrx:firegl_init_device_list] *ERROR* No supported display adapters were found
Feb  5 19:03:32 VGN-FW21Z kernel: [   33.753765] [fglrx:firegl_init_module] *ERROR* firegl_init_devices failed
Feb  5 19:03:32 VGN-FW21Z kernel: [   34.075140] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

```

When I check the syslog of yesterday, there is nothing wrong at that moment:
```

Feb  4 18:37:50 VGN-FW21Z kernel: [   19.883957] [fglrx] Maximum main memory to use for locked dma buffers: 3761 MBytes.
Feb  4 18:37:50 VGN-FW21Z kernel: [   19.884394] [fglrx]   vendor: 1002 device: 9591 count: 1
Feb  4 18:37:50 VGN-FW21Z kernel: [   19.885045] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
Feb  4 18:37:50 VGN-FW21Z kernel: [   19.885062] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb  4 18:37:50 VGN-FW21Z kernel: [   19.885067] pci 0000:01:00.0: setting latency timer to 64
Feb  4 18:37:50 VGN-FW21Z kernel: [   19.885343] [fglrx] Kernel PAT support is enabled
Feb  4 18:37:50 VGN-FW21Z kernel: [   19.885359] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors

```

I already tried another apt-get update & upgrade, but there were not updates. Also a dpkg-reconfigure of fglrx didn't make any difference.

Does anyone know whether a wrong version of fglrx was released, or is there something else I can do to have normal behaviour again.

---

### Post by Bashing-om on 2014-02-05
launchpad-wijzijnhet; Hi !

There is a situation beyond our control:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


So the question is - if you want to run the fglrx driver - what version of 12.04 are you running ? Do you re-install to version 12.04.1 ?
```

uname -a

```

[INDENT][INDENT]sometimes, there just ain't no help
[/INDENT][/INDENT]

---

### Post by egeezer on 2014-02-05
Had the same problem,m same update, different graphics card.  Take a look at
  	 	 	 	    [COLOR=#000000][FONT=Liberation Serif, serif][SIZE=3][I][URL="https://help.ubuntu.com/community/RadeonDriver"]https://help.ubuntu.com/community/RadeonDriver


[/URL][/I][/SIZE][/FONT][/COLOR]

---

### Post by egeezer on 2014-02-05
And the fix for it is here:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)

---

### Post by launchpad-wijzijnhet on 2014-02-05
> **Bashing-om said:**
> launchpad-wijzijnhet; Hi !

So the question is - if you want to run the fglrx driver - what version of 12.04 are you running ? Do you re-install to version 12.04.1 ?
```

uname -a

```
[INDENT][INDENT]sometimes, there just ain't no help
[/INDENT]
[/INDENT]


I'm currently on 12.04.4 and until today I didn't have any problems with it, and all updates where installed when available, so I must have run the newer Xserver you mention.
If I check my apt.log, I only se fglrx, fglrx-amdcccle and (lib)lightdm which are updated and might be causing this issue.

To be honest, I must say that I'm quite supprised that a new upstream version which apparently breaks with older cards is added to the LTS as a normal update instead of an backport package or something like that.

---

### Post by launchpad-wijzijnhet on 2014-02-05
> **egeezer said:**
> And the fix for it is here:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)

Thnx, will check it out tomorrow and hope that it works.

---

### Post by Bashing-om on 2014-02-05
launchpad-wijzijnhet; Hi !

I also am at a loss to explain. The driver situatiuon is as quoted.

The real question is not the version that you have installed, but the version of the xserver. I too am in the same boat with an older ATI card that no longer has ATI support. However, my solution - in 12.04.4 is to keep the original xserver from the 12.04.1 version, and not enable the "Hardware Enablement Stack" so I keep that 3.2 kernel version series. Works great, last long time.

Also, for my use case, the open source drivers perform well.

[INDENT][INDENT]we do as we have to do
[/INDENT][/INDENT]

---

### Post by soiled skivvies on 2014-02-11
[COLOR=#000000]I have a HD 4870 working as it should after this update totally caught me by surprise.
Fans were maxed on speed. CPU was not using 100% which told me there is still hope. Screen was off to the right. Unity was MASSIVE and stuck in 2D mode. The card was noticed by one command but the drivers were broken with all the other ones Google searches told me to use. Then I found this:

Bug: [/COLOR][https://bugs.launchpad.net/ubuntu/+s...r/+bug/1276379]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379")

[COLOR=#000000]Solution from that very page: [/COLOR][COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install [COLOR=#417394]fglrx[/COLOR]=2:[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]8.960-0ubuntu1[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]sudo apt-mark hold [COLOR=#417394]fglrx[/COLOR]

[/FONT][/COLOR][COLOR=#000000]Solution mentioned worked first try and I did it right through the regular terminal in UI mode with Ctrl + Alt + T. I hope it works for ya. [/COLOR]:smile:

Now the next question is how to make update manager totally ignore flgrx updates completely. It seems this will be the only driver available forever for these series cards.

---

### Post by launchpad-wijzijnhet on 2014-02-14
> **soiled skivvies said:**
> [COLOR=#000000]
Bug: [/COLOR][https://bugs.launchpad.net/ubuntu/+s...r/+bug/1276379]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379")

[COLOR=#000000]Solution from that very page: [/COLOR][COLOR=#333333][FONT=Ubuntu Mono]sudo apt-get install [COLOR=#417394]fglrx[/COLOR]=2:[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]8.960-0ubuntu1[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]sudo apt-mark hold [COLOR=#417394]fglrx[/COLOR]
[/FONT][/COLOR]

This did work indeed. As I didn't have the time to test the solution of egeezer last week, I first tried this solution and it works.
Now lets hope that a new package is created so that a reinstall (if necessary) won't cause the same issue.

---

