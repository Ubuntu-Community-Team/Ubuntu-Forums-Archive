---
title: "upgrade to 20.04 went south"
date: 2020-06-30
forum: Installation &amp; Upgrades
---

### Post by backspin on 2020-06-30
I upgraded to 20.04 from 18.04, and I tried to upgrade the amdgpu drivers, and I've lost my gui.

During the upgrade I kept my current repositories, so I don't have focal fossa's repositories.  What's the PPA, so I can get those added first.  

I need to start there to see if I can dig myself out of this hole.

Thanks,

David

---

### Post by ubfan1 on 2020-06-30
I have no idea on how you "upgraded" without the right repos, but here are the ones in my /etc/apt/sources.list:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main restricted #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal restricted multiverse universe main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates restricted multiverse universe main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security restricted multiverse universe main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

---

### Post by backspin on 2020-06-30
Thanks.. these things kinda just happen when one upgrades every few years or so, and doesn't plan. 

The root of the problem happened when I tried to upgrade lm-sensors which has dependencies.   Then I tried to upgrade my amdgpu, and it is failing due to dependencies. So, I cleared them up and now it won't install due to dkms.  I've now tried to clear up dkms, but say dkms is not configured.

I might end up having to blow this away depending... sigh.  Will keep chipping away at it.

---

### Post by backspin on 2020-06-30
The amdgpu installs successfully, but after a reboot just kicks me to command line..  Bunch of errors being spit out.

Does Ubuntu use amgpu by default? Is there a way I can reset so Ubuntu uses what it comes with?

---

### Post by Turbine1991 on 2020-07-02
I find removing all GPU drivers before an upgrade solves the majority of upgrade issues. Especially on nvidia and old amd driver's, not sure about the new.

Once upgraded, reinstall.

---

### Post by backspin on 2020-07-03
Thanks --  I ended up blowing away the current system, and installing 20.04 from scratch, and it works much better now.  This new Ubuntu 20.04 is using amdgpu, but I can't tell what revision, if that makes sense. On the amd website it is 20.20, but I can't tell what this is running.

avidc502@Ryzen3900x:~$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:150 memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:e000(size=256) memory:fcd00000-fcd7ffff memory:c0000-dffff

---

### Post by backspin on 2020-07-05
Some digging around on AMD driver tweaks, and a good resource that is  still good is found -> [https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

Specifically these should work for AMD GPU's -- Your path might vary depending. 

Manually setting the fan

The  Auto FAN Setting "2"  <- This should be what it is set to out of the  box.  To set it back to auto enter the command below.
sudo echo "2" > /sys/class/drm/card0/device/hwmon/hwmon4/pwm1_enable

Manual Setting for FAN speeds. The command below sets it to manual.
sudo echo "1" > /sys/class/drm/card0/device/hwmon/hwmon4/pwm1_enable

Fan speeds 1-255.  1 being Zero RPM and 255 being the Fastest RPM.

echo "150" > /sys/class/drm/card0/device/hwmon/hwmon4/pwm1

Playing  around, I found that manipulating the fan speeds during game play  boosted frame rates. If I crank the fan up to around 175-200 the GPU  stayed at higher clock speeds for longer period of times.  It appears  the automatic FAN settings are less aggressive. Auto still gives good  performance and is quiet, but at some FPS sacrifice. 

Manipulation  of GPU setting with auto FAN speeds did very little to increase  performance. I went with higher clock rates (more aggressive), but then  found GPU load for those speeds decreased rendering approximately the  same frame rates. Perhaps manually setting the FAN at higher RPM's and  aggressively setting the GPU would render better frame rates, but I  haven't tested.

*Edit*  How I monitored.

The easiest way is to open two cmd windows and enter the following line.  Also, you can run both commands in the same window and separate them by a semicolon ;  However, you will need to add quotes. 

sudo watch cat /sys/kernel/debug/dri/0/amdgpu_pm_info

You might have to install lm-sensors first before you can run the next command.

watch sensors

Watching sensors does give extra info you might not be interested in. This will help to knock down some of the extra stuff and just watch gpu info

watch "sensors | grep -E 'vddgfx|fan1|edge|junction|mem|power' |awk '{print \$2 \"\t\" \$1}'"

*EDIT*

All in one line --

sudo watch "sensors | grep -E 'vddgfx|fan1|edge|junction|mem|power' |awk '{print \$2 \"\t\" \$1}' ; cat /sys/kernel/debug/dri/0/amdgpu_pm_info |grep -E '\(SCLK\)|\(MCLK\)|\(average GPU\)' |awk '{print \$1, \$2, \$3, \$4}' ; cat /sys/kernel/debug/dri/0/amdgpu_pm_info |grep -E 'GPU Temperature|GPU Load|MEM Load' |awk '{print \$3\$4, \$1, \$2}'"

---

