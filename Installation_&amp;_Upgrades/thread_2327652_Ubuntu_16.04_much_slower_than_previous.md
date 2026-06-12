---
title: "Ubuntu 16.04 much slower than previous"
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by gustavolaufer on 2016-06-13
Hello Fellows,

I had been using the Ubuntu 14.10 LTS for a long time, but two weeks ago I decided to check "what is new in 16.04". The upgrade had success, and no major problem happened. However, now the initialisation and turning it off is taking a LONG time, more than 2 minutes! Before, I believe it took 30 seconds. 

Well, I have been investigating this a lot , and I found out many "ways" to improve boot time  but no good results. It is still taking more than 2 minutes.

Some interesting fact is that, when I boot showing the commands it is hold for a long time in:
> A start job running for detect the available GPUs and deal .... 

I searched a lot about that, and I have attached the *system-analyze blame* in this thread, which shows a LONG time for the gpu-manager, much longer than other reports that I could find in the internet. So, there is something wrong here. But I do not know how to fix.

Moreover, another issue that I noticed while booting was 
> started update UMTP ..... fail LSB ... printing
Actually I DO NOT HAVE ANY printer, when I need, I use PDF. Thus I have even removed CUPS from the initialisation in order to see it it help, though it has not.

Eventually, I provided the lshw and the logs which were generated today (/var/logs/).

I hope someone can help me or has already faced similar situation.

---

### Post by oldfred on 2016-06-13
At grub menu when booting try each of these options:
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size 

You add each like nomodeset.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Are you running 32bit?

---

### Post by gustavolaufer on 2016-06-14
Yes, I am running a 32 bit.

I am going to try the NOMODESET next boot.

---

### Post by gustavolaufer on 2016-06-14
Yes, I am running a 32 bit.

I did not find any VIDEO parameter in the boot/command line nor in the /etc/default/grub. So I did not change anything.

IT REALLY SPEED UP THE SYSTEM! BUT .....

My resolution should be 1366x768 though the Unity is showing 1024x768 with no other option. 
I lost the graphic accelerator... the compiz is working not as well as before. I believe that the ATI Mobility Radeon stopped working.

Well... that fixed the slowness but created a video problem...

---

### Post by oldfred on 2016-06-14
Did you try this instead of nomodeset?

video=VGA-1:1366x768-24@60

---

### Post by gustavolaufer on 2016-06-15
Well, unfortunately, it displayed the proper resolution but it is as slow as in the beginning.

---

### Post by mastablasta on 2016-06-15
> **gustavolaufer said:**
> Well, unfortunately, it displayed the proper resolution but it is as slow as in the beginning.

what is the GPU chip?

edit: sorry, didn't se the lshw file:

```
-cpu
          produto: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz

*-display
             descrição: VGA compatible controller
             produto: Core Processor Integrated Graphics Controller
             fabricante: Intel Corporation
             ID físico: 2
             informações do barramento: pci@0000:00:02.0
             versão: 12
             largura: 64 bits
             clock: 33MHz
             capacidades: msi pm vga_controller bus_master cap_list rom
             configuração: driver=i915 latency=0
             recursos: irq:26 memória:d8000000-d83fffff memória:c0000000-cfffffff porta de E/S:4050(tamanho=8)
```

are the drivers working propperly even? do they provide hardware acceleration? i think this test should work on intel as well.

> Make sure your OpenGL renderer string does not say "software rasterizer" or "llvmpipe" because that would mean you have no 3D hardware acceleration: ```
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```

you could try upgrading them as it seems that i915 has some issues in 16.04 on certain kernels.: [SIZE=2]http://askubuntu.com/questions/766931/how-to-change-graphics-driver-in-16-04-from-i915-to-open-source-driver
[/SIZE]
did you use any special setting before on 14.04?
[SIZE=2]http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus
[/SIZE]

---

### Post by RobGoss on 2016-06-17
I didn't see your specs posted here in the OP it might help others if we knew what your machines is running

---

### Post by gustavolaufer on 2016-06-24
@RobGoss,
I did not understand what you meant. Could you tell me what information do you need, and how I can get it?

@mastablasta,
Your comment makes sense, though I am using a Intel Core i3, and the link that you sent is referring to a AMD64 one.

**News about my case**
I tried to install a new Ubuntu from scratch.... 
So I saved all my /home and formatted it

The installation had success though the issue seems to be WORSE!

Doing a **systemd-analyze blame**, I got the following:
```
    1min 38.934s apparmor.service
    1min 33.449s plymouth-read-write.service
      1min 720ms gpu-manager.service    <--- it seems to be worse
         57.820s plymouth-quit-wait.service
          9.777s dev-sda4.device
... and more rows with some more seconds

``` 

Actually... during the morning, I wake up, turn on the computer, and go out and have breakfast... and eventually when I return to the computer it has turned on completely... I'm kidding.... but the boot time takes about **THREE MINUTES**. And I disable all uneeded stuff.

Please tell me what "report" you need, and how to get it... I will do that right away!

Thanks community

---

### Post by X-RED_Tech on 2016-06-26
I hope you didn't install a 32-bit Ubuntu in such modern 62-bit machine.

---

### Post by RobGoss on 2016-06-26
It's best to provide what specs your machines has so people know what kind of hardware you have

> [COLOR=#000000]I did not understand what you meant. Could you tell me what information do you need, and how I can get it?[/COLOR]

Run this commad:
```
lshw
```

Use the code tags when posting the out put

---

### Post by banceu_sergiu_ione on 2016-06-26
> **gustavolaufer said:**
> @mastablasta,Your comment makes sense, though I am using a Intel Core i3, and the link that you sent is referring to a AMD64 one.

AMD64 its made for both Intel and AMD.
AMD64  it say you are going to install something that have to do with 86_64bit architecture and its not part of AMD you know. If you not believe then got for the i385 which is a 32bit architecture but then not wonder why its slower.

@mastablasta point you on the right way by upgrading your graphic driver may or not resolve it, and I would add that you can try use [padoka PPA Paulo Dias]("https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa")/ to do it.

---

