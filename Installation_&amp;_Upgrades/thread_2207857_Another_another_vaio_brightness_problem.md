---
title: "Another another vaio brightness problem"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by omid55 on 2014-02-25
Dear Friends,

I have a VPCS116FG vaio laptop and I installed ubuntu 12.04.4 on it. But my brightness is always at the maximum. Ichecked and searched many forums but unfortunately none of them worked for me including this way:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

and many more ways but no luck so far.
I think there might be a power control that all the time never let driver change the screen brightness.
By the way, My Fn+bright keys are working and they do not change the actual brightness and it is all the time at the maximum.
Could any one help me with this situation that my eyes are kind of hurting so much right now???

---

### Post by varunendra on 2014-02-27
Welcome to the fourms omid55!

> By the way, My Fn+bright **keys are working** and they do not change the actual brightness and it is all the time at the maximum.
Do you mean the keys are NOT working? Because if the brightness is not changed, how do you consider them 'working'?

Please open a terminal (Ctrl-Alt-T), and post back the outputs of following commands/script -
```
lsb_release -cd
uname -mr
cat /proc/cmdline
lsmod
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

