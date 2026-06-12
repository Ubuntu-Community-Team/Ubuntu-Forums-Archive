---
title: "Upgrade too vast in size to be downloaded"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by derif on 2008-08-14
I just installed ubuntu 8.0.4 and the upgrade manager displays a list of over 200+ upgrades more than 250 MB. Cant these upgrades be downloaded and saved somewhere else (linke in a pen-drive)? And later when when I plug my pen-drive, I am able to install all these updates without any difficulty.

---

### Post by meindian523 on 2008-08-14
Problems with hard disk space?

---

### Post by issih on 2008-08-14
if you actually installed 8.04 rather than the point release 8.04.1, you could download the latest iso from ubuntu, which should be 8.04.1, then burn that disk and enable it as an apt repository. doing that will get you any upgrades up to .1, but will actually entail a larger download than just letting the update manager do its thing.

Hope that helps

---

### Post by fig_wright on 2008-09-07
I've just spent a day trying to free up enough space to upgrade from gutsy to hardy on a laptop. At first it wanted 3MB more space (I have about 800MB), but everything I removed made the space requirement even bigger. By the time I have 1,300 MB free it wanted an extra 100 MB!

In the end I just uninstalled Openoffice and that freed up enough room to start. The upgrade went fine, and the laptop now has 900 MB free! Clearly there is a requirement for about 500 MB of extra temp space for the packages during install.

Anyway, I then wondered if there was an easier way to avoid this requirement. So, are you saying that less space is used if I had burned hardy to a CD and then somehow upgraded from that CD?

Second, is there a way to use some other partition for the temp upgrade space (of which I have plenty elsewhere)?

---

### Post by Bucky Ball on 2008-09-07
How big is your swap?

---

