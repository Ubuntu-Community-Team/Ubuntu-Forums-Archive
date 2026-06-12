---
title: "Line in on macbook pro 5,3 (Lucid)"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KaOS-bEat on 2010-03-28
Hi,


I'm running ```
Linux 2.6.32-14-generic-pae #20-Ubuntu SMP Sat Feb 20 07:07:46 UTC 2010 i686 GNU/Linux
```
on my macbook pro 5,3 with a 
```
$ cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xe7480000 irq 21
```


Sound is working fine except for line in. There is no option for selecting it. The internal microphone works fine, but I want to capture audio and that seems impossible!

In OSX this works fine, but I use jack together with some linux only software, I really want to get this working. Ideas?

the only capture device listed is this one
```
$ cat /proc/asound/card0/pcm0c/info 
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: Cirrus Analog
name: Cirrus Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

```

pulseaudio gives me a lot of options like full stereo duplex and analog in/out, digital in/out, surround and all possible mixes of these, but when going to the input selection dialog, I only have the built-in mic to select from.

so for me getting the digital and/or analog in to work... that would be great.


Thanks


K

---

