---
title: "Upgrading to 16.10 stuck during install"
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by jml3473 on 2016-11-23
Hi all, some python script failed during the "Installing the upgrades"  phase from 16.04 to 16.10 and the update-manager window turned grey.  Fortunately there's no side-effect thus far so I basically want to abort  the whole thing cleanly. More details below.

0. This is my  home's only internet device. Yesterday's thought process: it's probably  simpler to upgrade rather than try to solve a couple of minor issues  independantly (games for my son: wine's too old and the unity flash  thing doesn't work in firefox).
1. I click the button of the update-manager and let the thing work through the night (4-5 hrs download)
2.  Back for lunch, it's asking something where I select default lightdm,  then after some disk activity, nothing happens and the update-manager  window turned grey. The terminal in said window says "Extracting  templates from packages: 100% // Preconfiguring packages ... " 4 times.  Other than that the system works just fine.
3. So what do I do now? I'm not touching anything for now :o Thank you.

I tried to find some info. Last lines of /var/log/dist-upgrade/main.log :
```
2016-11-23 07:16:23,473 DEBUG quirks: running StartUpgrade
2016-11-23 07:16:23,501 DEBUG skipping 'README' (no '.')
2016-11-23 07:16:23,521 DEBUG removing old .crash file '/var/crash/cups-daemon.0.crash'
2016-11-23 07:16:23,608 DEBUG killing update-notifier
2016-11-23 07:16:23,651 DEBUG killing kblueplugd kbluetooth4
2016-11-23 07:16:23,665 DEBUG killing gnome-screensaver
2016-11-23 07:16:23,676 DEBUG setup poke timer for the scrensaver
2016-11-23 07:16:23,933 DEBUG gnome-session not running for user
2016-11-23 07:16:23,968 DEBUG apt btrfs snapshots supported: False
2016-11-23 07:16:23,968 INFO cache.commit()
2016-11-23 07:16:23,968 DEBUG failed to SystemUnLock() (E:Not locked) 
2016-11-23 07:21:45,481 WARNING no activity on terminal for 300 seconds (Applying changes)
2016-11-23 12:19:14,900 ERROR not handled exception:
Traceback (most recent call last):

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/yakkety", line 8, in <module>
    sys.exit(main())

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeMain.py", line 242, in main
    if app.run():

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeController.py", line 1880, in run
    return self.fullUpgrade()

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeController.py", line 1845, in fullUpgrade
    if not self.doDistUpgrade():

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeController.py", line 1183, in doDistUpgrade
    res = self.cache.commit(fprogress,iprogress)

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeCache.py", line 267, in commit
    apt.Cache.commit(self, fprogress, iprogress)

  File "/usr/lib/python3/dist-packages/apt/cache.py", line 515, in commit
    res = self.install_archives(pm, install_progress)

  File "/usr/lib/python3/dist-packages/apt/cache.py", line 479, in install_archives
    res = install_progress.run(pm)

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeView.py", line 234, in run
    res = os.WEXITSTATUS(self.wait_child())

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeViewGtk3.py", line 339, in wait_child
    self.update_interface()

  File "/tmp/ubuntu-release-upgrader-4rle2qd_/DistUpgrade/DistUpgradeViewGtk3.py", line 346, in update_interface
    InstallProgress.update_interface(self)

  File "/usr/lib/python3/dist-packages/apt/progress/base.py", line 255, in update_interface
    if float(percent) != self.percent or status_str != self.status:

ValueError: could not convert string to float: '0,0000'

2016-11-23 12:19:14,900 DEBUG running apport_crash()
```

apt-term.log (timestamp 12:24) starts with ```
Log started: 2016-11-23  12:19:14
(Reading  database ...
``` and ends 566 lines later after unpacking a number  of packages, ending with accountsservice-ubuntu-schemas; so that should  be the disk activity I mentioned. history.log also says "Start-Date:  2016-11-23  12:19:14" with the accountsservice-ubuntu-schemas package  mentioned in the middle of 336 packages in the Install line.

EDIT
I killed the upgrade python process, then I did
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
The dpkg configure did a number of things but gnome-shell and gnome-session met dependency problems so I did a
sudo apt-get -f install
and I'm currently redoing dist-upgrade. I'll hopefully keep you posted :)

---

### Post by jml3473 on 2016-11-23
Update: I guess it was fun. The  Wifi got wrong (and internet was lost), the keyboard went arabic, then everything froze for 5  minutes... Fortunately there was still disc activity so I waited then everything  came back.
I also did an apt-get clean (and apt autoremove since space was  almost up).
Now nothing happens with any of the above commands. **Does this mean problem solved?**

I'll only reboot tomorrow when internet cafes are opened in case there's an issue. I'm worried about the following warning from apt autoremove:```
Processing triggers for initramfs-tools (0.125ubuntu6.1) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-28-generic
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915
```lshw says```
    *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
```

---

### Post by jml3473 on 2016-11-24
Hi again, turns out the problem was **not **solved. I used the system for a while but eventually I had to reboot, and I could only login in console mode and ran into a number of practical problem (I normally connect to the internet through a Wifi hotspot but I had no text browser installed so I couldn't open the connection, then I failed to get a relevant repository on a USB key at the internet cafe) until I could finally bring my laptop to some place where I could use an ethernet cable. The advices I had googled about my login problem could finally be put to use.
"sudo apt-get install ubuntu-session" only let me login to some unusable environment.
"sudo apt-get install ubuntu-desktop" installed a lot of new packages, and now it looks like everything's fine.

**tl;dr **I was probably missing a bunch of packages I didn't know I was missing, and perhaps I still am. It would be helpful to have some kind of list of packages to install before rebooting in case the dist-upgrade fails. I wish the python script would first point out some local helpful file to be read in case something went wrong.
I hope this will help someone

---

### Post by ian-weisser on 2016-11-24
> **jml3473 said:**
> It would be helpful to have some kind of list of packages to install before rebooting in case the dist-upgrade fails.
Here is the entire list: ubuntu-desktop

Best practice is to restore our systems to as close stock condition as possible. Uninstall PPA and other non-Ubuntu software, and restore the ubuntu-desktop metapackage if it has been removed.

It's the human's responsibility to do those things. The upgrade logic is not psychic and cannot discern your intent from my intent. It tries its best with what it has.

> **jml3473 said:**
> I wish the python script would first point out some local helpful file to be read in case something went wrong.
Not sure it would help in this case. The specific fault, regardless of cause, was a float/int confusion. That seems more like a fixable bug than a teachable moment.

---

### Post by jml3473 on 2016-11-27
> **ian-weisser said:**
> Best practice is to restore our systems to as close stock condition as possible. Uninstall PPA and other non-Ubuntu software, and restore the ubuntu-desktop metapackage if it has been removed.Thanks for your reply. Also, **to all people that make Ubuntu or Debian work, many many thanks**, I've used your software for years and it's just great.

I didn't know what was ubuntu-desktop, my system has been OK since then, your post confirms that I shouldn't be missing something, thanks for that.

Since scripts may have bugs, I'm simply suggesting to have a local file explaining how to "uninstall PPA and other non-Ubuntu software, and restore the ubuntu-desktop metapackage" in case the dist-upgrade meets a bug. I know I'll do that since the next time I'll meet a similar problem may be (if ever) a few years later, and I'll have completely forgotten the specifics of what I'm supposed to do.

---

