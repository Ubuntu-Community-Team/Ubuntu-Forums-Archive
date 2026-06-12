---
title: "Installscript for wireshark"
date: 2019-07-28
forum: Installation &amp; Upgrades
---

### Post by catman2 on 2019-07-28
I would like to install wireshark with an automatic install script. 

A script like that
```

#!/bin/bash
sudo apt install wireshark
# do lots of other stuff

```
will halt and wait for user input on allowing non-root users to run dumpcap. How can i provide the answer "yes" automatically?

---

