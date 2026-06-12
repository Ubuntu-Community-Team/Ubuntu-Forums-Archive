---
title: "Can't play back MIDI files"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by vanyat77 on 2011-11-06
Hi,
It doesn't matter what program I use. Midi files won't play back. Like in "LMMS" I receive this message when I import a midi file:

"*You do not have set up a default soundfont in the settings dialog (Edit->Settings). Therefore no sound will be played back after importing this MIDI file. You should download a General MIDI soundfont, specify it in settings dialog and try again.*"

The MIDI file will be imported, but in the program I don get any sound. I tried using other programs like "Note Edit" or "Rosegarden" but the problem remains.

MIDI-files will be played back when I move the cursor over the file in "Nautilus" or when I open them with "Totem"

Please can someone help me!

---

### Post by neu2buntu on 2011-11-10
you will need to have a soundfont installed ( use synaptic and search soundfont ). once installed it will reside in /usr/share/sounds/sf2 and just point lmms to the file within that folder. next in lmms you will have to use the soundfont player (sf2player) to load that soundfont into a track that your midi is on, alternatively you can use any instrument
on your midi track in the song editor as long as its not a drum track.
(i have created a few drum soundfonts from hydrogen drumkits which might make their way into lmms in the near future so this will not be a problem any more )

---

