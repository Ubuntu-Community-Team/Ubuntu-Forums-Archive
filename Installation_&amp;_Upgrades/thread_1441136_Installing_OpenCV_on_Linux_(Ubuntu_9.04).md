---
title: "Installing OpenCV on Linux (Ubuntu 9.04)"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by sarosh on 2010-03-28
i am doing Installing OpenCV on Linux (Ubuntu 9.04) from guidelines as given in [http://abhitak.wordpress.com/2009/08...x-ubuntu-9-04/]("http://abhitak.wordpress.com/2009/08/29/installing-opencv-on-linux-ubuntu-9-04/")    but in apt-get install licbcv or libcv-dev i get this error...

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcv-dev: Depends: libhighgui-dev (= 1.0.0-6.1ubuntu1) but it is not going to be installed
E: Broken packages


 this mens these r unresolvable issues? wat to do? plzzzzzzzzzzzzzzzzzzzzzz guide

---

### Post by rCXer on 2010-03-28
What happens when you try installing libhighgui-dev and then libcv-dev?
```

sudo apt-get install libhighgui-dev
sudo apt-get install libcv-dev

```

The people over at the [OpenCV mailing list](http://tech.groups.yahoo.com/group/OpenCV/messages) may be able to help you.

---

