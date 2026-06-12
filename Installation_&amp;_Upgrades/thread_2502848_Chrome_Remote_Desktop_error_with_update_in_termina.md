---
title: "Chrome Remote Desktop error with update in terminal"
date: 2024-12-02
forum: Installation &amp; Upgrades
---

### Post by jduff on 2024-12-02
If you are getting this error message when updating in terminal:

N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome-remote-desktop/deb stable InRelease' doesn't support architecture 'i386'

People will tell you that you need to remove # for [arch=amd64] in an etc file for chrome or chrome remote desktop to force your update to ignore i386. In theory that should work but it does not.

The way to stop this error message is to go to Software & Updates in your system, then click on tab Other Software, then uncheck [http://dl.google.com/linux/chrome-remote-desktop/deb/stable](http://dl.google.com/linux/chrome-remote-desktop/deb/stable) main and then click close, enter your password, then click close again, then click on reload, then enter password again and it will refresh your software cache. 

Then try updating terminal and you will not see the error message again. I have fixed several systems this way, so I know that this will work.

---

