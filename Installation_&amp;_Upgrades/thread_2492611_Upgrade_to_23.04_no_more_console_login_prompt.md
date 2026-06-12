---
title: "Upgrade to 23.04 no more console login prompt"
date: 2023-11-17
forum: Installation &amp; Upgrades
---

### Post by aathan on 2023-11-17
After upgrading to 23.04 from 22.04 on a virtualbox hypervisor host, there is no login: prompt on the console. I'm not sure what packages or system components to investigate. It looks like the login prompt should be visible, so maybe I'm dealing with some kind of video issue on virtualbox???  There's an underlying cursor at the top left of the screen immediately after boot, but it's no longer visible now.

```

# systemctl status getty.target
&#9679; getty.target - Login Prompts
     Loaded: loaded (/lib/systemd/system/getty.target; static)
     Active: active since Thu 2023-11-16 22:06:37 PST; 12min ago
      Until: Thu 2023-11-16 22:06:37 PST; 12min ago
       Docs: man:systemd.special(7)
             man:systemd-getty-generator(8)
             [http://0pointer.de/blog/projects/serial-console.html](http://0pointer.de/blog/projects/serial-console.html)


Nov 16 22:06:37 xxx systemd[1]: Reached target getty.target - Login Prompts.


# systemctl status getty@tty1
&#9679; [EMAIL="getty@tty1.servic"]getty@tty1.servic[/EMAIL]e - Getty on tty1
     Loaded: loaded (/lib/systemd/system/getty@.service; enabled; preset: enabled)
     Active: active (running) since Thu 2023-11-16 22:06:37 PST; 12min ago
       Docs: man:agetty(8)
             man:systemd-getty-generator(8)
             [http://0pointer.de/blog/projects/serial-console.html](http://0pointer.de/blog/projects/serial-console.html)
   Main PID: 506 (agetty)
      Tasks: 1 (limit: 2203)
     Memory: 248.0K
        CPU: 6ms
     CGroup: /system.slice/system-getty.slice/getty@tty1.service
             &#9492;&#9472;506 /sbin/agetty -o "-p -- \\u" --noclear - linux


Nov 16 22:06:37 xxx systemd[1]: Started [EMAIL="getty@tty1.servic"]getty@tty1.servic[/EMAIL]e - Getty on tty1.
# killall -HUP agetty

```

---

### Post by ajgreeny on 2023-11-17
Tell us more about your version of VBox as some older versions are incompatible with the newer kernels in recent Ubuntu versions.

It may be worth trying VBox version 7.0.12 direct from the VBox website [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)  which in my testing has been better than the older 6.1.# versions, though I no longer use VBox other than to simply test it; mostly I now use KVM/QEMU, the Linux virtualisation system/hypervisor which is faster, smoother and generally much better for Linux hosts.

---

### Post by aathan on 2023-11-17
[COLOR=#000000]Version 7.0.12 r159484 (Qt5.15.2) on a MacOS Ventura 13.6.1 (22G313) host.

I've run this machine on qemu on macOS but I'm not clear on whether that's an emulated CPU or a true hypervisor executing on hardware instructions. Qemu worked great, but qualitatively, I felt vbox is giving me better performance.

Any hints on what I can do to test whether agetty is in fact providing prompts but they're just not visible? I guess one thing I can try is to vary the display hardware configuration of the vbox instance to see if the display is the core issue... willdo.

EDIT:  Oh, by the way, the do-release-update (-upgrade?) on two separate hosts left me in a bad state, including no systemd-resolved installed & configured, and bad outcomes to "inspect the changes" from dpkg configure conflicts. Can you point me to the right forum to report on that and see what can be improved there?[/COLOR]

---

### Post by aathan on 2023-11-17
Ok, so that was it. login was visible when I switched to VBoxVGA from the recommended VMSVGA adapter.

VBox's GUI was indicating an "invalid settings detected" and the details included a statement (paraphrasing) that 26Mb of RAM was necessary to switch to full-screen or seamless mode (which I am not interested in).

Irrespective of that, I did a binary search for the minimum memory required to get a login: prompt under the VMSVGA adapter starting at 32Mb. 32, 16, and 8Mb worked, giving a login: prompt. 6Mb did not.

I was originally at 4Mb, which worked fine (under VMSVGA) under the prior iteration of ubuntu. I think it was 20.04 on this system. So, I guess something changed where the default video mode the system boots into post-upgrade is higher resolution than before, and the mode switch is failing.

This could be causing other people some headaches...maybe that regression should be reverted, and/or maybe something is missing as far as calling out config differences in grub and/or init params?  Not exactly sure where this is controlled, but I imagine grub configs???

EDIT: It also seems to me that if there's a way to detect the video mode switch failure (assuming that's what's happening), or lack of sufficient memory for a mode, that the next lowest mode should be automatically selected by that process??

---

### Post by MAFoElffen on 2023-11-17
Even more basic... You said you are "not getting a login prompt"...

Is the VM Guest of Ubuntu Desktop or Server Edition?

If Desktop, are you saying you are not getting a Graphical Login for GDM3? 

If Server, are you saying you are not being asked for your credentials to login? You said "console' so I am assuming "Server". 

You tagged it as "ubuntu', but could have marked it as "server"...

I see in later posts that it was a VM machine graphics setting... another way to get it lower, would be to turn off the vga graphics in /etc/default/grub, by uncommenting GRUB_Terminal=console...

---

