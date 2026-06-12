---
title: "How to configure igpu for xserver and nvidia gpu for cuda?"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by kay-b on 2016-06-02
Ubuntu 16.04
uname -a:
Linux HOST 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


 Desktop grade:
CPU: Intel
GPU: Nvidia with 361.42

 
"I am a Linux Newbie"

 
What I want:
 - the intel GPU shall run the xserver and my monitor, which is connected to the onboard DP
 - the nvidia GPU shall only be used for CUDA specific computation etc.
 - full control over the nvidia gpu (real time, stats, temps fan speeds...)

 
My Problem:
 - neither nvidia-smi nor nvidia-settings work and I cannot control my nvidia GPU
(errors cited further down)

 
My Story:

 After the short summary of my problem I want to dive into the topic:

 Since the release of Ubuntu 16.04 I am tinkering and failing to achieve the following:


[LIST]
[*]I want my intel GPU (i7 6700K) to drive my Xserver and everything associtated to it. 
[*]I want my dedicated nvidia GPU to only be used for Cuda based computation and the like. 
[*] I will add more than one nvidia GPU to the system, after I got my problems solved. 
[/LIST]
 
A short summary of my initial state:
I installed the proprietary Drivers for nvidia and intel  (intel-microcode and nvidia-361.42) via apt-get and disabled secure boot  via mokutul --disable-validation.
Then I set nvidia-prime to use the intel card.
Then I edited my xorg.conf to contain only one screen with intel gpu and intel driver. (ask for details if needed)
Testing the GPU for rendering with Blender, everything seemed fine,  except that I couldn't get any stats of my gpu and nvidia-settings  appeared empty.

 
Errors:
sudo nvidia-smi:
NVIDIA-SMI couldn't find libnvidia-ml.so library in your system. Please  make sure that the NVIDIA Display Driver is properly installed and  present in your system.
Please also try adding directory that contains libnvidia-ml.so to your system PATH.

 
What I have so far learned through all my tries and researches since the release (short version, ask for detail any time):

 My two Problems are releated but not the same:
 
Nvidia-settings Empty:
 - this is because these settings only show up, when there is an Xserver connected to the nvidia GPU
 - the solution for this would be to add a new screen in xorg.conf that forces and unused xserver to run on the nvidia GPU
 - but this is currently not possible (see other problem) and not desired, as I purely want the nvidia GPU to focus on Cuda

 
Nvidia-smi not working:
 - bbswitch is not a problem as my GPU (550ti) does not support it (errors in dmesg)
 - nvidia prime changes the entry for x86_64-linux-gnu_gl_conf to either /usr/lib/nvidia-361/ld.so.conf (nvidia GPU selected) or  /usr/lib/nvidia-361-prime/ld.so.conf (intel GPU selected)
 - the configuration for the intel selection is missing essential paths  to the essential nvidia modules which are all present in the conf for  nvidia selection
 - when switching to nvidia via prime-select, I don't have a Xserver as  the Display is connected to the integrated GPU, but logging in at a  virtual console nvidia-smi works

 
My Assumption:
 - Nvidia prime is bad and does not want the way I want.
 - I have to somehow overcome prime and configure the system (even manually writing new configs?)

 
My Tries:
I tried uninstalling nvidia-prime but I only recognised afterwards, that this cannot work. When the conf file for x86_64-linux-gnu_gl_conf is deleted, the outcome is a pure mess...
I even tried adding the missing paths to the x86_64-linux-gnu_gl_conf files manually, but I didn't really know what I was doing and had no success.

 
My Questions:

 1) How can I solve the nvidia-smi problem? Am I on the right track? Does anyone have instructions how I could proceed?

 2) Is it possible to enable fan control and further controls for the  nvidia gpu (coolbits in xorg.conf) without an Xserver on the gpu  (without a screen for the gpu in xorg.conf)?

 
Huge thanks in advance for any replies.
If I missed anything important, please tell me and do not hesitate to request log files etc...

 THANKS

I also created askubuntu and launchpad posts:
[URL="http://askubuntu.com/questions/779530/how-to-configure-igpu-for-xserver-and-nvidia-gpu-for-cuda"]
http://askubuntu.com/questions/779530/how-to-configure-igpu-for-xserver-and-nvidia-gpu-for-cuda[/URL]

[https://answers.launchpad.net/ubuntu/+question/294621](https://answers.launchpad.net/ubuntu/+question/294621)

---

### Post by kay-b on 2016-06-27
I (creator of this post) found the solution I need on my own!


  I will now explain the solution for anybody else who is in a similar situation and needs this help!
  

SOLUTION:
INSTALL THE NVIDIA DRIVER VIA THE RUNFILE PROVIDED AT [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) WITH THE FLAG "--no-opengl-files" !!
  This prevents not only the nvidia opengl files from overwriting the  existing mesa files but also installs the driver without nvidia prime!!
  So all of my problems are solved, simply by installing the driver  manually, instead of installing it from the repositories. The package  from the repositories is "Optimus-Friendly" and therefore has all the  useless troublemakers bundled with it.
  
SECONDLY
  
the xorg.conf has to be extended with another screen for the  dedicated GPU(s) so that it/they has/have entries in nvidia-settings.
  
mine looks like this
  

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen 0       "intel" 0 0
    Screen 1       "nvidia550ti" 3000 0
EndSection

Section "Device"
    Identifier     "intel"
    Driver         "intel"
    BusID          "PCI:0@0:2:0"
EndSection

Section "Device"
    Identifier     "nvidia550ti"
    Driver         "nvidia"
    BoardName      "GeForce GTX 550ti"
    BusID          "PCI:2@0:0:0"
EndSection

Section "Screen"
    Identifier     "intel"
    Device         "intel"
EndSection

Section "Screen"
    Identifier     "nvidia550ti"
    Device         "nvidia550ti"
    Option         "AllowEmptyInitialConfiguration" "on"
    Option         "Coolbits" "4"
    Option         "ConstrainCursor" "on"
EndSection
```

---

### Post by QDR06VV9 on 2016-06-27
Thanks for sharing your solution...
Regards

---

