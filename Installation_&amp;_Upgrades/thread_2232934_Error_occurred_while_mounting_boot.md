---
title: "Error occurred while mounting /boot"
date: 2014-07-05
forum: Installation &amp; Upgrades
---

### Post by Juul on 2014-07-05
I wanted to remove Windows 7 and Ubuntu 13.10 from my laptop and just create one partition for Ubuntu 14.04, but this seems to be more difficult then I thought it would be.

Installation seems to go perfect, but the first time I boot my PC I get a black rectangle with a small border of a few pixels in an other color (I think the computer is trying to load GRUB). The second time I try to boot GRUB appears. But then I get a screen with an error: `An error occurred while mounting /boot. Press S to skip mounting or M for manual recovery`. I have already tried a few things like formatting the whole disk and reinstalling, but this gives the same problem.

`grep boot /etc/fstab` gives:

```
    /boot was on /dev/sda1 during installation
    UUID=8f1dc104-1ba0-4783-9b16-4302e24855ce /boot ext2 defaults 0 2
```

`blkid | grep ext` gives:

```
    /dev/sda1: UUID="8f1dc104-1ba0-4783-9b16-4302e24855ce" SEC_TYPE="ext2" TYPE="ex4"
    /dev/mapper/ubuntu--vg-root: UUID="32787824-e81d-4a6a-92b5-ba7ca2ac6875" TYPE="ext4"
```

I used the boot repair program [which I found here]("https://help.ubuntu.com/community/Boot-Repair") and I still got the same problem. The output of the program is this: [http://paste.ubuntu.com/7750787/]("http://paste.ubuntu.com/7750787/")

All extra input about in which direction I need to seek is more then welcome!

---

### Post by steeldriver on 2014-07-05
What partition options did you choose at install time? I don't remember  LVM + separate boot partition being a 'standard' option - did you select  'someting else' and manually partition the disk?

I always find those bootinfo outputs hard to understand, however a couple of things stand out as suspicious:

```

ubuntu-vg-root[COLOR=#ff0000]**'**[/COLOR]: _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

ubuntu-vg-swap_1[COLOR=#ff0000]**'**[/COLOR]: _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

```

and then later
```

File descriptor 63 (pipe:[58625]) leaked on lvdisplay invocation. Parent PID 27400: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-root'
  Volume group name ubuntu-vg-root' has invalid characters
  Skipping volume group ubuntu-vg-root'

```
and
```

File descriptor 63 (pipe:[58625]) leaked on lvdisplay invocation. Parent PID 27432: bash
  skip_dev_dir: Couldn't split up device name ubuntu-vg-swap_1'
  Volume group name ubuntu-vg-swap_1' has invalid characters
  Skipping volume group ubuntu-vg-swap_1'

```

perhaps indicating a naming snafu (trailing single quotes) with the VGs?

---

