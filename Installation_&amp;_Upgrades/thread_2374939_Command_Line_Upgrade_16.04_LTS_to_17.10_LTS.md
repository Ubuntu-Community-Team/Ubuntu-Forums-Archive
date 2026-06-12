---
title: "Command Line Upgrade 16.04 LTS to 17.10 LTS?"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by tecknomage on 2017-10-20
Running **Ubuntu 16.04 LTS** on my desktop.

_Ubuntu Server site_ says use "do-release-upgrade"

For desktops, what is the correct steps (*all*) for **command-line upgrade** :-s

---

### Post by slickymaster on 2017-10-20
The exact same command```
sudo do-release-upgrade
``` but it's advisable that you check if the update-manager-core package is installed on your system by first running```
sudo apt-get install update-manager-core
```

---

### Post by Kirboosy on 2017-10-20
Just to make sure there isn't any confusion. **17.10 is not an LTS**. I'm not sure if that changes things for you since this is a server you want to upgrade. The next LTS will be 18.04.

Hope that helps!

---

### Post by deadflowr on 2017-10-20
Currently there will be no upgrade path directly to 17.10 from 16.04.
You have to upgrade to 17.04 first.
In a few months when 17.04 support ends, you can then upgrade directly from 16.04 to 17.10.

---

### Post by tecknomage on 2017-10-21
OK, I'm confused :-?

**What IS the current _Desktop LTS_ Release?**

---

### Post by jeremy31 on 2017-10-21
The newest LTS is 16.04 and the only other LTS is 14.04

---

### Post by deadflowr on 2017-10-21
LTS releases come out in April of even numbered years.
So the last was 2016.
Next will be 2018.

---

### Post by tecknomage on 2017-10-23
Thanks.

Now it would be nice if Conical/Ubuntu would allow us to signup for **email notification** when new LTS (not beta) are released. 8-)

---

### Post by ian-weisser on 2017-10-23
Normal releases are not 'beta'. They are normal.
You can sign up for notification (not email) using your Software & Updates control panel. It's a setting. Otherwise, simply put it on your calendar every two years in April.

---

