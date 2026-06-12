---
title: "Am I messing things up with new nvidia drivers?"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by PureRumble on 2010-02-15
Hi all.

My stationary has a nvidia graphic card.

Sometime ago I read that the new nvidia 190 drivers had arrived, but this was not yet included in the multiverse repository.

So I followed the instructions at the following address to get the drivers:

[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

Basically I added a new repository to my sources list, and installed the drivers.

All went well.

A while later, something odd happened; when trying to perform upgrades of packages, the update manager said some packages were being "blocked".

Another odd thing was that a new update for the nvidia drivers arrived. Naturally I installed it through the gui. After the installation (that did not complete properly but I couldn't tell) the same update was listed for the same drivers. I thought something has gone wrong and so I installed it again.

And again, and again, and again...

It just kept popping up, the exact same update.

I stopped installing it, and later when I rebooted my computer I realized my graphic card drivers had been broken. The ordinary nice ubuntu gui wouldn't start up, and instead I managed to reach the terminal.

From terminal I did "sudo apt-get upgrade", and I noted that it still insisted that the same update should be made to the nvidia drivers. Having accepted it, apt-get was kind enough to tell me that something was going wrong:

dpkg: error processing /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa10_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau_nvidia.so', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9

To solve this I did

sudo dpkg -i --force-overwrite --force-all /var/cache/apt/archives/nvidia-glx-190_190.53-0ubuntu1~karmic~nvidiavdpauppa10_amd64.deb

I placed the force-all because otherwise it would complain about some other package (some "nvidia source" package) not being configured.

This solved it. Now, remember the updates that were being blocked? To solve that I did

sudo aptitude full-upgrade

aptitude suggest that some nvidia drivers 185 package should be removed in order to install the blocked updates. I accepted and it went smoothly.

After reboot, ubuntu starts as normally.

So, I now arrive at my newbie questions :-)

What is going on here, and am I slowly but for sure breaking something here, or is my system safe and stable now?

Thanks for reading and helping out!

---

