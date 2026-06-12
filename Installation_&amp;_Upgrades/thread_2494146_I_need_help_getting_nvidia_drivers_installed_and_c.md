---
title: "I need help getting nvidia drivers installed and cuda and cudnn on Ubuntu 22.04"
date: 2024-01-06
forum: Installation &amp; Upgrades
---

### Post by tsisaris on 2024-01-06
[FONT=NVIDIA][COLOR=#333333]Hello and thank you in advance,

Below is the closest I could get to a formulaic presentation of my attempt to build up my system to begin engaging in machine learning after a fresh install of Ubuntu 22.04 LTS.

If you can help me please let me know. I am still new to this so if you can continue my sequential install build with my notation it would be awesome.

Also fact check this to make sure that I am using the best versions for everything.


[/COLOR][/FONT][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I have been at this for days. I have a Lenovo Legion y520. It has 32GB of RAM, a 1TB ssd, and an NVIDIA GeForce GTX 1050 ti with 4GB VRAM. I am trying to configure my computer for machine learning according to the following program.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
```
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I create a fresh install of Ubuntu 22.04.[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I select Ubuntu Pro for security and allow the software updater to update the software.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install Google Chrome –**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo dpkg -i google-chrome-stable_current_amd64.deb[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt --fix-broken install[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install DEAD SNAKES repository -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt install software-properties-common[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo add-apt-repository ppa:deadsnakes/ppa[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install PYTHON 3.12.1 -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt install python3.12[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install Git Repository -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo add-apt-repository ppa:git-core/ppa[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install Git CLI version 2.43.0 -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt install git[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo git –version[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install Curl 7.81.0 -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt install curl[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo curl --version[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install Homebrew -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed](echo; echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"') >> /home/tsisaris/.bashrc[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt-get install build-essential[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install DBUS-X11 -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt-get install dbus-x11[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt update && sudo apt upgrade[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]At this point everything is working just fine[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I then try to install the latest version of NVIDIA drivers for my particular GPU which is now a legacy card.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I have attempted to use the ubuntu drivers tool but it installs the wrong driver.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I go on NVIDIAS website and select the correct driver and download it.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]This happens to be NVIDIA-Linux-x86_64-535.146.02.run[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I want to update my driver to the latest possible version and install the latest versions of CUDA, CUDNN, and Pytorch that will work with my machine so that I can begin to study and practise machine learning.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]In my case it would seem that CUDA 11.8 and CUDNN 8.9.7 are the latest versions that will Work with Pytorch 2.1.1 and on my video card.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]This is where the problem comes in.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]After following almost every permutation and order of installation process and they all fail to update the driver because nvidia drm is in use?[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I finally try this procedure...[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Switch to tty3 by pressing Ctl+Alt+F3 -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Unload nvidia-drm before proceeding -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Isolate multi-user.target -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo systemctl isolate multi-user.target[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Note that nvidia-drm is currently in use -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]lsmod | grep nvidia.drm[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Unload nvidia-drm -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo modprobe -r nvidia-drm[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Note that nvidia-drm is not in use anymore -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]lsmod | grep nvidia.drm[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Install Newest Nvidia GPU Drivers 535.146.02 -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]cd ~/Downloads[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo chmod +x NVIDIA-Linux-x86_64-535.146.02.run[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo ./NVIDIA-Linux-x86_64-535.146.02.run[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I answer all prompts during installation. It still seems like there is come kind of conflict.[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I have to input the keyring key[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**When installation has finished, confirm that the new driver is installed**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]nvidia-smi[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I get that the Driver Version is 535.146.02 and the CUDA version is 12.2? I haven't even installed CUDA yet...[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Start the GUI again -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo systemctl start graphical.target[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I now want to install CUDA[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Switch to tty3 by pressing Ctl+Alt+F3 -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Unload nvidia-drm before proceeding -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Isolate multi-user.target -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo systemctl isolate multi-user.target[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Note that nvidia-drm is currently in use -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]lsmod | grep nvidia.drm[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Unload nvidia-drm -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo modprobe -r nvidia-drm[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Note that nvidia-drm is not in use anymore -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]lsmod | grep nvidia.drm[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Go to your download folder and run the cuda installation -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo dpkg -i cuda-repo-ubuntu2204-11-8-local_11.8.0-520.61.05-1_amd64.deb[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**Answer any prompts during installation -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**When installation has finished, confirm that the CUDA Version has been updated -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]nvidia-smi[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I start to understand this less and less[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]when I run the nvidia-smi command I get that the Driver Version is 535.146.02 and the CUDA version is 12.2?[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]**I have to install the NVIDIA CUDA toolkit so that I can run nvcc --version -**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]sudo apt install nvidia-cuda-toolkit[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]when I run the nvcc --version command I get this garbage...[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]nvcc: NVIDIA (R) Cuda compiler driver[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]Copyright (c) 2005-2021 NVIDIA Corporation[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]Built on Thu_Nov_18_09:45:30_PST_2021[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]Cuda compilation tools, release 11.5, V11.5.119[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]Build cuda_11.5.r11.5/compiler.30672275_0[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]Where does CUDA 11.5 come from? I installed CUDA 11.8 and in nvidia-smi it says CUDA version 12.2[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]How can I go through all of this process without a hangup?[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]I am sure that there is a bunch of broken garbage in my Ubuntu system now. I want a complete step by step method that corrects my code if necessary to finish installing CUDA 11.8 and CUDNN 8.9.7 without a hiccup and without creating a bunch of broken garbage...[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
```
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]What am I missing?[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]Thank you in advance,[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Condensed]Shawn[/FONT][/COLOR][/COLOR]

---

### Post by ubfan1 on 2024-01-06
The nvidia-smi is just reporting that it supports up to CUDA 12.2, not that it is installed. Using the Nvidia driver from any other source than the standard repositories will likely fail upon a kernel or driver upgrade -- avoid that by just getting the Nvidia drivers installed first (535.129.03 probably), then use the .run script from Nvidia and reject the offer of Nvidia drivers.  Override the system locations for bin and lib files too -- all that can go under cuda/lib and cuda/bin.  You can keep a clean system, no mixing of random versions of libraries and drivers, and run whatever versions of whatever for your project. See
[https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063](https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063)
[https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010](https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010)

---

### Post by oldfred on 2024-01-07
Please use Code tags on terminal or longer text output.
Easy to add code tags with Forum's advanced editor and # icon.

Do not know anything about most of what you installed.
Generally newer users should not add ppas until dyou know system and if ppa is safe to use.

You have to purge a driver, before installing a new driver or else you get conflicts. 
And do not install driver from nVidia with .run file, only install from Ubuntu repository.
The nVidia search says this is correct driver: 535.146.02

If you installed the .run version, use its instructions to remove it.

Ubuntu should give you the same:

#What is installed
dkms status

# list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 


sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall


man mkinitramfs
sudo update-initramfs -u 
or
sudo update-initramfs -k all -c

---

### Post by #&amp;thj^% on 2024-01-07
I'm having a tough time wondering why deadsnakes was added?
I can't for the life of me figure out why  python3.12 is needed??
If not careful it will render your system unable to update and upgrade.

I'm on Noble and python3 is 
```
python3 --version
Python 3.11.7

```
Since you asked:
>  Also fact check this to make sure that I am using the best versions for everything.
That's not always a good choice. :)
EDIT: I would first learn that New can be the Desktop destroyer.
Stable is the intended way to learn first.

---

### Post by deadflowr on 2024-01-07
> **Where does CUDA 11.5 come from?** I installed CUDA 11.8 and in nvidia-smi it says CUDA version 12.2

nvidia-cuda-toolkit.
You've mixed and matched packages from inside and outside of the Ubuntu ecosystem.
The toolkit package depends on packages from within the Ubuntu ecosystem.
Those packages are for version 11.5

Unless you did more than what you posted, this part says you only added a repository source entry with the 
following command
> **Go to your download folder and run the cuda installation -**
sudo dpkg -i cuda-repo-ubuntu2204-11-8-local_11.8.0-520.61.05-1_amd64.deb

Not sure if you followed the rest that is required
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda-repo-ubuntu2204-11-8-local_11.8.0-520.61.05-1_amd64.deb
**sudo dpkg -i cuda-repo-ubuntu2204-11-8-local_11.8.0-520.61.05-1_amd64.deb**
sudo cp /var/cuda-repo-ubuntu2204-11-8-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda
```
Highlighted the only part you posted.

---

### Post by tsisaris on 2024-01-07
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif][COLOR=#222222]I'm trying to reply to all of these for further help? Some of this was in what I posted? I was told to use the latest NVIDIA drivers for my card. I used the Ubuntu recommended drivers with the Ubuntu installation tool and they were not the ones that NVIDIA recommends... So I downloaded the current most up to date drivers directly from NVIDIA's website as I said. This is really where the issue exists. I had to do a manual install of the most recent driver which seems to be [/COLOR]535.146.02 as of today as per NVIDIA&#8217;s website&#8230; I need people to be very explicit here. Are you saying that I should ignore NVIDIA&#8217;s website and just use whatever the Ubuntu driver installation tool happens to install or recommend?[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]Using the NVIDIA driver from any other source than the standard repositories[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- what standard repositories? NVIDIA or Ubuntu? - CODE PLEASE... -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]will likely fail upon a kernel or driver upgrade -- avoid that by just getting the Nvidia drivers installed first (535.129.03 probably) (&#8211; wrong number according to NVIDIA -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]then use the .run script from Nvidia and reject the offer of Nvidia drivers.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- How? CODE PLEASE&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]Override the system locations for bin and lib files too -- all that can go under cuda/lib and cuda/bin.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- How? CODE PLEASE&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]Please use Code tags on terminal or longer text output.
Easy to add code tags with Forum's advanced editor and # icon.[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- I have no idea how to di this&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]The nVidia search says this is correct driver: 535.146.02[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- Yes. I said this. This was the issue. I couldn&#8217;t just install that driver. It kept giving me errors&#8230; I spent hours using Bing Chat to try new things and when I would get an error I would cut and paste the error into Bing Chat for it to be analyzed. I ended up trying nearly all of this. Bing Chat would give me the code and direct me to forums and websites to verify it. Low and behold it was the same advice that was being given on the forums&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]Ubuntu should give you the same:

#What is installed
dkms status

# list drivers available, same list as system settings, software updates, additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended


sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall


man mkinitramfs
sudo update-initramfs -u
or
sudo update-initramfs -k all -c[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- Nearly all of this code I got from Bing Chat and the forums and tried it multiple times in multiple ways to no avail&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- If python 3.11.7 is truly the best most stable version of python out then thank you. This was the kind of advice that I am looking for&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- In a similar manner I need to know that the combined relationship between CUDA, cuDNN, and Pytorch that is optimal for my machine. I read that I could do CUDA 11.8, cuDNN 8.9.7, and Pytorch 2.1.1. I also read that CUDA 12.2, cuDNN 8.9.7, and an older Pytorch 1.10.0 would be much better with this machine&#8230; How do I verify this? -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- In fact, how do I answer this type of question in general? I want to install docker, nvidiacudatoolkit, nvidia container toolkit, conda, jupyter notebooks, and whatever other tools or toolkits that will be helpful. I want all of them to be compatible with each other but also the most efficient, fastest, most stable version of each that is 100% compatible with all of the other programs and toolkits&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- Given that I am functionally illiterate in most of the mumbo jumbo, I need step by step in baby steps that even a caveman using fist sized buttons could implement with minimal effort and error and maximal success&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif](- CODE PLEASE&#8230; -) (- CODE PLEASE&#8230; -) (- CODE PLEASE&#8230; -)[/FONT][/COLOR][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=DejaVu Serif Condensed, serif]Thank you for your help[/FONT][/COLOR][/COLOR]

---

### Post by #&amp;thj^% on 2024-01-07
To try to explain  "standard repositories" means all software is tuned so to speak for Ubuntu already configured by the installer.
ie:
```
Active apt repos in: /etc/apt/sources.list
    1: deb http://archive.ubuntu.com/ubuntu noble main restricted
    2: deb http://archive.ubuntu.com/ubuntu noble-updates main restricted
    3: deb http://archive.ubuntu.com/ubuntu noble universe
    4: deb http://archive.ubuntu.com/ubuntu noble-updates universe
    5: deb http://archive.ubuntu.com/ubuntu noble multiverse
    6: deb http://archive.ubuntu.com/ubuntu noble-updates multiverse
    7: deb http://archive.ubuntu.com/ubuntu noble-backports main restricted universe multiverse
    8: deb http://archive.ubuntu.com/ubuntu noble-security main restricted
    9: deb http://archive.ubuntu.com/ubuntu noble-security universe
   10: deb http://archive.ubuntu.com/ubuntu noble-security multiverse

```
Now this is outside of the standard repo sources:
```
 Active apt repos in: /etc/apt/sources.list.d/archive_uri-https_download_sublimetext_com_-noble.list
    1: deb https://download.sublimetext.com/ apt/stable/
  Active apt repos in: /etc/apt/sources.list.d/surfshark.list
    1: deb https://ocean.surfshark.com/debian stretch main
  Active apt repos in: /etc/apt/sources.list.d/cubic-wizard-ubuntu-release-noble.sources
    1: deb https://ppa.launchpadcontent.net/cubic-wizard/release/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-noble.sources
    1: deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/mozillateam-ubuntu-ppa-noble.sources
    1: deb https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/ubuntuhandbook1-ubuntu-conkymanager2-noble.sources
    1: deb https://ppa.launchpadcontent.net/ubuntuhandbook1/conkymanager2/ubuntu/ jammy main

```
All Standard Repo's will look like "archive.ubuntu.com/ubuntu"
And ppa are considered a gamble because the code dose not come from Ubuntu Devs.

IMPORTANT: Learn to use code tags for Terminal results, please see my signature for Code Tags
Also please show me this:
```
apt policy nvidia-driver-535
```

---

### Post by tsisaris on 2024-01-07
Why is it that I get this - 

sudo apt-cache policy nvidia-driver-535
[sudo] password for tsisaris: 
nvidia-driver-535:
  Installed: 535.129.03-0ubuntu0.22.04.1
  Candidate: 535.129.03-0ubuntu0.22.04.1
  Version table:
 *** 535.129.03-0ubuntu0.22.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/restricted amd64 Packages
        100 /var/lib/dpkg/status

and I get this 

nvidia-smi
Sun Jan  7 16:39:31 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.146.02             Driver Version: 535.146.02   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1050 Ti     Off | 00000000:01:00.0 Off |                  N/A |
| N/A   33C    P8              N/A / ERR! |      4MiB /  4096MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      1725      G   /usr/lib/xorg/Xorg                            4MiB |
+---------------------------------------------------------------------------------------+

I want to know how to start over with a fresh installation of Ubuntu 22.04 LTS and add these things in an exact order where I get no conflicts.

I still need to know which are the best versions of cuda, cudnn, and pytorch to use together with this machine.

---

### Post by #&amp;thj^% on 2024-01-08
> **tsisaris said:**
> 

I still need to know which are the best versions of cuda, cudnn, and pytorch to use together with this machine.

Again it's best to keep a uniform software base intact hence "Standard Repository"
You show two different drivers because apt only reads from again the above "Standard Repository"
And you have the nVidia driver from nvidia. Also the cause of your troubles is that two drivers are installed not a good practice.

I say this in all kindness, you first need to  learn to walk your system, before unleashing a full gallop.

---

### Post by tsisaris on 2024-01-08
I don't believe that trying to install the correct driver for my card is a full gallop... I'd say it's more like sleeping and breathing... It's probably the most basic thing that you are supposed to do recommended by the manufacturer of the card. It's supposed to be super simple. It's really hard to believe that Ubuntu just doesn't understand how to install the correct fiver for my card. I there must be something that I'm doing wrong but even when I follow peoples exact advice it doesn't seem to work. I'll keep trying. If anyone has the complete set of code that can purge my old drivers and install the new ones I would appreciate it... And yes I followed exactly the steps on NVIDIA's website... I don't mind a complete reinstall. It was my intention to do so once I had the proper process. I just don't want to keep reinstalling over and over. Thank you, Shawn

---

### Post by #&amp;thj^% on 2024-01-08
It's all been said here already.
When you reinstall, then come back here and post a single request for help.
One for Nvidia, another for your python need and so on.
Multiple questions about different problems dilute the thread, and most here will just ignore.

Drivers are more of advanced or experienced user, and Ubuntu dose a pretty good job at that in the installation process. Just tick the box for Third party Software.

There no way anyone can give you a magic pill to satisfy everything a user needs/wants that's where you come in.
It's take a willing mind to learn. Or you can if you choose just keep banging your head against the same brick wall.

---

