---
title: "diablo 2 on wine after upgrade"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by Sempfinger on 2010-09-20
Hello there,

After upgrade from karmic to lucid, I am not able to play Diablo 2 (lod) under wine anymore.

I start D2 (installed on the win partition) via the following little script:
```

#! /bin/bash
# Run Diablo 2 on other X instance
export LAST_PWD=$PWD # Saves your last working path
cd /home/fps/mnt/sda2/Program\ Files/Diablo2/ #Goes to your diablo 2 install path
xinit /usr/bin/wine "Game.exe" -skiptobnet -- :1 vt9 # runs diablo 2 on a new X session at screen 1, on virtual terminal 9.
cd $LAST_PWD # On diablo exit, returns to your last working path.
exit 0

```

Now when I connect to battlenet, it says that my account does not exist. In windows everything runs as expected...

Strangest thing: When I tell a friend to log in for me, he can do so and play as usual with my account. If I then try to log in shortly after he has logged out, then there is no error message, but the game hangs and tries to connect forever...

Now I know that this is a very uncommon question, but I think this is the best place to ask for help, since there still are a few D2 gamers hanging out here (at least I hope so...)

Any ideas?

---

