---
title: "intel HDA: audio gone"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2009-06-19
I have an intel HDA chip, and the audio does not work. Instead of correct sounds I hear some freezes from the sound card, that stop when I mute the volume (or stop the audio track)

I've tried to fix if running the followind commands (as suggested in another forum thread) but they don't work:
```
pulseaudio --kill
rm -rf ~/.pulse*
pulseaudio --start

```

---

### Post by taavikko on 2009-06-19
Intel HDA doesn't say anything,
please post the output of: "aplay -l"

does "aplay /usr/share/sounds/question.wav" produce any sounds

also, check that no channels are muted with
"alsamixer" and "alsamixer -Dhw"

---

### Post by yelo3 on 2009-06-19
sorry, the model is STAC92xx
aplay produces "bzzz bzzz" as usual
alsamixer shows that PCM is at 0%

I have now fixed it using alsamixer, thanks for this help!

---

