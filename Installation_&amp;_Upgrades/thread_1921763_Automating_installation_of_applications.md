---
title: "Automating installation of applications"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by tehowe on 2012-02-07
I'm updating my notebook to 11.10 so that I can familiarize myself with some of  the new features that have been introduced since 10.04 LTS. I'd like to  script the installation of a lot of the applications I had on 10.04 so that I don't have to sit in front of the machine all day, but  am wary of just shovelling everything I've currently installed at the  new setup by using dpkg --get-selections and --set-selections. (A lot of things I have installed need some additional configuration.)

This time, I'd like to basically have a bash script with a list of things to install eg;

```

#!/bin/bash
sudo apt-get install evolution
sudo apt-get install keepassx
sudo apt-get install calibre
(etc)
```

My question for the community is, do I need to add in any kind of waits  or timing mechanisms for this to be successful or will bash execute each  command in turn, waiting until the previous one is done? If I nail this now, It will be all sorted out for when I need to do the same for 12.04. Also, if  you've a better idea I'm all ears... thanks!

---

