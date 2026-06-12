---
title: "Triple boot grub2 fixed but still some issues?"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by usmamyer on 2016-09-09
Hello all. I've been dual booting for a long time and have never had any issues using Windows 7 and Ubuntu or Kali in the past as dual is very easy. I recently decided to set up my laptop to triple boot Windows 10, Ubuntu 16.04 LTS, and Kali Linux 2016.2 64-bit on a single drive in my laptop. I decided to use this method because i prefer it over a virtual machine and can easily separate my work areas from my play ones.

I did experience some slight issues during installation and thought I had everything sorted, but there are some slight discrepancies in boot and performance that has me thinking I may have done something improperly and have not been able to find just the right answer anywhere yet. This is what I did.

System Specifications
Model: Acer Aspire E 15 (E5-571-563B)
Processor: Intel® Core™ i5-4210U CPU @ 1.70GHz × 4 
Memory: 6gb
Graphics: Intel Haswell Mobile
Disk: 1tb

fdisk -l output:

[IMG]http://i.imgur.com/34R9lel.jpg[/IMG]

This pc originally came with windows 8 which i found generally useless so I formatted and installed Kali 2.0 by itself to use as a penetration tester until deciding to make it triple boot. All installations were conducted from a USB drive with each OS on them individually using Rufus 2,1, GPT UEFI, Fat32, and official ISO's for each.

Installation Process and issues:
1. Delete all partitions and format full disk
2. Installed Windows 10 Enterprise without a hitch.
3. Installed Ubuntu 16.04 LTS without a problem.
4. Changed BIOS boot order to put ubuntu grub2 before Windows boot manager
5. Had issues getting Kali Linux 2016.2 to boot in UEFI after trying multiple suggestions to get it to do so, so...
6. Used Ubuntu installation's Startup Disk Creator and the Kali Linux 2016.2 ISO to create Kali installation drive. This is the only way I was able to get the Kali image to actually boot.
7. Kali 2016.2 seemed to install just like normal including saying it updated grub info and everything, used the option home folder and system on one partition recommended for new users.
8. Upon reboot I was able to boot from Win10 and Ubuntu, but Kali was not listed, so I booted into Ubuntu again and employed the Boot-repair program using recommended settings.
9. Rebooted and was now able to see my Kali installation on the list as well as a couple unknown listings like windows boot.efi type entries which simply reboot to the grub2 again but every OS does boot.
10. Booted into Windows and updated all drivers and windows system
11. Booted into Ubuntu and updated/upgraded dist/packages/drivers
12. Booted into Kali and updated/upgraded dist/packages/drivers

I noticed it seems to take a little longer to boot Ubuntu than I believe it should but it does not give me any errors. everything seems to operate properly but seems just a little slower than expected for sure, and I noticed that regardless of what OS I am running, whenever I open a new Firefox window, they all use the home page of "data:text/plain,browser.startup.homepage=file:///usr/share/kali-defaults/web/homepage.html" and the page below reads "browser.startup.homepage=file:///usr/share/kali-defaults/web/homepage.html" without quotes.

This makes me believe maybe my partitioning is out of order somehow or I missed/damaged a setting with boot repair in the Ubuntu environment (i did not use boot-repair from a live cd/usb environment, I booted into the Ubuntu already installed on my disk to run it.) I will generate a bootchart image soon and provide it here as well if that would help, but i figured i have to ask someone who knows more about this than me as I have tried every suggestion I was able to find so far and have yet to find an explanation as to why things are the way they are. Please let me know if there is anything else I left out or need to try to get this worked out.

Thanks in advance for your time and assistance.

---

### Post by oldfred on 2016-09-09
I do not know Boot chart.
Post this for Newer systems with systemd:
 systemd-analyze blame 

And post link to summary report from Boot-Repair to see details of your configuration.

---

### Post by usmamyer on 2016-09-09
> **oldfred said:**
> I do not know Boot chart.
Post this for Newer systems with systemd:
 systemd-analyze blame 

And post link to summary report from Boot-Repair to see details of your configuration.

sorry had a lot to do today but im back, heres the output:

dan@dan-Aspire-E5-571:~$ systemd-analyze blame
          5.064s dev-sda5.device
          5.003s apparmor.service
          3.867s snapd.firstboot.service
          3.605s lightdm.service
          3.479s grub-common.service
          3.290s ModemManager.service
          3.131s [email]systemd-fsck@dev-disk-by\x2duuid-2849\x2dA6FF.servic[/email]e
          2.992s NetworkManager.service
          2.684s ondemand.service
          2.607s accounts-daemon.service
          2.037s speech-dispatcher.service
          2.012s systemd-logind.service
          1.956s apt-daily.service
          1.941s alsa-restore.service
          1.935s systemd-user-sessions.service
          1.934s pppd-dns.service
          1.934s gpu-manager.service
          1.592s snapd.refresh.service
          1.583s bluetooth.service
          1.583s thermald.service
          1.583s iio-sensor-proxy.service
          1.504s irqbalance.service
          1.332s systemd-tmpfiles-setup.service
          1.182s polkitd.service
          1.070s plymouth-start.service
          1.063s colord.service
           994ms apport.service
           951ms plymouth-quit-wait.service
           941ms keyboard-setup.service
           906ms systemd-modules-load.service
           846ms systemd-tmpfiles-setup-dev.service
           718ms upower.service
           717ms console-setup.service
           631ms systemd-journald.service
           629ms systemd-hostnamed.service
           541ms dev-hugepages.mount
           540ms dev-mqueue.mount
           537ms systemd-timesyncd.service
           468ms rsyslog.service
           465ms wpa_supplicant.service
           452ms [email]systemd-backlight@backlight:intel_backlight.servic[/email]e
           447ms systemd-udevd.service
           446ms udisks2.service
           416ms [email]user@1000.servic[/email]e
           352ms sys-kernel-debug.mount
           343ms dev-sda6.swap
           278ms systemd-update-utmp.service
           235ms avahi-daemon.service
           227ms boot-efi.mount
           225ms dns-clean.service
           203ms systemd-sysctl.service
           190ms ufw.service
           164ms systemd-udev-trigger.service
           147ms systemd-localed.service
           124ms networking.service
           124ms setvtrgb.service
           122ms systemd-rfkill.service
           110ms systemd-journal-flush.service
            95ms systemd-random-seed.service
            92ms resolvconf.service
            78ms rtkit-daemon.service
            66ms kmod-static-nodes.service
            58ms systemd-remount-fs.service
            45ms rc-local.service
            41ms systemd-tmpfiles-clean.service
            26ms proc-sys-fs-binfmt_misc.mount
            15ms snapd.socket
            11ms plymouth-read-write.service
             5ms snapd.boot-ok.service
             4ms ureadahead-stop.service
             3ms systemd-update-utmp-runlevel.service
             2ms sys-fs-fuse-connections.mount
lines 50-72/72 (END)

---

### Post by usmamyer on 2016-09-09
and the boot-report: [http://paste2.org/63b5Cxwn](http://paste2.org/63b5Cxwn)

I'm pretty green to a bit of this but sda3 appears suspect to me?
I'm looking through the thread you posted as well, thanks for helping out.

---

### Post by oldfred on 2016-09-09
What is sda5?

It looks like that might be an issue.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by usmamyer on 2016-09-09
Man, I don't know why it never occurred to me to check the disk this way in the first place... but everything runs slicker than greased snot on a slip n slide now. :) e2fsck discovered a couple errors with my sda5 and fixed them up quickly. Afterwards I tested kali with it and Windows with sfc in safe mode to be sure there were no other problems, which there were not. I bookmarked the link to the other thread as well for future reference so I can handle my issues in the future.

Thanks a lot for taking the time to check everything out for me Fred, I definitely appreciate it.

---

