---
title: "No sound on SBx00 Azalia (Intel HDA) after upgrade 9.10 -&gt; 10.04"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by marllowe on 2010-12-31
Hi,

After upgrade sound stopped working.
```
alsamixer 
``` return:
cannot open mixer: No such file or directory

```
ls -l /dev/dsp
```return:
No such file or directory

```
aplay -l
```return: 
aplay: device_list:223: not found any sound card ...

```
lspci|grep Audio
```return:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Of course, before upgrade sound worked properly.

---

### Post by mörgæs on 2011-01-01
Do you have sound, if you boot a 10.04 live CD?

---

### Post by marllowe on 2011-01-03
> **mörgæs said:**
> Do you have sound, if you boot a 10.04 live CD?
I don't have 10.04 live CD.
I solved this problem.
Load module to kernel:
```
sudo modprobe snd_hda_intel model=asus
```To do this automatically add this line i /etc/rc.local
```
modprobe snd_hda_intel model=asus
```I don't understand why upgrade broke something that worked well...

---

