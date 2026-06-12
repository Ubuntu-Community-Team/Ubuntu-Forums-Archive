---
title: "Ubuntu 22.04 booting too slow (27.88 seconds)"
date: 2024-03-23
forum: Installation &amp; Upgrades
---

### Post by Alexboy on 2024-03-23
Hallo everyone,

My Ubuntu 22.04 is booting very slow, it takes around 28 seconds in total. It shouldn't be any hardware problem, because I consider my PC to be powerful. :-) Meaning, i5 12400 CPU, RX 6600XT GPU and 16 GB RAM.
Any chance to get it to start within seconds?
By the way, I started counting only from the GRUB menu. After Ubuntu being chosen, I started the the timer. If anybody wants, I could record it with my phone.

---

### Post by Impavidus on 2024-03-23
Maybe this will give some lead:```
systemd-analyze blame
```
Also, what kind of harddrive have you got? On a modern SDD, you should be able to boot faster than that, but if your Ubuntu is installed on a spinning hard drive, 27 seconds isn't too bad. It won't get as fast as Windows 8+ with standard settings, as that doesn't really boot. It's more like restoring from hibernation. Boot time on Ubuntu should be shorter than an actual boot on Windows.

---

### Post by oldfred on 2024-03-23
Do you have SSD or only HDD?
Boot is a lot faster with SSD. I changed from SSD to NVMe type SSD and it is a bit faster my  older system. But person at keyboard still seems to be bottleneck, and if anything getting slower?

Some settings you can review. Older post on 20.04, but still applies to newer versions.
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

I now have Kubuntu on NVMe type SSD. I do not allow any snaps. Same set of adjustments as above:
```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo systemd-analyze [/COLOR]
Startup finished in 4.022s (kernel) + 5.381s (userspace) = 9.404s  
graphical.target reached after 5.352s in userspace

[/FONT]
```

---

### Post by Alexboy on 2024-03-23
```
systemd-analyze blame
```

```
4.426s e2scrub_reap.service[/COLOR]
4.183s mysql.service
2.359s snapd.service
1.948s waydroid-container.service
1.873s winbind.service
1.640s libvirtd.service
1.501s systemd-journal-flush.service
1.476s dev-sda2.device
1.446s cups.service
1.402s networkd-dispatcher.service
1.380s snapd.seeded.service
1.272s udisks2.service
1.244s apache2.service
1.180s ModemManager.service
1.155s lxc-net.service
1.051s dev-loop19.device
1.041s dev-loop17.device
1.036s dev-loop16.device
1.031s dev-loop15.device
1.017s dev-loop14.device
1.007s dev-loop21.device
 999ms dev-loop20.device
 981ms dev-loop13.device
 975ms dev-loop18.device
 975ms dev-loop8.device
 961ms dev-loop12.device
 958ms dev-loop11.device
 950ms dev-loop9.device
 945ms dev-loop2.device
 944ms dev-loop10.device
 944ms dev-loop7.device
 908ms dev-loop1.device
 846ms accounts-daemon.service

```

```
[FONT=monospace][COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo systemd-analyze  [/COLOR]
[sudo] password for alex:  
Startup finished in 18.106s (firmware) + 6.215s (loader) + 7.851s (kernel) + 7.971s (userspace) = 40.144s  
graphical.target reached after 7.926s in userspace
[/FONT]
```

I bought Samsung 980 EVO SSD 1TB last year, so, it should be faster. ;-)

---

### Post by MAFoElffen on 2024-03-23
??? 28 seconds is not bad.

I have a whole lot going on, is 2nd Gen Intel i7, with 3 SSD's, and mine is this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo systemd-analyze
Startup finished in 8.572s (kernel) + 12.012s (userspace) = 20.585s 
graphical.target reached after 11.968s in userspace

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -o model | grep -v -e '^$'
MODEL
Samsung SSD 870 QVO 2TB
Samsung SSD 870 QVO 2TB
Dogfish SSD 2TB

```
It would be less without NetworkManager (using networkd):
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @11.968s
&#9492;&#9472;multi-user.target @11.967s
  &#9492;&#9472;smbd.service @11.795s +138ms
    &#9492;&#9472;nmbd.service @11.624s +136ms
      &#9492;&#9472;network-online.target @11.584s
        &#9492;&#9472;NetworkManager-wait-online.service @4.568s +7.015s
          &#9492;&#9472;NetworkManager.service @4.295s +264ms
            &#9492;&#9472;dbus.service @4.290s
              &#9492;&#9472;basic.target @4.274s
                &#9492;&#9472;sockets.target @4.274s
                  &#9492;&#9472;cockpit.socket @4.244s +29ms
                    &#9492;&#9472;sysinit.target @4.208s
                      &#9492;&#9472;snapd.apparmor.service @3.955s +252ms
                        &#9492;&#9472;apparmor.service @3.700s +210ms
                          &#9492;&#9472;local-fs.target @3.698s
                            &#9492;&#9472;run-snapd-ns-snapd\x2ddesktop\x2dintegration.mnt.>
                              &#9492;&#9472;run-snapd-ns.mount @6.794s
                                &#9492;&#9472;swap.target @2.086s
                                  &#9492;&#9472;dev-mapper-swap.swap @2.069s +15ms
                                    &#9492;&#9472;dev-mapper-swap.device @2.067s
lines 1-23/23 (END)

```

---

### Post by Alexboy on 2024-03-24
[FONT=monospace]My 40.144s compared to your 20.585s is almost two times longer. Plus, my 28 secs is the time I start counting after I've chosen Ubuntu from the Grub menu.[/FONT]
[FONT=monospace]Compared to other OS, I'd say it's pretty slow. Doesn't mean my expectations. Otherwise I have no complaints, Ubuntu 22.04 works flawlessly, any task is done very fast.[/FONT]
[FONT=monospace]But the booting time? It's just slow.[/FONT]

[FONT=monospace]Thank you for the links, @odlfred.[/FONT]
[FONT=monospace]What I've done so far:[/FONT]
[FONT=monospace]changed "quiet splash" to "noplymouth". No effect.[/FONT]
[FONT=monospace]disabled fast boot and secure boot disabled, or switched to "other OS".[/FONT]
[FONT=monospace]Disabled (systemctl mask ...) a few services:[/FONT]

```
[FONT=Ubuntu Mono]4.183s mysql.service[/FONT]
[FONT=Ubuntu Mono]2.359s snapd.service[/FONT]
[FONT=Ubuntu Mono]1.948s waydroid-container.service[/FONT]
[FONT=Ubuntu Mono]1.873s winbind.service[/FONT]
[FONT=Ubuntu Mono]1.640s libvirtd.service
apache2.service
[/FONT]
```[FONT=Ubuntu Mono]
[SIZE=3]And also the "network waiting service" (forgot the name).
Literally, no changes, still counting around 28 seconds.[/SIZE][/FONT][COLOR=#000000][SIZE=3]
[/SIZE]
[/COLOR]

---

### Post by MAFoElffen on 2024-03-24
Disabling libvirtd will break KVM. That is what it uses to visualize it's VM's...

For Network connection waiting during boot (I see you use networkd)... I add "optional: yes" to each connection. That skips the wait for a connection at boot.

If a machine is using NetworkManager, then I disable NetworkManager-wait-online.service and mask it. (I just did that on this laptop and saved 7 seconds.)
```

sudo systemctl disable NetworkManager.service
sudo systemctl mask NetworkManager.service

```
I have lxd and libvirtd, which I need, so I live with.

e2scrub_reap.service removes old stale snapshots at boot. It removes them since they are a waste of storage. But if you do not have LVM installed, then it is doing nothing, but a futile search for something that is not there (it is installed by default).
```

sudo systemctl disable e2scrub_reap.service
sudo systemctl mask e2scrub_reap.service

```
plymouth-quit-wait.service waits for all services are ready before leaving the splash screen. If you are not using plymouth, then it is not doing anything.
```

sudo systemctl disable plymouth-quit-wait.service 
sudo systemctl mask plymouth-quit-wait.service

```
I check and update my firmware myself, so I remove the autmated step in the boot process
```

sudo systemctl disable fwupdate.service
sudo systemctl mask fwupd.service

```
The avahi-daemon service is used to discover local network resources. If you do not need any quick search for local network resources, such as printers & scanners, then you can disable it
```

sudo systemctl disable avahi-daemon.service
sudo systemctl diable avahi-daemon.service

```
ModemManager service automatically sets up and connects 2G/3G/4G/5G modems and provides a high level of abstraction when interacting with modems. If ou are not using a WAN Card, you don't need that
```

sudo systemctl disable ModemManager.service
sudo systemctl mask ModemManager.service

```

Those are a few things off the top of my head to recommend.

---

### Post by Alexboy on 2024-03-24
I'm using two SSD's, so I don't know, if I'm using LVM. That's why I didn't disable the [COLOR=#000000][FONT=&quot]e2scrub_reap.service.
After disabling and masking the "[/FONT][/COLOR][COLOR=#000000][FONT=&quot]NetworkManager.service", I no longer had the internet connection.
I also left the [/FONT][/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]avahi-daemon.service, cause I'm using the HP Printer, wirelessly connected.

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ systemd-analyze  [/COLOR]
Startup finished in 19.272s (firmware) + 15.340s (loader) + 8.132s (kernel) + 5.999s (userspace) = 48.744s  
graphical.target reached after 5.974s in userspace
[COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```
[FONT=Ubuntu Mono, monospace][COLOR=#000000]I'm stucked with the [/COLOR][/FONT][FONT=monospace]48.744s.

```
[/FONT][FONT=monospace][COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ systemd-analyze critical-chain[/COLOR]
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @5.974s
&#9492;&#9472;multi-user.target @4.560s
  &#9492;&#9472;[COLOR=#FF5454]**winbind.service @3.492s +1.065s**[/COLOR][COLOR=#000000][/COLOR]
    &#9492;&#9472;network.target @3.408s
      &#9492;&#9472;[COLOR=#FF5454]**NetworkManager.service @3.028s +378ms**[/COLOR][COLOR=#000000][/COLOR]
        &#9492;&#9472;dbus.service @3.026s
          &#9492;&#9472;basic.target @2.988s
            &#9492;&#9472;sockets.target @2.987s
              &#9492;&#9472;virtlogd-admin.socket @2.987s
                &#9492;&#9472;virtlogd.socket @2.987s
                  &#9492;&#9472;sysinit.target @2.971s
                    &#9492;&#9472;[COLOR=#FF5454]**snapd.apparmor.service @2.813s +157ms**[/COLOR][COLOR=#000000][/COLOR]
                      &#9492;&#9472;[COLOR=#FF5454]**apparmor.service @2.649s +161ms**[/COLOR][COLOR=#000000][/COLOR]
                        &#9492;&#9472;local-fs.target @2.648s
                          &#9492;&#9472;var-lib-lxcfs.mount @3.246s
                            &#9492;&#9472;local-fs-pre.target @1.291s
                              &#9492;&#9472;[COLOR=#FF5454]**systemd-tmpfiles-setup-dev.service @1.223s +66ms**[/COLOR][COLOR=#000000][/COLOR]
                                &#9492;&#9472;[COLOR=#FF5454]**systemd-sysusers.service @1.192s +29ms**[/COLOR][COLOR=#000000][/COLOR]
                                  &#9492;&#9472;[COLOR=#FF5454]**systemd-remount-fs.service @1.127s +62ms**[/COLOR][COLOR=#000000][/COLOR]
                                    &#9492;&#9472;systemd-journald.socket @1.098s
                                      &#9492;&#9472;-.mount @1.057s
                                        &#9492;&#9472;-.slice @1.057s
[COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT][FONT=monospace]
```

On the other hand, I have IdeaPad Flex 5 CB, which originally (as a Chromebook) came with the ChromeOS, but I uninstalled it and installed Manjaro. From pushing the start button (or just opening the lid) till full booted, you'd never guess, around 18 seconds.

Any other ideas? Could it also be the consequence of me updating the 20.04 to the 22.04?
[/FONT]

---

### Post by MAFoElffen on 2024-03-24
Please show the output of these
```

grep . /etc/netplan/*.yaml
lsblk -e7 -o name,size,fstype,type,mountpoint
sudo lvs -o name,copy_percent,size,segtype,uuid,devices
sudo lvs -o lv_name,lv_attr --separator='|' --noheadings -S "lv_attr=~[^s.*]"

```
The first command to see what is there and what renderer is actually being used. Your blame shows both NetworkManager and netwrokd services running(?) Usually that is one or the other, not both concurrently.

If the second command has no lvm, vg<something> or lv<something>, then there is no need to do anything further. If you have LVM installed as a Volume Manager, and the last command is blank, then you have never done any snapshots.

But thinking that is you do not know if you have LVM2, then you probably haven't made any LVM snapshot, so then the check for old stale snapshots is not needed.

---

### Post by TheFu on 2024-03-25
Be happy:
```
$ systemd-analyze
Startup finished in 25.901s (firmware) + 2.635s (loader) + 7.169s (kernel) + 2min 28.329s (userspace) = [COLOR="#FF0000"]3min 4.036s [/COLOR]
graphical.target reached after 2min 27.753s in userspace
```

And on another physical machine:
```
$ systemd-analyze
Startup finished in 10.185s (firmware) + 2.845s (loader) + 5.081s (kernel) + 16.177s (userspace) = [COLOR="#FF0000"]34.290s 
[/COLOR]graphical.target reached after 14.210s in userspace

```

These are nearly identical systems, except one has 6 more HDDs connected. USB Peripherals make booting slower.  If the system has lots of USB ports, perhaps using an added front-panel with a 35-in-5 card reader, 4 USB2 ports, 2 USB3 ports, audio jacks and 1 eSATA port, if those are all enabled, the boot time can become 5+ minutes.  I ended up disconnecting all the USB2 things on my front-panel to prevent the _ludicrous_ boot times.  Basically the opposite of "they've gone plaid".  Hopefully, everyone will get that reference. ;)

If you want it to be faster, stop rebooting all the time, learn to boot and get coffee like the rest of the world does. Or use the time for mediation to find your happy place. 

If you want a really fast boot, use the 30MB **TinyCore** [http://tinycorelinux.net/downloads.html](http://tinycorelinux.net/downloads.html)

Just providing options.

I've already tuned my boot to remove all sorts of slow things that I'll never use - things like network-manager or ZFS checks or GUI things I just don't need, like the snap subsystem.
```
$ systemd-analyze critical-chain 
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @14.210s
&#9492;&#9472;udisks2.service @5.371s +8.838s
  &#9492;&#9472;basic.target @5.303s
    &#9492;&#9472;sockets.target @5.302s
      &#9492;&#9472;libvirtd-ro.socket @5.301s
        &#9492;&#9472;libvirtd.socket @5.285s +11ms
          &#9492;&#9472;sysinit.target @5.277s
            &#9492;&#9472;systemd-sysctl.service @5.469s +3ms
              &#9492;&#9472;systemd-modules-load.service @385ms +36ms
                &#9492;&#9472;systemd-journald.socket @335ms
                  &#9492;&#9472;-.mount @297ms
                    &#9492;&#9472;system.slice @297ms
                      &#9492;&#9472;-.slice @297ms

```
That's the entire critical chain on 1 system.  I need to look at removing udisks. It used to be useless for my needs.

On the slower booting system, 
```
$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @2min 27.753s
&#9492;&#9472;multi-user.target @2min 27.753s
  &#9492;&#9472;zfs.target @2min 27.753s
    &#9492;&#9472;zfs-share.service @2min 27.722s +30ms
      &#9492;&#9472;nfs-server.service @5.950s +2min 21.771s
        &#9492;&#9472;rpc-statd.service @2min 18.783s +15ms
          &#9492;&#9472;nss-lookup.target @2min 18.780s

```
I use LXD, which requires snaps and ZFS.  The other things are related to NFS, which I use extensively.

The worst offender on the slow booting system is NFS:
```
2min 21.771s nfs-server.service
     12.048s snap.lxd.activate.service                                                     >
      7.889s smartmontools.service                                                         >
      7.740s udisks2.service                                                               >
      7.129s snapd.service                                                                 >
      6.303s apt-daily.service                                                             >
      4.095s fstrim.service                                                                >
      3.029s systemd-networkd-wait-online.service                                          >
      1.324s apt-daily-upgrade.service                                                     >
      1.239s man-db.service                                                                >
      1.174s fwupd-refresh.service                                                        
... 
```
Slow disks, connected via USB is my initial guess.

I generally reboot every 2-3 weeks, when a new kernel is provided.

On a virtual machine, running on the slower booting system, with Linux Mint 21.2, but a minimal GUI, I see this:
```
$ systemd-analyze 
Startup finished in 6.402s (kernel) + 7.401s (userspace) = [COLOR="#00FF00"]13.804s [/COLOR]
graphical.target reached after 7.391s in userspace 
```
Plenty fast.
```
$ systemd-analyze blame
4.008s plocate-updatedb.service
3.748s postfix@-.service
1.810s munin-node.service
1.788s systemd-udev-settle.service
1.670s input-remapper-daemon.service
1.267s fwupd-refresh.service
 858ms x2goserver.service
...
```

That's my primary desktop system.

BTW, sudo isn't needed for systemd-analyze.

---

### Post by Alexboy on 2024-03-25
Dear MAFoElffen, here are the results:

```
[FONT=monospace][COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ grep . /etc/netplan/*.yaml[/COLOR]
[COLOR=#FF5454]**# Let NetworkManager manage all devices on this system**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FF5454]**network:**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FF5454]**  version: 2**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#FF5454]**  renderer: NetworkManager**[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ lsblk -e7 -o name,size,fstype,type,mountpoint[/COLOR]
NAME     SIZE FSTYPE TYPE MOUNTPOINT
sda    223,6G        disk  
&#9500;&#9472;sda1   512M vfat   part /boot/efi
&#9492;&#9472;sda2 223,1G ext4   part /
sdb    931,5G        disk  
&#9500;&#9472;sdb1   100M vfat   part  
&#9500;&#9472;sdb2    16M        part  
&#9500;&#9472;sdb3 930,6G ntfs   part  
&#9492;&#9472;sdb4   783M ntfs   part  
sdc    931,5G        disk  
&#9492;&#9472;sdc1 931,5G ext4   part /home/alex/data
[COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo lvs -o name,copy_percent,size,segtype,uuid,devices[/COLOR]
[sudo] password for alex:  
[COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sudo lvs -o lv_name,lv_attr --separator='|' --noheadings -S "lv_attr=~[[/COLOR]
^s.*]"
[COLOR=#54FF54]**alex@B660-GAMING-X-DDR4-i5-12400-RX6600XT**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT]
```

Does it mean that I don't have/use LVM? :-)

TheFu, I've read everything you've written and I'm sorry that you have to wait for that long, however, none of that is bringing me forward.
I cannot agree with the "be happy" part because of what Ubuntu and Linux always gave me: the ability to make things happen and expanding the ones curiosity. The exploring and thinking that it could be better is what pushes us forward.
Instead of comparing my issue to yours, I compare my 48.7 seconds to the almost 17 seconds, the time my less powerful machine (the Chromebook with Manjaro on it) takes to boot. ;-)

---

### Post by MAFoElffen on 2024-03-26
No. You do not have LVM. You do have NetworkManager...

If you found your IP devices and add "optional: yes"... for example:
```

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets: 
    enp0s25: 
      dhcp4: yes
      dhcp6: yes
      optional: yes
  wifis: 
    wlp3s0: 
      access-points:
        "AccessPointName":
          password: "SuperSecretPassWord"
      dhcp4: yes
      dhcp6: yes
      optional: yes

```
That (alone) should save you around 5-9 seconds on the average.

As TheFu said... My old WorkStation was on a SuperMicro 'Server' motherboard... It was Legacy BIOS only, and the server management checks in POST on it's 'FastBoot' (no RAM checks, shortened BMC checks, and such) took over 2 minutes. Then the OS boot process after that. Count your blessings. I do not consider under 1 minute to be (that) bad. LOL

---

### Post by TheFu on 2024-03-27
I provided 2 solutions to get a sub-10 second boot. Guess you missed that. Perhaps I wasn't clear enough. Oh well.

BTW, I showed my systems for a comparison, not as a solution.  Also, you can compare the things you have active at start up and see that I've removed most of those.  Another set of ideas for you to try.  What you consider "mandatory" to boot is likely different from my list, so only you can decide.

---

