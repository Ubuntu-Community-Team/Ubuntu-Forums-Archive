---
title: "Unable to boot after upgrade to 9.10 (possibly mount related)"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by nv22nv on 2010-02-19
Hello,

I need some help on the following subject:

I just upgraded from 8.04 to 9.10 in graphical mode (yes, I do already regret it). At the end of the process, I get an error message stating that there was an (unspecified) error and my system will be unusable.

I don't think that this has any importance, but just in case: I'm using encrypted home directories (but not an encrypted root partition). I allowed the upgrade wizard to replace *all* configuration files it wanted to and created backups of these files before they were overwritten. Immediately after they were replaced, I edited the new files so they had my manual changes applied to them again. The files I edited were:
```

/etc/bash.bashrc
/etc/pam.d/common-*

```

In the error message I was shown at the end of the upgrade process,

```
dpkg --configure -a
``` was recommended. I executed ```
dpkg --configure --pending
``` and rebooted.

Since then, I'm unable to boot my system. 

[b]This is what happens: 
[LIST]
[*]Grub will show as usual.
[*]I'm seeing the text "Starting up..."
[*]The splash screen or however this is called is shown for a few seconds, then I'm back to the console with the following error message:[/LIST]
```
General error mounting filesystems.
A maintainance shell will now be started.
```[/b]
Sometimes, some of the following lines are shown, but not always:
```

[  36.837297] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[  ##.######] usb 2-2: device not accepting address 3, error -71
usb_id[1095]: unable to access 'devices/pci0000:00/0000:00:1a.1/usb2/2-1'

``` (insert numbers for #)

Note: sdc is an external USB hard drive. When I switch it off, the first line from the previous code section won't be displayed, but my problem remains the same.

I'm given the option to login as root and analyze some stuff. When I do that, the root filesystem is mounted read-only, but other than that it shows everything correctly. The boot partition is not mounted, but can be mounted manually without a problem.

My boot partition does still only include the old 2.6.24-27 kernel. Could that be it? Using other, older kernel versions will lead to different kinds of problems, e.g. being unable to mount to root partition. Yet, when I enter the maintainance shell, the root partition **is** mounted (but just read-only). My boot partition does also include a self-compiled 2.6.30 kernel which has caused me some problems in the past and is therefore not used, but when I choose to boot with that one, the boot process advances further and I will end somewhere with just a black screen. How could I install the latest kernel version? After all, the root filesystem is mount read-only, so I can't use dpkg.

I don't have any clue what I can do. Any ideas? I'm grateful for any kind of input! Thanks in advance!

**Edit:** I created an exact backup of my root partition using dd before the upgrade. Restoring this backup would get my system working agin, would it? [-o<

---

### Post by nv22nv on 2010-02-19
It looks like the kernel was the problem. After installing the latest kernel by hand, I could reach the point where X starts but had a problem with graphics drivers ("Ubuntu will only wok in low-res mode"). I don't know why, but I couldn't find a way to get to a command line interface. Ctrl+Alt+F1, ..., Ctrl+Alt+F10 lead me to a text-only mode display, but there was no command prompt. 

I overwrote my root partition with the backup I created, and fortunately that get everything running again. I'll try again doing the update in text mode.

---

