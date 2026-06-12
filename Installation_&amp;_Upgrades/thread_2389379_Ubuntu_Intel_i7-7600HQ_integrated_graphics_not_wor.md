---
title: "Ubuntu Intel i7-7600HQ integrated graphics not working properly on 17.10"
date: 2018-04-16
forum: Installation &amp; Upgrades
---

### Post by emy149 on 2018-04-16
Notebook configuration:
Asus ROG G551VW
Intel Core i7-7600HQ
nVidia GeForce GTX960M

I know there has always been issues with the Linux kernel on this specific configuration. I have found lots of threads regarding boot problems and graphics performance issues, touchpad not working and so on. But none related to Intel's HD graphics driver which I have some problems with.

So, I only manged to install Ubuntu 17.10 on my machine in the following way:
[LIST]
[*]Add 'nomodeset' parameter when booting from USB
[*]Install Ubuntu
[*]Boot it up, again using 'nomodeset'
[*]Install nVidia proprietary drivers
[*]Restart and boot without 'nomodeset' (booting process goes smooth from this point on)
[/LIST]

The first thing I noticed after a few hours of use is that the processor stays at higher temperatures (about 3-5 degrees more) than in Windows 10.
After installing nVidia drivers I have the nvidia icon on the taskbar where I have the option to choose between nVidia or Intel's graphics (intel for power saving). I don't do gaming on Linux so I would like that power economy because my notebook stays on only for 30-40 minutes using the nVidia GPU. If I switch to Intel GPU the whole system becomes pretty unstable. It doesn't boot up everytime, when it boots up after a few minutes the fan starts spinning like crazy and I don't see any significant power saving. Is there some hope that I could solve this problems somehow and use Inte's GPU or should I just surrender and continue to use Windows until I'll buy another notebook?

Is there really a reason why this configuration is so buggy?

Also, Is there a way to solve that 'nomodeset' stuff? So I could boot linux from USB without using it?

---

