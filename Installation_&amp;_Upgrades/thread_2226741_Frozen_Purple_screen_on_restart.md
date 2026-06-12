---
title: "Frozen Purple screen on restart"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by Jerry_Price on 2014-05-28
I am new to Ubuntu and I am trying to install Ubuntu 14.04LTS onto a Toshiba Tecra M5 T2600 @2.16 Ghz with 3G Ram with Nvidia Quadro NVS110M. 
All appeared to go well and I was asked to restart but on restarting it freezes after I enter my password. 
Twice now whilst trying to restart I have managed to get it to "recovery mode" (not quite sure how) and it has loaded Ubuntu successfully. It mentioned that in recovery mode certain graphics would not work but that a "full Graphic reboot was required"?. 
On shutting down normally and restarting it returns to the frozen Purple screen. On this last occasion after some time a black screen appeared with:
[107.103680] nouveau  E [GPU lockup - switching to software fbcom
I have logged in and I'm sitting at a flashing prompt but not sure what I should do next. After some time it displayed a message ........ corrupted low memory a number of times......... and shut it self down.
I have read through "sticky note 1" but am somewhat lost on what to do next
Appreciate any help

---

### Post by sudodus on 2014-05-29
I think you can try a boot option. See these link (maybe the simplest thing would be to reinstall with one or more boot options, for example ***nomodeset***.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Later on it might work to install an nvidia proprietary driver for the graphics.

---

### Post by Jerry_Price on 2014-05-29
Thanks for the reply Sudodus
Not sure I understand the reboot options, I am working from an installed version of ubuntu and not from a disk.... and excuse me if I have missed your point. 
I have Ubuntu up and running in recovery mode. From forums etc it appears that Nvidia graphics cards can cause the "freeze" problem. I have a NVidia Quadro NVS 110M graphics car and Ubuntu is using a generic Nouveau driver and the alternative drivers listed do not match my NVS 110M card. I and have found a proprietary driver for the NVS 110M card for Linux and have downloaded it. 
It is in a xxx.run format.
1 How do I install it
2 If I do install it will the next Ubuntu software update replace it again

Cheers

---

### Post by sudodus on 2014-05-30
A. See this link

[https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

particularly 
> 8. **GRUB_CMDLINE_LINUX **

[LIST]
[*]Entries  on this line are added to the end of the 'linux' command line (GRUB  legacy's "kernel" line) for both normal and recovery modes. It is used  to pass options to the kernel. 
[/LIST]

9. **GRUB_CMDLINE_LINUX_DEFAULT*****=***"quiet splash" 

[LIST]
[*]This  line imports any entries to the end of the 'linux' line (GRUB legacy's  "kernel" line). The entries are appended to the end of the normal mode  only.
[LIST]
[*]To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 
[/LIST]
        
[/LIST]

So edit and save the file **/etc/default/grub** and run ```
sudo update-grub
``` to incorporate the changes into the GRUB 2 startup.

B. You can start trying to use the nvidia proprietary drivers that come with Ubuntu. Start a terminal window. Type the following and TAB to get a list of available nvidia drivers. In Ubuntu 12.04 LTS I get the following

```
[COLOR=#0000ff]sudo apt-get install nvidia-[/COLOR]{hit the TAB key}
nvidia-**173**                        nvidia-331-updates-uvm            nvidia-current-updates-dev
nvidia-173-dev                    nvidia-331-uvm                    nvidia-experimental-304
nvidia-173-updates                nvidia-**96**                         nvidia-experimental-304-dev
nvidia-173-updates-dev            nvidia-96-dev                     nvidia-experimental-310
nvidia-[COLOR=#0000ff]304[/COLOR]                        nvidia-96-updates                 nvidia-experimental-310-dev
nvidia-304-dev                    nvidia-96-updates-dev             nvidia-opencl-dev
nvidia-304-updates                nvidia-cg-toolkit                 nvidia-prime
nvidia-304-updates-dev            nvidia-common                     nvidia-settings
nvidia-**319**                        nvidia-compute-profiler           nvidia-settings-304
nvidia-319-dev                    nvidia-cuda-dev                   nvidia-settings-304-updates
nvidia-319-updates                nvidia-cuda-doc                   nvidia-settings-319
nvidia-319-updates-dev            nvidia-cuda-gdb                   nvidia-settings-319-updates
nvidia-**331**                        nvidia-cuda-toolkit               nvidia-settings-experimental-304
nvidia-331-dev                    nvidia-current                    nvidia-settings-experimental-310
nvidia-331-updates                nvidia-current-dev                nvidia-settings-updates
nvidia-331-updates-dev            nvidia-current-updates            
[COLOR=#0000ff]sudo apt-get install nvidia-[/COLOR]{and now you enter your choice, for example **[COLOR=#0000ff]304[/COLOR]**, and hit the Enter key}


```Try the available drivers. One of them is probably working better than the others. You can also try the experimental ones, if none of the 'standard' drivers works.

C. Only if this fails, you should install the downloaded package with an nvidia driver. There are instructions how to do it in the package.

---

### Post by Jerry_Price on 2014-05-31
Thanks again
I tried the [COLOR=#0000ff][FONT=Ubuntu Mono]sudo apt-get install nvidia-[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]{hit the TAB key}[/FONT][/COLOR]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]but it returned zero nvidia drivers. So I swapped around with the existing nvidia models installed and found one that did the trick. So I am over that hurdle thanks

Now to get the printer working  [/COLOR][/FONT]

---

### Post by sudodus on 2014-05-31
Please share the result, in other words, tell us which nvidia driver that works for you! It would be valuable for many users at the Ubuntu Forums :-)

And please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

> Now to get the printer working  

The problem with your printer is a completely different issue, and it is likely that other people know about it. In order to attract them, I suggest that you make a new thread with a good descriptive title in the [Hardware]("http://ubuntuforums.org/forumdisplay.php?f=332") forum.

---

### Post by Jerry_Price on 2014-06-04
The driver I used for the Nvidia Quadro NVS 110M was the Nvidia legacy binary driver version 304.117 from the sodtware updates - additional drivers

---

### Post by sudodus on 2014-06-04
Thanks for sharing :-)

---

