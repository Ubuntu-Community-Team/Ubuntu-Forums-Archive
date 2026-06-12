---
title: "System is unstable after upgrade"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by Frdric_Meyer on 2013-10-10
Hello,

I've just upgraded to 13.04. **With 12.10 all is ok, the system is nice.** But _with 13.04 all is slow_, my _Intel i3 often goes over 80%_, _many applications crashes_ when i do some action (button click, combo selection, ...). These are applications that i used today and that have often been crashed:
- Google Chrome
- Firefox
- Eclipse (Indigo, and Kepler)
- VLC
- Skype
- Kdevelop
- Gimp
- Bouml
- MySQL Workbench

What's happened ? Kernel 3.8 has problems ? How resolve that ?

Thanks.

---

### Post by VMC on 2013-10-10
More harware info - ram, video, etc.

Also run either 'top' from terminal or gui System Monitor, and watch what is consuming you cpu usage.

---

### Post by Frdric_Meyer on 2013-10-10
*_Computer Model:_* HP TouchSmart tm2 (Product specifications: [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02497792&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=4308646"))

'top' doesn't give any information, **all is slow, several aplications consuming cpu usage.**

I don't think that killing any processes which overload CPU is the solution. The problem is elsewhere. I've just upgraded and rebooted, that's all i done. The system had great performances (really great) with 12.10 but now i can't use my computer as well as 12.10. The problem may be kernel 3.8 cause before upgrading the kernel 3.2 was fine i didn't need change any driver or otherwise, all worked.
[B]
All my applications are slow. [/B]With _[SIZE=4]**12.10 all is fine**[/SIZE]_. No modification done on system after upgrade.

Informations on computer:
[COLOR=#000000][FONT=HPSimplified][TABLE="width: 100%"]
[TR="class: theme"]
[TH="width: 25%, align: left"]Product Name[/TH]
[TH="width: 75%, align: left"]tm2-2150us[/TH]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Product Number**[/TD]
[TD="class: columnReducedMargin, align: left"]XG892UA#ABA[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Microprocessor**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]1.33GHz Intel Core i3-380UM Processor[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Microprocessor Cache**[/TD]
[TD="class: columnReducedMargin, align: left"]3MB L3 Cache[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Memory**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]4GB DDR3 System Memory (2 DIMM)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Memory Max**[/TD]
[TD="class: columnReducedMargin, align: left"]8GB[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Video Graphics**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]Intel HD Graphics[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Video Memory**[/TD]
[TD="class: columnReducedMargin, align: left"]Up to 1695MB[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Hard Drive**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]500GB (7200RPM)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Display**[/TD]
[TD="class: columnReducedMargin, align: left"]12.1&#8221; diagonal High-Definition HP BrightView Touchscreen (1280 x 800). Panel rotates 180° and folds flat. Supports multi-gesture and stylus input through capacitative digitizer technology[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Network Card**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]Integrated 10/100/1000 Gigabit Ethernet LAN[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Wireless Connectivity**[/TD]
[TD="class: columnReducedMargin, align: left"]
[LIST]
[*]802.11b/g/n WLAN
[/LIST]
[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Sound**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]
[LIST]
[*]Dolby Advanced Audio with Altec Lansing speakers
[/LIST]
[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Keyboard**[/TD]
[TD="class: columnReducedMargin, align: left"]Full-size island-style keyboard[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Pointing Device**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]HP Clickpad with On/Off button[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**External Ports**[/TD]
[TD="class: columnReducedMargin, align: left"]
[LIST]
[*]5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
[*]3 Universal Serial Bus (USB) 2.0
[*]1 HDMI
[*]1 VGA (15-pin)
[*]1 RJ -45 (LAN)
[*]1 Headphone-out/Microphone-in combo jack (compatible with 3.5mm 4-conductor jack with stereo audio and mono mic)
[/LIST]
[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Dimensions**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]12.83" (L) x 9.06" (D) x 0.96" (min H)/ 1.18" (max H)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Weight**[/TD]
[TD="class: columnReducedMargin, align: left"]4.17 lbs[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**Security**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]
[LIST]
[*]Kensington MicroSaver lock slot
[*]Power-on password
[*]Accepts 3rd party security lock devices
[/LIST]
[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="class: columnReducedMargin, align: left"]**Power**[/TD]
[TD="class: columnReducedMargin, align: left"]
[LIST]
[*]65W AC Adapter
[*]6-Cell 62WHr Lithium-Ion Battery
[/LIST]
[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]**What's In The Box**[/TD]
[TD="class: columnReducedMargin, bgcolor: #FFFFFF, align: left"]HP TrueVision Webcam with integrated digital microphone 

HP SimplePass with integrated fingerprint reader[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

---

### Post by ian-weisser on 2013-10-11
What processes are hogging all the resources?

---

### Post by mörgæs on 2013-10-11
How does 13.04 work in a live boot?

---

### Post by Frdric_Meyer on 2013-10-15
I've found the solution.

In fact, the problem was Graphite module for Pango. It make crashes application (all that use GTK for example) with a segmentation fault sometimes.
I've removed ubuntu package: "pango-graphite".

Now, applications don't crash and my system works fast.

---

### Post by mörgæs on 2013-10-15
Good, please mark the thread 'solved' using 'thread tools'.

---

