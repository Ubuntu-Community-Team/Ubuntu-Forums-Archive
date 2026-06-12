---
title: "Ubuntu failed after upgrade from 10.04 to 12.04"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by ufukeskici on 2013-03-09
Hello,

I have installed Ubuntu 10.04 (64-Bit) to run with my existing Suse & Win7 partitions. 

It was working fine at the beginning, so I tried to upgrade to 12.04 LTS at first login.

After some time, it said like this: "process halted because of lot of erros". Then had to restart my computer.

Now when I start Ubuntu, it doesn't work. It says:
[B]
"disk drive for / is not ready yet or not present.
Continue to wait, or press S to skip mounting or M for manual recovery"[/B]

I'm completely newby to Linux staff, so any help is apprecaited. :(

Thanks in advance!
Ufuk

---

### Post by ufukeskici on 2013-03-09
I have searched the web and tried a solution:
```

mount -n -o remount,rw /
dpkg --configure -a

```

It worked and now Ubuntu is running. 
But there is a warning on the system bar about package manager.
When I want to install updates software crashes:
```

The following packages have unmet dependencies:

ntfs-3g: Depends: libntfs-3g75 but it is not installed
ubuntu-minimal: Depends: resolvconf but it is not installed

```
 and wants me to run the following commands:
```
ufuk@ufuk-ubuntu:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ufuk@ufuk-ubuntu:~$
```

How can I fix this issue?

---

### Post by tgalati4 on 2013-03-09
Go ahead and run:

```
sudo apt-get install -f
```

Post the output or perform the requested actions.

Clean installs are recommended over in-place upgrades.  It sounds like you installed 10.04 and then you immediately tried to install 12.04.  Why didn't you just install 12.04 instead?  Also, if you didn't perform any upgrades on the 10.04 system, then you might not have a clean base from which to upgrade to 12.04.  Just another pitfall of trying to perform an in-place upgrade.

---

### Post by ufukeskici on 2013-03-09
```

ufuk@ufuk-ubuntu:~$ sudo apt-get install -f
[sudo] password for ufuk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cups-pk-helper appmenu-gtk openoffice.org-l10n-en-gb
  linux-headers-2.6.32-21-generic appmenu-qt gir1.2-gconf-2.0
  linux-headers-2.6.32-21 appmenu-gtk3 openoffice.org-l10n-common
  gir1.2-panelapplet-4.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ntfs-3g resolvconf
The following NEW packages will be installed:
  resolvconf
The following packages will be upgraded:
  ntfs-3g
1 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/661 kB of archives.
After this operation, 1,437 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 195863 files and directories currently installed.)
Unpacking resolvconf (from .../resolvconf_1.63ubuntu16_all.deb) ...
Preparing to replace ntfs-3g 1:2010.3.6-1ubuntu1 (using .../ntfs-3g_1%3a2012.1.15AR.1-1ubuntu1.2_amd64.deb) ...
Unpacking replacement ntfs-3g ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
Processing triggers for hal ...
Regenerating hal fdi cache ...
Setting up resolvconf (1.63ubuntu16) ...
runlevel:/var/run/utmp: No such file or directory
resolvconf start/running
Setting up ubuntu-minimal (1.267.1) ...
Setting up ntfs-3g (1:2012.1.15AR.1-1ubuntu1.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for resolvconf ...
runlevel:/var/run/utmp: No such file or directory
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

is it OK now?

---

### Post by ibjsb4 on 2013-03-09
Looks like it did some good.  Will it boot?

---

### Post by tgalati4 on 2013-03-09
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

You will need to perform a few reboots, because there's a lot of new code that needs to be configured and certain packages have to be configured before others, so don't expect stable operation until a few days and a few reboots.  Perform the above steps every few days until there are no more updates.

Every so often, clean out the unused packages:

```
sudo apt-get autoremove
```

---

### Post by ufukeskici on 2013-03-10
> **ibjsb4 said:**
> Looks like it did some good.  Will it boot?

it boots normally now.


@tgalati4 thanks for the advices. ;)

---

### Post by osbeav on 2013-03-13
Hi. Still a newbie here with the same problem. Have enjoyed my Ubuntu journey so far.  In this case, I also went from 10.04 to 12.04.

@ufukeskici- Which commands worked for you?  And did you hit 'M' to manually recover to get the command line?

Thanks in advance for any assistance.

---

### Post by ufukeskici on 2013-03-13
> **osbeav said:**
> Hi. Still a newbie here with the same problem. Have enjoyed my Ubuntu journey so far.  In this case, I also went from 10.04 to 12.04.

@ufukeskici- Which commands worked for you?  And did you hit 'M' to manually recover to get the command line?

Thanks in advance for any assistance.

Yes, please hit "M" button to continue with Ubuntu CLI.

Then please use these:
```

mount -n -o remount,rw /
dpkg --configure -a

```

---

### Post by osbeav on 2013-03-13
@ufukeskici- Thanks. Can't wait to try this out.

One more question: what do I do after those commands?  Ctrl^d reboots the machine into GRUB.  Sorry, still a newbie.

Thanks again.

---

### Post by ufukeskici on 2013-03-14
> **osbeav said:**
> @ufukeskici- Thanks. Can't wait to try this out.

One more question: what do I do after those commands?  Ctrl^d reboots the machine into GRUB.  Sorry, still a newbie.

Thanks again.

Reboot the machine then you will see Ubuntu desktop. ;)

---

