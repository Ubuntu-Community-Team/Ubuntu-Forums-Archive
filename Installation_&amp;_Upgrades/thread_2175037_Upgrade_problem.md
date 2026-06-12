---
title: "Upgrade problem"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by spitfyre2 on 2013-09-17
[IMG]http://i5.imageban.ru/out/2013/09/17/615b5b70dc345963df18be1b8c4fc9e4.png[/IMG]

Keep having this problem since I tried to update about a week ago.

I'm using Voyager,but it's basically Xubuntu with a few additional programs.

I tried it in console to see what was going on,these are the results.I also tried it as root and had the same problem.It's really bugging me because it keeps asking me to restart,then once I do it tells me there are new updates once again and when I try to install them,same thing.You can see the restart icon here in my taskbar next to the envelope.

Anyone know how to fix this?

---

### Post by ibjsb4 on 2013-09-17
Welcome to the forum :)

Your getting the "no space left on device" message.

[http://ubuntuforums.org/showthread.php?t=2174867&p=12790906&viewfull=1#post12790906](http://ubuntuforums.org/showthread.php?t=2174867&p=12790906&viewfull=1#post12790906)

---

### Post by slickymaster on 2013-09-17
Most probably your boot is full of old kernel images, leaving no room for the new one apt-get is trying to install. Run this command to see all the kernels you have installed on your system:```
dpkg --get-selections | grep linux-image
```I my case the output of the command is the following:```
linux-image-3.11.0-031100rc5-generic  install
linux-image-3.11.0-031100rc6-generic  install

```Understand however that this will also show your current running kernel and basic system image, not just old versions.

To remove the older kernels simply use the following command ```
sudo apt-get purge linux-image-3.11.0-031100rc5-generic
``` replacing the linux-image file with your own. I would recommend leaving at least 1 or 2 older known good kernels just in case something goes wrong later down the road.
You can also remove multiple kernels at once:```
sudo apt-get purge linux-image-3.11.0-031100rc5-generic linux-image-3.11.0-031100rc6-generic
```

---

