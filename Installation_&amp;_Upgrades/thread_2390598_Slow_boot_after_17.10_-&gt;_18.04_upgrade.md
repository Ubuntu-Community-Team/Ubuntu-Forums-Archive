---
title: "Slow boot after 17.10 -&gt; 18.04 upgrade"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by piu130 on 2018-04-30
I've upgraded my kubuntu 17.10 to 18.04 recently. Now the boot is really slow. From about 8 seconds to 40 seconds. The ```
dmesg
``` peaks are:
```

[    3.772885] [drm] RC6 on
[   34.502625] EXT4-fs (nvme0n1p5): mounted filesystem with ordered data mode. Opts: (null)

```
and maybe
```

[   36.626981] Bluetooth: hci0: Applying Intel DDC parameters completed
[   39.306767] Could not find key with description: [448f93ab6910c98f]

```
Does someone has the same issue? How can I fix it?

---

### Post by Claus7 on 2018-04-30
Hello,

I'm searching the issue myself as well for my ubu box. I do not face such an issue as yours, yet I came accross the following commands:
```
systemd-analyze time
systemd-analyze blame
systemd-analyze critical-chain
```

which probably will shed more light to your issue.

Some thoughts from the messages you receive: do you have any bluetooth dongle attached to your system? Trying to remove it does it affect your boot time in great extent?

I do not have any messages that are the same as yours appart from:
> [    4.294531] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

Regards!

---

### Post by kassanunda on 2018-05-01
Same issue.

[    2.844760] [drm] RC6 on
[   63.454571] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)


I also tried modifying /etc/initramfs-tools/conf.d/resume (resume=none (instead of UUID)) but no help

---

### Post by piu130 on 2018-05-01
```
systemd-analyze time
```
Startup finished in 34.554s (kernel) + 5.078s (userspace) = 39.633s
graphical.target reached after 5.074s in userspace
```
systemd-analyze blame
```
4.107s NetworkManager-wait-online.service
           361ms systemd-logind.service
           340ms dev-nvme0n1p6.device
           268ms mpd.service
```
systemd-analyze critical-chain
```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @5.074s
&#9492;&#9472;multi-user.target @5.074s
  &#9492;&#9472;kerneloops.service @5.067s +6ms
    &#9492;&#9472;network-online.target @5.067s
      &#9492;&#9472;NetworkManager-wait-online.service @959ms +4.107s
        &#9492;&#9472;NetworkManager.service @794ms +162ms
          &#9492;&#9472;dbus.service @769ms
            &#9492;&#9472;basic.target @761ms
              &#9492;&#9472;sockets.target @761ms
                &#9492;&#9472;snapd.socket @760ms +1ms
                  &#9492;&#9472;sysinit.target @758ms
                    &#9492;&#9472;systemd-timesyncd.service @588ms +170ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @574ms +12ms
                        &#9492;&#9472;local-fs.target @572ms
                          &#9492;&#9472;boot-efi.mount @564ms +7ms
                            &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-1A02\x2dCCC9.service @506ms +57ms
                              &#9492;&#9472;dev-disk-by\x2duuid-1A02\x2dCCC9.device @505ms

> **Claus7 said:**
> Some thoughts from the messages you receive: do you have any bluetooth dongle attached to your system? Trying to remove it does it affect your boot time in great extent?
Build in bluetooth (notebook)

---

### Post by Claus7 on 2018-05-01
Hello,

> **piu130 said:**
> ```
systemd-analyze time
```
Startup finished in 34.554s (kernel) + 5.078s (userspace) = 39.633s
graphical.target reached after 5.074s in userspace


If you compare it with mine (I use hdd and installing different kernels at the time):
> $ systemd-analyze time
Startup finished in 5.483s (kernel) + 2min 32.315s (userspace) = 2min 37.798s
graphical.target reached after 2min 32.308s in userspace

then you will see that you have a huge boot time of your kernel.
Which kerner are you using? Check it with:
```
uname -a
```

I would suggest you to try a different one, if possible, and see the results. I cannot see any other component affecting your boot time.

Regards!

---

### Post by piu130 on 2018-05-02
```
uname -a
```
gives 4.15 then I tried it with 4.13. Same problem.

I turned off "quiet splash" in grub and the boot stocks at the line

```
Begin: Running /scripts/local-premount ... [ 3.805190] [drm] RC6 on
```

---

### Post by piu130 on 2018-05-02
I found the solution here: [https://askubuntu.com/questions/1013830/slow-boot-long-kernel-load-time-due-to-wrong-resume-device](https://askubuntu.com/questions/1013830/slow-boot-long-kernel-load-time-due-to-wrong-resume-device)

In the file /etc/initramfs-tools/conf.d/resume there was an UUID defined that did not match any of my partitions UUID ('sudo blkid' to see the UUIDs).

So I wrote 'RESUME=none' instead of 'RESUME=UUID=xyz' and then executed 'sudo update-initramfs -u'.

Is there a problem with this solution? What UUID should be there to resume instead of none or the wrong one? Should I use cryptswap UUID there? Or the normal swap?

---

### Post by Claus7 on 2018-05-02
Hello,

first of I do not have such a configuration. This means that in my case the numbers are the "correct" ones (the output UUID from blkid of the swap partition is the same as the one in the resume file). 

Now in your case:
1) by adding none it seems to me that you are disabling your swap partition. Take a look also here:
[https://ubuntuforums.org/showthread.php?t=2291078](https://ubuntuforums.org/showthread.php?t=2291078)

2) you could add the UUID of your swap partition instead of none in order not to deactivate it:
so from sudo blkid check the string number that you get for your swap partition

then go to /etc/initramfs-tools/conf.d/resume file and add the string number you just got

finally run sudo update-initramfs -u to apply changes.

You could check it out and see if it works. 

Regards!

---

