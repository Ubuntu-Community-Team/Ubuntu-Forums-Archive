---
title: "USB Soundblaster Optical Out not working"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2010-12-05
I migrated to 10.04 (clean install) from 9.10 recently. I have no problems with internal sound card playback but cannot get the USB Creative Audigy Optical port working. I have defined it as Digital Output in Pulse Audio and when an application plays audio I can see Pulse Audio showing output but no output from the Audigy.

I would appreciate if anyone has come across this problem and if so could give some pointers to fix this issue.

Thanks

---

### Post by gdesilva on 2010-12-06
Upon further checks I found that although I defined Digital Out as the output port (which is also confirmed by Alsamixer settings) actual output is done on the Surround Front port. In fact it makes no difference whether I change the output port to any other port still the sound is delivered to Surround Front port.

---

### Post by gdesilva on 2010-12-10
For the benefit of those who may come across the same problem the solution was outlined by daniel49 @ [http://www.linuxquestions.org/questions/ubuntu-63/sound-blaster-audigy-2-zs-337513/](http://www.linuxquestions.org/questions/ubuntu-63/sound-blaster-audigy-2-zs-337513/) - thanks daniel49.

Essentially this is what I did.

1. from a terminal start alsamixer by typing alsamixer.
2. F6 will give you a menu to choose the soundcard when you have more than one
3. F3 gives the playback settings
4. In my case the Digital Out box had 'MM' - this means the digital out port is muted. By selecting Digital Out and typing M it was possible to unmute the port.
5. Arrow across to next setting which picks the source for Digital Out. Set this to Front

This should get your sound working from Optical port.

---

