---
title: "soundblaster x-fi fatal1ty pro in karmic"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fcuk112 on 2009-10-23
i've just installed karmic RC, the x-fi is detected but i still get no sound.  i tried **alsamixer -c0** but no joy. the x-fi is currently configured to analog stereo output.  anyone have any idea how i can get it to work?

thanks.

---

### Post by fcuk112 on 2009-10-23
bump

---

### Post by raygj on 2009-10-24
go to your Desktop menu -->"System" and open "Control Center".click on "Volume Control" a "Sound Preferences" window will open.click on the "Output" tab.
Your detected and running sound cards will show up with a "o" at the begining of each line.this "o" will have a "dot" inside to show the selected output sound card.to change "output" to X-Fi sound card listed you must "left mouse click with the "mouse pointer" "within" the empty "o" at the left of the line naming your X-Fi sound card.

---

### Post by fcuk112 on 2009-10-24
i assume you mean open the sound dialog from system->preferences.  on the output tab i only see "SB X-Fi Analog Stereo" and it's selected.

---

### Post by fcuk112 on 2009-10-24
after some searching on google, i created the ~/.asoundrc file with the following:

pcm.!default {
  type plug
  slave.pcm "surround51"
  slave.channels 6
  route_policy duplicate
}

now gstreamer-properties sound output test works fine.  and when i set my output to SB X-Fi Analog Surround Sound 5.1, i am getting sound.

the problem now is that i am getting some crackling/hiss/static.  i tried lowering the PCM and that helps a little.  but how do i completely get rid of the noise?

thanks.

---

### Post by fcuk112 on 2009-10-24
hummm, i think i seem to have resolved the issue.  the .asoundrc file was a red herring, it could be completely removed.

all i did was install the pulseaudio volume control via the ubuntu software centre and turned the rear right channel down.  that was the one that was causing the crackling noise - why i have no idea.

i am using a 2.1 setup, but the output is configured as analog surround 5.1 (there was no 2.1 option).

---

