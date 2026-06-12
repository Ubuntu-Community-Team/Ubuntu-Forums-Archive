---
title: "Unbootable after installing Ubuntu 12.10"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by durami on 2013-03-11
[FONT=&amp]Hello,

My first goal was to install Ubuntu 12.10 on my old computer to replace Windows XP. I began by installing Ubuntu 12.10 alongside WinXP, just for a test. It worked pretty well. But I did not want to keep WinXP. 

So I installed Ubuntu to replace WinXP. But the installation stops at the window that asks ''_Who Are You_'', the files are copied and the activity indicator stops spinning after a while. I can never get the ''_Welcome window_'' neither the message ''_installation complete_''.

If I shut the power off and I restart, the computer does not boot. Instead I get a black screen with a small dash that turns on and off in the upper left corner. I did make the proper changes to the boot priority in the bios.

However, when I try to reinstall Ubuntu, it recognizes that it is already installed offering me to install Ubuntu 12.10 alongside Ubuntu 12.10 or to replace Ubuntu 12.10! 

What went wrong? Can someone help me?[/FONT] :confused:

[FONT=&amp]
Thank you.[/FONT]

---

### Post by oldfred on 2013-03-11
Did you have a working install on this computer?

Some older computers may not have the resources for full Ubuntu with Unity. I use fallback on my 6 year old system with 1.5GB of RAM and that works well. If less than that then Xubuntu or Lubuntu may be better choices.

---

### Post by durami on 2013-03-11
> **oldfred said:**
> Did you have a working install on this computer?

Some older computers may not have the resources for full Ubuntu with Unity. I use fallback on my 6 year old system with 1.5GB of RAM and that works well. If less than that then Xubuntu or Lubuntu may be better choices.

  The computer on which I am trying to install Ubuntu 12.10 is 10 years old. I upgraded the ram to 3Gb and installed a 500Gb HD. Since the installation of Ubuntu alongside WinXP did work fine, is it possible that something has gone wrong when I tried to install Ubuntu in order to replace WinXP? And if so, what could it be?

---

### Post by oldfred on 2013-03-11
Some really old BIOS cannot boot any boot files beyond 100GB. You usually can use the remaining space for data but the / partition must be fully within the first 137GB.

If BIOS is that old it may not even support a drive that large. Does BIOS show drive?

---

### Post by durami on 2013-03-11
> **oldfred said:**
> Some really old BIOS cannot boot any boot files beyond 100GB. You usually can use the remaining space for data but the / partition must be fully within the first 137GB.

If BIOS is that old it may not even support a drive that large. Does BIOS show drive?

This is interesting but I am not shure if I understand the question: ''Does BIOS show drive?''. Where and what should I read in the BIOS to give a useful answer?

---

### Post by oldfred on 2013-03-11
I assume if install disk sees drive, BIOS has reported it to operating system. But you should go into BIOS and see what it says about drive. Do you have it in IDE or LBA or Large. It may not even have the newer AHCI setting.

---

### Post by ManamiVixen on 2013-03-11
What are your computers's specs? Unity and Ubuntu 12.10 need really fast hardware and a good 3D accelerated card such as an Nvidia 8200 or newer. Older cards are not supported by 12.10 but are under 12.04. Some ATI cards are supported by I don't know which ones. Intel graphics are not supported on 12.10 below and including the i915 chipset. But Intel has released an installer for that driver on Ubuntu 12.10

---

### Post by durami on 2013-03-13
[FONT=&quot]The drive is in IDE.[/FONT] (Please read reply to [FONT=&quot]ManamiVixen)[/FONT]

---

### Post by durami on 2013-03-13
> **ManamiVixen said:**
> What are your computers's specs? Unity and Ubuntu 12.10 need really fast hardware and a good 3D accelerated card such as an Nvidia 8200 or newer. Older cards are not supported by 12.10 but are under 12.04. Some ATI cards are supported by I don't know which ones. Intel graphics are not supported on 12.10 below and including the i915 chipset. But Intel has released an installer for that driver on Ubuntu 12.10

[FONT=&quot]I'll give[/FONT][FONT=&quot] the specs of my computer but first here's what I did:
1 - I reinstalled WinXP
2 - During the process formatting is proposed
3 - I pressed format
4 - I then reinstalled Ubuntu
5 - It is proposed: _alongside_ or _replacing_ WinXP
6 - I pressed _replacing_
7 - The installation seems to have completed successfully and Ubuntu seems to be operating without any problem.

Is the fact that the drive was formated that made the difference? I do not know.

One small problem remains: when asked to choose the language, I selected ' French (ca)'', but Ubuntu was installed  in English!?! Is there a way **_without reinstalling_****_ Ubuntu_** to switch from English to French.

That computer specs: MB Asus P4P800 Deluxe; Graphics Radeon 9600SE; Ram 3Gb; Drive WD 500Gb
DVD drive LG SuperMulti.

Thanks to you all for your help.[/FONT]

---

### Post by oldfred on 2013-03-13
I have not tried changing languages, but in System Settings is Language support which seems to be the settings you need. How you get to System Settings varies based on gui  or DE you are using.

Did you install 64 bit or 32 bit version?

---

### Post by durami on 2013-03-13
> **oldfred said:**
> I have not tried changing languages, but in System Settings is Language support which seems to be the settings you need. How you get to System Settings varies based on gui  or DE you are using.

Did you install 64 bit or 32 bit version?

The 32 bit version.

How do I [COLOR=Navy]mark the thread as[/COLOR] [SOLVED][COLOR=Navy] ? 
[/COLOR]

---

### Post by oldfred on 2013-03-13
I run the 64 bit version on my 6 year old laptop that really has too little RAM only 1.5Gb, but it works just fine.

See my signature.

---

### Post by durami on 2013-03-14
> **oldfred said:**
> I run the 64 bit version on my 6 year old laptop that really has too little RAM only 1.5Gb, but it works just fine.

See my signature.

I did not think the 64 bit version would work with that mother board and graphic card.
Is there a big difference between the two versions. I might try installing the 64 bit version eventually.

---

### Post by diskdude on 2013-04-15
I have the same 'problem' - I had a nice working 64bit version running on a HP Z420 (sweet) however something broke when I tried to update my graphics drivers for a NVIDA NVS 310 and I could not boot passed the splash screen. Playing with it only made things worse so I figured I could use the reinstall option. No such luck - 'reinstall' option always greyed (unavailable) and the next option reads the same unreasonable message **'Install Ubuntu 12.10 alongside Ubuntu 12.10'.** No other option available to no choice :-(. Fresh installation works again.

---

### Post by oldfred on 2013-04-15
Did you have Kernel headers installed. 

I think some others had issues and the headers were not updated like they should with a new kernel. So you have to add new kernel headers and reinstall nVidia again to get nVidia to work with new kernel. 
Can you boot older kernel?

---

