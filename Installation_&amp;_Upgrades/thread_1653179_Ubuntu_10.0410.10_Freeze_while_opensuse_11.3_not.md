---
title: "Ubuntu 10.04/10.10 Freeze while opensuse 11.3 not"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by miltof on 2010-12-26
Hi,
I am a user of Ubuntu since 5 years, never had a problem like that before. (lot of install, update on many computers)
Today, a friend, give me an old computer but it freeze with a fresh install of ubuntu if the hyperthreading is enable in bios. 
After 5 minutes or sometime less ... lost the keyboard, the mouse and nothing to do exept switch off !!

The same computer never freeze with a fresh install of Opensuse 11.3 when the hyperthreading is on.

I there any major difference between this 2 linux which could explain this ?
Could someone help me to find the solution ?

Regards,
PS : sorry for my very bad english.

---

### Post by dino99 on 2010-12-26
5 years on Ubuntu, and you post for the first time :)

with such experience you might know what to do ,where & what to search :)

what you mean by "old" computer" ? how much ram ? special effects enabled ? Driver enabled ?

---

### Post by miltof on 2010-12-26
Hello thanks for you anwser,
Yes 5 years (perhaps 6) so of course I m not a beginner in using linux but I posted here because I dont know how to deal  with this ! 
The computer is a P4 3ghz with 1 Go of ram, no issue on hard disk, memory or my install media. (tested)
That why I tried Opensuse just to be sure to exclude hardware issues.
So it's works very well with opensuse (exept that I prefer ubuntu) and I just need some help.

Ubuntu works only without hyperthreading 
Opensuse works with or without hyperthreading 

Regards.

---

### Post by wojox on 2010-12-26
Could be the way the kernel is compiled. 

OpenSUSE = .rpm

Ubuntu = .deb

You did run a memtest?

What happens if you install without HT enabled and then turn it on?

With it disabled does it seem laggy at all?

---

### Post by dino99 on 2010-12-26
first check bios settings about hyperthreading

check driver activation: system admin additional driver 

then watch logs: .xsession-errors (/home, ctrl+h to unhide it), & "system admin logviewer", can watch /var/crash/ to know if something is logged, if so, double-click on it to run a report)

try the latest kernel 2.6.37 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by miltof on 2010-12-28
hi,
Thanks for your help !
First no pb with mem (as I said) .deb .rpm I dont think that the way of packaging the software  could be a cause.
xsession error and log give me these informations, perhaps compiz ?

Dec 27 21:11:42 christ-scaleo kernel: [   44.816024] ------------[ cut here ]------------
Dec 27 21:11:42 christ-scaleo kernel: [   44.816040] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
Dec 27 21:11:42 christ-scaleo kernel: [   44.816044] Hardware name: GA-8SGXP
Dec 27 21:11:42 christ-scaleo kernel: [   44.816047] NETDEV WATCHDOG: eth0 (sis900): transmit queue 0 timed out
Dec 27 21:11:42 christ-scaleo kernel: [   44.816050] Modules linked in: binfmt_misc ppdev fbcon tileblit font bitblit softcursor vga16fb vgastate snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device arc4 radeon joydev snd rt2500pci rt2x00pci ttm psmouse drm_kms_helper rt2x00lib led_class soundcore wacom sis_agp serio_raw drm i2c_algo_bit mac80211 snd_page_alloc cfg80211 eeprom_93cx6 agpgart shpchp lp parport usbhid hid ohci1394 usb_storage ieee1394 sis900 mii
Dec 27 21:11:42 christ-scaleo kernel: [   44.816122] Pid: 0, comm: swapper Not tainted 2.6.32-27-generic #49-Ubuntu
Dec 27 21:11:42 christ-scaleo kernel: [   44.816126] Call Trace:
Dec 27 21:11:42 christ-scaleo kernel: [   44.816135]  [<c014c802>] warn_slowpath_common+0x72/0xa0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816141]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
Dec 27 21:11:42 christ-scaleo kernel: [   44.816146]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
Dec 27 21:11:42 christ-scaleo kernel: [   44.816151]  [<c014c87b>] warn_slowpath_fmt+0x2b/0x30
Dec 27 21:11:42 christ-scaleo kernel: [   44.816156]  [<c04da1ee>] dev_watchdog+0x1fe/0x210
Dec 27 21:11:42 christ-scaleo kernel: [   44.816162]  [<c014248f>] ? try_to_wake_up+0x2ef/0x4a0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816169]  [<c0163d70>] ? insert_work+0x60/0xb0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816174]  [<c015ba1e>] run_timer_softirq+0x13e/0x2c0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816181]  [<c0176c54>] ? tick_dev_program_event+0x74/0xd0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816186]  [<c04d9ff0>] ? dev_watchdog+0x0/0x210
Dec 27 21:11:42 christ-scaleo kernel: [   44.816191]  [<c0153448>] __do_softirq+0x98/0x1b0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816196]  [<c01535a5>] do_softirq+0x45/0x50
Dec 27 21:11:42 christ-scaleo kernel: [   44.816200]  [<c01536f5>] irq_exit+0x65/0x70
Dec 27 21:11:42 christ-scaleo kernel: [   44.816207]  [<c0591efc>] smp_apic_timer_interrupt+0x5c/0x8b
Dec 27 21:11:42 christ-scaleo kernel: [   44.816212]  [<c058b8ec>] ? schedule+0x44c/0x840
Dec 27 21:11:42 christ-scaleo kernel: [   44.816218]  [<c0103df1>] apic_timer_interrupt+0x31/0x40
Dec 27 21:11:42 christ-scaleo kernel: [   44.816223]  [<c010ab65>] ? mwait_idle+0x55/0xa0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816228]  [<c01021d4>] cpu_idle+0x94/0xd0
Dec 27 21:11:42 christ-scaleo kernel: [   44.816234]  [<c057b248>] rest_init+0x58/0x60
Dec 27 21:11:42 christ-scaleo kernel: [   44.816242]  [<c07a58ec>] start_kernel+0x351/0x357
Dec 27 21:11:42 christ-scaleo kernel: [   44.816247]  [<c07a53c7>] ? unknown_bootoption+0x0/0x19e
Dec 27 21:11:42 christ-scaleo kernel: [   44.816253]  [<c07a50aa>] i386_start_kernel+0xaa/0xb1
Dec 27 21:11:42 christ-scaleo kernel: [   44.816257] ---[ end trace 36824d45f47a96b1 ]---



WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
I/O warning : failed to load external entity "/home/christ/.compiz/session/10f0a7bde414e7cd16129348094017249100000012880026"
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
evolution-alarm-notify-Message: Setting timeout for 13429 1293494400 1293480971
evolution-alarm-notify-Message:  Tue Dec 28 01:00:00 2010

evolution-alarm-notify-Message:  Mon Dec 27 21:16:11 2010

** (update-notifier:1475): DEBUG: Skipping reboot required

(gnome-power-manager:1364): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
gnome-settings-daemon: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
nm-applet: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
applet.py: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
update-notifier: Fatal IO error 11 (Ressource temporairement non disponible) on X server :0.0.
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

---

### Post by wandalalakers on 2010-12-28
This might be reaching but try the 10.10 alternative iso.
[http://ubuntu.cs.utah.edu/releases//10.10/ubuntu-10.10-alternate-i386.iso](http://ubuntu.cs.utah.edu/releases//10.10/ubuntu-10.10-alternate-i386.iso)

I also assume that you have an ati radeon video card by looking at your post above.

---

### Post by miltof on 2010-12-28
Hi,
Yes I have an ATI vido card (I can change it but same issue with an nvidia card)
I removed comipz this morning, reboot with hyperthreading enable, seems to be more stable, in fact I worked 15 minutes an then crash again (freeze keyboard and screen, the cpu graph didn't move).
Is it possible to activate some more verbose mode in kernel just to try to cach some more information.
About 10.10, in fact I tried it last week and it was the same issue.

Regards.
And Again Merci from France.

---

### Post by dino99 on 2010-12-28
your trace talk about "watchdog" , is it installed ? (look at synaptic) (might not be installed)

you can try : nomodeset (add it into /etc/default/grub , at the beginning of line ending with "quiet splash")

you can remove "quiet splash" (sometimes "splash" give issues)

--debug : give more errors comments

sudo dpkg-reconfigure -phigh -a
(could be long, dont stop it)

---

### Post by miltof on 2011-08-26
Just put a new vido card in the computer and no more issue. So probably the integrated one was less supported by ubunu than by opensuse, in fact I dont know but all is good now !
Thank for your help, hope this case can help other people.

---

