---
title: "Ubuntu Hybrid GPU"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by menges on 2014-07-30
I recentley purchased a Sony Vaio 15F Notebook, How can i make ubuntu use both GPU Intel GPU 4000 Series and Nvidia GeForce 740M Like on windows, when you start a game it uses that Nvidia and when close the game it switches off and uses Intel...I tried Bumblebee but that requires me to restart X org, which requires a Logoff on my computer, Is there any way to swap GPU's without Rebooting

Is ubuntu games able to call out the Nvidia GPU - Like on Bumblebee you use Optirun, but can you make it automatically dependant on the GPU Load

---

### Post by grahammechanical on 2014-07-30
I do not have hybrid graphics. So, I am not talking from experience but from what I have read. The answer to this question, is No.

> [COLOR=#000000]but can you make it automatically dependant on the GPU Load[/COLOR]

This, I think, is the latest information out there. There may be more.

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

The above post was written 4 months before Ubuntu 14.04 was released.

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

As with some other matters, it is best to have the latest Ubuntu because it has the latest Linux hardware enablement stack and the latest proprietary video drivers.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

On 14.04 you will find Nvidia prime tools in the software centre.

Regards.

---

### Post by mastablasta on 2014-07-30
> **menges said:**
> 
Is ubuntu games able to call out the Nvidia GPU - Like on Bumblebee you use Optirun, but can you make it automatically dependant on the GPU Load

NVidia said no you won't. so.... no.

but maybe they will find a way to hack this...

but you can use optirun.
are you saying you need to reboot when using optirun?: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
> 
To run your application with the discrete NVIDIA card run in the terminal: 
[LIST]
[*]$ optirun [options] <application> [application-parameters]
[/LIST]


Since nVidia is needed mostly for games only simply put optirun and options you might need in the game's shortcut.

---

### Post by menges on 2014-07-30
Why does Nvidia say No, and also you must logout of ubuntu and relog on to switch the gpu

---

