---
title: "Ubuntu 7.10 kernel freezes BAD on Clevo M720S (OEM)"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by perlhead on 2008-03-13
The kernel in 7.10 fails to boot on Clevo M720S notebooks (Clevo is an OEM, these notebooks are sold under different brands in different parts of the world, I got this in Argentina under the "Bangho" brand).

The symptoms are as follows:
[LIST=1]
[*]System begins booting
[*]Message appears "Cannot allocate resource region 0 of device 0000.00.09.0"
[*]The "console font change" thing happens
[*]The Ubuntu boot splash screen appears
[*]The system freezes with the progress bar still nearly empty (only a couple of pixels)
[/LIST]

The only way to resurrect the system is to power cycle it.

Oddly enough, the 7.04 kernel works if kernel flags "noapic nolapic" are specified (7.10 kernel does not), so I was able to install 7.04 and then upgrade to 7.10 minus kernel.

I am at a loss as to what additional information can be provided to help debugging this.

Device 00.09.0 is a multi-format flash memory reader, which doesn' t seem to give any trouble under the 7.04 kernel (inserting an SD car into it is a NOP), but it doesn' t seem to give any trouble either.

> 
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
        Subsystem: CLEVO/KAPOK Computer Unknown device 0720
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (250ns min, 1000ns max), Cache Line Size: 16 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 40000200 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-


---

### Post by dropedrobarri on 2008-04-20
Hy!!! I`have the same problem with my notebook (BANGHO`s un Argentina).
Click the next link: [http://yobangho.com/productos/buscador.php?producto=110&includes_predet=](http://yobangho.com/productos/buscador.php?producto=110&includes_predet=)
BanghóMov CQ1405CB 
Microprocesador Intel Pentium Dual T2330
Memoria 1Gb. DDR2 667Mhz. 
Disco Rígido SATA 80Gb. 5400RPM 
Lectoragrabadora de DVD 
Chipset Via VN896CE + VT8237A 
Placa de red 10/100, Wireless 802.11b/g 
Peso 2,2Kg. 
Batería 6 celdas
3 X USB 2.0 – One Express Card/54(34) Slot
Modem 56Kbps. MDC v. 92
Lector de Memorias 7 en 1
Pantalla 14" WXGA

So, I installed UBUNTU 7.10 ISO RELEASE, then my notebook freeze!!!!!
So, if you reboot and restart with safe graphics mode, you can type in the terminal "startx" AND UBUNTU RUN.
I think the problem is in some driver, I recomend "driverguide.com" in order to solve this problem.
If anyone know how run UBUNTU 7.10 please answer us!!!!! 

 [email]barrientosloayza@gmail.com[/email]

---

### Post by perlhead on 2008-04-26
It still doesn't work with Hardy. Some more information (BTW: this machine is labelled by Banghó).

Booting from the Hardy CD-ROM without the 'quiet splash' parameters, I can see the messages the system emits immediately before hanging:

[47.327431] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[47.327430] ACPI: Processor [CPU0] (supports 8 throttling states)
[47.328445] ACPI: SSDT 37D962E8, 022D (r1 PmRef Cpu1Ist 3000 INTL 20050228)
[47.329109] ACPI: SSDT 37D95FB2, 022D (r1 PmRef Cpu1Ist 3000 INTL 20050228)
[47.330533] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[47.330730] ACPI: Processor [CPU1] (supports 8 throttling states)
[47.330882] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[47.331063] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[47.331235] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[47.331405] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[47.331574] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[47.331743] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]

The only way to revive the machine at this point is to power cycle.

The kernel *does* boot with either the 'nosmp' or 'acpi=off' options, but both options leave the notebook seriously crippled: either it limps along on only one core, or it can't do any power management.

---

### Post by dropedrobarri on 2008-04-28
Dear Friend: 
I have a very good news for you. Last saturday I was in Free Software Install Party (InstallFest)with a lot of students from  university of cordoba argentina. In order to see more information please you must visit this link: [http://www.grulic.org.ar/](http://www.grulic.org.ar/).
So, I met a very good Linux`s User,  his name was Marco, and then in two or three hours he put in MY BANGHO a new Kernel and then I can start my ubuntu. (more details I can ask to him if you want) 
I cant see the first window when you writte usser and pasword. It`s look like a graphic mode, then I can writte my User and my password (in text mode). Then I have to writte "startx"  and UBUNTU works very good!!!!
He told me that the problem is a video driver. Right now I`m in google in order to take more information!!!
Pedro (if you talk spanish I can help you more and best!!):)

---

### Post by perlhead on 2008-04-29
> **dropedrobarri said:**
> 
So, I met a very good Linux`s User,  his name was Marco, and then in two or three hours he put in MY BANGHO a new Kernel and then I can start my ubuntu. 

Marcos just happens to be my cousin :-) I talked to him on the phone, but he told me that your machine is not the same as mine: yours has a via chipset, while mine has a sis chipset. As a consequence, everything is different. According to him, your problem was entirely with the video driver, not with the kernel. I can't get my machine to boot, whereas in yours, it was just a matter of not being able to get it to work properly in graphics mode.

---

### Post by dropedrobarri on 2008-06-28
> **perlhead said:**
> Marcos just happens to be my cousin :-) I talked to him on the phone, but he told me that your machine is not the same as mine: yours has a via chipset, while mine has a sis chipset. As a consequence, everything is different. According to him, your problem was entirely with the video driver, not with the kernel. I can't get my machine to boot, whereas in yours, it was just a matter of not being able to get it to work properly in graphics mode.
I found this page.... for Chipset Via VN896CE + VT8237A drivers....
the webpage is: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

---

### Post by dropedrobarri on 2008-06-28
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) 
you can download the driver for  Chipset Via VN896CE + VT8237A

---

### Post by perlhead on 2008-06-28
> **dropedrobarri said:**
> I found this page.... for Chipset Via VN896CE + VT8237A drivers....
the webpage is: [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

Unfotunately, this doesn't help at all, because the machine is based on a SiS chipset, not VIA.

---

### Post by dropedrobarri on 2008-06-29
> **perlhead said:**
> Unfotunately, this doesn't help at all, because the machine is based on a SiS chipset, not VIA.
Estimado Pearl:
Me imagino que ya probaste estos drives no? Te cuento que mi laptop.... se trunco nuevamente
puedo entrar al modo texto.... es más puedo usar el MidnightCommander.... pero en modo grafico no pasa absolutamente nada.... se me queda en negro la pantalla.... pongo a ciegas el usuario y mi psswd...y allí queda todo....
ni siquiera como startx puedo hacer funcionar.... la verdad es que estoy perdido.
Todo sucedio cuando se me ocurrio entrar en modo recuperacion, allí te da la alternativa de hacer un fix en el xserver.... y se me truncó todo....
tenes idea como hacer para solucionar entonces?
NO QUIERO VOLVER A WINDOWS
un abrazo

---

### Post by perlhead on 2008-06-29
> **dropedrobarri said:**
> Estimado Pearl:
Me imagino que ya probaste estos drives no? Te cuento que mi laptop.... se trunco nuevamente puedo entrar al modo texto.... es más puedo usar el MidnightCommander.... pero en modo grafico no pasa absolutamente nada.... 

No los probé, porque no tienen la más mínima chance de funcionar. No sé de dónde sacaste que podían servir. Acerca de qué hacer para volver a tener tu máquina andando: ni idea, no sé qué se rompió. Lo mejor que se me ocurre es que vuelvas a instalar desde cero.

---

### Post by dropedrobarri on 2008-06-30
Buenas Noticias!!!
A través del Midnight Commander pude desempaquetar el driver de VIA para UBUNTU 8.04 [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
Lo instalé....y felizmente reviví mi UBUNTU. AHora solo queda que ajuste o edite el X11config para darle la dimensión exacta de pixeles...... este es mi problema actual...pero por lo menos ya FUNCIONA!!!!!!
Un abrazo

---

