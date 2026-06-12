---
title: "Screen text appears &quot;stretched&quot; after 22.04 LTS upgrade"
date: 2022-08-25
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2022-08-25
I just successfully upgraded to 22.04 LTS but for some reason my 
screen text is displaying "stretched"  for a lack of a better word.
I tried changing resolution under settings - appearance - resolution
and went from 1280 x 1024 to 1024 x 768 and that made a difference.

Is this where I should be trying to get it to look like it was under 20.04 LTS
or is there a different area to make the appropriate adjustments?

thanks....

---

### Post by bobunderwood99 on 2022-08-26
Hello,

Verify the native resolution of your monitor and set the computer resolution to that.

---

### Post by ozark_hillbilly on 2022-08-27
hello bob,

my LG display is 1440 x 990.
My options under Settings > Display are:
1024 x 768
1280 x 1024
800 x 600

Is there a way to manually enter the resolution?

---

### Post by ajgreeny on 2022-08-27
Show us the output of terminal command ***xrandr*** which will list all the resolutions available for your hardware.
If you are using Ubuntu with the default gnome DE you may be using wayland and xrandr will not work in wayland as it needs an x-session. 
For wayland graphics use ***wlr-randr*** instead which you will have to install first.

More detail of your hardware will also possibly give more clues to a solution for you so also show us the output of command ***inxi -Fzx***

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by bobunderwood99 on 2022-08-28
> **ozark_hillbilly said:**
> hello bob,

my LG display is 1440 x 990.
My options under Settings > Display are:
1024 x 768
1280 x 1024
800 x 600

Is there a way to manually enter the resolution?

Yes. If using Wayland see 
[https://davejansen.com/add-custom-resolution-and-refresh-rate-when-using-wayland-gnome/](https://davejansen.com/add-custom-resolution-and-refresh-rate-when-using-wayland-gnome/) 

If X11 see
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by ajgreeny on 2022-08-29
Bob, your first link is not working and goes to a 
[B]500- Internal server error.
[/B]
Can you repair it for us please

---

### Post by bobunderwood99 on 2022-08-29
It's not the link. Whois.com reports

Domain: davejansen.com

Registrar: NameCheap, Inc.

Registered On: 2004-06-17

Expires On: 2023-06-17

**Updated On: 2022-08-29**

I would expect it to be back up soon.
----
As of 7:10 PM PDT it's up.

---

### Post by ajgreeny on 2022-08-30
Many thanks.

---

### Post by ozark_hillbilly on 2022-09-02
ajgreeny,

```

ed@ed-G41MT-S2PT:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected primary 1280x1024+0+0 0mm x 0mm
   1280x1024      0.00* 
   1024x768       0.00  
   800x600        0.00  
   640x480        0.00  

```

---

