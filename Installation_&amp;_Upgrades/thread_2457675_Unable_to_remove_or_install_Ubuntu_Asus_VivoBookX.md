---
title: "Unable to remove or install Ubuntu: Asus VivoBookX"
date: 2021-02-06
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2021-02-06
Last year I bought an Asus VivoBookX. 

As described in this thread,   [https://ubuntuforums.org/showthread.php?t=2446590](https://ubuntuforums.org/showthread.php?t=2446590)         which also links to another, it did not accept Ubuntu installation well. Although I've successfully installed it on our previous machines, I quickly got beyond my understanding/experience level, and have only used this Asus on Windows, which was not the intention.

It was a mistake buying it, I misunderstood its specifications, and would do better restoring it to its original Windows state, selling, and buying something else, hopefully to succeed better. At the time I spotted accounts of other Asus Vivobooks not taking well to Ubuntu, I don't know how common this is.  There were solutions kindly suggested, but in the end they involved going well out of my depth.

At present, Ubuntu shows as installed, but when chosen in the opening menu, stalls.

If I insert the USB drive & choose "Try Ubuntu" it hits the black screen. If I choose "Install Ubuntu" it gets as far as keyboard choice, and  either stalls completely or produces the error message screen endlessly scrolling lines too rapidly to read.

I was hoping to move it as far as "uninstall Ubuntu". Otherwise it's back to the local Windows engineer, who doesn't work with Ubuntu but would happily charge me to restore it to its original state. If there's a work-round possible for my ability level I'll be grateful.

I have to add that while I prefer Ubuntu to Windows nearly every time, working with computers for prolonged periods still tends to trigger my Chronic Fatigue, so sometimes I may reply after a delay. 
Thanks.

---

### Post by TheFu on 2021-02-06
I have an Asus Vivobook.
```
Machine:   Device: laptop System: ASUSTeK product: X510UAR v: 1.0 serial: N/A
           Mobo: ASUSTeK model: X510UAR v: 1.0 serial: N/A
           UEFI: American Megatrends v: X510UAR.310 date: 04/19/2019
```
Can't recall any specific issue with it - well - except the fingerprint reader doesn't have a driver. Everything else has worked.

We don't know your ability, so it is impossible to say what is or isn't beyond it.
Before getting too far, we need FACTS about the system.  Gather those by logging into the system (text is fine), and running **inxi -Fz |tee /tmp/sys.log**.  Then post the output from that command back here.  If you don't have a GUI, I'd use normal command redirection to write the output to a file, copy that file some where you can use a different computer to post here.  My example above will do that - the file will be /tmp/sys.log.

If inxi isn't installed already - just install it.  **sudo apt install inxi**

Those facts will help us. Would be nice if, when posted, you wrapped them in "code tags" - [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)  explains how to do that.

---

### Post by Richard_York on 2021-02-11
Thanks for this reply. 
I didn't post the system spec in my OP here as it's at the top of the thread I linked to. 

Since my post #1 in this thread, the machine appeared to have changed its mind - it opened perfectly in Ubuntu 20, updated itself massively, (I'd not tried it for several months), behaved nicely.  I didn't get to try your inxi command that time. Since then it's been inconsistent. Twice it opened well, once quickly, once very slowly, today not at all. On repeated tries it sometimes fails to get as far as displaying the initial "Ubuntu" logo with progress wheel, sometimes gets as far as accepting my login password then stalls, sometimes on a mauve screen, sometimes black, sometimes dark grey. 

To save wading through my earlier threads, this is more or less what happened when I first installed 20.04  dual boot with Windows, when I first bought the laptop.

So my plan to try the inxi line seems unavailable, as I take it Ineed to be logged into Ubuntu before I can run it.

My ability level - I can blindly follow instructions quite well. I have now installed Ubuntu 5 or 6 times since I started, from 14LTS to 18LTS but when it requires decisions based on knowledge of what I'm doing I'm quickly out of my depth.

I'm hoping that if I try starting it every now &then it will catch one of these times, so I can try your command line, but otherwise appear to be stuck.

Thanks again for help.

---

### Post by Richard_York on 2021-02-14
Progress!
 Since Ubuntu kept stalling I tried with a different USB installer, and it's installed ubuntu 20.04. Given its history I don't trust it not to stall again soon, (see earlier threads), as it has done this before. 
And I realise I picked the wrong one of the various French/Canadian options for the keyboard... something the vendor forgot to mention... and now can't get  @, so I will need to reinstall anyway, and choose differently.
But I was able to install and run inxi for you. Here's the result:
[HTML]$ inxi -Fz|tee /tmp/sys.log
 System:
   Kernel: 5.8.0-43-generic x86_64 bits: 64 Desktop: Gnome 3.36.1  
   Distro: Ubuntu 20.04 LTS (Focal Fossa)  
 Machine:
   Type: Laptop System: ASUSTeK product: X541UAK v: 1.0 serial: <filter>  
   Mobo: ASUSTeK model: X541UAK v: 1.0 serial: <filter>  
   UEFI: American Megatrends v: X541UAK.311 date: 03/14/2018  
 Battery:
   ID-1: BAT0 charge: 34.3 Wh condition: 34.5/34.6 Wh (100%)  
 CPU:
   Topology: Dual Core model: Intel Core i3-6006U bits: 64 type: MT MCP  
   L2 cache: 3072 KiB 
   Speed: 500 MHz min/max: 400/2000 MHz Core speeds (MHz): 1: 500 2: 500  
   3: 500 4: 501  
 Graphics:
   Device-1: Intel Skylake GT2 [HD Graphics 520] driver: i915 v: kernel  
   Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1366x768~60Hz  
   OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2) v: 4.6 Mesa 20.0.4  
 Audio:
   Device-1: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel  
   Sound Server: ALSA v: k5.8.0-43-generic  
 Network:
   Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169  
   IF: enp2s0f2 state: down mac: <filter>  
   Device-2: Realtek RTL8821AE 802.11ac PCIe Wireless Network Adapter  
   driver: rtl8821ae  
   IF: wlp3s0 state: up mac: <filter>  
 Drives:
   Local Storage: total: 931.51 GiB used: 7.80 GiB (0.8%)  
   ID-1: /dev/sda vendor: Seagate model: ST1000LM035-1RK172 size: 931.51 GiB  
 Partition:
   ID-1: / size: 767.62 GiB used: 7.77 GiB (1.0%) fs: ext4 dev: /dev/sda5  
 Sensors:
   System Temperatures: cpu: 34.0 C mobo: N/A  
   Fan Speeds (RPM): cpu: 1900  
 Info:
   Processes: 206 Uptime: 12m Memory: 7.66 GiB used: 839.8 MiB (10.7%)  
   Shell: bash inxi: 3.0.38  
  p { margin-bottom: 0.25cm; line-height: 115% } 
[/HTML]
I hope this helps.

Thanks again.

---

### Post by CelticWarrior on 2021-02-14
You can add/remove different keyboard layouts anytime. There's absolutely no reason to reinstall due to that.

---

### Post by Richard_York on 2021-02-14
That is good to know, thanks. Sadly, after starting nicely that once, it is inconsistent again - one stall on blank grey screen,  then on restarting,  taking 10 min to produce a screen full of error messages, all the same as in my earlier thread as far as I can see.

The earlier error message was:[HTML][  323.846114 ]  pcireport 0000:001c – 5: AER: pc1e Bus Error :  severity=Corrected  type=Physical Layer. (Receiver ID) device  [8086:9d15] error status/mask=00000001/ 00002000 [ 0] RxErr
[/HTML]

---

### Post by CelticWarrior on 2021-02-15
[https://itsfoss.com/pcie-bus-error-severity-corrected/](https://itsfoss.com/pcie-bus-error-severity-corrected/)

---

### Post by Richard_York on 2021-02-15
Thanks, CelticWarrior, that looks truly useful.

 It appears so thoroughly written that I can blindly follow the steps.  That's good, because I get lost when I have to take decisions not mentioned in the script.
Is this impression right?

A large part of me is still inclined to sell the machine on before very long. You were right in your comment when I bought it that the spec wasn't as good as I thought. But if I can get it working with Ubuntu that would be far better than things are at present.

---

### Post by TheFu on 2021-02-15
> **CelticWarrior said:**
> [https://itsfoss.com/pcie-bus-error-severity-corrected/](https://itsfoss.com/pcie-bus-error-severity-corrected/)

The link claims it is a fix. Appears to just silence the reporting of issues, not fix anything.

---

### Post by CelticWarrior on 2021-02-15
Indeed.

But here [https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id) there's an explanation and several different "solutions".

It boils down to [COLOR=#242729][FONT=Arial]PCI Express native power management. It can simply be disabled in UEFI or with the '[/FONT][/COLOR][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#242729]pcie_aspm=off' Grub parameter resulting in increased power consumption whereas '[/COLOR][/FONT][COLOR=#242729][FONT=Consolas]pci=noaer' disables error reporting but should not impact battery life.[/FONT][/COLOR]

---

### Post by Richard_York on 2021-02-15
Yes, I noted that, on further reading.
 It rather makes me more inclined to swap machines for one that likes Ubuntu better. (There are other aspects of this machine which I find don't suit me as well as hoped. I'll check on this community's "Hardware" threads before buying this time, rather than asking a non-Ubuntu friend!)

So going off on a logical tangent, does this [https://helpdeskgeek.com/linux-tips/how-to-uninstall-ubuntu-in-a-windows-10-dual-boot-system/](https://helpdeskgeek.com/linux-tips/how-to-uninstall-ubuntu-in-a-windows-10-dual-boot-system/)    look sensible and workable to you?  It would save me having to spend yet more on the local computer fixer.
But it would be a pity to jump in and find myself way out of my depth.

---

### Post by Richard_York on 2021-02-16
> **CelticWarrior said:**
> Indeed.

But here [https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id) there's an explanation and several different "solutions".

It boils down to [COLOR=#242729][FONT=Arial]PCI Express native power management. It can simply be disabled in UEFI or with the '[/FONT][/COLOR][FONT=Consolas][COLOR=#242729]pcie_aspm=off' Grub parameter resulting in increased power consumption whereas '[/COLOR][/FONT][COLOR=#242729][FONT=Consolas]pci=noaer' disables error reporting but should not impact battery life.[/FONT][/COLOR]

I appreciate your posting the link you did for my benefit - I can follow that, and not this one! Thank you.

While awaiting a comment on my link on how to remove Ubuntu, I find I'm more than ever inclined to change to a different laptop - as I said, this one has other issues largely irrelevant here.
It would be interesting to try Xubuntu meanwhile, while I've still got it, if I can, just to compare. I guess that it would make more sense to carry out this error message correction procedure once the Xubuntu is installed, if it does, assuming that the installation would wipe whatever I'd achieved by following your link. Is that right?

---

