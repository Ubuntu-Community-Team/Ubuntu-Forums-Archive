---
title: "Mini Howto / Workaround Ubuntu Server to Desktop Conversion"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by nowhere@cox.net on 2008-11-30
Hey all,

I had some troubles today installing Ubuntu Intrepid and had to come up with a workaround. So here it is.

Problem: Live CD won't launch X (graphical window interface) and installing with the alternative CD results in the same problem when rebooting to Ubuntu the first time. X won't start or hangs up just after logging in.

For me the problem is that the open source nvidia driver that is installed by default for nvidia systems will not start on my nvidia Geforce 7800 GT. Also, I wanted the Ubuntu server optimizations and servers installed so I decided to use the ubuntu server installation disk. The process is as follows:
[LIST=1]
[*]Download, boot and install the Ubuntu Server Distribution
[*]After installation and reboot, login and issue the following commands```
sudo apt-get install ubuntu-desktop
```
[*]After a ton of downloading and a very long wait, check your xorg.conf file. Mine was empty, indicating a problem setting up X```
sudo nano /etc/X11/xorg.conf
```
[*]If empty, reboot but select the recovery option, and scroll down to the fix X option
[*]Now the tricky part. I had to modify the /etc/X11/xorg.conf file generated to change the driver "nv" or whatever it selected to driver " vesa" in order for my X to start without hanging. Mine was actually blank like this:```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

```I chose to log in via ssh from another machine to do this.```
ssh 192.168.0.101
sudo nano /etc/X11/xorg.conf

``` add this in the Device section right before the end ```
driver "vesa"
```Save and reboot.
[*]Once I did this I was able to get X started, but without any 3D capabilities since the restricted drivers are not running. I installed the source and headers required to compile stuff and also to install the nvidia restricted drivers.```
sudo apt-get install build-essential
```
[*]Unfortunately, with Ubuntu Server Intrepid, this isn't enough. The restricted driver packages are looking for the header files in a specific place (hopefully the developers read this and fix it!). The restricted package manager would claim to install the driver, but never showed the request to reboot (the little reboot icon). Also, when trying to installed the correct nvidia-glx-177 driver via apt-get I got an error:```
Error! Your kernel source for kernel 2.6.27-9-server cannot be found at
/lib/modules/2.6.27-9-server/build or /lib/modules/2.6.27-9-server/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.27-9-server (i686) first.
Done.

```The first error is complaining because the headers are not where they are expected. The second is because the driver was not installed. The build-essential installs the generic source. So I installed the server headers also.```
sudo apt-get install linux-headers-2.6.27-9-server
```This will not work once there is an update to the kernel since the kernel version number will change so modify yours accordingly or you can use synaptic from the System->Administration->Synaptic Package Manager. Search for linux-headers and you will see the generic package installed and can also select the server version right next to it.
[*]After I did this, the restricted drivers installed just fine with the restricted package manager.
[/LIST]Hopefully this will help someone with the same problem or someone with similar problems get things working. I have this problem with this particular graphics card every time I install Ubuntu. I also don't know if anyone else has these types of troubles.

Good Luck All!

---

### Post by nowhere@cox.net on 2008-12-01
Ok bummer,

First kernel update breaks this because you have to go in a install the headers for the new kernel by hand and reactive the nvidia restricted driver via the Hardware drivers program. This is not an acceptable solution. 
In this case I had to```
sudo apt-get install linux-headers-2.6.27-10-server
```

Does anyone have a better solution to fix this? This seems to be a major problem for anyone installing server and adding the desktop. 

Thanks!

---

