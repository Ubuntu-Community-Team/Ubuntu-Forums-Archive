---
title: "I cannot hear any sound after trying to upgrade ALSA"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-09-15
Hiyas:

I downloaded, extracted and installed the ALSA tarball that can be found at [http://ubuntuforums.org/attachment.p...8&d=1273598001]("http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001")
which includes every ALSA package needed.

However, I cannot hear any sound, the sound icon appears as muted, and no matter what I try to do with it, it always stays muted.

I have also run wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh

```
hihihi100@hihihi100-laptop:~$ wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh
--2010-09-15 22:12:34--  http://alsa-project.org/alsa-info.sh
Resolving alsa-project.org... 212.20.107.51
Connecting to alsa-project.org|212.20.107.51|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2010-09-15 22:12:35--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [   <=>                                 ] 27,026      36.8K/s   in 0.7s    

2010-09-15 22:12:36 (36.8 KB/s) - `alsa-info.sh' saved [27026]

WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.MACihE1KGT/alsactl.tmp: No such file or directory



Your ALSA information is in /tmp/alsa-info.txt.7wAXgH3x3j

hihihi100@hihihi100-laptop:~$ 

```I also uploaded the whole thing:

```
Your ALSA information is located at http://www.alsa-project.org/db/?f=e5bc33251111b7c8551e4cd9734227ca02a8657a


```
check it here: [http://www.alsa-project.org/db/?f=e5bc33251111b7c8551e4cd9734227ca02a8657a](http://www.alsa-project.org/db/?f=e5bc33251111b7c8551e4cd9734227ca02a8657a)
Help please

---

