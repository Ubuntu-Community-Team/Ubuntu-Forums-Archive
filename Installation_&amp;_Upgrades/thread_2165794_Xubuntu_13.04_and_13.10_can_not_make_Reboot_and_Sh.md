---
title: "Xubuntu 13.04 and 13.10 can not make Reboot and Shutdown"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by prookie on 2013-08-06
Hello everyone,

  Recently I've installed Xubuntu 13.04 on my HP nx7300 laptop. I'm experiencing some difficulties when I want to make "Reboot" or "Shut Down" from XCFE. 

  When I click on mentioned system actions in upper panel, the reboot or shut down sequence is started, but after a few seconds my laptop is stuck. I only see Xubuntu wallpaper with that moving part of circe which indicates some activity. In that state my laptop is stuck for a long time. Only way to reboot or shut down is manually on power button.

  Please, do someone have a workaround for this. I had installed Xubuntu 12.04 and there were no problems like that. I had to install 13.04 because of kernel's compatibility for DVB USB dongle.

  Is there any system logs to check to trace where the problem can be?

  Thank you in advance.

  pRookie

---

### Post by prookie on 2014-01-09
Hello,

It passed half a year and I still have the same problem with hanging shutdown on Xubuntu 13.10. I've get used to turn off my laptop on power button and from time to time I've searched forum post for solution.

I found out that there is no shutdown logs in Linux. The following statement on **[askUbuntu post]("http://askubuntu.com/questions/58625/where-is-the-shutdown-log")** is the cold truth: "It's not physically possible for linux to record a log after the "Unmounting local filesystems" message."
On the other hand, it is possible to see what is behind the curtain during shutdown by just pressing ***Esc*** key during the Xubuntu image before power off (which for some reason does not happen to me). Please check what I see behind the curtain:
[SIZE=2][FONT=courier new]
The system is going down for power off NOW!
speech-dispatcher disabled: edit /etc/default/speech-dispatcher
                    * Asking all remaining processes to terminate ...        [ OK ]
modem-manager[635]: <info> Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)

modem-manager[635]: <info> Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> registered)

modem-manager[635]: <info> (ttyUSB0) closing serial port...

modem-manager[635]: <info> (ttyUSB0) serial port closed

* Killing all remaining processes...                                          [fail]
* Deactivating swap...                                                        [ OK ]
mount: / is busy
* Will now halt[/FONT][/SIZE]

After a while, with few strokes on keyboard, I get addition line saying:

[FONT=courier new][ 5606.912462] option1 ttyUSB0: option_instant_callback: error -108[/FONT]

Please notice that this log above was cought by my camera and rewriten by hand. All this happening in the century of Copy-Paste, for Christ sake!

Does anyone recognize the potential solution for this? How to continue my investigation?

Thank you in advance.

Take care,
pRookie

---

### Post by mörgæs on 2014-01-09
Does anything happen if you press enter while the system is hanging?

---

### Post by prookie on 2014-01-11
> **mörgæs said:**
> Does anything happen if you press enter while the system is hanging?

Nothing. Absolutely nothing. Even pressing combination of ***Ctrl & Alt & Del*** keys is worthless. 
Laptop only reacts on holding ***Power*** button for 5 seconds and then it goes power off.

---

### Post by egeezer on 2014-01-11
Open a terminal and try the following for reboot:

```
sudo shutdown -r now
```

Or for total shutdown and power off

```
sudo shutdown now -h -P
```

Not really a fix, mind you, but a workaround.  And don't forget, 13.04 reaches end-of-life January 27 (two weeks from Monday!)

---

### Post by prookie on 2014-01-11
Thank you egeezer for commands. Unfortunately, this didn't make the change; reboot and shutdown still hangs.

But there is something different what I see in the shutdown printout:

[SIZE=2][FONT=courier new]* Killing all remaining processes...                                          [fail]
[COLOR=#ff0000]modem-manager[657]: <info> Caught signal 15, shutting down...
modem-manager[657]: <info> modem /[SIZE=2][FONT=courier new]org/freedesktop/ModemManager/Modems/0: state changed (registered -> disabling)[/FONT][/SIZE][/COLOR]
* Deactivating swap...                                                        [ OK ]
mount: / is busy
* Will now halt[/FONT][/SIZE]

I have to mention the fact that I've upgraded to Xubuntu 13.10 by reinstalling Xubuntu. The title of this thread is old for months, but I didn't want to start a new one.
 I hoped that upgrading to 13.10 will make a change but it didn't. On the contrary, when I was using 12.04 installation I didn't have this problem. I somehow believe that kernel upgrade brought this fault and it's sneaking through revisions.

---

### Post by egeezer on 2014-01-11
Did you ever use a USB and remove it without either unmounting or (preferably) ejecting it?  I saw the reference to USB0 in your earlier post, and since your root partition is "busy", I wondered if it is busy with something that appears as mounted but really isn't.

(Sorry about the incoherent description, but I've had troubles myself with mounted stuff not going away!)

---

### Post by mörgæs on 2014-01-12
Changed the title accordingly.

Do you care for testing 14.04 in a fresh install? If we are dealing with a bug it would be good to get it fixed in 14.04, as this is a long term support release.

---

### Post by prookie on 2014-01-13
> **egeezer said:**
> Did you ever use a USB and remove it without either unmounting or (preferably) ejecting it?  I saw the reference to USB0 in your earlier post, and since your root partition is "busy", I wondered if it is busy with something that appears as mounted but really isn't.

The most important USB device I use is wireless modem for 3G. The model is Huawei E372 Dual Carrier HSPA+. When it is plugged in USB, I usually do not see it on Desktop as a mounted device. I see it only when I attach microSD card in the modem and then the icon is created but only for my device as a storage.
I do not follow special procedure for unmounting the device. But as I recall, the system hangs on shutdown no matter is the modem plugged or not. I will make a test today late afternoon to confirm this.

---

### Post by prookie on 2014-01-13
> **mörgæs said:**
> Do you care for testing 14.04 in a fresh install? If we are dealing with a bug it would be good to get it fixed in 14.04, as this is a long term support release.

Of course, I would be glad if I can help to Xubuntu somehow. I was using Windows XP for 8 years on my laptop and as it was announced that the end of support for Windows XP is April 2014, I was looking for replacement. I found Xubuntu as the best solution for me in Linux world.
I have to admit that my knowledge of core Linux is low. I understand some basic concepts but I'm far from troubleshooting faults, chasing bugs and finding solution. I would definitely need some guidance. Also, due to private obligations I will have a slow pace of making test scenarios. 

If all above is acceptable, please, can you tell me where to start? I would like to get familiar with some documentation.

---

### Post by mörgæs on 2014-01-13
Great, the best place for starting is the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=427"). 

You could just begin with trying 14.04 and post in the forum, if you find a bug which you would like to discuss before reporting.

---

### Post by chris183 on 2014-03-02
> **egeezer said:**
> Did you ever use a USB and remove it without either unmounting or (preferably) ejecting it?  I saw the reference to USB0 in your earlier post, and since your root partition is "busy", I wondered if it is busy with something that appears as mounted but really isn't.

(Sorry about the incoherent description, but I've had troubles myself with mounted stuff not going away!)

Firstly, apologies for jumping in on this thread - but I'm experiencing SIMILAR problems.

I'm now on Xubuntu 12.04 BTW (from Ubuntu 12.04) - and all through earlier versions I had no problem, I also think that the problem appeared in a kernel update, however RESTART seems to work, but SHUTDOWN hangs.

I run XP32 HE/SP3 and Vista64 HPE/SP2 on separate HDs on this machine, Xubuntu on separate HD also.

Your remark about USB got me thinking that I have a 4GB usb stick PERMANENTLY plugged in that supposedly improves Vista startup . . . . 

Could THIS be causing problems perhaps? - [COLOR=#0000ff]Removed stick - no change . . . [/COLOR]

[EDIT - some extra detail - AMD64 3700 processor - SanDiego core (socket 939) on GigaByte GA-K8NF-9 (Rev1) Mobo - nForce4-4x chipset  4Gb Ram, video card GT6600/128Mb

Initial screen after initiating shutdown:

Xubuntu 12.04

modem manager [914]: <info> CAUGHT SIGNAL 15, shutting down . . . 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
nm-dispatcher.action: Caught signal 15, shutting down . . .
nm-dispatcher.action: Disconnected from the system bus, exiting        [ OK ]
  * Deconfiguring network interfaces. . .                    [ OK ]
  * Deactivating swap. . .                         [ OK ]
umount: /run/lock: not mounted
umount /run/shm: not mounted
  * Will now halt

[This screen then disappears to be replaced by THIS:]

[    58.062177]    <#MC>        [<ffffffff81649f85>]    panic+0x91/0x1a4
[    58.062177]    [<ffffffff8102ab0b>]    mce_panic.part.14+0x18b/0x1c0
[    58.062177]    [<ffffffff8102aba0>]    mce_panic+0x60/0xb0
[    58.062177]    [<ffffffff8102b877>]    do_machine_check+0x427/0x600
[    58.062177]    [<ffffffff8166324c>]    machine_check+0x1c/0x30
[    58.062177]    [<ffffffff8152b9d1>]    ? pci_conf1_write+0x101/0x110
[    58.062177]    <<EOE>>    [<ffffffff8152e224>]    raw_pci_write+0x24/0x50
[    58.062177]    [<ffffffff8152e27c>]    pci_write+0x2c/0x30
[    58.062177]    [<ffffffff81331e21>]    pci_write_config_word+0x71/0xa0
[    58.062177]    [<ffffffff81335ac2>]    pci_intx+0x52/0x90
[    58.062177]    [<ffffffff8134c3bd>]    pci_intx_for_msi+0x1d/0x30
[    58.062177]    [<ffffffff8134d2fb>]    pci_msi_shutdown+0x7b/0x100
[    58.062177]    [<ffffffffa001d4f2>]    ? rt1_shutdown+0x172/0x1a0    [r8169]
[    58.062177]    [<ffffffff81338d24>]    pci_device_shutdown+0x34/0x50
[    58.062177]    [<ffffffff813f8a45>]    device_shutdown+0x15/0xd0
[    58.062177]    [<ffffffff8107f9fb>]    kernel_shutdown_prepare+0x3b/0x50
[    58.062177]    [<ffffffff8107fa93>]    kernel_power_off+0x13/0x50
[    58.062177]    [<ffffffff81080657>]    sys_reboot+0x147/0x280
[    58.062177]    [<ffffffff811a9650>]    ?__sync_filesystem+0x90/0x90
[    58.062177]    [<ffffffff810602da>]    ?__cond_resched+0x2a/0x40
[    58.062177]    [<ffffffff816608d2>]    ?_cond_resched+0x32/0x40
[    58.062177]    [<ffffffff81015711>]    ? math_state_restore+0x51/0x80
[    58.062177]    [<ffffffff81663abe>]    ? do_device_not_available+0xe/0x10
[    58.062177]    [<ffffffff8166b0c2>]    system_call_fastpath+0x16/0x1b

 . . . . end of EDIT]



Any thoughts?

Best Regards

Chris183

---

### Post by mörgæs on 2014-03-03
As I mentioned the best you can do is to test the development version. If there's a non-security bug in an old kernel there's little chance that it will be fixed.

---

### Post by Kurt_Alan on 2014-07-05
I'm a new user of Xubuntu 14.04. I've noticed some weird glitchy stuff with respect to reboot and shutdown.

First, the shutdown icons on my panel often fail to function with a message that the session must close . . .

Second, I can shutdown from terminal but my pc goes into suspend or hibernate and I have to hold down the power button. This has never happened before and I've run various flavors of Ubuntu on this machine for seven years.

Reboot from terminal is fine.

Workaround:

I dumped the shutdown icons. Shutdown from terminal; then press power button until shutoff. I can live with workarounds . . .

---

### Post by prookie on 2015-03-22
Hello community,

I've changed a distribution from Xubuntu 14.04 to LXLE 14.04 and there is no more problem with the Reboot and Shutdown on my old laptop HP Compaq nx7300.

I guess that quality of distribution plays a big role also.

pRookie

---

### Post by Irihapeti on 2015-03-22
Thread closed. This refers to unsupported releases of Xubuntu.

If you wish to ask a question about current releases, please start a new thread in the relevant forum.

---

