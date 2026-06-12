---
title: "Ubuntu LTS Radeon Boot Issue"
date: 2015-09-08
forum: Installation &amp; Upgrades
---

### Post by turkel.christopher on 2015-09-08
[COLOR=#000000][FONT=Verdana]I have a Dell Optiplex 360 and I installed a Radeon HD 8670 / R7 250 in, otherwise nothing has changed. The only distro that will install is Ubuntu 12.04 LTS, everything else won't start an installer or just hang on a black screen.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]To even get Ubuntu to not freeze I had to boot into safe mode and install the proprietary Radeon drivers.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Half the time when I shut down or reboot it will just go to a black screen and to get it to work I have to boot into safe mode and run aticonfig --initial and reboot.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Any help?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2015-09-08
Did you install the fglrx package or ATI's binary driver?

In your next post, could you press the "#" code icon in the advanced post toolbar and paste your /etc/X11/xorg.conf contents in between the [ code ] tags?

Also, do the same again and paste the results of 
```

sudo lspici | grep VGA && sudo lshw -n -c video

```
There is a conflict challenge when you install an PCI channel mounted R7 and if an onboard GPU or APU is stil active...

---

### Post by turkel.christopher on 2015-09-13
I have disabled on my board graphics;

chris@terminalfrost:~$ sudo lspci | grep VGA && sudo lshw -numeric -c video01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland XT [Radeon HD 8670 / R7 250]
  *-display               
       description: VGA compatible controller
       product: Oland XT [Radeon HD 8670 / R7 250] [1002:6610]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:29 memory:c0000000-cfffffff memory:dfdc0000-dfdfffff ioport:dc00(size=256) memory:dfe00000-dfe1ffff

---

### Post by MAFoElffen on 2015-09-14
Let me ask again:
> **MAFoElffen said:**
> Did you install the fglrx package or ATI's binary driver?

You said
> **turkel.christopher said:**
> [COLOR=#000000][FONT=Verdana]To even get Ubuntu to not freeze I had to boot into safe mode and install the proprietary Radeon drivers.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Half the time when I shut down or reboot it will just go to a black screen and to get it to work I have to boot into safe mode and run aticonfig --initial and reboot.
[/FONT][/COLOR]
Remember my last post where I asked you to put your pasteed results within Code tags?
```

This is some text residing within code tags

```
You didn't do that with the last results and if I ask you to post your /etc/X11/xorg.conf file (within code tags)... it may be a mess. So could you please instead attach that file to your next post? Your may have to copy it to somewhere and append a .txt extension to it to be able to upload it as an attachment.

---

