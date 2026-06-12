---
title: "GPU installation on Ubuntu 14.04 LTS"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by richard58 on 2014-06-05
Hello guys,

I am new in this message board and just started installing Ubuntu 14.04 LTS on my laptop

I encounter big issues while installing my GPU (Geforce 860m) and I can't pinpoint the solution...I have tried for several days already without any success.

I tried this 

[COLOR=#333333]"Do a clean install of 14.04LTS allowing Ubuntu Installer to install the default driver (this will be the Nouveau open-source driver).[/COLOR]
[COLOR=#333333]On first boot run your updates - if the updater doesn't appear after a few seconds then go to The Dash (top left), type "soft" and click on the updater - the icon with the "A" in the centre.[/COLOR]
[COLOR=#333333]Once that's done, reboot.[/COLOR]
[COLOR=#333333]When back in the desktop, go to The Dash, type "soft" and this time select "Software & Updates". Go to the "Other..." tab, enable the two Ubuntu Partner/Third Party options, close the dialogue box & click "reload" when the option appears.[/COLOR]
[COLOR=#333333]Go back to The Dash & reopen "Software & Updates" and go to the last Tab (Additional Drivers). Wait a while while it searches... it may take a few minutes. It should show a series of nVidia Drivers to choose from. I normally choose the one with the highest number & most recent updates.[/COLOR]
[COLOR=#333333]Once done, reboot and, hopefully, all should be good.



However, w[/COLOR][COLOR=#333333]hen I go to Additional Drivers, it says "No additional drivers available"
I have run the command "[/COLOR][COLOR=#333333]sudo lshw" 
and it is what it says

[/COLOR][COLOR=#333333]*-display UNCLAIMED[/COLOR]
[COLOR=#333333]description: 3D controller[/COLOR]
[COLOR=#333333]product: GM107M [GeForce GTX 860M][/COLOR]
[COLOR=#333333]vendor: NVIDIA Corporation[/COLOR]
[COLOR=#333333]physical id: 0[/COLOR]
[COLOR=#333333]bus info: pci@0000:01:00.0[/COLOR]
[COLOR=#333333]version: a2[/COLOR]
[COLOR=#333333]width: 64 bits[/COLOR]
[COLOR=#333333]clock: 33MHz[/COLOR]
[COLOR=#333333]capabilities: pm msi pciexpress cap_list[/COLOR]
[COLOR=#333333]configuration: latency=0[/COLOR]
[COLOR=#333333]resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff[/COLOR]
[COLOR=#333333]*-display[/COLOR]
[COLOR=#333333]description: VGA compatible controller[/COLOR]
[COLOR=#333333]product: 4th Gen Core Processor Integrated Graphics Controller[/COLOR]
[COLOR=#333333]vendor: Intel Corporation[/COLOR]
[COLOR=#333333]physical id: 2[/COLOR]
[COLOR=#333333]bus info: pci@0000:00:02.0[/COLOR]
[COLOR=#333333]version: 06[/COLOR]
[COLOR=#333333]width: 64 bits[/COLOR]
[COLOR=#333333]clock: 33MHz[/COLOR]
[COLOR=#333333]capabilities: msi pm vga_controller bus_master cap_list rom[/COLOR]
[COLOR=#333333]configuration: driver=i915 latency=0[/COLOR]
[COLOR=#333333]resources: irq:48 memory:f7400000-f77fffff memory:d0000000-dfffffff


I have also tried the tutorial here
[/COLOR][http://www.yourownlinux.com/2014/04/how-to-install-nvidia-331-67-stable-graphics-drivers-in-linux.html](http://www.yourownlinux.com/2014/04/how-to-install-nvidia-331-67-stable-graphics-drivers-in-linux.html)
[COLOR=#333333]
[/COLOR][COLOR=#333333]When I reboot, I can't access my desktop anymore.I can login but then everything disappears, leaving me only the background and blank screen[/COLOR][COLOR=#333333]

Any help is welcome...

[/COLOR][COLOR=#333333]This is my specs[/COLOR]

[COLOR=#333333]Chassis & Display    Optimus Series: 13.3" Matte Full HD LED IPS Widescreen (1920x1080)[/COLOR]
[COLOR=#333333]Processor (CPU)    Intel® Core&#8482;i7 Quad Core Mobile Processor i7-4810MQ (2.80GHz) 6MB[/COLOR]
[COLOR=#333333]Memory (RAM)    16GB KINGSTON HYPER-X GENESIS 1600MHz SODIMM DDR3 (2 x 8GB)[/COLOR]
[COLOR=#333333]Graphics Card    NVIDIA® GeForce® GTX 860M - 2.0GB DDR5, 640 CUDA Cores - DirectX® 11[/COLOR]
[COLOR=#333333]2nd Graphics Card    NONE[/COLOR]
[COLOR=#333333]Memory - Hard Disk    750GB WD SCORPIO BLACK WD7500BPKX, SATA 6 Gb/s, 16MB CACHE (7200 rpm)[/COLOR]
[COLOR=#333333]mSATA SSD Drive    NONE[/COLOR]
[COLOR=#333333]External DVD/BLU-RAY Drive    NONE[/COLOR]
[COLOR=#333333]Memory Card Reader    Integrated 6 in 1 Card Reader (SD /Mini SD/ SDHC / SDXC / MMC / RSMMC)[/COLOR]
[COLOR=#333333]Thermal Paste    ARCTIC MX-4 EXTREME THERMAL CONDUCTIVITY COMPOUND[/COLOR]
[COLOR=#333333]Sound Card    Intel 2 Channel High Definition Audio + MIC/Headphone Jack[/COLOR]
[COLOR=#333333]Bluetooth & Wireless    GIGABIT LAN & WIRELESS INTEL® AC-7260 (867Mbps, 802.11AC) + BLUETOOTH[/COLOR]
[COLOR=#333333]Wireless Router/HomePlugs    NONE[/COLOR]
[COLOR=#333333]USB Options    3 x USB 3.0 PORTS + 1 x USB 2.0 PORT AS STANDARD[/COLOR]
[COLOR=#333333]Battery    13.3" Optimus Series 6 Cell Lithium Ion Battery (62.16WH)[/COLOR]
[COLOR=#333333]Power Lead & Adaptor    1 x UK Power Lead & 120W AC Adaptor[/COLOR]
[COLOR=#333333]Operating System    NO OPERATING SYSTEM REQUIRED[/COLOR]
[COLOR=#333333]DVD Recovery Media    NO DVD RECOVERY MEDIA REQUIRED[/COLOR]
[COLOR=#333333]Office Software    NO OFFICE SOFTWARE[/COLOR]
[COLOR=#333333]Anti-Virus    NO ANTI-VIRUS SOFTWARE[/COLOR]
[COLOR=#333333]Laptop Cooling Stands    NONE[/COLOR]
[COLOR=#333333]Carry Case    NONE[/COLOR]
[COLOR=#333333]Stand-Alone Monitor    NONE[/COLOR]
[COLOR=#333333]Keyboard Language    13.3" OPTIMUS SERIES BACKLIT UK KEYBOARD[/COLOR]
[COLOR=#333333]Additional Keyboard    NONE[/COLOR]
[COLOR=#333333]Notebook Mouse    INTEGRATED 2 BUTTON TOUCHPAD MOUSE[/COLOR]
[COLOR=#333333]Gaming Mouse Pad    NONE[/COLOR]
[COLOR=#333333]External Speakers    NONE[/COLOR]
[COLOR=#333333]Webcam    INTEGRATED 2.0 MEGAPIXEL WEBCAM
[/COLOR][COLOR=#333333]

Thanks 

Richard

[/COLOR]

---

### Post by grahammechanical on 2014-06-05
How long did you wait? And were you connected to the internet when you opened Additional Drivers? The utility has to search for the drivers. They are not installed with a default installed. So, the utility accesses a server to identify the drivers and then give you an option to install one.

Another way to do this is to open a terminal and run

```
ubuntu-drivers list
```

You may need to run that command with sudo. That will list the proprietary drivers available, if we allow enough time. Now, if we want we can run

```
ubuntu-drivers autoinstall
```

That will install the latest but standard proprietary video driver. Another command, if we are interested is

```
ubuntu-drivers devices
```

That will tell us the name of the graphic adapter and the drivers available for it. If you reboot and do not get to a desktop, it can happen, select Recovery mode from the Grub boot menu. It is under the Advance Options sub-menu and at the recovery menu select Resume. That shoud get you to a desktop using an open source video driver and so bypassing the proprietary video driver that is causing the problems.

Regards.

---

### Post by richard58 on 2014-06-05
Hello,

Yes I was connected. When I run the command 

ubuntu-drivers list

Nothing happen.

Then

ubuntu-drivers autoinstall
it says
No drivers found for automatic installation

And when I run the command 
ubuntu-drivers devices

It does not do anything...

---

### Post by richard58 on 2014-06-06
does anyone have any idea ?

I have spoke with someone 

[COLOR=#333333]"My nVidia chip is an old integrated thing and the highest numbered driver it lists for it is 304.117 which is obviously not recent enough for your nVidia chip.[/COLOR]

[COLOR=#333333]Your nVidia Graphics card will definitely run under Ubuntu (as I mentioned, System76 sell Ubuntu pre-installed laptops with your exact graphics installed) so the solution may be simple but beyond my knowledge, I'm afraid.[/COLOR]

[COLOR=#333333]The fact that the lshw command listed it as UNCLAIMED suggests it can't find a suitable driver but it is being identified correctly."
[/COLOR]

Thanks

---

