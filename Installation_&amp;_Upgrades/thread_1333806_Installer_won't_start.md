---
title: "Installer won't start"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by moogal on 2009-11-21
I've used various previous versions of ubuntu and xubuntu, and wanted to install 9.10 on my machine (which currently runs XP). Usually I download the ISO, burn and boot from the CD, and select "install" from the menu, which (unsurprisingly) usually starts the installer.

I downloaded xubuntu 9.10 and burned the CD, and as usual got the boot menu. Selected Install and got a screen with a flashing mouse image on it for a minute or two, then the screen went completely blank for a minute or two, then I just got an xfce desktop as if I'd selected to run the LiveCD instead!

On the menu bar was an icon for a crash report, which said:
File /usr/bin/ubiquity-dm line 271 in <module> ret=dm.run (*sys.argv[4])
File /usr/bin/ubiquity-dm line 100 in run raise XStartupError
"X Server failed to start after 60 seconds."

I'm not sure what ubiquity-dm is, nor what any of that error message means. Googling has come up with several people asking similar questions but I haven't found an answer yet.

I've done a check of the CD and even tried the memory check, both came up clean. A friend who'd also had install issues suggested I try some of the different APIC options under F6 on the installer menu, but these yielded the same problem.

Any ideas what else to try? I should point out that this machine has previously (at one time or another) run versions of Ubuntu and xubuntu from about 6.10 upwards, and they all installed like clockwork - this is the first time I've ever had a problem with the install process.

---

### Post by moogal on 2009-11-22
Since I posted the above I've also tried running the installer from the LiveCD, which was more successful in that the installer actually started, however, when it came to partitioning it only listed one of my disk drives (I have two physical disks in my machine, one 80 GB and one 250 GB) and stated that there were no operating systems on the machine (it boots XP), so I cancelled the install as I didn't want it screwing that up.

---

### Post by dcottingham on 2009-11-22
Here's a thing to try to debug it. When you get to the partition screen, hit ctrl-alt-F2, which gets you to a terminal screen. Then you can take a look in syslog to see what's going on, e.g. "more /var/log/syslog". You should see your disks listed by name somewhere in there, or you might see a useful error message.

Also, you can try manually looking at your disk's partition table, using fdisk. This requires some caution, because misuse of fdisk can trash your disk. To do this safely, say "fdisk -l /dev/sda". Don't forget the "-l". You can also check your other disk which is likely named /dev/sdb.

I would find it interesting if fdisk says your disk has no partition table, when you know perfectly it does, because this would then look like a bug I've recently encountered.

---

### Post by moogal on 2009-11-22
Starting with the Syslog, I took a look and the only potentially useful things I can see are the following (this is from a fresh attempt at choosing Install from the boot menu)

Several of these, mostly with exactly the same block number and sector number.
```
[sr0] Unhandled sense code
[sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[sr0] Sense Key: Medium Error [current]
[sr0] Add. Sense: L-EC uncorrectable error
end_request: I/O error, dev sr0, sector 1360208
Buffer I/O error on device sr0, logical block 340052

```These are occasionally interrupted with what looks like attempts to identify my printer, which throws a lot of errors while trying to work out what it is, but then finds it successfully.

It also throws an error when trying to start the wireless driver, but I don't think that's important here.

Then we get onto the interesting bit about the hard disks:
```

20microsoft: result: /dev/sda1:Microsoft Windows XP Professional:Windows:chain
50mounted-tests: debug: os found by subtest /usr/lib/os-probes/mounted/20microsoft
ntfs-3g[4141] Unmounting /dev/sda1 ()

```In a similar way it then finds my 2nd hard disk (sdb1) and correctly identifies that as well. No error messages anywhere in this section, until it's had a few plays with ntfsresize and comes up with the following:
```

ubiquity: /lib/partman/display.d/10initial_auto: 119: /lib/partman/automatically_partition//do_option: not found
ubiquity[2972]: debconffilter_done: ubiquity.components.partman (current: ubiquity.components.partman)
init: ubiquity main process (2017) terminated with status 1
gdm-binary[6336]: WARNING: Unable to find users: no seat-id found
gdm-binary[6336]: WARNING: GdmDisplay: display lasted 0.482606 seconds.
acpid: client 2429[0:0] has disconnected
acpid: client connected from 6343[0:0]

```Not sure what any of that actually means or if it's just normal.

On running the installer manually from the icon on the LiveCD desktop, I get the same set of hard disk detection output again with no error messages.

Trying to use "Manually partition" seemed to work, it brought up a progress bar, then a crash report appeared saying that devkit-disks-daemon closed unexpectedly. Clicking on this to find out what happened then knocked ubiquity-dm over as well. I then found a bug report (#452208 ) that basically said it's not a problem. I'm now trying the gung-ho approach of ignoring the error messages and trying to sort it out manually - will report back on how that goes.

What I'm still confused about is why choosing Install from the boot menu doesn't work at all.

---

