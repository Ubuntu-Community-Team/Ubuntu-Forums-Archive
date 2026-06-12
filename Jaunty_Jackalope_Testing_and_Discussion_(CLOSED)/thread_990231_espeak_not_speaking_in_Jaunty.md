---
title: "espeak not speaking in Jaunty"
date: 2008-11-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RockDoctor on 2008-11-22
Nothing like grabbing from the Jaunty repositories 5 months before release. Desktop is LXDE (more or less). Anyway, sound seems to be working (play, aplay both work) but espeak won't speak. The only pulseaudio package installed is libpulse0 (gxine objects if I remove it). Synaptic indicates no broken packages. Am I missing an undocumented dependency?

---

### Post by bapoumba on 2008-11-23
Moved to Jaunty.

---

### Post by RockDoctor on 2008-11-25
> **RockDoctor said:**
> Nothing like grabbing from the Jaunty repositories 5 months before release. Desktop is LXDE (more or less). Anyway, sound seems to be working (play, aplay both work) but espeak won't speak. The only pulseaudio package installed is libpulse0 (gxine objects if I remove it). Synaptic indicates no broken packages. Am I missing an undocumented dependency?

Responding to my own post with this crude workaround:	:confused:
```

#!/bin/bash

# espeaker.sh - a temporary work-around for espeak not working in Jaunty
# 20081125 RockDoctor

#0. generate wav_file_name
#1. espeak -w <wav_file_name> <text_to_be_spoken>
#2. aplay wav_file_name
#3. rm wav_file_name

FILENAME=$RANDOM.WAV
espeak -w $FILENAME "$@"
aplay $FILENAME 2> /dev/null
rm $FILENAME
exit 0

```

---

### Post by rivalarrival on 2009-03-19
I've got a similar problem. Playback from espeak is incredibly choppy on a jaunty alpha-6 installation. It sounds like its only playing back a short part of each phenome. "Machine-gun" would be the best way I could describe it.

RockDoctor's crude workaround works. :-)

---

