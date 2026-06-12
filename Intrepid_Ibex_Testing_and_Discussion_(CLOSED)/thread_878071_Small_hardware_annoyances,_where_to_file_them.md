---
title: "Small hardware annoyances, where to file them?"
date: 2008-08-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-08-02
Hi,

I recently bought a new laptop, and I'm getting some small problems with my hardware, which seem to be easily solved following [this]("http://www.patrasblogs.gr/InShame/2008/06/05/Ubuntu_Hardy_Heron_on_a_Sony_Vaio_VGN-FZ31E"):

> Camera (05ca:183b): HAL loads a wrong module for the camera that in addition to not working, makes the laptop crash when you try to suspend it. So you must remove the misbehaving module from the kernel and prohibit reloading it (long process)

> Sleep and Hibernate: They don't work initially. The computers go to sleep but when awaken it stays in a black screen. Fixing the camera will fix this problem too. :-)

> Sound Card (8086:284b): Well, playback worked out of the box but when opening the sound options there were no recording controls and the sound was coming out only through the builtin speakers, plugging in headphones changed nothing. To fix all these problems follow these simple steps:

Type the following in a console:

echo "options snd-hda-intel model=vaio" | sudo tee -a /etc/modprobe.d/snd-hda-intel
and append the following line to the end of the file:
options snd-hda-intel model=vaio

Restart you computer

> Bluetooth (044e:3010): It is properly recognized by the system but it will not work. I found a simple solution but I hope to find a better one.

(Run) gksudo hciconfig hci0 reset

And a couple more issues. The question is, since it's actually quite easy to solve these issues, is there something I can do to get the laptop working fine "out of the box" when Intrepid comes out? Can I file bugs somewhere?

---

### Post by mitchellcipriano on 2008-08-02
There is a Hardware & Laptop section here: [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

### Post by Talon2 on 2008-08-02
File the bugs individually here:

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

