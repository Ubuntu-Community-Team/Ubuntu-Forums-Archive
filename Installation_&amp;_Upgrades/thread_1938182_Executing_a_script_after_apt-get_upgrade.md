---
title: "Executing a script after apt-get upgrade"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by Axio on 2012-03-09
Hi,

I would like to execute a script automatically after each apt-get upgrade. Is there an easy way to do that?

---

### Post by codemaniac on 2012-03-09
Try doing an apt-get upgrade through a script and call your script other script from current one .

---

### Post by baumanno on 2012-03-09
```

#!/bin/bash

# This runs update and upgrade
sudo apt-get update; sudo apt-get upgrade

# Change into the directory of your script
cd ~/scripts

# And run it
./my_script.sh

# Or run some other command
dpkg --get-selections | grep firefox

```

Then, providing this script is called "after-update.sh", run

```
chmod +x after-update.sh
./after-update.sh
```

Cheers

---

### Post by raja.genupula on 2012-03-09
```
sudo apt-get upgrade ; ./<your script >
```

---

### Post by Axio on 2012-03-09
THanks it is what I needed! I should have thought about it before.

---

### Post by codemaniac on 2012-03-09
IF you have got your solution , never forget to mark the thread as closed .
Cheers .

---

### Post by pavi_elex on 2012-03-09
apt-get upgrade && sh "path of your script"

---

