---
title: "unable to boot kernel 6.2.0-32"
date: 2023-09-09
forum: Installation &amp; Upgrades
---

### Post by chopra on 2023-09-09
Hi guys,
I have a bit of an unusual problem. My kernel updated recently, from 6.2.0-31 to 6.2.0-32 (I think), and the system will not fully boot up from the grub menu with the most recent kernel.
If I go to advanced options from the grub menu, then select the previous kernel, (6.2.0-31), it seems to work fine.

I cannot copy and paste, or take a screen shot, during the bootup process, but I do remember seeing something about kernel null pointer. 
There was also something about processes involving userspace out-of-memory process killer, timy syncronization, and network name resolution not being completed.
After booting with the older kernel, I did perform the following commands:

```
systemctl status systemd-timesyncd.service

systemctl status systemd-oomd.service

systemctl status systemd-resolved.service
```

which gave the following output:

```
&#9679; systemd-timesyncd.service - Network Time Synchronization
     Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2023-09-08 23:43:31 EDT; 5min ago
       Docs: man:systemd-timesyncd.service(8)
   Main PID: 505 (systemd-timesyn)
     Status: "Initial synchronization to time server [2620:2d:4000:1::41]:123 (ntp.ubuntu.com)."
      Tasks: 2 (limit: 18809)
     Memory: 1.4M
        CPU: 89ms
     CGroup: /system.slice/systemd-timesyncd.service
             &#9492;&#9472;505 /lib/systemd/systemd-timesyncd

Sep 08 23:43:31 dynabook-TECRA-A50-F systemd[1]: Starting Network Time Synchronization...
Sep 08 23:43:31 dynabook-TECRA-A50-F systemd[1]: Started Network Time Synchronization.
Sep 08 23:44:02 dynabook-TECRA-A50-F systemd-timesyncd[505]: Initial synchronization to time server [2620:2d:4000:1::41]:123 (ntp.ubuntu.com).
&#9679; systemd-oomd.service - Userspace Out-Of-Memory (OOM) Killer
     Loaded: loaded (/lib/systemd/system/systemd-oomd.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2023-09-08 23:43:31 EDT; 5min ago
       Docs: man:systemd-oomd.service(8)
   Main PID: 499 (systemd-oomd)
     Status: "Processing requests..."
      Tasks: 1 (limit: 18809)
     Memory: 1.4M (min: 64.0M low: 64.0M)
        CPU: 532ms
     CGroup: /system.slice/systemd-oomd.service
             &#9492;&#9472;499 /lib/systemd/systemd-oomd

Sep 08 23:43:31 dynabook-TECRA-A50-F systemd[1]: Starting Userspace Out-Of-Memory (OOM) Killer...
Sep 08 23:43:31 dynabook-TECRA-A50-F systemd[1]: Started Userspace Out-Of-Memory (OOM) Killer.
&#9679; systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/lib/systemd/system/systemd-resolved.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2023-09-08 23:43:32 EDT; 6min ago
       Docs: man:systemd-resolved.service(8)
             man:org.freedesktop.resolve1(5)
             [https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers](https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers)
             [https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients](https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients)
   Main PID: 501 (systemd-resolve)
     Status: "Processing requests..."
      Tasks: 1 (limit: 18809)
     Memory: 9.5M
        CPU: 177ms
     CGroup: /system.slice/systemd-resolved.service
             &#9492;&#9472;501 /lib/systemd/systemd-resolved

Sep 08 23:43:31 dynabook-TECRA-A50-F systemd[1]: Starting Network Name Resolution...
Sep 08 23:43:31 dynabook-TECRA-A50-F systemd-resolved[501]: Positive Trust Anchors:
Sep 08 23:43:31 dynabook-TECRA-A50-F systemd-resolved[501]: . IN DS 20326 8 2 e06d44b80b8f1d39a95c0b0d7c65d08458e880409bbc683457104237c7f8ec8d
Sep 08 23:43:31 dynabook-TECRA-A50-F systemd-resolved[501]: Negative trust anchors: home.arpa 10.in-addr.arpa 16.172.in-addr.arpa 17.172.in-addr.arpa 18.172.in-addr.arpa 19.172.in-addr.arpa 20.172.in-addr.arpa 21.172.in-addr.arpa 22.172.in-addr.arpa 23.172.in-addr.arpa 24.172.in-addr.arpa 25.172.in-addr.arpa 26.172.in-addr.arpa 27.172.in-addr.arpa 28.172.in-addr.arpa 29.172.in-addr.arpa 30.172.in-addr.arpa 31.172.in-addr.arpa 168.192.in-addr.arpa d.f.ip6.arpa corp home internal intranet lan local private test
Sep 08 23:43:31 dynabook-TECRA-A50-F systemd-resolved[501]: Using system hostname 'dynabook-TECRA-A50-F'.
Sep 08 23:43:32 dynabook-TECRA-A50-F systemd[1]: Started Network Name Resolution.
Sep 08 23:43:37 dynabook-TECRA-A50-F systemd-resolved[501]: wlp1s0: Bus client set search domain list to: hsd1.mi.comcast.net
Sep 08 23:43:37 dynabook-TECRA-A50-F systemd-resolved[501]: wlp1s0: Bus client set default route setting: yes
Sep 08 23:43:37 dynabook-TECRA-A50-F systemd-resolved[501]: wlp1s0: Bus client set DNS server list to: 75.75.75.75, 75.75.76.76
Sep 08 23:43:39 dynabook-TECRA-A50-F systemd-resolved[501]: wlp1s0: Bus client set DNS server list to: 75.75.75.75, 75.75.76.76, 2001:558:feed::1, 2001:558:feed
```

Also, here is the output of the command ```
vdir /boot
```
```
total 261436
-rw-r--r-- 1 root root   262053 Aug 14 05:05 config-5.15.0-83-generic
-rw-r--r-- 1 root root   275587 Aug 16 05:42 config-6.2.0-31-generic
-rw-r--r-- 1 root root   275587 Aug 18 05:38 config-6.2.0-32-generic
drwx------ 4 root root     4096 Dec 31  1969 efi
drwxr-xr-x 5 root root     4096 Sep  5 21:16 grub
lrwxrwxrwx 1 root root       28 Sep  5 21:15 initrd.img -> initrd.img-5.15.0-83-generic
-rw-r--r-- 1 root root 65684040 Sep  5 21:15 initrd.img-5.15.0-83-generic
-rw-r--r-- 1 root root 69602500 Sep  4 10:56 initrd.img-6.2.0-31-generic
-rw-r--r-- 1 root root 69599829 Sep  5 21:15 initrd.img-6.2.0-32-generic
lrwxrwxrwx 1 root root       27 Sep  5 21:16 initrd.img.old -> initrd.img-6.2.0-32-generic
-rw-r--r-- 1 root root   182800 Feb  6  2022 memtest86+.bin
-rw-r--r-- 1 root root   184476 Feb  6  2022 memtest86+.elf
-rw-r--r-- 1 root root   184980 Feb  6  2022 memtest86+_multiboot.bin
-rw------- 1 root root  6273612 Aug 14 05:05 System.map-5.15.0-83-generic
-rw------- 1 root root  7967590 Aug 16 05:42 System.map-6.2.0-31-generic
-rw------- 1 root root  7969006 Aug 18 05:38 System.map-6.2.0-32-generic
lrwxrwxrwx 1 root root       25 Sep  5 21:15 vmlinuz -> vmlinuz-5.15.0-83-generic
-rw------- 1 root root 11615656 Aug 14 05:07 vmlinuz-5.15.0-83-generic
-rw------- 1 root root 13796616 Aug 16 08:43 vmlinuz-6.2.0-31-generic
-rw------- 1 root root 13791304 Aug 18 05:40 vmlinuz-6.2.0-32-generic
lrwxrwxrwx 1 root root       24 Sep  5 21:15 vmlinuz.old -> vmlinuz-6.2.0-32-generic

```

I noticed that the sofltlink with the .old suffix is pointing to the most recent kernel.
Not sure if that information helps or not.
My hardware is a Tecra dynabook intel core i7.

Thanks for any insights,
Chopra

---

### Post by deadflowr on 2023-09-09
Very interesting.
You seem to have both the 5.15 kernels series and the 6.2 kernel series installed.
It seems to be defaulting to the 5.15 since that is set as the current in /boot.

Is this a single boot system or dual/multiple-boot system?

Do you have anything setup to manipulate grub?
Like grub-customizer or a manually customized script like from this:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")


Anyway, your log files in /var/log can help as they should contain the output you saw during the odd bootups.
Probably look at dmesg, kern.log. syslog and you can also use systemd's journalctl commands to view a spew of various logging information.


Sorry I'm not being more helpful, I guess.

---

### Post by srdawson on 2023-09-13
I'm having the same issue and have been digging through the logs. Nothing I am finding indicates there is an issue, it just completes the boot process, then stalls on an empty console line. Not seeing anything fancy being done with grub, other than me removing 'quiet splash` from grub's DEFAULT parameter. I'm not exactly experienced with kernel debuging though. I'm about to do another with `nomodeset` and then compile the logs to share here.

---

### Post by srdawson on 2023-09-13
turns out the logs are getting overwritten by the most recent successful boot, which makes getting them a little difficult. Unless someone has a quick answer here to address that, I've got some man pages to read.

---

### Post by chopra on 2023-09-14
Thanks for the response.
I have been unable to connect to the ubuntu forums recently.

The kern.log has about a thousand lines, the journalctl is has five times as many.

Here is something that may be of intereset.
```

Sep 12 00:11:01 dynabook-TECRA-A50-F kernel: [11168.260790] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
Sep 12 23:10:41 dynabook-TECRA-A50-F kernel: [    0.000000] Kernel is locked down from EFI Secure Boot mode; see man kernel_lockdown.7
Sep 12 23:10:41 dynabook-TECRA-A50-F kernel: [    0.205984] LSM: initializing lsm=lockdown,capability,landlock,yama,integrity,apparmor
Sep 12 23:10:41 dynabook-TECRA-A50-F kernel: [    1.086864] Lockdown: swapper/0: hibernation is restricted; see man kernel_lockdown.7
Sep 12 23:10:41 dynabook-TECRA-A50-F kernel: [    3.980170] Lockdown: systemd: /dev/mem,kmem,port is restricted; see man kernel_lockdown.7
Sep 12 23:10:45 dynabook-TECRA-A50-F kernel: [    9.829113] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
Sep 12 23:11:01 dynabook-TECRA-A50-F kernel: [   25.314443] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7
Sep 12 23:28:02 dynabook-TECRA-A50-F kernel: [ 1048.053698] Lockdown: systemd-logind: hibernation is restricted; see man kernel_lockdown.7

```

I don't know if that's related or not.
Chopra

---

### Post by chopra on 2023-09-24
With the new kernel, 6.2.0-33, the problem seems to have resolved itself.
Whatever it was, the kernel developers must have fixed it, because I have 6.2.0-33 and 6.2.0-31 in my boot directory, but not 6.2.0-32.

---

### Post by chopra on 2023-09-25
actually, the problem started up again with the new kernel as well.
I don't know how to un-mark this solved, but no-one seemed to know the solution.
I may just remap the symlink to 6.2.0-31
I should probably make it immutable as well, to prevent it from being deleted until a newer one starts to work.

Chopra

---

