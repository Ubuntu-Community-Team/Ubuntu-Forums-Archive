---
title: "'Error: BrokenCount &gt; 0' : your installed packages have unmet dependencies"
date: 2018-07-11
forum: Installation &amp; Upgrades
---

### Post by zeynep2 on 2018-07-11
Hi everyone,

I have installed CUDA 9.2 and then remove this version again install CUDA 9.0. 
But CUDA 9.0 does not work then, i have tried to install CUDA multiple times.


I have got error as following 
```
An error occurred, please run package manager from the right-click menu or apt-get in the terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies
```

tried these commands 
sudo apt-get install -f
But i could not solve this problem.

```
$ sudo apt-get update
Get:1 file:/var/cuda-repo-9-0-local  InRelease
Ign:1 file:/var/cuda-repo-9-0-local  InRelease
Get:2 file:/var/cuda-repo-9-2-local  InRelease
Ign:2 file:/var/cuda-repo-9-2-local  InRelease
Get:3 file:/var/nvinfer-runtime-trt-repo-3.0.4-ga-cuda9.0  InRelease
Ign:3 file:/var/nvinfer-runtime-trt-repo-3.0.4-ga-cuda9.0  InRelease
Get:4 file:/var/cuda-repo-9-0-local  Release [574 B]
Get:5 file:/var/cuda-repo-9-2-local  Release [574 B]
Get:6 file:/var/nvinfer-runtime-trt-repo-3.0.4-ga-cuda9.0  Release [574 B]     
Get:4 file:/var/cuda-repo-9-0-local  Release [574 B]                           
Get:5 file:/var/cuda-repo-9-2-local  Release [574 B]                           
Get:6 file:/var/nvinfer-runtime-trt-repo-3.0.4-ga-cuda9.0  Release [574 B]     
Hit:8 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial InRelease    
Hit:10 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                        
Hit:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease             
Hit:12 [http://ppa.launchpad.net/jonathonf/ffmpeg-3/ubuntu](http://ppa.launchpad.net/jonathonf/ffmpeg-3/ubuntu) xenial InRelease     
Hit:13 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview InRelease                       
Get:14 [http://storage.googleapis.com/bazel-apt](http://storage.googleapis.com/bazel-apt) stable InRelease [2.450 B]      
Hit:16 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) xenial InRelease                    
Hit:17 [http://ppa.launchpad.net/tmate.io/archive/ubuntu](http://ppa.launchpad.net/tmate.io/archive/ubuntu) xenial InRelease       
Hit:18 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) xenial-updates InRelease            
Hit:19 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Hit:20 [http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu](http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu) xenial InRelease
Hit:21 [http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu) xenial InRelease
Err:14 [http://storage.googleapis.com/bazel-apt](http://storage.googleapis.com/bazel-apt) stable InRelease               
  The following signatures were invalid: KEYEXPIRED 1527185977  KEYEXPIRED 1527185977  KEYEXPIRED 1527185977
Hit:22 [https://download.sublimetext.com](https://download.sublimetext.com) apt/dev/ InRelease
Reading package lists... Done 
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://storage.googleapis.com/bazel-apt](http://storage.googleapis.com/bazel-apt) stable InRelease: The following signatures were invalid: KEYEXPIRED 1527185977  KEYEXPIRED 1527185977  KEYEXPIRED 1527185977
W: Failed to fetch [http://storage.googleapis.com/bazel-apt/dists/stable/InRelease](http://storage.googleapis.com/bazel-apt/dists/stable/InRelease)  The following signatures were invalid: KEYEXPIRED 1527185977  KEYEXPIRED 1527185977  KEYEXPIRED 1527185977
W: Some index files failed to download. They have been ignored, or old ones used instead.

```



```

~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  cuda-cublas-9-0 cuda-cufft-9-0 cuda-curand-9-0 cuda-cusolver-9-0
  cuda-cusparse-9-0 cuda-npp-9-0 cuda-nvgraph-9-0 cuda-nvml-dev-9-0
  cuda-nvrtc-9-0
The following NEW packages will be installed:
  cuda-cublas-9-0 cuda-cufft-9-0 cuda-curand-9-0 cuda-cusolver-9-0
  cuda-cusparse-9-0 cuda-npp-9-0 cuda-nvgraph-9-0 cuda-nvml-dev-9-0
  cuda-nvrtc-9-0
0 upgraded, 9 newly installed, 0 to remove and 10 not upgraded.
18 not fully installed or removed.
Need to get 0 B/258 MB of archives.
After this operation, 571 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 file:/var/cuda-repo-9-0-local  cuda-nvrtc-9-0 9.0.176-1 [6.348 kB]
Get:2 file:/var/cuda-repo-9-0-local  cuda-cusolver-9-0 9.0.176-1 [26,2 MB]
Get:3 file:/var/cuda-repo-9-0-local  cuda-cublas-9-0 9.0.176-1 [25,0 MB]
Get:4 file:/var/cuda-repo-9-0-local  cuda-cufft-9-0 9.0.176-1 [84,1 MB]
Get:5 file:/var/cuda-repo-9-0-local  cuda-curand-9-0 9.0.176-1 [38,8 MB]
Get:6 file:/var/cuda-repo-9-0-local  cuda-cusparse-9-0 9.0.176-1 [25,2 MB]
Get:7 file:/var/cuda-repo-9-0-local  cuda-npp-9-0 9.0.176-1 [46,6 MB]
Get:8 file:/var/cuda-repo-9-0-local  cuda-nvgraph-9-0 9.0.176-1 [6.081 kB]
Get:9 file:/var/cuda-repo-9-0-local  cuda-nvml-dev-9-0 9.0.176-1 [47,6 kB]
(Reading database ... 306709 files and directories currently installed.)
Preparing to unpack .../cuda-nvrtc-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-nvrtc-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-nvrtc-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
Preparing to unpack .../cuda-cusolver-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-cusolver-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-cusolver-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
Preparing to unpack .../cuda-cublas-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-cublas-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-cublas-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
Preparing to unpack .../cuda-cufft-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-cufft-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-cufft-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../cuda-curand-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-curand-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-curand-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../cuda-cusparse-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-cusparse-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-cusparse-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../cuda-npp-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-npp-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-npp-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../cuda-nvgraph-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-nvgraph-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-nvgraph-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
No apport report written because MaxReports is reached already
                                                              Preparing to unpack .../cuda-nvml-dev-9-0_9.0.176-1_amd64.deb ...
Unpacking cuda-nvml-dev-9-0 (9.0.176-1) ...
dpkg: error processing archive /var/cuda-repo-9-0-local/./cuda-nvml-dev-9-0_9.0.176-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-9.0/lib64', which is also in package cuda-driver-dev-9-0 9.0.176-1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cuda-repo-9-0-local/./cuda-nvrtc-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-cusolver-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-cublas-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-cufft-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-curand-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-cusparse-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-npp-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-nvgraph-9-0_9.0.176-1_amd64.deb
 /var/cuda-repo-9-0-local/./cuda-nvml-dev-9-0_9.0.176-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Any suggestion ?
Thank you

---

