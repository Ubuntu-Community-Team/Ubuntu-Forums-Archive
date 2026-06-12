---
title: "Ubuntu 19.04 install hangs on disk partitioning"
date: 2019-07-12
forum: Installation &amp; Upgrades
---

### Post by djole94hns2 on 2019-07-12
Hello,

I hope I'm posting this in the right forum. While installing 19.04, my install just freezes on disk partitioning. I can set up the partitions, but when I write changes to disk, it just hangs. I tried waiting (for an hour at most), but it just won't move.
It's an ongoing issue since 18.04. I haven't had that problem with 16.04 or Debian 10 (currently using). I even tried upgrading from 16.04, and it worked, but only for a short while: after a minute or so, everything but mouse movement would just freeze. I would like to provide logs, I just don't know where they're created.

What I tried already:

Downloading a fresh ISO, trough both torrent and http
Changing the USB stick
Writing to USB with a different program (LiLi, Rufus, Unetbootin)

System:

AMD FX-8300 CPU
AMD R7 270 GPU
10GB RAM
1TB HDD
Windows installation on another partition

Thank you in advance!

UPDATE:

I've managed to extract the logs, here they are:

partman (cut to only the last ~50 lines, it's thousands of lines long)

```
parted_server: Closing infifo and outfifoparted_server: main_loop: iteration 203
parted_server: Opening infifo
/lib/partman/active_partition/87delete/choices: *******************************************************
/lib/partman/active_partition/87delete/choices: IN: GET_LABEL_TYPE =dev=sda
parted_server: Read command: GET_LABEL_TYPE
parted_server: command_get_label_type()
parted_server: Opening outfifo
parted_server: OUT: OK




parted_server: OUT: msdos




parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 204
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: *******************************************************
/lib/partman/active_partition/80resize/do_option: IN: VIRTUAL =dev=sda 1048576-500102048767
parted_server: Read command: VIRTUAL
parted_server: command_virtual()
parted_server: Opening outfifo
parted_server: is virtual partition with id 1048576-500102048767
parted_server: partition_with_id(1048576-500102048767)
parted_server: OUT: OK




parted_server: named_partition_is_virtual(=dev=sda,2048,976761813)
parted_server: no
parted_server: OUT: no




parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 205
parted_server: Opening infifo
/lib/partman/active_partition/80resize/do_option: IN: GET_VIRTUAL_RESIZE_RANGE =dev=sda 1048576-500102048767
parted_server: Read command: GET_VIRTUAL_RESIZE_RANGE
parted_server: command_get_virtual_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(1048576-500102048767)
parted_server: OUT: OK

parted_server: OUT: 512 500101000192 500101545984

parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 206
parted_server: Opening infifo
```

syslog (also cut to around when the problem started):

```
Jul 12 11:49:23 ubuntu systemd[1]: Starting Snappy daemon...Jul 12 11:49:23 ubuntu snapd[5430]: AppArmor status: apparmor is enabled and all features are available
Jul 12 11:49:23 ubuntu snapd[5430]: backend.go:127: snapd enabled root filesystem on overlay support, additional upperdir permissions granted
Jul 12 11:49:23 ubuntu snapd[5430]: daemon.go:379: started snapd/2.38+19.04 (series 16; classic) ubuntu/19.04 (amd64) linux/5.0.0-13-generic.
Jul 12 11:49:23 ubuntu systemd[1885]: tmp-sanity\x2dmountpoint\x2d677918614.mount: Succeeded.
Jul 12 11:49:23 ubuntu systemd[1]: tmp-sanity\x2dmountpoint\x2d677918614.mount: Succeeded.
Jul 12 11:49:23 ubuntu systemd[1]: Started Snappy daemon.
Jul 12 11:49:24 ubuntu systemd[1]: Reloading.
Jul 12 11:49:24 ubuntu systemd[1]: /lib/systemd/system/spice-vdagentd.service:8: PIDFile= references path below legacy directory /var/run/, updating /var/run/spice-vdagentd/spice-vdagentd.pid &#8594; /run/spice-vdagentd/spice-vdagentd.pid; please update the unit file accordingly.
Jul 12 11:49:24 ubuntu systemd[1]: Mounting Mount unit for core18, revision 941...
Jul 12 11:49:24 ubuntu systemd[1]: Mounted Mount unit for core18, revision 941.
Jul 12 11:49:25 ubuntu systemd[1]: Reloading.
Jul 12 11:49:25 ubuntu systemd[1]: /lib/systemd/system/spice-vdagentd.service:8: PIDFile= references path below legacy directory /var/run/, updating /var/run/spice-vdagentd/spice-vdagentd.pid &#8594; /run/spice-vdagentd/spice-vdagentd.pid; please update the unit file accordingly.
Jul 12 11:49:25 ubuntu systemd[1]: Mounting Mount unit for gnome-3-28-1804, revision 31...
Jul 12 11:49:25 ubuntu systemd[1]: Mounted Mount unit for gnome-3-28-1804, revision 31.
Jul 12 11:49:26 ubuntu systemd[1]: Reloading.
Jul 12 11:49:26 ubuntu systemd[1]: /lib/systemd/system/spice-vdagentd.service:8: PIDFile= references path below legacy directory /var/run/, updating /var/run/spice-vdagentd/spice-vdagentd.pid &#8594; /run/spice-vdagentd/spice-vdagentd.pid; please update the unit file accordingly.
Jul 12 11:49:26 ubuntu systemd[1]: Mounting Mount unit for gnome-calculator, revision 406...
Jul 12 11:49:26 ubuntu systemd[1]: Mounted Mount unit for gnome-calculator, revision 406.
Jul 12 11:49:26 ubuntu kernel: [   97.135451] audit: type=1400 audit(1562932166.449:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.gnome-calculator" pid=5808 comm="apparmor_parser"
Jul 12 11:49:26 ubuntu kernel: [   97.222914] audit: type=1400 audit(1562932166.537:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.gnome-calculator.gnome-calculator" pid=5809 comm="apparmor_parser"
Jul 12 11:49:26 ubuntu kernel: [   97.419045] audit: type=1400 audit(1562932166.733:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-calculator" pid=5820 comm="apparmor_parser"
Jul 12 11:49:26 ubuntu kernel: [   97.493675] audit: type=1400 audit(1562932166.809:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-calculator.gnome-calculator" pid=5821 comm="apparmor_parser"
Jul 12 11:49:27 ubuntu kernel: [   97.902197] audit: type=1400 audit(1562932167.217:12): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=5829 comm="apparmor_parser"
Jul 12 11:49:27 ubuntu kernel: [   97.902317] audit: type=1400 audit(1562932167.217:13): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=5829 comm="apparmor_parser"
Jul 12 11:49:27 ubuntu kernel: [   97.925414] audit: type=1400 audit(1562932167.241:14): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=5831 comm="apparmor_parser"
Jul 12 11:49:27 ubuntu kernel: [   97.987197] audit: type=1400 audit(1562932167.301:15): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=5832 comm="apparmor_parser"
Jul 12 11:49:27 ubuntu kernel: [   98.165740] audit: type=1400 audit(1562932167.481:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-calculator.gnome-calculator" pid=5840 comm="apparmor_parser"
Jul 12 11:49:27 ubuntu kernel: [   98.198555] audit: type=1400 audit(1562932167.513:17): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.gnome-calculator" pid=5842 comm="apparmor_parser"
Jul 12 11:49:30 ubuntu xdg-desktop-por[2146]: Failed to create app chooser proxy: Error calling StartServiceByName for org.freedesktop.impl.portal.desktop.gtk: Timeout was reached
Jul 12 11:49:30 ubuntu xdg-desktop-por[2146]: No skeleton to export
Jul 12 11:49:31 ubuntu systemd[1]: Reloading.
Jul 12 11:49:31 ubuntu systemd[1]: /lib/systemd/system/spice-vdagentd.service:8: PIDFile= references path below legacy directory /var/run/, updating /var/run/spice-vdagentd/spice-vdagentd.pid &#8594; /run/spice-vdagentd/spice-vdagentd.pid; please update the unit file accordingly.
Jul 12 11:49:31 ubuntu systemd[1]: Mounting Mount unit for gnome-characters, revision 254...
Jul 12 11:49:31 ubuntu systemd[1]: Mounted Mount unit for gnome-characters, revision 254.
Jul 12 11:49:31 ubuntu kernel: [  102.607752] kauditd_printk_skb: 30 callbacks suppressed
Jul 12 11:49:31 ubuntu kernel: [  102.607754] audit: type=1400 audit(1562932171.922:48): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.gnome-characters" pid=6061 comm="apparmor_parser"
Jul 12 11:49:32 ubuntu kernel: [  102.687174] audit: type=1400 audit(1562932172.002:49): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=6062 comm="apparmor_parser"
Jul 12 11:49:32 ubuntu kernel: [  103.214528] audit: type=1400 audit(1562932172.530:50): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6073 comm="apparmor_parser"
Jul 12 11:49:32 ubuntu kernel: [  103.214645] audit: type=1400 audit(1562932172.530:51): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6073 comm="apparmor_parser"
Jul 12 11:49:32 ubuntu kernel: [  103.235910] audit: type=1400 audit(1562932172.550:52): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=6075 comm="apparmor_parser"
Jul 12 11:49:32 ubuntu kernel: [  103.298596] audit: type=1400 audit(1562932172.614:53): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6076 comm="apparmor_parser"
Jul 12 11:49:32 ubuntu kernel: [  103.452000] audit: type=1400 audit(1562932172.766:54): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=6084 comm="apparmor_parser"
Jul 12 11:49:32 ubuntu kernel: [  103.477899] audit: type=1400 audit(1562932172.794:55): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.gnome-characters" pid=6086 comm="apparmor_parser"
Jul 12 11:49:33 ubuntu kernel: [  103.888245] audit: type=1400 audit(1562932173.202:56): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6094 comm="apparmor_parser"
Jul 12 11:49:33 ubuntu kernel: [  103.888426] audit: type=1400 audit(1562932173.202:57): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6094 comm="apparmor_parser"
Jul 12 11:49:36 ubuntu kernel: [  107.611130] kauditd_printk_skb: 27 callbacks suppressed
Jul 12 11:49:36 ubuntu kernel: [  107.611133] audit: type=1400 audit(1562932176.926:85): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6190 comm="apparmor_parser"
Jul 12 11:49:37 ubuntu kernel: [  107.965131] audit: type=1400 audit(1562932177.282:86): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=6198 comm="apparmor_parser"
Jul 12 11:49:37 ubuntu kernel: [  108.003295] audit: type=1400 audit(1562932177.318:87): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.gnome-characters" pid=6200 comm="apparmor_parser"
Jul 12 11:49:37 ubuntu kernel: [  108.404800] audit: type=1400 audit(1562932177.722:88): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6208 comm="apparmor_parser"
Jul 12 11:49:37 ubuntu kernel: [  108.404925] audit: type=1400 audit(1562932177.722:89): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6208 comm="apparmor_parser"
Jul 12 11:49:37 ubuntu kernel: [  108.426651] audit: type=1400 audit(1562932177.742:90): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=6210 comm="apparmor_parser"
Jul 12 11:49:37 ubuntu kernel: [  108.489843] audit: type=1400 audit(1562932177.806:91): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6211 comm="apparmor_parser"
Jul 12 11:49:37 ubuntu kernel: [  108.579468] audit: type=1400 audit(1562932177.894:92): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-characters" pid=6219 comm="apparmor_parser"
Jul 12 11:49:38 ubuntu kernel: [  108.877284] audit: type=1400 audit(1562932178.194:93): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=6220 comm="apparmor_parser"
Jul 12 11:49:38 ubuntu systemd[1]: Reloading.
Jul 12 11:49:38 ubuntu systemd[1]: /lib/systemd/system/spice-vdagentd.service:8: PIDFile= references path below legacy directory /var/run/, updating /var/run/spice-vdagentd/spice-vdagentd.pid &#8594; /run/spice-vdagentd/spice-vdagentd.pid; please update the unit file accordingly.
Jul 12 11:49:38 ubuntu systemd[1]: Mounting Mount unit for gnome-logs, revision 61...
Jul 12 11:49:38 ubuntu systemd[1]: Mounted Mount unit for gnome-logs, revision 61.
Jul 12 11:49:38 ubuntu kernel: [  109.392937] audit: type=1400 audit(1562932178.710:94): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.gnome-logs" pid=6337 comm="apparmor_parser"
Jul 12 11:49:42 ubuntu kernel: [  113.012498] kauditd_printk_skb: 25 callbacks suppressed
Jul 12 11:49:42 ubuntu kernel: [  113.012501] audit: type=1400 audit(1562932182.326:120): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6434 comm="apparmor_parser"
Jul 12 11:49:42 ubuntu kernel: [  113.012616] audit: type=1400 audit(1562932182.330:121): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6434 comm="apparmor_parser"
Jul 12 11:49:42 ubuntu kernel: [  113.033507] audit: type=1400 audit(1562932182.350:122): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=6436 comm="apparmor_parser"
Jul 12 11:49:42 ubuntu kernel: [  113.098713] audit: type=1400 audit(1562932182.414:123): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6437 comm="apparmor_parser"
Jul 12 11:49:42 ubuntu kernel: [  113.168664] audit: type=1400 audit(1562932182.486:124): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-logs" pid=6445 comm="apparmor_parser"
Jul 12 11:49:42 ubuntu kernel: [  113.462749] audit: type=1400 audit(1562932182.778:125): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-logs.gnome-logs" pid=6446 comm="apparmor_parser"
Jul 12 11:49:42 ubuntu kernel: [  113.566947] audit: type=1400 audit(1562932182.882:126): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-logs" pid=6454 comm="apparmor_parser"
Jul 12 11:49:43 ubuntu kernel: [  113.853910] audit: type=1400 audit(1562932183.170:127): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-logs.gnome-logs" pid=6455 comm="apparmor_parser"
Jul 12 11:49:43 ubuntu kernel: [  114.256457] audit: type=1400 audit(1562932183.570:128): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6463 comm="apparmor_parser"
Jul 12 11:49:43 ubuntu kernel: [  114.256664] audit: type=1400 audit(1562932183.574:129): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6463 comm="apparmor_parser"
Jul 12 11:49:44 ubuntu systemd[1885]: xdg-desktop-portal.service: Start operation timed out. Terminating.
Jul 12 11:49:44 ubuntu systemd[1885]: xdg-desktop-portal.service: Main process exited, code=killed, status=15/TERM
Jul 12 11:49:44 ubuntu systemd[1885]: xdg-desktop-portal.service: Failed with result 'timeout'.
Jul 12 11:49:44 ubuntu systemd[1885]: Failed to start Portal service.
Jul 12 11:49:46 ubuntu systemd[1]: Reloading.
Jul 12 11:49:46 ubuntu systemd[1]: /lib/systemd/system/spice-vdagentd.service:8: PIDFile= references path below legacy directory /var/run/, updating /var/run/spice-vdagentd/spice-vdagentd.pid &#8594; /run/spice-vdagentd/spice-vdagentd.pid; please update the unit file accordingly.
Jul 12 11:49:46 ubuntu systemd[1]: Mounting Mount unit for gnome-system-monitor, revision 77...
Jul 12 11:49:46 ubuntu systemd[1]: Mounted Mount unit for gnome-system-monitor, revision 77.
Jul 12 11:49:47 ubuntu kernel: [  118.398062] kauditd_printk_skb: 24 callbacks suppressed
Jul 12 11:49:47 ubuntu kernel: [  118.398065] audit: type=1400 audit(1562932187.714:154): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6669 comm="apparmor_parser"
Jul 12 11:49:47 ubuntu kernel: [  118.398157] audit: type=1400 audit(1562932187.714:155): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6669 comm="apparmor_parser"
Jul 12 11:49:47 ubuntu kernel: [  118.418731] audit: type=1400 audit(1562932187.734:156): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=6671 comm="apparmor_parser"
Jul 12 11:49:47 ubuntu kernel: [  118.483831] audit: type=1400 audit(1562932187.798:157): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6672 comm="apparmor_parser"
Jul 12 11:49:47 ubuntu kernel: [  118.634742] audit: type=1400 audit(1562932187.950:158): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-system-monitor.gnome-system-monitor" pid=6680 comm="apparmor_parser"
Jul 12 11:49:47 ubuntu kernel: [  118.653827] audit: type=1400 audit(1562932187.970:159): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.gnome-system-monitor" pid=6682 comm="apparmor_parser"
Jul 12 11:49:48 ubuntu kernel: [  119.055890] audit: type=1400 audit(1562932188.370:160): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6690 comm="apparmor_parser"
Jul 12 11:49:48 ubuntu kernel: [  119.056073] audit: type=1400 audit(1562932188.370:161): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6690 comm="apparmor_parser"
Jul 12 11:49:48 ubuntu kernel: [  119.080683] audit: type=1400 audit(1562932188.398:162): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=6692 comm="apparmor_parser"
Jul 12 11:49:48 ubuntu kernel: [  119.142669] audit: type=1400 audit(1562932188.458:163): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6693 comm="apparmor_parser"
Jul 12 11:49:53 ubuntu kernel: [  123.714518] kauditd_printk_skb: 32 callbacks suppressed
Jul 12 11:49:53 ubuntu kernel: [  123.714521] audit: type=1400 audit(1562932193.030:196): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6814 comm="apparmor_parser"
Jul 12 11:49:53 ubuntu kernel: [  123.714716] audit: type=1400 audit(1562932193.030:197): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6814 comm="apparmor_parser"
Jul 12 11:49:53 ubuntu kernel: [  123.739057] audit: type=1400 audit(1562932193.054:198): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=6816 comm="apparmor_parser"
Jul 12 11:49:53 ubuntu kernel: [  123.802382] audit: type=1400 audit(1562932193.118:199): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6817 comm="apparmor_parser"
Jul 12 11:49:53 ubuntu kernel: [  124.266990] audit: type=1400 audit(1562932193.582:200): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-system-monitor.gnome-system-monitor" pid=6825 comm="apparmor_parser"
Jul 12 11:49:53 ubuntu kernel: [  124.293112] audit: type=1400 audit(1562932193.610:201): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.gnome-system-monitor" pid=6827 comm="apparmor_parser"
Jul 12 11:49:54 ubuntu kernel: [  124.716132] audit: type=1400 audit(1562932194.030:202): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine" pid=6835 comm="apparmor_parser"
Jul 12 11:49:54 ubuntu kernel: [  124.716347] audit: type=1400 audit(1562932194.034:203): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/6673/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=6835 comm="apparmor_parser"
Jul 12 11:49:54 ubuntu kernel: [  124.738922] audit: type=1400 audit(1562932194.054:204): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=6837 comm="apparmor_parser"
Jul 12 11:49:54 ubuntu kernel: [  124.802237] audit: type=1400 audit(1562932194.118:205): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=6838 comm="apparmor_parser"
Jul 12 11:49:55 ubuntu systemd[1]: Reloading.
Jul 12 11:49:56 ubuntu systemd[1]: /lib/systemd/system/spice-vdagentd.service:8: PIDFile= references path below legacy directory /var/run/, updating /var/run/spice-vdagentd/spice-vdagentd.pid &#8594; /run/spice-vdagentd/spice-vdagentd.pid; please update the unit file accordingly.
Jul 12 11:49:56 ubuntu systemd[1]: Mounting Mount unit for gtk-common-themes, revision 1198...
Jul 12 11:49:56 ubuntu systemd[1]: Mounted Mount unit for gtk-common-themes, revision 1198.
Jul 12 11:49:58 ubuntu kernel: [  129.152678] kauditd_printk_skb: 10 callbacks suppressed
Jul 12 11:49:58 ubuntu kernel: [  129.152681] audit: type=1400 audit(1562932198.470:216): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-system-monitor.gnome-system-monitor" pid=7005 comm="apparmor_parser"
Jul 12 11:49:58 ubuntu kernel: [  129.267959] audit: type=1400 audit(1562932198.582:217): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-system-monitor" pid=7004 comm="apparmor_parser"
Jul 12 11:49:59 ubuntu kernel: [  129.727910] audit: type=1400 audit(1562932199.042:218): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=7014 comm="apparmor_parser"
Jul 12 11:49:59 ubuntu kernel: [  129.813817] audit: type=1400 audit(1562932199.130:219): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-characters" pid=7013 comm="apparmor_parser"
Jul 12 11:49:59 ubuntu kernel: [  130.254983] audit: type=1400 audit(1562932199.570:220): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=7023 comm="apparmor_parser"
Jul 12 11:49:59 ubuntu kernel: [  130.436093] audit: type=1400 audit(1562932199.750:221): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-characters" pid=7022 comm="apparmor_parser"
Jul 12 11:50:00 ubuntu kernel: [  130.933111] audit: type=1400 audit(1562932200.250:222): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-calculator.gnome-calculator" pid=7032 comm="apparmor_parser"
Jul 12 11:50:00 ubuntu kernel: [  131.558464] audit: type=1400 audit(1562932200.874:223): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-calculator" pid=7031 comm="apparmor_parser"
Jul 12 11:50:01 ubuntu kernel: [  132.040222] audit: type=1400 audit(1562932201.354:224): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-logs.gnome-logs" pid=7041 comm="apparmor_parser"
Jul 12 11:50:01 ubuntu kernel: [  132.634927] audit: type=1400 audit(1562932201.950:225): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-logs" pid=7040 comm="apparmor_parser"
Jul 12 11:50:03 ubuntu kernel: [  134.323316] kauditd_printk_skb: 2 callbacks suppressed
Jul 12 11:50:03 ubuntu kernel: [  134.323320] audit: type=1400 audit(1562932203.638:228): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-calculator.gnome-calculator" pid=7059 comm="apparmor_parser"
Jul 12 11:50:04 ubuntu kernel: [  135.054329] audit: type=1400 audit(1562932204.370:229): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-calculator" pid=7058 comm="apparmor_parser"
Jul 12 11:50:04 ubuntu kernel: [  135.528593] audit: type=1400 audit(1562932204.846:230): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-characters.gnome-characters" pid=7068 comm="apparmor_parser"
Jul 12 11:50:05 ubuntu kernel: [  136.300409] audit: type=1400 audit(1562932205.618:231): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-characters" pid=7067 comm="apparmor_parser"
Jul 12 11:50:06 ubuntu kernel: [  136.840589] audit: type=1400 audit(1562932206.158:232): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-system-monitor.gnome-system-monitor" pid=7077 comm="apparmor_parser"
Jul 12 11:50:06 ubuntu kernel: [  137.554869] audit: type=1400 audit(1562932206.870:233): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-system-monitor" pid=7076 comm="apparmor_parser"
Jul 12 11:50:07 ubuntu systemd[1]: Started Wait until snapd is fully seeded.
Jul 12 11:50:07 ubuntu systemd[1]: Condition check resulted in Auto import assertions from block devices being skipped.
Jul 12 11:50:07 ubuntu systemd[1]: Reached target Multi-User System.
Jul 12 11:50:11 ubuntu ntfsresize: ntfsresize v2017.3.23AR.3 (libntfs-3g)
Jul 12 11:50:11 ubuntu ntfsresize: Device name        : /dev/sda3
Jul 12 11:50:11 ubuntu ntfsresize: NTFS volume version: 3.1
Jul 12 11:50:11 ubuntu ntfsresize: Cluster size       : 4096 bytes
Jul 12 11:50:11 ubuntu ntfsresize: Current volume size: 499524825600 bytes (499525 MB)
Jul 12 11:50:11 ubuntu ntfsresize: Current device size: 499524829184 bytes (499525 MB)
Jul 12 11:50:11 ubuntu ntfsresize: Checking filesystem consistency ...
Jul 12 11:50:11 ubuntu ntfsresize: Accounting clusters ...
Jul 12 11:50:11 ubuntu ntfsresize: Space in use       : 223895 MB (44.8%)
Jul 12 11:50:11 ubuntu ntfsresize: Collecting resizing constraints ...
Jul 12 11:50:11 ubuntu ntfsresize: You might resize at 223894122496 bytes or 223895 MB (freeing 275630 MB).
Jul 12 11:50:11 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Jul 12 11:50:11 ubuntu systemd[1]: tmp-tmp.DoFrcRQVsV.mount: Succeeded.
Jul 12 11:50:11 ubuntu systemd[1885]: tmp-tmp.DoFrcRQVsV.mount: Succeeded.
Jul 12 11:50:11 ubuntu systemd[1885]: tmp-tmp.GhDbJ7qMfG.mount: Succeeded.
Jul 12 11:50:11 ubuntu systemd[1]: tmp-tmp.GhDbJ7qMfG.mount: Succeeded.
Jul 12 11:50:11 ubuntu systemd[1885]: tmp-tmp.2kdqznf34Y.mount: Succeeded.
Jul 12 11:50:11 ubuntu systemd[1]: tmp-tmp.2kdqznf34Y.mount: Succeeded.
Jul 12 11:50:12 ubuntu systemd[1885]: tmp-tmp.S1YxHmn2E6.mount: Succeeded.
Jul 12 11:50:12 ubuntu systemd[1]: tmp-tmp.S1YxHmn2E6.mount: Succeeded.
Jul 12 11:50:12 ubuntu systemd[1885]: tmp-tmp.i8rnjuth5G.mount: Succeeded.
Jul 12 11:50:12 ubuntu systemd[1]: tmp-tmp.i8rnjuth5G.mount: Succeeded.
Jul 12 11:50:12 ubuntu systemd[1885]: tmp-tmp.Yx7QysZkMs.mount: Succeeded.
Jul 12 11:50:12 ubuntu systemd[1]: tmp-tmp.Yx7QysZkMs.mount: Succeeded.
Jul 12 11:50:12 ubuntu kernel: [  143.195468] ntfs: driver 2.1.32 [Flags: R/O MODULE].
Jul 12 11:50:12 ubuntu kernel: [  143.228806] QNX4 filesystem 0.2.3 registered.
Jul 12 11:50:12 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: mounted using GRUB ext2 filesystem driver
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Jul 12 11:50:13 ubuntu 05efi: debug: Not on UEFI platform
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jul 12 11:50:13 ubuntu 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jul 12 11:50:13 ubuntu 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jul 12 11:50:13 ubuntu macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jul 12 11:50:13 ubuntu 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jul 12 11:50:13 ubuntu 30utility: debug: /dev/sda1 is not a FAT partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Jul 12 11:50:13 ubuntu 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Jul 12 11:50:13 ubuntu systemd[1]: var-lib-os\x2dprober-mount.mount: Succeeded.
Jul 12 11:50:13 ubuntu systemd[1885]: var-lib-os\x2dprober-mount.mount: Succeeded.
Jul 12 11:50:13 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Jul 12 11:50:13 ubuntu 05efi: debug: Not on UEFI platform
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jul 12 11:50:13 ubuntu 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jul 12 11:50:13 ubuntu 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jul 12 11:50:13 ubuntu macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jul 12 11:50:13 ubuntu 20microsoft: debug: /dev/sda2 is a NTFS partition
Jul 12 11:50:13 ubuntu 20microsoft: result: /dev/sda2:Windows 10:Windows:chain
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
Jul 12 11:50:13 ubuntu systemd[1]: var-lib-os\x2dprober-mount.mount: Succeeded.
Jul 12 11:50:13 ubuntu systemd[1885]: var-lib-os\x2dprober-mount.mount: Succeeded.
Jul 12 11:50:13 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jul 12 11:50:13 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: mounted using GRUB ntfs filesystem driver
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/05efi
Jul 12 11:50:13 ubuntu 05efi: debug: Not on UEFI platform
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Jul 12 11:50:13 ubuntu 10freedos: debug: /dev/sda3 is not a FAT partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Jul 12 11:50:13 ubuntu 10qnx: debug: /dev/sda3 is not a QNX4 partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20macosx
Jul 12 11:50:13 ubuntu macosx-prober: debug: /dev/sda3 is not an HFS+ partition: exiting
Jul 12 11:50:13 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Jul 12 11:50:13 ubuntu 20microsoft: debug: /dev/sda3 is a NTFS partition
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Jul 12 11:50:14 ubuntu 30utility: debug: /dev/sda3 is not a FAT partition: exiting
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Jul 12 11:50:14 ubuntu 83haiku: debug: /dev/sda3 is not a BeFS partition: exiting
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Jul 12 11:50:14 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/efi
Jul 12 11:50:14 ubuntu systemd[1]: var-lib-os\x2dprober-mount.mount: Succeeded.
Jul 12 11:50:14 ubuntu systemd[1885]: var-lib-os\x2dprober-mount.mount: Succeeded.
Jul 12 11:50:14 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sdb1
Jul 12 11:50:14 ubuntu 05efi: debug: Not on UEFI platform
Jul 12 11:50:14 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Jul 12 11:50:14 ubuntu 10freedos: debug: /dev/sdb1 is a FAT32 partition
Jul 12 11:50:14 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Jul 12 11:50:14 ubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Jul 12 11:50:14 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Jul 12 11:50:14 ubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Jul 12 11:50:14 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Jul 12 11:50:14 ubuntu 20microsoft: debug: /dev/sdb1 is a FAT32 partition
Jul 12 11:50:14 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Jul 12 11:50:14 ubuntu 30utility: debug: /dev/sdb1 is a FAT32 partition
Jul 12 11:50:15 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Jul 12 11:50:15 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Jul 12 11:50:15 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Jul 12 11:50:15 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdb1
Jul 12 11:50:15 ubuntu 83haiku: debug: /dev/sdb1 is not a BeFS partition: exiting
Jul 12 11:50:15 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Jul 12 11:50:15 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Jul 12 11:50:15 ubuntu ubiquity[1954]: Device /dev/sda1 not found in os-prober output
Jul 12 11:50:15 ubuntu ubiquity[1954]: Device /dev/sda3 not found in os-prober output
Jul 12 11:50:15 ubuntu ubiquity[1954]: switched to page partman
Jul 12 11:50:20 ubuntu ubiquity[1954]: message repeated 2 times: [ switched to page partman]
Jul 12 11:50:20 ubuntu ubiquity: /lib/partman/choose_partition/60partition_tree/do_option: 205: /lib/partman/choose_partition/60partition_tree/do_option: /lib/partman/active_partition/copy/choices: not found
Jul 12 11:50:21 ubuntu ubiquity: message repeated 2 times: [ /lib/partman/choose_partition/60partition_tree/do_option: 205: /lib/partman/choose_partition/60partition_tree/do_option: /lib/partman/active_partition/copy/choices: not found]
Jul 12 11:50:21 ubuntu ubiquity[1954]: switched to page partman
Jul 12 11:50:33 ubuntu ubiquity: /lib/partman/choose_partition/60partition_tree/do_option: 205: /lib/partman/choose_partition/60partition_tree/do_option: /lib/partman/active_partition/copy/choices: not found
Jul 12 11:50:35 ubuntu ubiquity: message repeated 3 times: [ /lib/partman/choose_partition/60partition_tree/do_option: 205: /lib/partman/choose_partition/60partition_tree/do_option: /lib/partman/active_partition/copy/choices: not found]
Jul 12 11:53:21 ubuntu PackageKit: daemon quit
Jul 12 11:53:21 ubuntu systemd[1]: packagekit.service: Main process exited, code=killed, status=15/TERM
Jul 12 11:53:21 ubuntu systemd[1]: packagekit.service: Succeeded.
Jul 12 11:55:26 ubuntu kernel: [  457.333793] radeon_dp_aux_transfer_native: 158 callbacks suppressed
Jul 12 11:55:26 ubuntu systemd[1]: Started Getty on tty2.
Jul 12 11:55:32 ubuntu systemd[1]: Started Session 2 of user ubuntu.

```

installer debug:

```
Ubiquity 19.04.9/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:54: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GObject, GLib, Atk, Gio


(ubiquity:1954): IBUS-WARNING **: 11:48:15.997: The owner of /home/ubuntu/.config/ibus/bus is not root!
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:5: PyGIWarning: NM was imported without specifying a version first. Use gi.require_version('NM', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import NM, NMA
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:5: PyGIWarning: NMA was imported without specifying a version first. Use gi.require_version('NMA', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import NM, NMA
/usr/lib/ubiquity/plugins/ubi-timezone.py:195: PyGIWarning: TimezoneMap was imported without specifying a version first. Use gi.require_version('TimezoneMap', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import TimezoneMap
No such schema &#8220;org.gnome.nautilus.desktop&#8221;
Failed to play sound: File or data not found
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
update_release_notes_label()
/usr/lib/ubiquity/ubiquity/misc.py:668: PyGIWarning: Xkl was imported without specifying a version first. Use gi.require_version('Xkl', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Xkl, GdkX11
update_release_notes_label()
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
Could not translate page (prepare): 'NoneType' object has no attribute 'replace'
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 457 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:116: Warning: Source ID 1211 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:138: Warning: Source ID 463 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:138: Warning: Source ID 1299 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:72: Warning: Source ID 1287 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_layout_timeout_id)
/usr/lib/ubiquity/plugins/ubi-console-setup.py:74: Warning: Source ID 1426 was not found when attempting to remove it
  GLib.source_remove(self.keyboard_variant_timeout_id)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
/usr/lib/ubiquity/ubiquity/segmented_bar.py:34: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import GObject, Gdk, Gtk, PangoCairo


(ubiquity:1954): Gtk-CRITICAL **: 11:50:21.703: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed


(ubiquity:1954): Gtk-CRITICAL **: 11:50:21.704: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed


(ubiquity:1954): Gtk-CRITICAL **: 11:50:21.704: gtk_widget_set_allocation: assertion '_gtk_widget_get_visible (widget) || _gtk_widget_is_toplevel (widget)' failed
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
XDG_RUNTIME_DIR (/run/user/999) is not owned by us (uid 0), but by uid 999! (This could e g happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)



```

---

### Post by oldfred on 2019-07-13
Changed quote to code tags.

Partition issues are most common related to Windows fast start up being on. That sets hibernation flag and prevents Linux NTFS driver from fully seeing NTFS partitions. Check that fast start up is off.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If SSD or NVMe SSD, then you need firmware update for SSD, even if new.
And almost all systems need UEFI update, even if new.

Best to resize NTFS partitions with Windows own partitioning tools and reboot immediately, so it can run chkdsk. Linux  tools, installer or gparted normally work, but when they do not (usually Windows issue) users blame Linux. If you use Windows issues are resolved or apparently Windows related.

---

