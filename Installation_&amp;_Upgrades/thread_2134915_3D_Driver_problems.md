---
title: "3D Driver problems"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2013-04-12
Hi all,

I'm using kubuntu 12.04. First I had an nvidia card and working proprietary drivers with nice hardware accelerated 3D.
But my nvidia card broke and I got a temporary replacement card from ATI/AMD.

So I purged the nividia drivers, installed the ati drivers and all was good.

Now my nvidia card is repaired and I can't seem to find how to restore the nvidia driver to good working order.
I purged the ati drivers first using apt.

Then I tried to use jockey-kde. It presented me with a few choices on drivers. It downloaded them but then it complained
that the driver was activated and not in use. And indeed it was not in use. 3D was slow.

So I followed the instructions from: [http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

Now everything seems to work better. The resolution is ok but 3D apps simply crash immediatelly with the
following error:

> 
jorrit@jorrit-H67A-USB3-B3:~/projects/crystal$ glxinfo
name of display: :0
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  137 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x3200003
  Serial number of failed request:  34
  Current serial number in output stream:  34
jorrit@jorrit-H67A-USB3-B3:~/projects/crystal$ 


This happens with every 3D app. i.e. glxgears as well.

Any idea? What can I do to fix this?

Greetings and thanks,

---

