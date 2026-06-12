---
title: "Need to reinstallUbuntu on second half of hardrive because of non working install"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by NotWindows on 2010-10-28
Hello,

I have a laptop with Win XP and Ubuntu installed as dual boot. Well something happened with the Ubuntu install and I need to reinstall but can't figure out how to do it.

Help!
Thanks,
Kevin/NotWindows

---

### Post by oldfred on 2010-10-28
If you just want to reinstall use manual install and choose the same / (root) partition. If /home was separate you have to choose it but DO NOT format it.

To see partitions:

```
sudo fdisk -l
```

Is current install not repairable?

---

### Post by NotWindows on 2010-10-28
I haven't tried to repair, I am new to Ubuntu and not sure how to do this. One other time I did an update to Ubuntu on my desktop and had problems and someone helped me and told me how to do it through the partition manger and all of that but I sure don't remember exactly what he told me to do. I also couldn't find the post in my profile info.

If I want to repair how do I do that? I guess I need some very specific step by step instructions.

Thanks,
Kevin

---

### Post by oldfred on 2010-10-28
What is not working. Can you boot? Do you get a grub menu. Is it perhaps a video issue? Or something else. Please describe the issue as best as you can. 

If a booting issue run this from a liveCD. 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by NotWindows on 2010-10-29
It will not boot into Ubuntu. I see grub come up before the Ubuntu screen and then it gives a text screen and I am not sure what it is saying. I would just rather format the petition and reinstall.

---

### Post by oldfred on 2010-10-29
If it is a video issue, you may still have that after a reinstall. You can edit the grub menu with parameter to work around video issues. 

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

(from Fedora)
All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
nouveau.modeset=1

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

---

### Post by NotWindows on 2010-10-29
No Video Issue! Windows works just fine and Ubuntu used to work just fine! I just want to reformat that petition and reinstall Ubuntu becuase it won't load up! I know there is a way to do what I want and have done it before but can't remember how the gentleman walked me through it before. It is all done in the patition menus just got to set it up correctly.
 
I need to be able to have this done tonight!

---

### Post by ronparent on 2010-10-29
You just need to use the cd to reinstall, except this time when you get to the partitioning step, select manual partitioning. This allows you to select the partition you previously installed to as the target for the new install. Just select the partition, elect to 'change' and then verify that the block to format is checked and that you have '/' selected as your mount point. Proceed thru the install and the partition will be formatted and the new install will be in place. Let us know if you run into any other problems.

---

### Post by NotWindows on 2010-10-29
Yes Yes Yes! I am sure that was it, strikes a memory! I will make a note of that in case I ever need it again and I will post later tonight when I get home that it is solved!
 
THANK YOU!
Kevin/NotWindows

---

### Post by NotWindows on 2010-11-06
That did the trick, Thanks!

Kevin
NotWindows

---

