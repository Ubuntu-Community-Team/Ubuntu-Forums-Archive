---
title: "No sound anymore after upgrade from 22.4 to 22.10"
date: 2022-10-26
forum: Installation &amp; Upgrades
---

### Post by c-tuxe on 2022-10-26
Hello. I also have no audio after upgrading from 22.04 to 22.10. I presume it is because 22.10 now uses Pipewire rather than pulse audio?

How do I install Pipewire?

I also only have the dummy output. 

In contrast to the OP, I use an AMD RX480 graphics card with audio via Displayport (there are two screens daisychained and I previously set up Pulse Audio to select the correct screen for audio output)

---

### Post by QIII on 2022-10-27
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2480339").

Please do not hijack the threads of other users.  That causes confusion for everyone.  In this case specifically, your issue my seem to be the same, but you are using different hardware than the OP of the other thread, so your solution may be entirely different.

---

### Post by c-tuxe on 2022-10-27
Good point, although there's a possibility that the solution might be the same also, as the fact that two different hardware performing the same upgrade step  resulted in only 'Dummy output' pointed to the source of the problem in all likelihood being abstracted from the hardware layer.

I also felt I could contribute to the OP's thread by pointing out that the new version of Ubuntu uses a new audio stack which is why I replied there rather than creating a new thread and the most likely target of my debugging efforts.

I really don't want to reinstall Ubuntu and would love some hints on how to fix the audio on 22.10.

---

### Post by c-tuxe on 2022-10-27
OK I seem to have fixed it.

After making sure the various pipewire packages were installed, I added my user to the 'audio' group and that has restored my audio. pavucontrol applet now shows all my devices like it used to.

Previously only the 'pulse' user was a member of the 'audio' group so I guess that pipewire works on a per-user basis.

---

### Post by cigtoxdoc on 2022-12-04
Please provide details of how you fixed the no sound, dummy output problem.

John

---

