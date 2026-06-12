---
title: "what does this mean?"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by xoron on 2010-11-26
hi everyone! :D

im trying to install player/stage with a script but the install gets stuck on the last line of this bit 

but i dont know what it means so i cant tinker with it

```


#Setting the path by appending to .bashrc
STAGE_INSTALL_DIR=/usr/local
echo "" >> ~/.bashrc 
#echo "export PATH=\"\$PATH:/<PLAYER_INSTALL_DIR>/bin\"" >> ~/.bashrc  # Used if not installing in usr/local
echo "export LD_LIBRARY_PATH=\"$STAGE_INSTALL_DIR/lib\"" >> ~/.bashrc
echo "export STAGEPATH=\"$STAGE_INSTALL_DIR/lib\"" >> ~/.bashrc
echo "export PLAYERPATH=\"$STAGE_INSTALL_DIR/lib\"" >> ~/.bashrc


source ~/.bashrc


```

thanks in advanced :D

---

### Post by ToFue on 2010-12-04
I may be off, but does the script have the bash header on the first line?

```

#!/bin/bash

...<script material>


```


what's the errors? output? that'll help someone more knowledgable as well..
:popcorn:

edit: I ran accross two places that would help you, after finding out what player/stage was:
[http://www.haroldsoh.com/tutorials/technical-skills/installing-playerstage-from-2/](http://www.haroldsoh.com/tutorials/technical-skills/installing-playerstage-from-2/)
...and...
[http://ubuntuforums.org/showthread.php?t=1124418](http://ubuntuforums.org/showthread.php?t=1124418)

---

