---
title: "software index broken"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by polarsnow on 2011-04-28
I recently upgraded Ubuntu from 10.04 to 10.10 - which may not have actually completed. After that, upgrades no longer work, and message(s) say(s) to try a partial upgrade, or the command below. 

The software index is broken, and installs and removals of packages no longer work. The message said to use the command below first, but it did not work. The output is below.

The linux-image-xxxxx packages seem to be not completely installed and not completely removed.

Any suggestions?

This is the output from

sudo apt-get install -f

$ sudo apt-get install -f
[sudo] password for xxxxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.32-23-generic linux-image-2.6.32-24-generic linux-image-2.6.32-25-generic
  linux-image-2.6.32-26-generic linux-image-2.6.32-27-generic linux-image-2.6.32-28-generic
  linux-image-2.6.32-29-generic
0 upgraded, 0 newly installed, 7 to remove and 206 not upgraded.
7 not fully installed or removed.
After this operation, 895MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 298960 files and directories currently installed.)
Removing linux-image-2.6.32-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
Cannot delete /boot/dracut.img-2.6.32-23-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.32-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
Cannot delete /boot/dracut.img-2.6.32-24-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.32-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic
Cannot delete /boot/dracut.img-2.6.32-25-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-25-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-25-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.32-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-26-generic /boot/vmlinuz-2.6.32-26-generic
Cannot delete /boot/dracut.img-2.6.32-26-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-26-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-26-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-2.6.32-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-27-generic /boot/vmlinuz-2.6.32-27-generic
Cannot delete /boot/dracut.img-2.6.32-27-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-27-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-2.6.32-28-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
Cannot delete /boot/dracut.img-2.6.32-28-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-28-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-2.6.32-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-29-generic /boot/vmlinuz-2.6.32-29-generic
Cannot delete /boot/dracut.img-2.6.32-29-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-29-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-29-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-23-generic
 linux-image-2.6.32-24-generic
 linux-image-2.6.32-25-generic
 linux-image-2.6.32-26-generic
 linux-image-2.6.32-27-generic
 linux-image-2.6.32-28-generic
 linux-image-2.6.32-29-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mörgæs on 2011-04-29
How does a live boot of 10.10 work?

---

### Post by matt_symes on 2011-04-29
Hi

> Removing linux-image-2.6.32-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
Cannot delete /boot/dracut.img-2.6.32-23-generic, doesn't exist.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-23-generic (--remove):
subprocess installed post-removal script returned error exit status 1

Try this. Open a terminal and type

```
sudo touch /boot/dracut.img-2.6.32-23-generic
sudo apt-get install -f
```

Enter your password. It will not be echoed to the screen.

Do you get any more error message with _this specific_ kernel (2.6.32-23) ?

Kind regards

---

### Post by polarsnow on 2011-05-01
> **matt_symes said:**
> Hi



Try this. Open a terminal and type

```
sudo touch /boot/dracut.img-2.6.32-23-generic
sudo apt-get install -f
```

Enter your password. It will not be echoed to the screen.

Do you get any more error message with _this specific_ kernel (2.6.32-23) ?

Kind regards

Thanks,

I did this, and got more or less the same errors - the one difference is highlighted in bold below (just a part of the messages is shown):

...
Removing linux-image-2.6.32-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/dracut-kernel-postrm 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
Cannot delete version 2.6.32-23-generic: **Not created by this utility**.
run-parts: /etc/kernel/postrm.d/dracut-kernel-postrm exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.32-24-generic ...
...

Before, the message was 

Cannot delete /boot/dracut.img-2.6.32-23-generic, **doesn't exist**.

---

### Post by polarsnow on 2011-05-01
I could edit the script /etc/kernel/postrm.d/dracut-kernel-postrm .  It seems this is one way to deal with this problem,  but ... I don't want to possibly create other problems. I have never dealt with this script before now. 

Anyone familiar with the code who would offer suggestions? The script is short, so here is the code:

#!/bin/sh

version="$1"
bootopt=""

# passing the kernel version is required
[ -z "${version}" ] && exit 0

# kernel-package passes an extra arg
if [ -n "$2" ]; then
        if [ -n "${KERNEL_PACKAGE_VERSION}" ]; then
                bootdir=$(dirname "$2")
                bootopt="-b ${bootdir}"
        fi
fi

# avoid running multiple times
if [ -n "$DEB_MAINT_PARAMS" ]; then
        eval set -- "$DEB_MAINT_PARAMS"
        if [ -z "$1" ] || [ "$1" != "remove" ]; then
                exit 0
        fi
fi

# delete initramfs
dracut-update-initramfs -d -t -k "${version}" ${bootopt} >&2

---

### Post by matt_symes on 2011-05-01
Hi

> **polarsnow said:**
> I could edit the script /etc/kernel/postrm.d/dracut-kernel-postrm .  It seems this is one way to deal with this problem,  but ... I don't want to possibly create other problems. I have never dealt with this script before now. 

Anyone familiar with the code who would offer suggestions? The script is short, so here is the code:

#!/bin/sh

version="$1"
bootopt=""

# passing the kernel version is required
[ -z "${version}" ] && exit 0

# kernel-package passes an extra arg
if [ -n "$2" ]; then
        if [ -n "${KERNEL_PACKAGE_VERSION}" ]; then
                bootdir=$(dirname "$2")
                bootopt="-b ${bootdir}"
        fi
fi

# avoid running multiple times
if [ -n "$DEB_MAINT_PARAMS" ]; then
        eval set -- "$DEB_MAINT_PARAMS"
        if [ -z "$1" ] || [ "$1" != "remove" ]; then
                exit 0
        fi
fi

# delete initramfs
dracut-update-initramfs -d -t -k "${version}" ${bootopt} >&2

Backup your system first.

Make a backup copy of the file first.

```
sudo cp /etc/kernel/postrm.d/dracut-kernel-postrm  /etc/kernel/postrm.d/dracut-kernel-postrm.old
```

Comment out the last line so it becomes

```
#dracut-update-initramfs -d -t -k "${version}" ${bootopt} >&2
```

Save and update as before. 

If all goes well

```
sudo rm /etc/kernel/postrm.d/dracut-kernel-postrm.old
```

Depending on where it stopped before you might have some cruft hanging around your system. Please backup your system before upgrading next time ;)

Kind regards

---

### Post by polarsnow on 2011-05-02
> **mörgæs said:**
> How does a live boot of 10.10 work?

Haven't tried it. I may later, but may try other things first. It would take more time to burn a disk.

I plan to post the results here.

Thanks

---

### Post by polarsnow on 2011-05-03
> **matt_symes said:**
> Hi



Backup your system first.

Make a backup copy of the file first.

```
sudo cp /etc/kernel/postrm.d/dracut-kernel-postrm  /etc/kernel/postrm.d/dracut-kernel-postrm.old
```

Comment out the last line so it becomes

```
#dracut-update-initramfs -d -t -k "${version}" ${bootopt} >&2
```

Save and update as before. 

If all goes well

```
sudo rm /etc/kernel/postrm.d/dracut-kernel-postrm.old
```

Depending on where it stopped before you might have some cruft hanging around your system. Please backup your system before upgrading next time ;)

Kind regards

Did you mean, if all goes well, to delete the copy of the original script (dracut-kernel-postrm.old) and leave the modified version, with the last line still commented out?

I would suspect you might have meant to add the last line back, after (and if) all goes well.

Thanks much for the insight!

---

### Post by polarsnow on 2011-05-03
After commenting out the last line of the script, I was able to execute

sudo apt-get install -f

Thanks.

---

### Post by matt_symes on 2011-05-04
Hi

I' glad it's fixed :D

> Did you mean, if all goes well, to delete the copy of the original script (dracut-kernel-postrm.old) and leave the modified version, with the last line still commented out?

BTW: I did mean to delete the backup file dracut-kernel-postrm.old as dracut-kernel-postrm should have been handled by the update process.

Please mark this post as solved.

Kind regards

---

### Post by polarsnow on 2011-05-05
> **matt_symes said:**
> Hi

I' glad it's fixed :D



BTW: I did mean to delete the backup file dracut-kernel-postrm.old as dracut-kernel-postrm should have been handled by the update process.

Please mark this post as solved.

Kind regards

Thanks again. I have one question, just to be clear: 

Deleting the backup file leaves the modified file with the last line commented out. 

Is that last line never required again? 

I would have thought that after getting the not-removed, not-installed "broken" packages fixed, the commented out line might be added back. 

If this is not to be done, then it would seem this line is not needed - which then leads one to question, What was the purpose of it, if it is not needed? Why is that line in the script at all?

I just want to verify if it is safe or desirable to leave the last line commented out, so it will not be invoked in future package software updates.

Thanks!

---

### Post by matt_symes on 2011-05-05
Hi

To be honest i thought that file might be removed by the uninstallation process.

As it has not been uncomment the line and update and upgrade again. Report an issues.

Kind regards

---

### Post by polarsnow on 2011-05-06
> **matt_symes said:**
> Hi

To be honest i thought that file might be removed by the uninstallation process.

As it has not been uncomment the line and update and upgrade again. Report an issues.

Kind regards

After un-commenting the last line, then I ran the following with the following result:

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I had already done the upgrade of all that needed upgrading.

---

