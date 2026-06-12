---
title: "upgrade whoas to karmic  .ICEauthority  errors"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by harrismh777 on 2010-05-19
Greetings folks,
I bit the bullet tonight and upgraded over the net from jaunty to karmic. 

In the process I found that I did not have enough space in var, so I had to move things around a bit, mount a larger partition as var, copy var stuff... and yadda yadda... the install was successful. BUT,  somehow, in moving everything back I honked up the permissions for gdm. So, I get that message about not being able to update /var/lib/gdm/.ICEauthority and then the message about the config server having an error (256) ...blah. 

I got around the problem with  sudo chown -R gdm /var/lib/gdm  

(and)                         sudo chgrp -R gdm /var/lib/gdm

BUT, what I'd really like is for someone who is running karmic to post the permissions for everything in  /var/lib/gdm please.

thanks much.     (yes, I feel silly... I almost never do stuff like this)

---

