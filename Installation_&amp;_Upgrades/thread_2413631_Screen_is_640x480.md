---
title: "Screen is 640x480"
date: 2019-02-28
forum: Installation &amp; Upgrades
---

### Post by asearle on 2019-02-28
Hallo everyone,

I am currently installing Lubuntu on an older laptop and am having trouble with the display resolution.

When I boot from the install CD the display is not recognised but the resolution is (correctly) set to 1024x768. That's fine.

However, after installation the resolution/display detected is "640x480 (unknown) The X.Org Foundation" with no other option available to be selected.

Can anyone help me here? Can I install other tools or drivers to get the resolution that I need (and which is obviously technically possible)?

Many thanks for any tips that you can give me.

Yours,
Alan

PS: I am using 18.04.2

---

### Post by mastablasta on 2019-02-28
what is the GPU?

---

### Post by asearle on 2019-02-28
CPU is "Pentium Dual CPU T2390, 1.86 GHz."

PS: I know what you were thinking: Some AMD processors have issues with the graphics.

PPS: Is there a way for me to see/query which display processor is being used?

---

### Post by Bashing-om on 2019-02-28
asearle; Hey hey -

> 
PPS: Is there a way for me to see/query which display processor is being used?

Post back:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

shows what we have to work with - then we see where we go from there.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by asearle on 2019-03-04
Many thanks for the syntax.

I checked out the display which seems to be the following ...

VGA Compatible Controller
Product: 771/671 PCIE VGA
Manufacturer: Silicon Integrated Systems

I searched on these key words and there seemed to be a lot of discussion about the problem but no clear resolution.

The strange thing is that an install-boot gets the resolution right but my final install only gives minimum resolution. That is weird.

Any thoughts?

Many thanks,
Alan

---

### Post by asearle on 2019-03-04
The more I search, the more I seem to come across people cursing SIS-graphics adapters (that this computer has).

This has got me worried: Does anyone have an idea on this point?

Thanks,
Alan

---

### Post by CatKiller on 2019-03-04
> **asearle said:**
> The more I search, the more I seem to come across people cursing SIS-graphics adapters (that this computer has).
And correctly so. The manufacturer has never bothered to support it. What support there is comes from volunteers reverse-engineering it, which falls off from the undetectable level of usage of SIS.

You can still use xorg.conf to configure the resolution. You won't have any acceleration. You won't have modern niceties like auto-detection.

The laptop would have been terrible when it was new. It's no less terrible now.

---

### Post by asearle on 2019-03-08
Hi again everyone,

It looks like I have a bit of a duff graphics card in this one.

But aside from that, it would be interesting/important to know why on live boot the resolution is correct but after installing (Lubuntu 18.04) only minimal resolution is available.

The fact that live boot produces the correct resolution shows me that this setting must be available. So how do I force/prompt the installed system to reproduce those settings?  Here I am talking about exactly the same system i.e. the live boot is the source from which I installed.

Any tips here would be a great help and I am sure of general interest.

Many thanks,
Alan

---

### Post by CatKiller on 2019-03-08
> **asearle said:**
> But aside from that, it would be interesting/important to know why on live boot the resolution is correct but after installing (Lubuntu 18.04) only minimal resolution is available.

The screen resolution has to be explicitly set. The BIOS sets it to 640×480 because BIOS is ancient. The installer takes a punt, if it can't detect a higher resolution, at 1024×768, since that's generally produceable on anything and 640×480 is horrible. If 1024×768 is actually the native resolution of your screen, that's simply a coincidence and your screen is ancient.

> So how do I force/prompt the installed system to reproduce those settings?  Here I am talking about exactly the same system i.e. the live boot is the source from which I installed.

The modern (well, it was invented in 1994) way to determine the capabilities of a display is to use EDID. The monitor simply says which resolutions it can do. Simple.

Your system isn't using EDID, for some reason. Either the display doesn't provide it, or the GPU ignores it. In your case, the latter is certainly true, but the former may be as well.

However, there is a text file that can be used to supplement the information from the display and the GPU - /etc/X11/xorg.conf. This used to be the only way to do this, but since modern hardware has become more widespread and auto-detection has become more robust it is no longer included by default. It will be used if it's there, though.

A skeletal xorg.conf will look something like

```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

In the Monitor section you can put HorizSync and VertRefresh entries for the frequency ranges your monitor supports. You can get values for those entries either by using *read-edid* (if your display provides EDID information) or from your display's manual. Then X should be able to auto-configure resolutions that fit in those ranges.

---

### Post by asearle on 2019-03-09
Yippee: I fixed the problem by doing the following ...

The xorg.conf does not exist by default any more. You CAN create one though.

Boot into recovery mode and select Root Shell. Then run:

```
X -configure
```

Then:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

Reboot and you can edit the new Xorg.conf. But I didn't need to because reasonable graphics (1024x768) were already available.

---

### Post by Bashing-om on 2019-03-09
asearle; Outstanding :)

> 
Yippee: I fixed the problem by doing the following ...


You do good work. Pleased that you provided your solution for the edification of others.

Please now mark this thread solved:
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

