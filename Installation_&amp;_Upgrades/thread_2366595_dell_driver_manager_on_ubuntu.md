---
title: "dell driver manager on ubuntu"
date: 2017-07-19
forum: Installation &amp; Upgrades
---

### Post by azim3 on 2017-07-19
Hello everyone,
Before 2m I buy dell laptop with installed Ubuntu 16.04 and I make a quick tour and see one app with name "dell driver manager" in my dash, but I format HDD and install ubuntu 17 and now cannot find this app..
Can anyone support me to find it ? 
Thanks :)

---

### Post by deadflowr on 2017-07-19
It's possible the package has not nor will not have been built for 17.04.
If the machines were pre-built with 16.04 then maybe the packages are from dell's repositories.
Which you would need to install yourself.
(I see dell has repos here, [http://linux.dell.com/repo/community/ubuntu/]("http://linux.dell.com/repo/community/ubuntu/")
but I don't know if they have what you want)

---

### Post by oldfred on 2017-07-19
What did Dell Driver Manager do?

Previous releases of Dell Sputnik were later incorporated into default Ubuntu/Linux software. So all the functions may be available, just not called Dell Driver manager?

         Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by vasa1 on 2017-07-19
Some Dell-related stuff found in the default repos can be found by running```
apt list --all-versions | grep -i dell | grep -v model
```I see```
dell-recovery/xenial,xenial 1.48 all
dell-recovery-bootloader/xenial,xenial 1.48 all
dell-recovery-casper/xenial,xenial 1.48 all
firmware-addon-dell/xenial,xenial 2.2.9-0ubuntu2 all
```


If you have```
deb http://dell.archive.canonical.com/updates/ xenial-dell public
```in your software sources, you may see more. But, again, as deadflowr points out, it depends on whether Dell has done anything for 17.04: I think that it's highly unlikely that they do anything for non-LTS versions.

---

### Post by azim3 on 2017-07-20
hello,
sorry for delay I was on business trip..
So, I just want to install it again with only one hope - to make my discrete AMD GPU works.
because now when I start something with intel GPU have experimentally 1000 FPS, but when I try with DRI_PRIME=1 {app} my FPS is very poor approximately 505 FPS this is half of intel FPS
I try Kernel 4.12 with Mesa 17.2, but same results...
I just wan to try configure drivers with dell driver manager and find way to install this manager.
Any ideas about my issue ? 
Thank you all :)

---

### Post by oldfred on 2017-07-20
You may just need to install correct AMD driver for your AMD card/chip.
I do not know AMD and current versions that apply. They have been in the process of obsoleting some drivers like fglrx and trying to just use the open source driver.

 Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

---

### Post by azim3 on 2017-07-22
> **oldfred said:**
> You may just need to install correct AMD driver for your AMD card/chip.
I do not know AMD and current versions that apply. They have been in the process of obsoleting some drivers like fglrx and trying to just use the open source driver.

 Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver)

 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

I did a lot of experiments with drivers but without success...
I have AMD R7 M445 in my laptop with i5-7200 processor
I post output from xrandr --listproviders bellow
```
xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x64 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 2 associated providers: 1 name:modesetting
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:Unknown AMD Radeon GPU @ pci:0000:01:00.0
```
And from vgaswitcheroo:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
[sudo] password for azim: 
0:DIS: :DynOff:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0

``` 
I don`t know what I need to do to have worked AMD GPU on my Ubuntu... I was trying amdgpu-pro, but when is install have blackscreen after login...
Please support me to install and configure the right drivers..
Thank you! 
Again sorry for delay I`m online now :)

---

