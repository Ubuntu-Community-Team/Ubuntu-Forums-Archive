---
title: "Upgraded Everything except GRUB?"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by X1R1 on 2009-11-17
hello guys, after I upgraded everything works fine except for 2 things, one being the brightness (on an acer aspire 5810tz). I got it fixed with the following line in jaunty:

```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

However, now this command does not work anymore, when I run it now I get the following output:

```
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```

So I started searching and find out that you need to pass some line to the kernel at boot (I dont know the exact line, I THINK its noapic, if im wrong point it out).

Thing is its supposed that grub2 comes with this upgrade, but when I type:

```
x1r1@ACER5810TZ:/$ grub-install -v
grub-install (GNU GRUB 0.97)

```

So, according to that command grub is version 0.97 and not version 2. So I cant use the fix provided on this forums because the file structure changed with this version.

The second problem is the battery life but I wont discuss it here because I prefer to have 2 separate threads in order to mantain them organized.

So bottom line, either of this 2 options:
-How do I fix the brightness problem in this scenario without screwing up my current boot?
-How do I upgrade this grub to the new one without messing up current settings? the goal of the upgrade is to apply the brightness fix that I found on the forums somewhere.

Sorry for the long post but I wanted to make things clear :popcorn:

---

### Post by It-Alien on 2009-11-17
GRUB2 is not installed on upgrades: only fresh installations get GRUB2; I have read that this is due to the risks of a conversion from GRUB to GRUB2

---

### Post by X1R1 on 2009-11-17
it-alien

thanks for the clarification, how can I fix this brightness issue then? If GRUB2 is a dangerous move then I would prefer a fix that doesnt involve converting to GRUB2.

---

### Post by slakkie on 2009-11-17
For your brightness issue, you might want to have a look here: 
[http://ubuntuforums.org/showthread.php?t=1308041](http://ubuntuforums.org/showthread.php?t=1308041)

And you can upgrade to grub2 from your legacy-grub. Although if you wait a release it will be done for you iirc.

---

### Post by X1R1 on 2009-11-17
Thank you, solution was at this post:

[http://ubuntuforums.org/showthread.php?t=1217421]("http://ubuntuforums.org/showthread.php?t=1217421")

I found it navigating through the post you pointed to. Thanks a lot!

---

