---
title: "Unable to parse Unattended-Upgrade::Allowed-Origins"
date: 2021-10-19
forum: Installation &amp; Upgrades
---

### Post by alesko7777 on 2021-10-19
[COLOR=#333333][FONT=&quot]Hi[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]I have Ubuntu 20.04.2 LTS, Kernel: Linux 5.4.0-73-generic where I set up unattended upgrades. I get following error when upgrade runs. Would you know what to fix, not to get this error? Thank you
[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Unattended-upgrades log:
Starting unattended upgrades script
Unable to parse Unattended-Upgrade::Allowed-Origins.
An error occurred: not enough values to unpack (expected 2, got 0)
Traceback (most recent call last):
  File "/usr/bin/unattended-upgrade", line 1985, in main
    res = run(options, rootdir, mem_log, logfile_dpkg,
  File "/usr/bin/unattended-upgrade", line 2126, in run
    cache = UnattendedUpgradesCache(rootdir=rootdir)
  File "/usr/bin/unattended-upgrade", line 156, in __init__
    self.allowed_origins = get_allowed_origins()
  File "/usr/bin/unattended-upgrade", line 785, in get_allowed_origins
    allowed_origins = get_allowed_origins_legacy()
  File "/usr/bin/unattended-upgrade", line 764, in get_allowed_origins_legacy
    (distro_id, distro_codename) = s.split()
ValueError: not enough values to unpack (expected 2, got 0)[/FONT][/COLOR]

---

### Post by deadflowr on 2021-10-19
How did you set it?
Did you make changes to the 50unattended-upgrades file?

---

### Post by alesko7777 on 2021-10-20
This is my 50unattended-upgrades file

```
// Automatically upgrade packages from these (origin:archive) pairs
//
// Note that in Ubuntu security updates may pull in new dependencies
// from non-security sources (e.g. chromium). By allowing the release
// pocket these get automatically pulled in.
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESMApps:${distro_codename}-apps-security";
        "${distro_id}ESM:${distro_codename}-infra-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};


// Python regular expressions, matching packages to exclude from upgrading
Unattended-Upgrade::Package-Blacklist {
    // The following matches all packages starting with linux-
//  "linux-";


    // Use $ to explicitely define the end of a package name. Without
    // the $, "libc6" would match all of them.
//  "libc6$";
//  "libc6-dev$";
//  "libc6-i686$";


    // Special characters need escaping
//  "libstdc\+\+6$";


    // The following matches packages like xen-system-amd64, xen-utils-4.1,
    // xenstore-utils and libxenstore3.0
//  "(lib)?xen(store)?";


    // For more information about Python regular expressions, see
    // [https://docs.python.org/3/howto/regex.html](https://docs.python.org/3/howto/regex.html)
};


// This option controls whether the development release of Ubuntu will be
// upgraded automatically. Valid values are "true", "false", and "auto".
Unattended-Upgrade::DevRelease "auto";


// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "true";


// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGTERM. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";


// Install all updates when the machine is shutting down
// instead of doing it in the background while the machine is running.
// This will (obviously) make shutdown slower.
// Unattended-upgrades increases logind's InhibitDelayMaxSec to 30s.
// This allows more time for unattended-upgrades to shut down gracefully
// or even install a few packages in InstallOnShutdown mode, but is still a
// big step back from the 30 minutes allowed for InstallOnShutdown previously.
// Users enabling InstallOnShutdown mode are advised to increase
// InhibitDelayMaxSec even further, possibly to 30 minutes.
//Unattended-Upgrade::InstallOnShutdown "false";


// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
Unattended-Upgrade::Mail "e-mail@addres.com";


// Set this value to one of:
//    "always", "only-on-error" or "on-change"
// If this is not set, then any legacy MailOnlyOnError (boolean) value
// is used to chose between "only-on-error" and "on-change"
Unattended-Upgrade::MailOnlyError "true";


// Remove unused automatically installed kernel-related packages
// (kernel images, kernel headers and kernel version locked tools).
//Unattended-Upgrade::Remove-Unused-Kernel-Packages "true";


// Do automatic removal of newly unused dependencies after the upgrade
//Unattended-Upgrade::Remove-New-Unused-Dependencies "true";


// Do automatic removal of unused packages after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";


// Automatically reboot *WITHOUT CONFIRMATION* if
//  the file /var/run/reboot-required is found after the upgrade
//Unattended-Upgrade::Automatic-Reboot "false";


// Automatically reboot even if there are users currently logged in
// when Unattended-Upgrade::Automatic-Reboot is set to true
//Unattended-Upgrade::Automatic-Reboot-WithUsers "true";


// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";


// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";


// Enable logging to syslog. Default is False
Unattended-Upgrade::SyslogEnable "true";


// Specify syslog facility. Default is daemon
// Unattended-Upgrade::SyslogFacility "daemon";


// Download and install upgrades only on AC power
// (i.e. skip or gracefully stop updates on battery)
// Unattended-Upgrade::OnlyOnACPower "true";


// Download and install upgrades only on non-metered connection
// (i.e. skip or gracefully stop updates on a metered connection)
// Unattended-Upgrade::Skip-Updates-On-Metered-Connections "true";


// Verbose logging
// Unattended-Upgrade::Verbose "false";


// Print debugging information both in unattended-upgrades and
// in unattended-upgrade-shutdown
// Unattended-Upgrade::Debug "false";


// Allow package downgrade if Pin-Priority exceeds 1000
// Unattended-Upgrade::Allow-downgrade "false";
```

---

### Post by deadflowr on 2021-10-21
The config looks fine.
The only option I've found for anyone with this issue that seemed to work is to try is to purge unattended-upgrades and reinstall it.
Maybe also move or remove the current config file as well so it starts of fresh.
I would then test it with the fresh config and see if the problem persists or not.
In order of commands to run I do
```
sudo rm /etc/apt/apt.conf.d/50unattended-upgrades
sudo apt purge unattended-upgrades
sudo apt clean
sudo apt update
sudo apt full-upgrade
sudo apt install unattended-upgrades
sudo unattended-upgrades --debug --dry-run
```

FTR, The 3 middle commands 

1) Clean will remove any archived installer packages, it might help in case an archived package was somehow corrupt.

2) Update will ensure your system is in sync with what the Ubuntu repositories, this ensures that the packages are the most recent, and most bug free (hopefully)

3) Full-upgrade upgrades all the installed software on your system to the most up-to-date they can be, it's always best to be up-to-date whenever installing new software or configuring anything.

The last command to run the unattended-upgrades command is just a testing command to see what it outputs, if it output the same as the original errors or if it outputs a more common and correct output.
The --dry-run option sets it to run in a simulated mode which means it won't actually do anything to the system.

---

### Post by alesko7777 on 2021-10-22
Thank you Deadflower

I have something wrong with my Ubuntu

When I purged unattended-upgrades package, i got this messages

The following packages will be REMOVED:
  unattended-upgrades*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 451 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 619002 files and directories currently installed.)
Removing unattended-upgrades (2.3ubuntu0.1) ...
Setting up initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.187.19) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-84-generic
cat: write error: No space left on device
update-initramfs: failed for /boot/initrd.img-5.4.0-84-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 installed linux-firmware package post-installation script subprocess returned error exit status 1
Setting up linux-image-5.4.0-89-generic (5.4.0-89.100) ...
I: /boot/initrd.img is now a symlink to initrd.img-5.4.0-89-generic
Setting up linux-image-5.4.0-88-generic (5.4.0-88.99) ...
I: /boot/initrd.img.old is now a symlink to initrd.img-5.4.0-88-generic
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:No apport report written because the error message indicates its a followup error from a previous failu
re.


 linux-generic depends on linux-image-generic (= 5.4.0.89.93); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.9.1-1) ...No apport report written because the error message indicates its a followup error from a previous failure.


Errors were encountered while processing:
 linux-firmware
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I see I have also problem to upgrade Kernel from 5.4.0-84-generic to the latest 5.4.0-89-generic. Could you please advice me how can I repair this?

---

### Post by deadflowr on 2021-10-22
Your drive shows as full.
Post the output of
```
df -Th -x squashfs -x tmpfs
```

---

### Post by alesko7777 on 2021-10-23
```
Filesystem                        Type      Size  Used Avail Use% Mounted on
udev                              devtmpfs  950M     0  950M   0% /dev
/dev/mapper/ubuntu--vg-ubuntu--lv ext4       15G   12G  2.0G  86% /
/dev/sda2                         ext4      976M  959M     0 100% /boot
//200.200.26.3/backdrive          cifs      6.8T  6.5T  283G  96% /media/backdrive
//200.200.26.3/projekty           cifs      6.8T  6.5T  283G  96% /media/data
```

---

### Post by deadflowr on 2021-10-23
So it shows that boot is full, which even though it's on it's own partition still affects the updating.
With over 900MB used that means you must have a whole bunch of old outdated kernels.
What does
```
dpkg -l | grep linux-image
```
show?
It also doesn't help that the root partition is very tiny and is also on the verge of using all it's space.

---

### Post by alesko7777 on 2021-10-23
Thank you again!

rc  linux-image-5.4.0-65-generic         5.4.0-65.73                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-66-generic         5.4.0-66.74                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-67-generic         5.4.0-67.75                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-70-generic         5.4.0-70.78                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-71-generic         5.4.0-71.79                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-72-generic         5.4.0-72.80                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-73-generic         5.4.0-73.82                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-74-generic         5.4.0-74.83                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-77-generic         5.4.0-77.86                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-80-generic         5.4.0-80.90                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-81-generic         5.4.0-81.91                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-84-generic         5.4.0-84.94                           amd64        Signed kernel image generic
it  linux-image-5.4.0-88-generic         5.4.0-88.99                           amd64        Signed kernel image generic
it  linux-image-5.4.0-89-generic         5.4.0-89.100                          amd64        Signed kernel image generic
iU  linux-image-generic                  5.4.0.89.93                           amd64        Generic Linux kernel image

---

### Post by deadflowr on 2021-10-23
What happens if you run
```
sudo apt autoremove --purge
```

---

### Post by alesko7777 on 2021-10-23
This happened

```
Purging configuration files for linux-modules-5.4.0-77-generic (5.4.0-77.86) ...
dpkg: warning: while removing linux-modules-5.4.0-77-generic, directory '/lib/modules/5.4.0-77-generic' not empty so not removed
Purging configuration files for linux-image-5.4.0-77-generic (5.4.0-77.86) ...
I: /boot/initrd.img.old is now a symlink to initrd.img-5.4.0-88-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.4.0-89-generic
Purging configuration files for linux-modules-extra-5.4.0-80-generic (5.4.0-80.90) ...
Purging configuration files for linux-modules-extra-5.4.0-74-generic (5.4.0-74.83) ...
Purging configuration files for linux-modules-extra-5.4.0-73-generic (5.4.0-73.82) ...
Purging configuration files for linux-image-5.4.0-80-generic (5.4.0-80.90) ...
Purging configuration files for linux-modules-5.4.0-81-generic (5.4.0-81.91) ...
dpkg: warning: while removing linux-modules-5.4.0-81-generic, directory '/lib/modules/5.4.0-81-generic' not empty so not removed
Purging configuration files for linux-modules-5.4.0-80-generic (5.4.0-80.90) ...
Purging configuration files for linux-image-5.4.0-73-generic (5.4.0-73.82) ...
Purging configuration files for linux-image-5.4.0-72-generic (5.4.0-72.80) ...
Purging configuration files for linux-modules-5.4.0-74-generic (5.4.0-74.83) ...
dpkg: warning: while removing linux-modules-5.4.0-74-generic, directory '/lib/modules/5.4.0-74-generic' not empty so not removed
Purging configuration files for linux-image-5.4.0-74-generic (5.4.0-74.83) ...
Purging configuration files for linux-modules-5.4.0-73-generic (5.4.0-73.82) ...
Purging configuration files for linux-image-5.4.0-81-generic (5.4.0-81.91) ...
rmdir: failed to remove '/lib/modules/5.4.0-81-generic': Directory not empty
Purging configuration files for linux-modules-extra-5.4.0-72-generic (5.4.0-72.80) ...
Purging configuration files for linux-modules-5.4.0-72-generic (5.4.0-72.80) ...
Purging configuration files for linux-modules-extra-5.4.0-77-generic (5.4.0-77.86) ...
Purging configuration files for linux-modules-extra-5.4.0-81-generic (5.4.0-81.91) ...

```
No I have this 
```
dpkg -l | grep linux-image
rc  linux-image-5.4.0-65-generic         5.4.0-65.73                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-66-generic         5.4.0-66.74                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-67-generic         5.4.0-67.75                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-70-generic         5.4.0-70.78                           amd64        Signed kernel image generic
rc  linux-image-5.4.0-71-generic         5.4.0-71.79                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-84-generic         5.4.0-84.94                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-88-generic         5.4.0-88.99                           amd64        Signed kernel image generic
ii  linux-image-5.4.0-89-generic         5.4.0-89.100                          amd64        Signed kernel image generic
ii  linux-image-generic                  5.4.0.89.93                           amd64        Generic Linux kernel image

```
Now Boot has 208MB free space. Would it be enough? Can I delete more older packages?
```
df -Th -x squashfs -x tmpfs
Filesystem                        Type      Size  Used Avail Use% Mounted on
udev                              devtmpfs  950M     0  950M   0% /dev
/dev/mapper/ubuntu--vg-ubuntu--lv ext4       15G  8.6G  5.4G  62% /
/dev/sda2                         ext4      976M  702M  208M  78% /boot
//200.200.26.3/backdrive          cifs      6.8T  6.5T  283G  96% /media/backdrive
//200.200.26.3/projekty           cifs      6.8T  6.5T  283G  96% /media/data
```

---

### Post by deadflowr on 2021-10-24
> Would it be enough? 
You should now have enough wiggle room to work with.
It might be possible to get more space.
A reboot should boot into the newer 5.4.0-89 kernel as it's now shown as properly installed.
Running autoremove again should then remove the 5.4.0-84 kernel, and leave you with just 2.
That should help clear up another 50MB or more.

---

### Post by alesko7777 on 2021-10-24
As you said, after reboot there is more free space

I runned this

sudo rm /etc/apt/apt.conf.d/50unattended-upgrades
sudo apt purge unattended-upgrades
sudo apt clean
sudo apt update
sudo apt full-upgrade
sudo apt install unattended-upgrades
sudo unattended-upgrades --debug --dry-run

and got this after dry run. I googled little bit and found there are some type in Ubuntu. But I am not able to find where. It does not look in conf file. It looks like conf file on my another Ubuntu machine where everything works perfect.

     
Running on the development release
Starting unattended upgrades script
Unable to parse Unattended-Upgrade::Allowed-Origins.
An error occurred: not enough values to unpack (expected 2, got 0)
Traceback (most recent call last):
  File "/usr/bin/unattended-upgrades", line 1985, in main
    res = run(options, rootdir, mem_log, logfile_dpkg,
  File "/usr/bin/unattended-upgrades", line 2126, in run
    cache = UnattendedUpgradesCache(rootdir=rootdir)
  File "/usr/bin/unattended-upgrades", line 156, in __init__
    self.allowed_origins = get_allowed_origins()
  File "/usr/bin/unattended-upgrades", line 785, in get_allowed_origins
    allowed_origins = get_allowed_origins_legacy()
  File "/usr/bin/unattended-upgrades", line 764, in get_allowed_origins_legacy
    (distro_id, distro_codename) = s.split()
ValueError: not enough values to unpack (expected 2, got 0)
Extracting content from /var/log/unattended-upgrades/unattended-upgrades-dpkg.log since 2021-10-24 12:02:07
Traceback (most recent call last):
  File "/usr/bin/unattended-upgrades", line 2514, in <module>
    sys.exit(main(options))
  File "/usr/bin/unattended-upgrades", line 1985, in main
    res = run(options, rootdir, mem_log, logfile_dpkg,
  File "/usr/bin/unattended-upgrades", line 2126, in run
    cache = UnattendedUpgradesCache(rootdir=rootdir)
  File "/usr/bin/unattended-upgrades", line 156, in __init__
    self.allowed_origins = get_allowed_origins()
  File "/usr/bin/unattended-upgrades", line 785, in get_allowed_origins
    allowed_origins = get_allowed_origins_legacy()
  File "/usr/bin/unattended-upgrades", line 764, in get_allowed_origins_legacy
    (distro_id, distro_codename) = s.split()
ValueError: not enough values to unpack (expected 2, got 0)

---

