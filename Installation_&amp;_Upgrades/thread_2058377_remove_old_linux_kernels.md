---
title: "remove old linux kernels"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by wencyfutado on 2012-09-15
How does one remove the extra entries of the old linux kernels after upgrade of a new version. Remember Synaptic used to do that but it was the case when Startup manager used to do a good job. Please help if i'm missing something.

---

### Post by josephmills on 2012-09-15
This is how I do it might be easier ways. 

open terminal and see what kernel you are using. 

```
uname -a 
```

then see what is installed 

```
dpkg-query -l | awk '/linux-image-*/ {print $2}'
```

remove the ones  that you do not want

```
sudo apt-get --purge remove <Kernel>
```

then 
```
sudo update-grub
```


MAKE SURE YOU DO NOT DELETE THE KERNEL THAT YOU ARE USING

---

### Post by digitalzy on 2012-09-15
Please look at this: [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---

