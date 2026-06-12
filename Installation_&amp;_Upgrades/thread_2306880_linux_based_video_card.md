---
title: "linux based video card"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by stompin-tom on 2015-12-19
I have a notebook with an Intel graphics media accelerator 950- is there a linux based video card I can upgrade to, or any other solution to upgrade/change this? My operating system is xubuntu 15.10. Thanks. Tom.

---

### Post by TheFu on 2015-12-19
Upgrading the GPU on a laptop is NOT usually supported/possible.  You might be able to connect an external USB graphics adapter, but don't expect high performance with that.  Using a current-generation nvidia or AMD GPU is usually sufficient. With releases after 14.04, AMD support for their older GPUs has dropped and only the F/LOSS drivers are supported. There is a warning about this in the release notes for 15.10.

For folks who aren't very familiar with Linux, it is best to run only the LTS released versions. The current LTS is 14.04.  16.04 will be the next LTS release with 5 yrs of support. All others only get 6-9 months of support. Just for your consideration.

Are you certain the correct driver is being used with your GPU?  **sudo lshw -C video** output would be helpful. Please use "code tags" so things line up correctly.
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: **driver=i915** latency=0
       resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
```
I didn't do anything special to get the correct driver for this system. A normal 14.04 install handled it.

---

### Post by stompin-tom on 2015-12-19
Thanks, Thefu. I entered that command and came up with the same driver. I plan on upgrading to 16.04 when it is released. I am a newbie, so I have much to learn.

---

### Post by TheFu on 2015-12-20
> **stompin-tom said:**
> Thanks, Thefu. I entered that command and came up with the same driver. I plan on upgrading to 16.04 when it is released. I am a newbie, so I have much to learn.

We were all new at some point, plus there are always new things being added or old things being changed, so the learning will continue.  The upgrade to 16.04 is an easy choice. It is the installations of non-LTS releases that really shouldn't be suggested to folks new to Linux, IMHO. Basically, it is beta software where Canonical (and devs) try new stuff out.  They've been slowly introducing systemd since 14.04 .... by 16.04, I think it will be completely there, but in the meantime, some things work the old way and other things work the new way. It is already a steep learning curve, so adding the "sometimes do it this way" aspects for each non-LTS release can only add to the confusion. That's exactly what Ubuntu needs, more confusion. ;)

Please post the requested cmd and output. This prevents misinterpretation, plus we are very familiar reading these things and might see something you don't.  For example, that driver is used with many different onboard Intel GPUs, but the performance of those is vastly different. Your interpretation of the GPU model was really my question.  I posted the output from one of mine to show that sharing this data isn't "dangerous." Depending on the hardware involved, there may be nothing you can do to make it perform better - I assume that is why you are posting.  For example, a 5 yr old Atom Netbook will use the same driver as my 2 yr old Haswell CPU, but the performance is night/day different.  Also, copy/paste text is best, not an image. Images aren't friendly for people with low-bandwidth. Lots of people here use cellular data to read the forums and on a 10MB plan, an image sucks bandwidth.

There aren't really any "Linux" video cards to my knowledge. Perhaps you meant to say "Linux compatible"? Plus, some of the newest cards from nVidia and AMD/ATI will have driver issues, so those would be a very poor choice for someone new to Linux. Drivers for newer cards often don't work or don't exist.  I haven't spent more than $35 on a video card in years ... a decade perhaps, because my needs around graphics are modest and the built-in Intel GPUs blow away whatever I needed for about the last 5 years. I don't "game" - well, I do, but WordDrop and Sudoku don't really need great graphics. ;)  For office productivity, any GPU is fine and whatever I have laying around that fits into the slot will be overkill.  

[http://plugable.com/products/uga-2k-a](http://plugable.com/products/uga-2k-a) is a USB video connector for monitors. > Linux configuration for advanced users only, so I wouldn't recommend it. Further:
> As of Linux kernel 2.6.31, this adapter has open source drivers in the kernel staging tree. As of 2.6.38, the driver was promoted to the main kernel tree. Configuration of X Windows for USB displays is still distribution and scenario dependent, however, and only for very adventurous users. Plugable is involved with Linux development work, see [http://plugable.com/category/platform/linux/](http://plugable.com/category/platform/linux/) for details.

That's my perspective.  You ask for an upgrade, but didn't say why, so it is very hard for anyone to suggest a specific solution.  Some are good for gaming. Some are good for video playback, and others are good for adding additional outputs - more monitors. If you want a 6 monitor system, the answer will be different than crazy gaming with FPS stuff. Why do you want an upgrade?  A $600 video card for a gamer will be wasted on someone who just wants to watch movies.

"notebook" is a little vague too. Specifics please.  [http://blog.jdpfu.com/2015/09/05/getting-comprehensive-system-information](http://blog.jdpfu.com/2015/09/05/getting-comprehensive-system-information) explains.

---

### Post by stompin-tom on 2015-12-20
om@tom-Compaq-Mini-CQ10-100:~$ sudo lshw -C video

 [sudo] password for tom:  
   *-display:0              
        description: VGA compatible controller
        product: Mobile 945GSE Express Integrated Graphics Controller
        vendor: Intel Corporation
        physical id: 2
        bus info: pci@0000:00:02.0
        version: 03
        width: 32 bits
        clock: 33MHz

        capabilities: msi pm vga_controller bus_master cap_list rom
        configuration: driver=i915 latency=0
        resources: irq:16 memory:fe980000-fe9fffff ioport:dc80(size=8) memory:d0000000-dfffffff memory:fe940000-fe97ffff
   *-display:1 UNCLAIMED
        description: Display controller
        product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
        vendor: Intel Corporation
        physical id: 2.1
        bus info: pci@0000:00:02.1
        version: 03
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list
        configuration: latency=0
        resources: memory:fe880000-fe8fffff             HOW CAN I UPDATE MY DRIVERS USING XUBUNTU SYSTEM- IT IS MY SOLE OPERATING SYSTEM.

---

