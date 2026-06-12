---
title: "Battery died during system upgrade, now get blank screen on login"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by joegav24 on 2010-09-14
Please help. I believe i was performing a standard system upgrade (i think a new version of ubuntu was being downloaded and installed) and without realising, the battery died on my laptop. When i turned the laptop back on i got as far as the user log on screen where i entered my details expecting to see my usual desktop but i instead just got a blank screen.

What can i do to fix this problem?

Thanks 

Joe

---

### Post by sikander3786 on 2010-09-14
Press and hold down the shift key as soon as the computer gets past the Bios screen. GRUB menu will show up. Select recovery mode and select "Fix Broken Packages". If it doesn't work, select "Drop to root shell" or something like that. Try

```

apt-get clean

```

```

apt-get update

```

```

apt-get upgrade

```

If the above commands give some error, try,

```

apt-get install -f

```

Make sure your Ubuntu box is connected to the internet while you carry on the above mentioned commands.

And if you are unable to even drop to the shell, you might need a reinstall.

Post back any error messages received.

---

