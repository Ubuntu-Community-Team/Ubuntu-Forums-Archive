---
title: "Dell C640 screen brightness &lt;not supported&gt;"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bubba_169 on 2008-10-04
After upgrading to Intrepid I have noticed that my brightness hotkeys no longer work. The strange thing is there seems to be no way at all to change the brightness once ubuntu has loaded, during boot the keys work fine which I assume means the problem is in software.

After digging around on google I found references to changing the /proc/acpi/video/VID/LCD/brightness but whenever I try the command:

```
root@simon-laptop:~# echo -n 87 > /proc/acpi/video/VID/LCD/brightness
bash: echo: write error: Invalid argument

```

Viewing this file in a text editor shows the only content is the line "<not supported>".

I know this worked fine in hardy and below so any ideas where I should be looking to configure this correctly and should I post a bug report on launchpad?

---

### Post by rekado on 2008-10-06
Do you have any other folders in /proc/acpi/video?
Try the same command on other brightness files in the subdirectories.

---

### Post by bubba_169 on 2008-10-06
Come to mention it I think I did see a CRT in video/VID/ folder? Might try that when I get home... It is a laptop that Im working on though so you'd think it was LCD?

---

### Post by rekado on 2008-10-06
Well, I've got 

/proc/acpi/video/IGD/LCD/brightness
/proc/acpi/video/IGD/TV/brightness
/proc/acpi/video/IGD/CRT/brightness
/proc/acpi/video/VGA/DVIA/brightness
/proc/acpi/video/VGA/DVI/brightness
/proc/acpi/video/VGA/LCD/brightness
/proc/acpi/video/VGA/CRT/brightness

of which all but /proc/acpi/video/IGD/LCD/brightness are <not supported>. Only the one mentioned first contains some numbers and the current brightness setting. But maybe I'm not be right person to help you here as my brightness control doesn't work...

---

### Post by bubba_169 on 2008-10-06
I only seem to have the one VID folder but nothing in the CRT folder seems relevant. In the VID/LCD/info however I've found something interesting...

```
device_id: 0x0110
type: UNKNOWN
known by bios: no

```

I've also tried looking for the screens and graphics app to try configure something correctly but it seems that was removed recently and its up to X to autodetect everything. I think thats where my problem lies...

---

### Post by rekado on 2008-10-07
> **bubba_169 said:**
> I only seem to have the one VID folder but nothing in the CRT folder seems relevant. In the VID/LCD/info however I've found something interesting...

```
device_id: 0x0110
type: UNKNOWN
known by bios: no

```


Now that looks very similar to my problem as described here:
[http://ubuntuforums.org/showthread.php?t=922401](http://ubuntuforums.org/showthread.php?t=922401)

Maybe you could try to apply the mentioned workarounds (which had no effect on my machine) and see if they work for you. If they don't it might be the same bug.

Could you try booting with the boot-option *acpi=off* and see if the brightness control works?

---

### Post by Ric_NYC on 2008-10-08
The same thing is happenig to my Dell Latitude C610.
There's another bug... When I disconnect the power cord the brightness stays the same.
No brightness control at all.


> **bubba_169 said:**
> After upgrading to Intrepid I have noticed that my brightness hotkeys no longer work. The strange thing is there seems to be no way at all to change the brightness once ubuntu has loaded, during boot the keys work fine which I assume means the problem is in software.

After digging around on google I found references to changing the /proc/acpi/video/VID/LCD/brightness but whenever I try the command:

```
root@simon-laptop:~# echo -n 87 > /proc/acpi/video/VID/LCD/brightness
bash: echo: write error: Invalid argument

```

Viewing this file in a text editor shows the only content is the line "<not supported>".

I know this worked fine in hardy and below so any ideas where I should be looking to configure this correctly and should I post a bug report on launchpad?

---

