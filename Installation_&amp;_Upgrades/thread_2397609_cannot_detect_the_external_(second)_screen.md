---
title: "cannot detect the external (second) screen"
date: 2018-07-31
forum: Installation &amp; Upgrades
---

### Post by derelero on 2018-07-31
Could someone help me to detect second screen of display? I currently install ubuntu 17.10, but the interface is configure by KDE community. I also have a NVIDIA CARD GTX 1070 in my laptop, becuase something is centered my problems  with this card.

[HTML] xrandr[/HTML]

this is output
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 381mm x 214mm
   1920x1080    120.00*+  59.93  
   1680x1050     84.94    74.89    69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     85.00    74.76    70.00    59.98  
   1280x1024     85.02    75.02    60.02  
   1440x900      59.89  
   1280x960      85.00    60.00  
   1360x768      59.80    59.96  
   1152x864     100.00    85.06    85.00    75.00    75.00    70.00    60.00  
   1024x768      85.00    75.05    60.04    85.00    75.03    70.07    60.00  
   1024x768i     86.96  
   960x720       85.00    75.00    60.00  
   928x696       75.00    60.05  
   896x672       75.05    60.01  
   960x600       60.00  
   832x624       74.55  
   960x540       59.99  
   800x600       85.00    75.00    70.00    65.00    60.00    85.14    72.19    75.00    60.32    56.25  
   840x525       85.02    74.96    69.88    60.01    59.88  
   800x512       60.17  
   700x525       85.08    74.76    70.06    59.98  
   640x512       85.02    75.02    60.02  
   720x450       59.89  
   640x480       85.09    60.00    85.01    72.81    75.00    59.94  
   720x400       85.04  
   680x384       59.80    59.96  
   640x400       85.08  
   576x432      100.11    85.15    85.09    75.00    75.00    70.00    60.06  
   640x350       85.08  
   512x384       85.00    75.03    70.07    60.00  
   512x384i      87.06  
   416x312       74.66  
   400x300       85.27    72.19    75.12    60.32    56.34  
   320x240       85.18    72.81    75.00    60.05  
   360x200       85.04  
   320x200       85.27  
   320x175       85.27

---

### Post by mIk3_08 on 2018-08-01
I think you should do the upgrade.
[Click Here]("https://tutorials.ubuntu.com/tutorial/tutorial-upgrading-ubuntu-desktop#4") for instruction.
or you can do the command using the terminal;
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by QIII on 2018-08-01
The link does not work and ***the suggestion is not a good one***.

Updating that way from an unsupported, possibly not fully updated, EOL release is likely a recipe for disaster.

Best to back up all important files and reinstall -- which can be done while preserving your /home directory.

If you have any questions about how to do that, feel free to ask.

---

### Post by derelero on 2018-08-01
> **mIk3_08 said:**
> I think you should do the upgrade.
[Click Here]("https://tutorials.ubuntu.com/tutorial/tutorial-upgrading-ubuntu-desktop#4") for instruction.
or you can do the command using the terminal;
```
sudo apt-get update && sudo apt-get dist-upgrade
```
```

Get:1 [http://storage.googleapis.com/bazel-apt](http://storage.googleapis.com/bazel-apt) stable InRelease [2,450 B]
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                     
Ign:3 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64)  InRelease                                                                                       
Hit:4 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1704/x86_64)  Release                                                                                         
Hit:5 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                                                                                                                           
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                                                       
Hit:7 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview InRelease                                                                                                                          
Hit:8 [https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017) xenial InRelease                                                                                             
Err:1 [http://storage.googleapis.com/bazel-apt](http://storage.googleapis.com/bazel-apt) stable InRelease                                                                                                                   
  The following signatures were invalid: EXPKEYSIG 3D5919B448457EE0 Bazel Developer (Bazel APT repository key) <bazel-dev@googlegroups.com>
Hit:9 [https://packages.microsoft.com/ubuntu/16.04/prod](https://packages.microsoft.com/ubuntu/16.04/prod) xenial InRelease                                                                                                          
Hit:10 [http://repo.ros2.org/ubuntu/main](http://repo.ros2.org/ubuntu/main) xenial InRelease                                                                                                                         
Hit:11 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                                                                                                                               
Get:12 [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable InRelease [2,801 B]                                                                                                    
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety InRelease                                                                                                                     
Hit:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful InRelease                                                                                                                         
Hit:15 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful InRelease                                                                                                                      
Ign:16 [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu) artful InRelease                                                                                        
Hit:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                                                                                                                      
Hit:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates InRelease                                                                                                                 
Hit:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-backports InRelease                                                                                                            
Err:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) yakkety Release                                                                                                                
  404  Not Found [IP: 91.189.91.23 80]
Ign:23 [http://ppa.launchpad.net/george-edison55/cmake-3.x/ubuntu](http://ppa.launchpad.net/george-edison55/cmake-3.x/ubuntu) artful InRelease                                                                                         
Hit:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-security InRelease                                                                                   
Get:26 [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable/main amd64 Packages [56.9 kB]                                                          
Hit:27 [http://mirrors.ustc.edu.cn/ros/ubuntu](http://mirrors.ustc.edu.cn/ros/ubuntu) artful InRelease                                                                                                                    
Ign:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) artful InRelease                                                                                                                               
Hit:29 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) artful InRelease                    
Hit:24 [https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu](https://packages.gitlab.com/gitlab/gitlab-ee/ubuntu) artful InRelease                                                
Err:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) artful Release                                                      
  404  Not Found [IP: 91.189.88.161 80]
Hit:31 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) artful InRelease  
Hit:32 [http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu](http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu) artful InRelease
Hit:33 [http://ppa.launchpad.net/viktor-krivak/pycharm/ubuntu](http://ppa.launchpad.net/viktor-krivak/pycharm/ubuntu) artful InRelease  
Hit:34 [http://ppa.launchpad.net/wireshark-dev/stable/ubuntu](http://ppa.launchpad.net/wireshark-dev/stable/ubuntu) artful InRelease   
Err:35 [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu) artful Release                                                                                          
  404  Not Found
Err:36 [http://ppa.launchpad.net/george-edison55/cmake-3.x/ubuntu](http://ppa.launchpad.net/george-edison55/cmake-3.x/ubuntu) artful Release                                                                                                  
  404  Not Found
Reading package lists... Done                                                                                                                                                    
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://storage.googleapis.com/bazel-apt](http://storage.googleapis.com/bazel-apt) stable InRelease: The following signatures were invalid: EXPKEYSIG 3D5919B448457EE0 Bazel Developer (Bazel APT repository key) <bazel-dev@googlegroups.com>
E: The repository 'http://us.archive.ubuntu.com/ubuntu yakkety Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/george-edison55/cmake-3.x/ubuntu artful Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

Cannot solved it.

---

### Post by QIII on 2018-08-01
Did you read my post #3?

The advice you followed was poor.

Back up your important files and do a fresh installation of 18.04.

---

