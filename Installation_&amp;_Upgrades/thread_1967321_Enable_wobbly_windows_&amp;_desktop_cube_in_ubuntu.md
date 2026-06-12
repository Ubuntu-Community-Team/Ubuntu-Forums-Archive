---
title: "Enable wobbly windows &amp; desktop cube in ubuntu 12.04"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Nando88 on 2012-04-28
I upgraded to Lubuntu 12.04, and saw that wobbly windows didn't work and the desktop cube didn't rotate, can someone please tell me how to fix this?
Thanks in advance!

---

### Post by gianluca.pettinello on 2012-04-28
Same problem!
Why Ubuntu takes away functionalities on every version?
Probably they want to keep people going away from this distro in favour of mint...

---

### Post by tomatoe on 2012-04-28
You have to enable them in compiz.

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Nando88 on 2012-04-28
I installed the compiz settings manager and enabled them, but the title bar disappears and the wobbly windows don't work.

---

### Post by jamesisin on 2012-04-29
Agreed.  I tried this solution as well and still no wobble.

---

### Post by tomatoe on 2012-04-29
I'm not sure, but you might need to enable nVidia drivers to enable wobbly windows and stuff like that. Be cause default drivers don't have 3D support. But as I said, not sure.

---

### Post by dbombtek on 2012-04-29
Are the correct video drivers installed? If so then reinstall compriz and log back in.

---

### Post by jamesisin on 2012-04-29
I show nothing in Additional Drivers which is where I suspect it ought to be found.

---

### Post by Thelinuxgeek on 2012-04-29
Go to [http://www.nvidia.com](http://www.nvidia.com) and download the correct graphics drivers from there.

---

### Post by tomatoe on 2012-04-29
What graphic card do you have? If you have 6th series or higher you can just do this

```
sudo apt-get install nvidia-current
```

And then enable it in additional drivers and then

```
sudo service lightdm restart
```

or just reboot.

---

### Post by jamesisin on 2012-04-29
My video card is on-board in a Dell Studio D540:

[http://www.dell.com/support/troubleshooting/us/en/19/index?c=us&s=dhs&cs=19&l=en&servicetag=5JP6VH1](http://www.dell.com/support/troubleshooting/us/en/19/index?c=us&s=dhs&cs=19&l=en&servicetag=5JP6VH1)

---

### Post by tomatoe on 2012-04-29
Sorry, dude, don't know how to get 3D working on that graphic card. Instructions I gave will work only for nVidia cards.

---

### Post by jadtech on 2012-04-29
i had the same trouble with my dell lap top I could not get 3d to work evn wit h the driver installed on 11.10 or 12.04 beta  when i finish getting the release version I could boot ubuntu 3d  same results as you all was there  nothing worked scrolled and couldnt click the icons either ..

i cant help any father with this issue it was at the point my dell crashed and burned it is no longer ..

---

### Post by ubifree on 2012-05-01
> **tomatoe said:**
> What graphic card do you have? If you have 6th series or higher you can just do this

```
sudo apt-get install nvidia-current
```

And then enable it in additional drivers...

After installing nvidia-current it did not show up under Additional Drivers for me. So instead I activated the driver that was there already (not the post-release updates), restarted the laptop and then my wobbly windows were back again:). As an added bonus I could now also resume my laptop after suspending it. Until now it wouldn't do that after upgrading from 11.10 to 12.04.

---

### Post by livewire94 on 2012-05-01
Does Wobbly Windows work in regular Ubuntu 12.04 with Unity too?  I am hesitant to try it until I know it should work without crashes first.  I am fairly new to Linux and really don't know what to do if it crashes other than hit reset.

I have an ATI Radeon HD 4670 and am using the regular proprietary drivers under additional drivers.

---

### Post by Bouvet on 2012-05-01
> **livewire94 said:**
> Does Wobbly Windows work in regular Ubuntu 12.04 with Unity too?  I am hesitant to try it until I know it should work without crashes first.  I am fairly new to Linux and really don't know what to do if it crashes other than hit reset.

I have an ATI Radeon HD 4670 and am using the regular proprietary drivers under additional drivers.

Good question. I'm knew to Linux as well and have always marveled 
at the 'wobbly' window. I'd like to try it.

---

### Post by kelt65 on 2012-05-04
You just need compiz-config-settings-manager

---

### Post by cgkades on 2012-05-10
> **kelt65 said:**
> You just need compiz-config-settings-manager

is that package somewhere special? i could not find it with apt-cache search compiz

---

### Post by hypnot0ad on 2012-06-27
> **tomatoe said:**
> You have to enable them in compiz.

```
sudo apt-get install compizconfig-settings-manager
```

This worked perfect for me.

---

