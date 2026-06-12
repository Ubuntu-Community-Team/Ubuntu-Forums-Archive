---
title: "Install/Unistall and Partition"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by arobe30 on 2010-03-30
I cannot get my Sony Vaio PCG-V505EX to install or unistall or boot fromthe optical drive.  Everything says it is unable to mount.  I tried using terminal to get to the partition and this is a screenshot from it.

elizabeth@elizabeth-laptop:~$ sudo ntfsfix
[sudo] password for elizabeth: 
ERROR: You must specify a device.
ntfsfix v2.0.0 (libntfs 10:0:0)

Usage: ntfsfix [options] device
    Attempt to fix an NTFS partition.

    -h, --help             Display this help
    -V, --version          Display version information

For example: ntfsfix /dev/hda6

Developers' email address: [EMAIL="linux-ntfs-dev@lists.sf.net"]linux-ntfs-dev@lists.sf.net[/EMAIL]
Linux NTFS homepage: [http://www.linux-ntfs.org](http://www.linux-ntfs.org)
elizabeth@elizabeth-laptop:~$ -h, --help
-h,: command not found
elizabeth@elizabeth-laptop:~$ ntfsfix /dev/hda6
Failed to determine whether /dev/hda6 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.
 run chkdsk
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (multiverse)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found
elizabeth@elizabeth-laptop:~$ elizabeth@elizabeth-laptop:~$ sudo ntfsfix
elizabeth@elizabeth-laptop:~$: command not found
elizabeth@elizabeth-laptop:~$ [sudo] password for elizabeth: 
[sudo]: command not found
elizabeth@elizabeth-laptop:~$ ERROR: You must specify a device.
ERROR:: command not found
elizabeth@elizabeth-laptop:~$ ntfsfix v2.0.0 (libntfs 10:0:0)
bash: syntax error near unexpected token `('
elizabeth@elizabeth-laptop:~$ 
elizabeth@elizabeth-laptop:~$ Usage: ntfsfix [options] device
Usage:: command not found
elizabeth@elizabeth-laptop:~$     Attempt to fix an NTFS partition.
Attempt: command not found
elizabeth@elizabeth-laptop:~$ 
elizabeth@elizabeth-laptop:~$     -h, --help             Display this help
-h,: command not found
elizabeth@elizabeth-laptop:~$     -V, --version          Display version information
-V,: command not found
elizabeth@elizabeth-laptop:~$ 
elizabeth@elizabeth-laptop:~$ For example: ntfsfix /dev/hda6
No command 'For' found, did you mean:
 Command 'sor' from package 'pccts' (universe)
For: command not found
elizabeth@elizabeth-laptop:~$ 
elizabeth@elizabeth-laptop:~$ Developers' email address: [EMAIL="linux-ntfs-dev@lists.sf.net"]linux-ntfs-dev@lists.sf.net[/EMAIL]
> Linux NTFS homepage: [http://www.linux-ntfs.org](http://www.linux-ntfs.org)
> elizabeth@elizabeth-laptop:~$ -h, --help
> -h,: command not found
> elizabeth@elizabeth-laptop:~$ ntfsfix /dev/hda6
> Failed to determine whether /dev/hda6 is mounted: No such file or directory.
> Mounting volume... Error opening partition device: No such file or directory.
> Failed to startup volume: No such file or directory.
> FAILED
> Attempting to correct errors... Error opening partition device: No such file or directory.
> FAILED
> Failed to startup volume: No such file or directory.
> Volume is corrupt. You should run chkdsk


I need to split the partition or altogether unistall Ubuntu, and reinstall Windows for business reasons.  Please help. Thanks

---

