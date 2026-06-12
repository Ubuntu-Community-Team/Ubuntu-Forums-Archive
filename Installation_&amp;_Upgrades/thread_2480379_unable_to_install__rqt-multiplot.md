---
title: "unable to install  rqt-multiplot"
date: 2022-10-27
forum: Installation &amp; Upgrades
---

### Post by moaiadhany on 2022-10-27
Hello,

I am trying to install rqt_multipolt using this line 


[LIST]
[*]sudo apt install ros-noetic-rqt-multiplot
[/LIST]
but it keep shows this errors :
Err:1 [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) focal/main amd64 ros-noetic-variant-msgs amd64 0.1.6-1focal.20210423.224434
  404  Not Found [IP: 140.211.166.134 80]
Err:2 [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) focal/main amd64 ros-noetic-variant-topic-tools amd64 0.1.6-1focal.20220106.234434
  404  Not Found [IP: 140.211.166.134 80]
Err:3 [http://packages.ros.org/ros/ubuntu](http://packages.ros.org/ros/ubuntu) focal/main amd64 ros-noetic-rqt-multiplot amd64 0.0.12-1focal.20220328.224855
  404  Not Found [IP: 140.211.166.134 80]
E: Failed to fetch [http://packages.ros.org/ros/ubuntu/pool/main/r/ros-noetic-variant-msgs/ros-noetic-variant-msgs_0.1.6-1focal.20210423.224434_amd64.deb](http://packages.ros.org/ros/ubuntu/pool/main/r/ros-noetic-variant-msgs/ros-noetic-variant-msgs_0.1.6-1focal.20210423.224434_amd64.deb)  404  Not Found [IP: 140.211.166.134 80]
E: Failed to fetch [http://packages.ros.org/ros/ubuntu/pool/main/r/ros-noetic-variant-topic-tools/ros-noetic-variant-topic-tools_0.1.6-1focal.20220106.234434_amd64.deb](http://packages.ros.org/ros/ubuntu/pool/main/r/ros-noetic-variant-topic-tools/ros-noetic-variant-topic-tools_0.1.6-1focal.20220106.234434_amd64.deb)  404  Not Found [IP: 140.211.166.134 80]
E: Failed to fetch [http://packages.ros.org/ros/ubuntu/pool/main/r/ros-noetic-rqt-multiplot/ros-noetic-rqt-multiplot_0.0.12-1focal.20220328.224855_amd64.deb](http://packages.ros.org/ros/ubuntu/pool/main/r/ros-noetic-rqt-multiplot/ros-noetic-rqt-multiplot_0.0.12-1focal.20220328.224855_amd64.deb)  404  Not Found [IP: 140.211.166.134 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I tried sudo apt-get udpdate, but did not work either !

is there any solve of this problem ?

I use ubunto 20.04

---

### Post by MAFoElffen on 2022-10-28
I checked the package list at [http://packages.ros.org/ros/ubuntu/dists/focal/main/binary-amd64/Packages](http://packages.ros.org/ros/ubuntu/dists/focal/main/binary-amd64/Packages)...
package 'ros-noetic-rqt-multiplot' exists there for 'focal'.

maybe if you did
```

sudo apt-cache show ros-noetic-rqt-multi*

```
...it would show you that. Maybe at a different source?

This is what I found there:
```

Package: ros-noetic-rqt-multiplot
Version: 0.0.12-1focal.20220926.212043
Architecture: amd64
Maintainer: Samuel Bachmann <sbachmann@anybotics.com>
Installed-Size: 1932
Depends: libboost-program-options1.71.0, libc6 (>= 2.14), libconsole-bridge0.4, libgcc-s1 (>= 3.0), libqt5core5a (>= 5.12.2), libqt5gui5 (>= 5.2.0) | libqt5gui5-gles (>= 5.2.0), libqt5widgets5 (>= 5.11.0~rc1), libqwt-qt5-6 (>= 6.1.2), libstdc++6 (>= 9), libqwt-qt5-dev, qtbase5-dev, ros-noetic-rosbag, ros-noetic-roscpp, ros-noetic-rqt-gui, ros-noetic-rqt-gui-cpp, ros-noetic-variant-topic-tools
Priority: optional
Section: misc
Filename: pool/main/r/ros-noetic-rqt-multiplot/ros-noetic-rqt-multiplot_0.0.12-1focal.20220926.212043_amd64.deb
Size: 421732
SHA256: d399ad20863f9a60d6e38cc30f147e2b0f283d7f1f65db78fc2f4c2a23be9958
SHA1: c1f98f767c67c27d4ab66355fec393c1a133c2cc
MD5sum: e133f5e1aa706ab2c92e12fd90409f79
Description: rqt_multiplot provides a GUI plugin for visualizing numeric values in multiple 2D plots using the Qwt plotting backend.

```

---

### Post by moaiadhany on 2022-10-28
> **MAFoElffen said:**
> I checked the package list at [http://packages.ros.org/ros/ubuntu/dists/focal/main/binary-amd64/Packages](http://packages.ros.org/ros/ubuntu/dists/focal/main/binary-amd64/Packages)...
package 'ros-noetic-rqt-multiplot' exists there for 'focal'.

maybe if you did
```

sudo apt-cache show ros-noetic-rqt-multi*

```
...it would show you that. Maybe at a different source?

This is what I found there:
```

Package: ros-noetic-rqt-multiplot
Version: 0.0.12-1focal.20220926.212043
Architecture: amd64
Maintainer: Samuel Bachmann <sbachmann@anybotics.com>
Installed-Size: 1932
Depends: libboost-program-options1.71.0, libc6 (>= 2.14), libconsole-bridge0.4, libgcc-s1 (>= 3.0), libqt5core5a (>= 5.12.2), libqt5gui5 (>= 5.2.0) | libqt5gui5-gles (>= 5.2.0), libqt5widgets5 (>= 5.11.0~rc1), libqwt-qt5-6 (>= 6.1.2), libstdc++6 (>= 9), libqwt-qt5-dev, qtbase5-dev, ros-noetic-rosbag, ros-noetic-roscpp, ros-noetic-rqt-gui, ros-noetic-rqt-gui-cpp, ros-noetic-variant-topic-tools
Priority: optional
Section: misc
Filename: pool/main/r/ros-noetic-rqt-multiplot/ros-noetic-rqt-multiplot_0.0.12-1focal.20220926.212043_amd64.deb
Size: 421732
SHA256: d399ad20863f9a60d6e38cc30f147e2b0f283d7f1f65db78fc2f4c2a23be9958
SHA1: c1f98f767c67c27d4ab66355fec393c1a133c2cc
MD5sum: e133f5e1aa706ab2c92e12fd90409f79
Description: rqt_multiplot provides a GUI plugin for visualizing numeric values in multiple 2D plots using the Qwt plotting backend.

```


i wrote the code that u gave me and this what i got

---

### Post by MAFoElffen on 2022-10-28
So now
```

ping -c 4 140.211.166.134
ping -c 4 ros.org
sudo apt update
sudo apt install ros-noetic-rqt-multiplot

```

---

### Post by moaiadhany on 2022-10-28
> **MAFoElffen said:**
> So now
```

ping -c 4 140.211.166.134
ping -c 4 ros.org
sudo apt update
sudo apt install ros-noetic-rqt-multiplot

```


thanks for your help and your effort. unfortunately , still the same issue!

and this what i got

---

