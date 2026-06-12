---
title: "Ubuntu 11.04 problem"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by Robbo42 on 2011-08-29
I'm new to linux and therefore to begin with I tried running Ubuntu 11.04 from the live CD and this worked fine.

I therefore installed this along side my current operating system which is windows 7.

The install seemed to be successful and now when I boot I get the choice  of which operating system to use. If I select Ubuntu it is either  freezing on a purple/pink screen or I'm getting a flashing cursor in the  top left on a black screen. I've also seen the caps lock flashing but  not all of the time.

I tried removing Ubuntu and reinstalling but getting the same problem.[LEFT][COLOR=#000000]
As it ran ok from the live CD I'm confused why it wouldn't run from the hard drive installation.

Any ideas ?

Cheers

Robbo42
[/COLOR][/LEFT]

---

### Post by realzippy on 2011-08-29
When you are in grub choosing OS,try 
ubuntu..kernel... (recovery mode).. 
select => failsafe graphics

..and Welcome!

---

### Post by Rubi1200 on 2011-08-29
Hi and welcome to the forums Robbo42 :-)

Please post the specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by jerrrys on 2011-08-29
this purple/pink screen has come up before.  there are solutions out there, but since your new i would suggest just installing 10.10 for now.  it should work out of the box.  in about 2 months 11.10 will be out and this screen problem should be resolved.  then would be a good time to move up.

---

### Post by Robbo42 on 2011-08-29
Thanks for all the replies !!

The failsafe graphics option seems to have worked.

I'm now however getting the following message regarding drivers.

No proprietary drivers are in use on this system.

The following option has a green mark next to it :- 

NVIDIA accelerated graphics driver (version 173)

3D accelerated proprietary graphics drivers for NVIDIA cards are required if you want to run Unity.

The message says that it is activated but not currently in use.

---

### Post by realzippy on 2011-08-29
So you have installed the nvidia-173 driver?

---

### Post by Robbo42 on 2011-08-29
> **realzippy said:**
> So you have installed the nvidia-173 driver?

It is activated but currently not in use ? Would this be because I booted in failsafe graphics mode and will I have to take this option every time I boot ?

---

### Post by realzippy on 2011-08-29
Again,
**Did** you install the driver?
It cannot be activated/not in use if nobody installed it formerly..

---

### Post by BlacqWolf on 2011-08-29
Hello, and welcome to Ubuntu!

Since failsafe graphics have worked, and you appear to have an nVidia graphics card, I recommend you download and install the latest proprietary driver, either through the "Additional Drivers" application or download it directly through the [nVidia website]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). The default Nouveau driver used for nVidia systems has a few problems with some cards. Since you're new to Ubuntu and Linux, I recommend you try "Additional Drivers" first, and then try the nVidia site as a new user may find installing it a bit hard or intimidating at first (but don't worry, when you get used to it, it's easy!). If you happen to need to install it manually from a package downloaded from the website, I'll be happy to help you with that.

Also, so me and others can help you more easily, may I ask that you tell us which video card you have?

---

### Post by Hakunka-Matata on 2011-08-29
installed graphics details: Open Terminal, run

```
sudo lshw -C display
```


post output

---

### Post by Robbo42 on 2011-08-29
When I go into the "Additional Drivers" application I get the following :-

No proprietary drivers are in use on this system.

Proprietary drivers do not have public source code that Ubuntu developers are free to modify. Security updates and corrections depend solely on the responsiveness of the manufacturer. Ubuntu cannot fix or improve these drivers.

- NVIDIA accelerated graphics driver (version 173)     (this has a green mark next to it)
- Firmware for DVB cards
- NVIDIA accelerated graphics driver (version current) [Recommended]

the green mark indicated "The Driver is activated but currently not in use"

The only option I have for this is to remove.

I haven't manually installed any drivers at all. 

I assume I should select the recommended option and activate (does it need downloading also ?)

I believe my graphics card is Nvidia Geforce 9600M GT

---

### Post by Robbo42 on 2011-08-29
> **Hakunka-Matata said:**
> installed graphics details: Open Terminal, run

```
sudo lshw -C display
```
post output

 *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9600M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128)
robbo@robbo-Qosmio-F50:~$

---

### Post by realzippy on 2011-08-29
remove it.(although it can't be there if nobody formerly installed it.)
Then update your system,run:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Then reboot,1rst test normal mode,if no-go,recovery.
When rebooted,install the driver (additional tool).
Then reboot again.

---

### Post by Robbo42 on 2011-08-29
> **realzippy said:**
> remove it.(although it can't be there if nobody formerly installed it.)
Then update your system,run:

```
sudo apt-get update
``````
sudo apt-get upgrade
```Then reboot,1rst test normal mode,if no-go,recovery.
When rebooted,install the driver (additional tool).
Then reboot again.

Ok, removed driver, ran both commands. On reboot normal didn't work so used recovery.

Installed recommended driver, reboot and normal still didn't work. Had to use recovery again

---

### Post by wackenroader on 2011-08-29
Do you run the command: sudo nvidia-xconfig before installation of the recommended driver?

---

### Post by Robbo42 on 2011-08-29
> **wackenroader said:**
> Do you run the command: sudo nvidia-xconfig before installation of the recommended driver?

Just tried a 2nd reboot just in case and it booted fine in normal mode :guitar:
Thanks for all your help guys. Looking forward to getting to learn the system.

---

### Post by BlacqWolf on 2011-08-29
Great! I'm glad that you could get it to work. I hope you enjoy Ubuntu.

---

### Post by Johnb0y on 2011-08-29
p.s. dont forget to mark as solved please? thanks

*just under thread tools ;)

---

