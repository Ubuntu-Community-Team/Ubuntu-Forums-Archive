---
title: "Synaptic touchpad problems after upgrade"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by rflores2323 on 2010-01-18
I just upgraded 9.04 to 9.10 and I love it.  I have a gateway laptop and the **Synaptic touchpad **does not work however.  I have tried to install the gsynaptic repository however when I try to run it an error message comes up saying "You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I followed these steps to set up shmconfig

```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fd
```put the below in

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>
```how do I know if it is enabled?  I try to see if the touchpad has been detected by the below

[PHP]xinput list[/PHP]but it does not dtect my touchpad?

I am also having a problem in the grub loading screen as I have two kernels in there.  one that just hangs and the other does boot up correctly. I tried to delete the kernel that hangs in the synaptic manager and it shows that its deleted but it doesnt delete from the grub screen?  How is this done?
  
Would it be easier to just do a clean install of 9.10 to get the grub screen ok and the touchpad working?

---

### Post by kseise on 2010-01-18
Leave the broken kernel in there for now.  It is not hurting anything.

Try uninstalling the gsynaptic package and see if the trackpad works.  I don't have this installed on my 2 dell laptops and the pad works fine.  I think that the gsynaptics might be for a digitizer type of pad.

---

