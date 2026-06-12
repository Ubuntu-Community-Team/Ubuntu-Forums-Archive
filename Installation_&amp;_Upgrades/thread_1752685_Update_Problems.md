---
title: "Update Problems"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by DaMonsterMonster on 2011-05-08
hey guys i was being a little impacient with my friends Dell Inspiron 1545 tonight..
i was updating to 11.04 from 10.10 and decided to install adobe flash player plugins at the same time...
so since i was installing 11.04 it wouldnt install adobe...i went back to the distribution upgrade now this pulls up...
Not all updates can be installed
run a partial upgrade.....
i hit run partial...now this comes up..
Can not upgrade
An upgrade from 'maverick' to 'lucid' is not supported with this tool.

ive restarted the computer....nothing...any help??
UPDATE:when i hit reload this comes up
AN ERROR HAS OCCURRED
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

---

### Post by zvacet on 2011-05-08
If you upgraded to Natty you should not have Maverick lines in your source list.In terminal

```
gksudo gedit /etc/apt/sources.list
```

check if you have 

[http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

and 

[http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main 


If you have both of them delete one witch point to maverick release.If you have just one with maverick in line,then just replace maverick with natty.save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

