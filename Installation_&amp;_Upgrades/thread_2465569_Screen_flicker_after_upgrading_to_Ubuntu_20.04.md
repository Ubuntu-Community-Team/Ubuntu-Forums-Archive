---
title: "Screen flicker after upgrading to Ubuntu 20.04"
date: 2021-08-05
forum: Installation &amp; Upgrades
---

### Post by kws3778 on 2021-08-05
I recently upgraded from Ubuntu 18.04 to 20.04 LTS on my laptop (Lenovo Ideapad FLEX 6-14IKB). After a while the screen would start flickering (similar to the video in this post [here]("https://www.reddit.com/r/linuxhardware/comments/ihjig0/screen_flickering_on_ubuntu_2004_please_help/")). I notice that sometimes it would flicker a lot an then stop for a while - it would usually happen more often when I'm actively browsing Chrome/Firefox. The issue does not exist on an external monitor that I connect to the laptop (flicker only happens on laptop built in screen). The issue also did not happen in 18.04.
I've tried to adjust the refresh rate of the screen to less than 60hz and also tried other solutions from similar posts such as switching to Ubuntu Wayland display, [modifying Grub settings]("https://wiki.archlinux.org/title/intel_graphics#Screen_flickering") by adding "i915.enable_psr=0", and [creating xorg config]("https://bugs.chromium.org/p/chromium/issues/detail?id=606152#c72") (see comment 72). I also do not have any Additional Drivers to install in Software & Updates. However the issue still persists.

System info:
CPU info is in the attachment cpuinfo.txt

```
Kernel version: 5.4.0-80-generic
```

```

lshw -c video
description: VGA compatible controller
   product: UHD Graphics 620
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 07
   width: 64 bits
   clock: 33MHz
   capabilities: vga_controller bus_master cap_list rom
   configuration: driver=i915 latency=0
   resources: irq:137 memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:4000(size=64) memory:c0000-dffff
```

---

### Post by MAFoElffen on 2021-08-05
> **kws3778 said:**
> I recently upgraded from Ubuntu 18.04 to 20.04 LTS on my laptop (Lenovo Ideapad FLEX 6-14IKB). After a while the screen would start flickering (similar to the video in this post [here]("https://www.reddit.com/r/linuxhardware/comments/ihjig0/screen_flickering_on_ubuntu_2004_please_help/")). I notice that sometimes it would flicker a lot an then stop for a while - it would usually happen more often when I'm actively browsing Chrome/Firefox. The issue does not exist on an external monitor that I connect to the laptop (flicker only happens on laptop built in screen). The issue also did not happen in 18.04.
I've tried to adjust the refresh rate of the screen to less than 60hz and also tried other solutions from similar posts such as switching to Ubuntu Wayland display, [modifying Grub settings]("https://wiki.archlinux.org/title/intel_graphics#Screen_flickering") by adding "i915.enable_psr=0", and [creating xorg config]("https://bugs.chromium.org/p/chromium/issues/detail?id=606152#c72") (see comment 72). I also do not have any Additional Drivers to install in Software & Updates. However the issue still persists.

System info:
```
[COLOR=#ff0000]Kernel version: 5.4.0-80-generic[/COLOR]
```
```

lshw -c video
description: VGA compatible controller
   product: UHD Graphics 620
   vendor: Intel Corporation
   physical id: 2
   bus info: pci@0000:00:02.0
   version: 07
   width: 64 bits
   clock: 33MHz
   capabilities: vga_controller bus_master cap_list rom
   configuration: driver=i915 latency=0
   resources: irq:137 memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:4000(size=64) memory:c0000-dffff
```
A few things... First... Look at your kernel version and type. Note that the current version of Linux kernel for Ubuntu 20.04.2 today is 
```
$ uname -r 
5.8.0-63
```
Which means that you are running the GA kernel for 20.04.0 without the HWE (Hardware Ennoblement Stack) and It's Kernel which helps with Graphics and other hardware... The HWE is now default for Desktop, if you had installed from ISO, but you upgraded from 18.04...

Do this...
```
sudo apt update
sudo apt install --install-recommends linux-generic-hwe-20.04
sudo reboot

```
This will install the Hardware Ennoblement Stack and it's series of Kernels that is tied into that stack. ...And reboot into that kernel...

Next, do 
```
sudo spt update
sudo apt install --install-recommends mesa-utils
sudo apt full-upgrade
sudo apt autoremove
sudo reboot

```
This will get you to LTS version 20.04.2 and make sure all your Mesa Drivers are up to date.

Explanation for that: Your APU, meaning the Intel GPU inside your CPU, is Intel, which gets your video drivers from inside the Linux Kernel, and From the Mesa Drivers... Those versions matter to you.

Remove the Hardwired Xorg.conf file you created by just adding an .backup file extension to it. There is actually a Intel xorg conf file already installed by default in another directory (Besides /etc/X11/xorg/). That should already be good, as is. As of Kernel 5.4.x, there were some changes to that, which are affected by each kernel version... of what people used to do, now can break your Intel graphics. Those are updated by kernel version now.

Remove the Grub boot parameter for now and try it. If you have problems and need one... I know some that work for your graphics... But for now just try it without it. That specific parameter was a work-around for Kernels 4.12.x through 4.16.x and was supposedly fixed in Kernel 4.17.0... Just saying...

*** What you haven't mentioned is what specific CPU that has... (???)

---

### Post by MAFoElffen on 2021-08-05
Of note,,, since your Mesa drivers are very closely tied into your graphics, along with your Kernel Version, after you do all that, please post the results of
```
uname -r
glxinfo | grep -i "OpenGL ES profile version string:"

```

---

### Post by kws3778 on 2021-08-05
Thanks for the reply. I've edited the original post to include an attachment containing my CPU information. 

I've went through all the steps described. Here's the new info:
After Running "uname -r":
5.11.0-25-generic

After running "[COLOR=#000000][FONT=&amp]glxinfo | grep -i "mesa":

[/FONT][/COLOR]
```
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, GLX_OML_swap_method, 
client glx vendor string: Mesa Project and SGI
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_query_renderer, GLX_MESA_swap_control, GLX_OML_swap_method, 
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
Extended renderer info (GLX_MESA_query_renderer):
    Device: Mesa Intel(R) UHD Graphics 620 (KBL GT2) (0x5917)
OpenGL renderer string: Mesa Intel(R) UHD Graphics 620 (KBL GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 21.0.3
    GL_KHR_texture_compression_astc_sliced_3d, GL_MESA_framebuffer_flip_y, 
    GL_MESA_pack_invert, GL_MESA_shader_integer_functions, 
    GL_MESA_texture_signed_rgba, GL_NV_compute_shader_derivatives, 
OpenGL version string: 4.6 (Compatibility Profile) Mesa 21.0.3
    GL_KHR_texture_compression_astc_sliced_3d, GL_MESA_framebuffer_flip_y, 
    GL_MESA_pack_invert, GL_MESA_shader_integer_functions, 
    GL_MESA_texture_signed_rgba, GL_MESA_window_pos, GL_NV_blend_square, 
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 21.0.3
    GL_KHR_texture_compression_astc_sliced_3d, GL_MESA_framebuffer_flip_y, 
    GL_MESA_shader_integer_functions, GL_NV_compute_shader_derivatives, 

```

After running "glxinfo | grep -i "OpenGL ES profile version string:"
```

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 21.0.3

```

---

### Post by MAFoElffen on 2021-08-05
How is it working now?

Just for documentation: 
> Intel Core i5-8250U, CPU Family, 8th Generation Intel Core, "Kaby Lake R", UHD Graphics 620

---

### Post by kws3778 on 2021-08-05
I just completed the steps about half an hour ago. I'll monitor it for 24-48 hours and will let you know.

---

### Post by MAFoElffen on 2021-08-05
Thank you. Please keep me updated.

---

### Post by kws3778 on 2021-08-06
> **MAFoElffen said:**
> Thank you. Please keep me updated.

Update: It seem to worked for the first 12 hours with no flickering but the next day after I started up the computer it started flickering again. I would say the flickering is slghtly less than before but I've only been monitoring for about 24-36 hours at this point.

I also feel like whenever a more intensive process is running it will flicker more (such as watching video, having PyCharm open and running programs, or when a webpage is loading in Chrome/Firefox), whereas if I'm just not doing anything or just reading an article it would only flicker occasionally. But I'm not sure if there's a definite correlation as this is just from obersavtion

---

