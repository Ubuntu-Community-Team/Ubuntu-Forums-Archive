---
title: "Critical temperaure reached (100°), shutting down"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by openversus on 2008-05-10
Hi to everybody.
I use my laptop with the new Hardy but I still have a great problem...
sometimes the pc crash suddenly...
I read in the syslog that the problem's this:
**Critical temperaure reached (100°), shutting down.**
I read a lot of posts but I still haven't found what is the problem.
My lspci output's:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
06:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:07.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:09.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

Please help me :-)
Buena vida!!!

---

### Post by openversus on 2008-05-14
Hi!
I think that's a great problem because none answer me...
so I don't know if I'm so stupid that I didn't find the solution in some posts or if is it an unresolved problem...
Please help me to understand....
Buena vida :-)

---

### Post by brigux on 2008-05-14
Might be your bios settings are stating that the fan is controled by the OS. May be your Hardy installation doesn't undestand that. So at the end the fan is never working. Just a thought tho... May be you can check your Bios and play around with the power saving options to make sure the fan is working.

---

### Post by openversus on 2008-05-14
Thanks brigux
I check the bios I did't find a contol of fan.
The version's *bios version: AB010F05*x
So I think the control fan is by the OS...
And so...
What I have to do?

---

### Post by forestpixie on 2008-05-14
There are a lot of thread's about fan's and laptops - unfortunately I've never looked into the problem myself - this is a list I got from a search - have a look at them.

[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=no+fan+laptop&sa.x=65&sa.y=17](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=no+fan+laptop&sa.x=65&sa.y=17)


Also it might be worth searching for your laptop model in a search, on another note it might be worth reporting your first post and asking a mod to move it to absolute beginners for you.

Finally it might be worth trying xsensors and using sensors detect, open a terminal

```
sudo apt-get install xsensors
```
let that install along with lm-sensors

Now in terminal run

```
sudo sensors-detect
```

enter when it want's input - when it has finished you will need to edit the command to run it as there is a bug with xsensors.

Right click the menus - then edit menus, system tools -= in the right hand pane - you should see xsensors - right click that and then properties you should get the launcher for xsensors - chnage the command to 

> /usr/bin/xsensors -c /etc/sensors3.conf

Reboot and see if xsensors is working 

All I can say is that it appeared to work for me, but that is a desktop.

Good luck

---

### Post by openversus on 2008-05-15
Hi forestpixie!
Hi try to do what you write me. Here's the output
 
[I]root@joda:~# sudo apt-get install xsensors
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
xsensors è già alla versione più recente.
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
root@joda:~# sudo sensors-detect
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 18c0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

[/I]
So I tried to find my chip (Intel ICH6) but in ([http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)) the list of SENSOR CHIP DRIVERS - STATUS I find only Intel ICH8: I find ICH6 only in the list I2C/SMBUS BUS DRIVERS - STATUS.
So lm-sensors seems to be correctly installed and also xsensors... 
I check the CPU status when the T° begin to be hot (92° C) but the % CPU is normally and not high... 
So I'm still here with the problem... :-(

---

### Post by wpshooter on 2008-05-15
Have you tried installing and running Ubuntu/Gutsy on this same computer to see if you still have that problem ?

I really don't trust the reliability of Hardy at this time !!!

---

### Post by openversus on 2008-05-15
... the same problem with Gutsy :confused:

---

### Post by wpshooter on 2008-05-15
Are your computer BIOS up-to-date ?

Do you have this same/similar problems if you run M/S windows O/S on this computer ?

---

### Post by openversus on 2008-05-15
The bios 's the original I've buy with laptop (two years ago)... no update...
and this laptop have never see (and will never) Microsoft :cool:

---

### Post by openversus on 2008-05-15
Now I show the image of the sistem monitor.
You can see it here in the Attached Thumbnails

I only opened firefox and saw a video on youtube...

as you can see the graphic show an high level of CPU...
but I don't undestand why whith this hardware I have this problem...

---

### Post by adult swim on 2008-05-15
just an observation from your screenshot, you might want to shut off the tracker (magnifying glass in your taskbar), it has been known to eat up system resources whenever it is indexing.

---

### Post by wpshooter on 2008-05-15
Are you saying that there is NO update for the BIOS or that you just have not updated it ?

If you have had a computer for 2 years and the BIOS have never been updated, then it is my opinion that it is high time !!!

Thanks.

---

### Post by openversus on 2008-05-16
Ok next weekend I'll try to update the phoenix bios.
Now I shut down the tracker but I still have the problem...
have you some thing to suggest me?

---

### Post by openversus on 2008-06-20
Hi people!
After a lot of time I finally find a simple solution:
1) re-install Ubuntu Hardy from CD 
2) now I'm using this to control the cpu frequency and monitor the t°: **_powersaved_** (you'll find in synaptic).
Now everythig is Ok: I've only some t° problem watching video that uses flash plug-in... but this is a known problem...
So I hope someone can use this info... and have a nice time :-)

Buena vida!

---

