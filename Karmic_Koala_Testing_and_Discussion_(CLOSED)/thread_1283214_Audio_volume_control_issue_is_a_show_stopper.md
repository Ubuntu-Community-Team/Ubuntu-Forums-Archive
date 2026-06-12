---
title: "Audio volume control issue is a show stopper"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-10-05
My laptop has a sub-woofer controlled via an LFE channel, but I can't use it as it reaches full volume before the main speakers increase. I can disable the LFE channel, but that is not a good workaround. I know this issue only affects a few users, but is this behaviour going to change? I'd like to be able to configure which channels the volume controls the same way it is in Jaunty. If this is not going to change, is there a way to upgrade to Karmic without this problem, perhaps by using some Jaunty packages?

Any thoughts?

---

### Post by phenest on 2009-10-05
I worked out an interesting "fix" based on [this comment]("http://ubuntuforums.org/showpost.php?p=7827819&postcount=18"). Set the LFE channel and the Master channel to ignore (volume = ignore). Open alsamixer in a terminal and set the Master and LFE to 100%. You'll then find (at least I did), that the volume control moves PCM ONLY.

---

