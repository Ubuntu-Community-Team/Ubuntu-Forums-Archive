---
title: "Wubi Kubuntu 9.10 not booting up after Amarok media codecs installation"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by manishsk on 2009-11-21
I am not sure where toopen this thread but this seems a better category.

I am using Toshiba Laptop with AMD Turion, with Vista installed.
I decided use Kubuntu 9.10 using the wubi installer. things worked well till I got my ATI drivers. But when I started Amarok it suggested me to install all the mp3/DVD codecs etc for the media files. After that I am not able to boot my kubuntu. 

Kubuntu just hangs up at start. After some time screen goes blank. And CAPS lock LED starts blinking.

CTRL+ALT+F1 or CTRL+ALT+F8 doesn't work. Kubuntu 9.04 used to work well.

Please let me know if any of faced such problem. I need to re-install my kubunu but I am not sure I will face this problem again. I did updated it with latest security and bug fix update but looks like Amrok suggetion killed it.

Thanks,
Manish

---

### Post by manishsk on 2009-11-30
I am able to solve this issue.

It basically  not the media drivers issue but a issue with ATI drivers.

Please refer below thread for solution. i hope it works. Working so far, I am able to boot well with this solution applied.

[http://ubuntuforums.org/showthread.php?t=1315199]("http://ubuntuforums.org/showthread.php?t=1315199")

```
   
sudo aticonfig --initial -f
sudo aticonfig --acpi-services=off

```

The acpi-services was bugging me. But I don't know how does actually helps my system to solve it. what changes it does to my system in background.

Do let me know if you have any comments or ideas...

---

