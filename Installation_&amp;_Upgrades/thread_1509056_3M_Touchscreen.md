---
title: "3M Touchscreen"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by tsx_5 on 2010-06-13
Hi,

I am trying to get my 3M touchscreen to work in Ubuntu.  Presently, I have the usbtouchscreen module loaded -- which results in touches being recognized, but the y-axis is backwards (ie: if I press at the top, it shows up at the bottom).  Given that hal is depreciated, the only place I could note for configuration options the xorg.conf.d directory. But, I'm unsure what needs to be added there.

Additionally, I am confused over usbtouchscreen vs evdev vs evtouch -- which is supposed to be used at this point?

Ok, some system info:

I am running Ubuntu 10.04

xinput list
 Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=11   [slave  pointer  (2)]
&#9116;   &#8627; 3M 3M USB Touchscreen - EX II             id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]

xinput -test ... (output sample)
motion a[0]=3295 a[1]=12508
motion a[0]=3277 a[1]=12498
button press   1
button release 1
motion a[0]=4250 a[1]=12035
motion a[0]=4306 a[1]=11986
motion a[0]=4324 a[1]=11963
motion a[0]=4304 a[1]=12031
motion a[0]=4323 a[1]=11998
motion a[0]=4367 a[1]=11937
motion a[0]=4376 a[1]=11986
motion a[0]=4431 a[1]=11967
motion a[0]=4435 a[1]=11938
motion a[0]=4491 a[1]=11825
motion a[0]=4482 a[1]=11859
motion a[0]=4517 a[1]=11863
motion a[0]=4528 a[1]=11890

Thanks in advance,

---

### Post by tsx_5 on 2010-06-14
Bump...

Would appreciate any hints.

---

