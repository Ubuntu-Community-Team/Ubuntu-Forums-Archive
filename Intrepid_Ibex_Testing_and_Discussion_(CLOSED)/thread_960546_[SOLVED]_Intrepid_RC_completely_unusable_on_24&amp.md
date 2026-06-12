---
title: "[SOLVED] Intrepid RC completely unusable on 24&amp;quot; iMac"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2008-10-27
Hi guys,

so I got myself an iMac with the intent of running Ubuntu as the main system. I've been using Ubuntu for 3/4 of a year now on several machines and liked the concept of the iMac (pc in a screen...) so the choice was an easy one.

As I got my machine (latest model, 24" with 2,8GHz) last week I figured I'd wait for 8.10 and today I wanted to give the RC a shot.

Here's the problems I ran into:

- normal boot is not possible, Ubuntu fails to initialize the graphical UI. Can't go into verbose mode or restart X either...
- safe boot works with a resolution of 1600x1200
- sound doesn't work (well, I didn't get to play around much with the settings due to another bug, see below)
- WiFi is not detected (I had hoped the driver would be included in 2.6.27 and it should be included, but, obviously, there is some kinda glitch)
- After starting into gnome the help-application starts in some kinda loop - hundreds of windows pop up with no possibility to kill them as they take up all the system resources
- after a while the machine freezes due to the help-center-bug and has to be powered off via the power switch

I just popped the CD into my old laptop - no help-center killing-spree there so it has to be a problem with the iMac.

Anyone have any input?

(Please do excuse any errors, I'm not a native speaker)
thanks,
moviemaniac

---

### Post by cyberdork33 on 2008-10-27
This is quite suprising actually. Can you check the information under the "Before you post" link in my signature?

If you can get the system to boot and install then you can fix the graphics with the fglrx, so let's pass on that for now...

The sound on these machines has had trouble off and on for awhile. You might need to file a bug report on this one in launchpad.

For the Wifi, it doesn't (and never has) worked out of the box, but you can now use the "wl" driver that is on the Ubuntu LiveCD. You need to unload the b43 module(s) and load wl.

```
sudo modprobe -r b43 b43legacy ssb
sudo modprobe wl
```You can force this in your install by blacklisting the open Broadcom drivers and putting wl in /etc/modules. Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)

IDK about your other issue. Definitely sounds like a bug. You should check launchpad to see if it has been reported.

---

### Post by moviemaniac on 2008-10-27
Thanks very much. I have already bookmarked the Wiki-page as reference after installing Ubuntu. While I don't worry about the graphics after installing it, it is definitely a bug in the live-cd (already reported it on launchpad). 

WiFi is less of an issue for me as I don't need it, but thanks very much for the hints on activating it. I just hope I'll be able to get the sound to work - I switch frequently between the internal speakers and Mini-Toslink (when watching DVDs). I just hope that'll work.

I'll give the install a shot tomorrow and will report back.

---

### Post by cyberdork33 on 2008-10-27
> **moviemaniac said:**
> Thanks very much. I have already bookmarked the Wiki-page as reference after installing Ubuntu. While I don't worry about the graphics after installing it, it is definitely a bug in the live-cd (already reported it on launchpad).
I was really going after the version number of your iMac ;)

---

### Post by moviemaniac on 2008-10-27
Oh, sorry, it's 8,1

---

### Post by skaplan77 on 2008-10-27
I have a 24in aluminum imac running Ubuntu 8.04, and I used the following website to setup sound:

[http://idebian.wordpress.com/2008/06/23/24-imac-alsa-configuration/](http://idebian.wordpress.com/2008/06/23/24-imac-alsa-configuration/)

Worked like a charm, although I'm not sure if the instructions also apply to Ubuntu 8.10.

---

### Post by kosumi68 on 2008-10-27
> **moviemaniac said:**
> Oh, sorry, it's 8,1

You might be interested in reporting output for the applesmc part of the commands listed here: [http://ubuntuforums.org/showpost.php?p=5982275&postcount=4](http://ubuntuforums.org/showpost.php?p=5982275&postcount=4)

---

### Post by moviemaniac on 2008-10-27
> **skaplan77 said:**
> I have a 24in aluminum imac running Ubuntu 8.04, and I used the following website to setup sound:

[http://idebian.wordpress.com/2008/06/23/24-imac-alsa-configuration/](http://idebian.wordpress.com/2008/06/23/24-imac-alsa-configuration/)

Worked like a charm, although I'm not sure if the instructions also apply to Ubuntu 8.10.

I'll give that a try tomorrow, thanks! I just installed 8.10 on my machine and so far it works. But since it's already midnight over here, I'll call it a day now :D

@kosumi68: Will post the output tomorrow, too :)

---

### Post by moviemaniac on 2008-10-28
> **kosumi68 said:**
> You might be interested in reporting output for the applesmc part of the commands listed here: [http://ubuntuforums.org/showpost.php?p=5982275&postcount=4](http://ubuntuforums.org/showpost.php?p=5982275&postcount=4)

there you go:

```
sudo dmidecode | grep 'Product Name:'
	Product Name: iMac8,1
	Product Name: Mac-F227BEC8

```

```
 lsusb
Bus 007 Device 002: ID 05ac:8502 Apple, Inc. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 008: ID 05ac:0221 Apple, Inc. Keyboard (Aluminium) (ISO)
Bus 003 Device 006: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 007: ID 045e:071f Microsoft Corp. 
Bus 003 Device 005: ID 152e:1640 LG (HLDS) 
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:820f Apple, Inc. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

can't run the scan-smc script, it tells me "permission denied"...

Nonetheless, after working for a few hours today I have to say that everything works just fine over here. No fiddling with the aluminium keyboard, sound (internal speakers and optical out) was quickly enabled (as described in the wiki), the isight-camera worked ootb....

I can't say anything about wifi, though, as I don't need it and the new network-manager is ... well... unusable. It doesn't allow me to use internet (pppoe - ppp0) and ethernet (normal lan, eth0) at the same time, only either the one or the other. So I can't even print (over lan) when I'm browsing the web. I ditched network-manager and configured everything manually, this is why I haven't bothered getting wifi to work.

---

### Post by cyberdork33 on 2008-10-28
> **moviemaniac said:**
> can't run the scan-smc script, it tells me "permission denied"... run it with 'sudo'

---

### Post by moviemaniac on 2008-10-28
I did run it in the terminal with root-rights as well as with sudo - it gives me a "command not found" error... And yes, I'm in the right directory....

Oh, and another question: I finally got the hardware sensors to work (can read them either with KSensors GUI or via "sensors" from the terminal), but what is what? I know that temp2 is the ambient temperature, but what about the rest? I couldn't find anything on that...

here's the output of "sensors" in the terminal:


ODD :        700 RPM  (min =  700 RPM)
HDD :       1199 RPM  (min = 1200 RPM)
CPU :       1200 RPM  (min = 1200 RPM)
temp1:       +37.0                                
temp2:       +18.8                          
temp3:       +46.0                                   
temp4:       +45.5                                    
temp5:       +43.5                             
temp6:       +51.0                                  
temp7:       +42.2                                  
temp8:       +43.5                                  
ERROR: Can't get value of subfeature temp9_input: I/O error
temp9:        +0.0

---

### Post by moviemaniac on 2008-10-28
Oh, I just noticed another great thing: I wanted to configure my IR-remote and looked for the howto. But I was curious and just pressed the play/stop button. Rhythmbox paused. Tried all the other buttons - volume up and down work too, out of the box in Intrepid :D Now it's off to get the other buttons to work...

---

### Post by cyberdork33 on 2008-10-28
> **moviemaniac said:**
> I did run it in the terminal with root-rights as well as with sudo - it gives me a "command not found" error... And yes, I'm in the right directory....
Make sure the script is executable.

```
chmod +x ./scan-smc.sh
sudo ./scan-smc.sh
```

---

### Post by moviemaniac on 2008-10-28
You learn something new every day :D

```
root@klaus-imac:/home/klaus/Desktop# sudo ./scan-smc.sh
0: #KEY [4-ui32] 000000e0 [....]
1: +LKS [1-flag] 07 [.]
2: AL! [1-ui8 ] 00 [.]
3: ALA0 [6-{ala] 7a0400340090 [z..4..]
4: ALA1 [6-{ala] 1dc9007a00c4 [...z..]
5: ALA2 [6-{ala] 09d600ac0124 [.....$]
6: ALA3 [6-{ala] 03a900f70185 [......]
7: ALA4 [6-{ala] 01d3013e0400 [...>..]
8: ALA5 [6-{ala] 000100010400 [......]
9: ALAT [4-{alt] 00000000 [....]
10: ALI0 [3-{ali] 030101 [...]
11: ALI1 [3-{ali] 000000 [...]
12: ALRV [2-ui16] 0000 [..]
13: ALSC [16-{alc] 0192009600c800020001015e14ea0100 [...........^....]
14: ALSF [2-fp1f] 0148 [.H]
15: ALSL [2-ui16] 0000 [..]
16: ALT0 [2-ui16] 0000 [..]
17: ALT1 [2-ui16] 0000 [..]
18: ALTH [10-{alr] 00000000000000000000 [..........]
19: ALV0 [6-{alv] 010000000000 [......]
20: ALV1 [6-{alv] 000100000000 [......]
21: AUPO [1-ui8 ] 00 [.]
22: BATP [1-flag] 00 [.]
23: BNum [1-ui8 ] 00 [.]
24: BSIn [1-ui8 ] 42 [B]
25: CLKT [4-ui32] 00012269 [.."i]
26: CRCB [4-ui32] 69b50663 [i..c]
27: CRCU [4-ui32]
28: DPLM [3-{lim]
29: EPCA [4-ui32] 0000f000 [....]
30: EPCF [1-flag] 01 [.]
31: EPCI [4-ui32] 02300700 [.0..]
32: EPCV [2-ui16] 0001 [..]
33: EPMA [4-ch8*] 0000e080 [....]
34: EPMI [1-ui8 ] 00 [.]
35: EPUA [4-ui32] 0000e000 [....]
36: EPUF [1-flag] 01 [.]
37: EPUI [4-ui32] 02300001 [.0..]
38: EPUV [2-ui16] 0001 [..]
39: EVCT [2-ui16] 0101 [..]
40: EVMD [4-ui32]
41: EVRD [32-ch8*] f6060300004000d8000000000000000000000000000000000000000000000000 [.....@..........................]
42: F0Ac [2-fpe2] 0aec [..]
43: F0ID [16-{fds] 01010e004f4444200000000000000000 [....ODD ........]
44: F0Mn [2-fpe2] 0af0 [..]
45: F0Mt [2-ui16] 0000 [..]
46: F0Mx [2-fpe2] 4b00 [K.]
47: F0Sf [2-fpe2] 0000 [..]
48: F0Tg [2-fpe2] 0af0 [..]
49: F1Ac [2-fpe2] 12b7 [..]
50: F1ID [16-{fds] 01020000484444200000000000000000 [....HDD ........]
51: F1Mn [2-fpe2] 12c0 [..]
52: F1Mt [2-ui16] 0000 [..]
53: F1Mx [2-fpe2] 5c30 [\0]
54: F1Sf [2-fpe2] 0000 [..]
55: F1Tg [2-fpe2]
56: F2Ac [2-fpe2] 12b2 [..]
57: F2ID [16-{fds] 01040d00435055200000000000000000 [....CPU ........]
58: F2Mn [2-fpe2] 12c0 [..]
59: F2Mt [2-ui16] 0000 [..]
60: F2Mx [2-fpe2] 3840 [8@]
61: F2Sf [2-fpe2] 0000 [..]
62: F2Tg [2-fpe2] 12c0 [..]
63: FNum [1-ui8 ] 03 [.]
64: FPhz [2-si16]
65: FS! [2-ui16] 0000 [..]
66: GCID [4-ui32] 95831002 [....]
67: GPU! [1-ui8 ] 00 [.]
68: GTHR [1-ui8 ] 01 [.]
69: HBWK [1-flag] 00 [.]
70: HDBS [1-ui8 ] 01 [.]
71: HDST [4-ui16] 00000000 [....]
72: HDSW [4-ui32] 00000000 [....]
73: IC0C [2-fp79] 1060 [.`]
74: ID0R [2-fp5b] 13f1 [..]
75: ID5R [2-fp4c] 0fa8 [..]
76: IG0R [2-fp4c] 0841 [.A]
77: IG0r [2-ui16] 0e40 [.@]
78: LAcN [1-ui8 ]
79: LAtN [2-ui16]
80: LCCN [1-ui8 ] 0c [.]
81: LCCQ [1-ui8 ] 0c [.]
82: LCKA [1-ui8 ] 23 [#]
83: LCSA [1-ui8 ] 00 [.]
84: LCTN [1-ui8 ] 01 [.]
85: LCTQ [1-ui8 ] 03 [.]
86: LDSP [1-flag]
87: LS! [1-ui8 ] 00 [.]
88: LSCF [10-{lsc] 00000190800000020046 [.........F]
89: LSDD [8-{lsd] 0002000300030019 [........]
90: LSDU [8-{lsd] 0003000200140003 [........]
91: LSFD [6-{lsf] 00000004008c [......]
92: LSFU [6-{lsf] 00000004008c [......]
93: LSLB [2-{pwm] ffff [..]
94: LSLF [2-{pwm] 0000 [..]
95: LSLN [2-{pwm] ffff [..]
96: LSOF [1-flag] 01 [.]
97: LSOO [1-flag]
98: LSPV [2-{pwm] 0000 [..]
99: LSRB [1-flag]
100: LSSB [2-{lso]
101: LSSE [1-flag] 01 [.]
102: LSSS [2-{lso]
103: LSSV [2-ui16] f332 [.2]
104: LSUP [1-ui8 ]
105: MACA [4-ui32] 00000000 [....]
106: MACM [1-flag] 01 [.]
107: MACR [32-ch8*] 6368382a904000d8000000000000000000000000000000000000000000000000 [ch8*.@..........................]
108: MOCF [2-ui16] 0000 [..]
109: MOCN [2-ui16] 0000 [..]
110: MSAL [1-ui8 ] 4b [K]
111: MSAc [2-fp88] 0000 [..]
112: MSAg [2-fp88] 0000 [..]
113: MSAm [2-fp88] 0000 [..]
114: MSC0 [2-ui16] 167a [.z]
115: MSC1 [2-ui16] 0000 [..]
116: MSC2 [2-ui16] 0000 [..]
117: MSC3 [2-ui16] 0000 [..]
118: MSCP [2-ui16] 0008 [..]
119: MSCR [2-ui16] 0001 [..]
120: MSCS [1-ui8 ]
121: MSCT [1-ui8 ] 04 [.]
122: MSCa [2-ui16] 0400 [..]
123: MSCb [2-ui16] 0400 [..]
124: MSCc [2-ui16] 0400 [..]
125: MSCd [2-ui16] 0400 [..]
126: MSCl [2-ui16] 0008 [..]
127: MSCm [2-ui16] 0008 [..]
128: MSCn [2-ui16] 0008 [..]
129: MSCo [2-ui16] 0008 [..]
130: MSDI [1-flag] 00 [.]
131: MSDW [1-flag]
132: MSHA [2-fp79] 0008 [..]
133: MSLD [1-ui8 ] 00 [.]
134: MSPA [2-fp6a] 0000 [..]
135: MSPC [1-ui8 ] 07 [.]
136: MSPS [1-{msp] 00 [.]
137: MSSD [1-si8 ] 00 [.]
138: MSSF [4-ui32] 00000000 [....]
139: MSSP [1-si8 ] 00 [.]
140: MSSS [1-{mss] 00 [.]
141: MSTC [2-ui16] 0000 [..]
142: MSTM [1-ui8 ] 01 [.]
143: MSTc [1-ui8 ] 00 [.]
144: MSTg [1-ui8 ] 00 [.]
145: MSTm [1-ui8 ] 00 [.]
146: MSWR [1-ui8 ]
147: NATJ [1-ui8 ] 00 [.]
148: NATi [2-ui16] 0000 [..]
149: NTOK [1-ui8 ]
150: ONMI [1-ui8 ] 00 [.]
151: PC0C [2-fp88] 0cb2 [..]
152: PC0c [2-ui16] 1540 [.@]
153: PD0R [2-fp88] 2229 [")]
154: PD5R [2-fp88] 0bed [..]
155: PDMR [2-fp88] 2e16 [..]
156: PDTR [2-fpa6] 2085 [ .]
157: PG0R [2-fp88] 0643 [.C]
158: PZ0E [2-fp88] 8100 [..]
159: PZ0G [2-fp88] 12f5 [..]
160: RBr [8-ch8*]
161: REV [6-{rev] 01300f000001 [.0....]
162: RMde [1-char] 41 [A]
163: RPlt [8-ch8*] 6b33000000000000 [k3......]
164: RSvn [4-ui32] 00004411 [..D.]
165: RVBF [6-{rev] 01300f000001 [.0....]
166: RVUF [6-{rev] 01300f000001 [.0....]
167: SAS! [4-ui32] 000008ff [....]
168: SBF [2-ui16] 0000 [..]
169: SBFC [2-ui16] 0000 [..]
170: SBFE [1-flag] 01 [.]
171: SCIA [2-ui16] 03f8 [..]
172: SCIL [1-ui8] 00 [.]
173: SCTg [2-sp78] 5000 [P.]
174: SDPE [1-ui8 ] 01 [.]
175: SDRd [2-ui16]
176: SGHT [1-ui8 ] 00 [.]
177: SGTT [2-sp78] 5a00 [Z.]
178: SGTg [2-sp78] 5500 [U.]
179: SHTg [2-sp78] 3a20 [: ]
180: SIS! [2-ui16] 0000 [..]
181: SLPT [2-sp78] 4200 [B.]
182: SLST [2-sp78] 4400 [D.]
183: SLTg [2-sp78] 38e0 [8.]
184: SLTp [2-sp78] 3a60 [:`]
185: SOTg [2-sp78] 3200 [2.]
186: SPH0 [2-ui16] 0000 [..]
187: SPHR [4-ui32] 00000000 [....]
188: SPHS [1-ui8 ] 00 [.]
189: SPHT [2-ui16] 0000 [..]
190: SPHZ [1-ui8]
191: SPS! [2-ui16] 0000 [..]
192: SpCP [4-fps4] 0b00aaaa [....]
193: SpCS [4-fps4] 0a2c2aaa [.,*.]
194: SpCT [2-fpc4] 1b20 [. ]
195: SpPT [2-sp78] 5b00 [[.]
196: SpST [2-sp78] 5f00 [_.]
197: SpTg [2-sp78] 5300 [S.]
198: TA0P [2-sp78] 1360 [.`]
199: TC0D [2-sp78] 29c0 [).]
200: TC0H [2-sp78]
201: TC0P [2-sp78] 2a00 [*.]
202: TG0D [2-sp78] 2ec0 [..]
203: TG0H [2-sp78] 2d40 [-@]
204: TG0P [2-sp78] 2f00 [/.]
205: TH0P [2-sp78] 3400 [4.]
206: TL0P [2-sp78] 30f0 [0.]
207: TO0P [2-sp78] 2c40 [,@]
208: TW0P [2-sp78] 2680 [&.]
209: Tm0P [2-sp78] 2b80 [+.]
210: Tp0P [2-sp78] 478b [G.]
211: UPRC [2-ui16] 0844 [.D]
212: VC0C [2-fp1f] 8b42 [.B]
213: VC0c [2-ui16] 5480 [T.]
214: VD0R [2-fp4c] c1fb [..]
215: VD5R [2-fp4c] c2d4 [..]
216: VG0R [2-fp4c] c1a9 [..]
217: VG0r [2-ui16] e9c0 [..]
218: dBA0 [2-sp78] 098d [..]
219: dBA1 [2-sp78] 0e64 [.d]
220: dBA2 [2-sp78] 13b7 [..]
221: dBAH [2-sp78] 1100 [..]
222: dBAT [2-sp78] 16b7 [..]
223: zDBG [1-ui8] 01 [.]

```

---

### Post by kosumi68 on 2008-10-28
> **moviemaniac said:**
> You learn something new every day :D


Indeed :-) Here is a release candidate package for applesmc-dkms, including your iMac8. Please test it with the script found here: [http://ubuntuforums.org/attachment.php?attachmentid=88935&d=1224488583](http://ubuntuforums.org/attachment.php?attachmentid=88935&d=1224488583)

As always, if the test works out well, the patch will go upstream. Please post me a private message with name and email if you want to appear in the linux kernel log as Tested-by ;-)

---

### Post by moviemaniac on 2008-10-28
here's the output of the script after updating applesmc-dkms:

```
root@klaus-imac:/home/klaus/Desktop# ./applesmc-test.sh
accelerometer: not present
fan:           present, readable, output: 900
light:         not present
leds:          not present
temperatures:  present,
 temperature:           readable, output: 42250
 temperature:           readable, output: 35000
 temperature:           readable, output: 41500
 temperature:           readable, output: 64500
 temperature:           readable, output: 18250
 temperature:           readable, output: 46000
 temperature:           readable, output: 37000
 temperature:           readable, output: 41000
 temperature:           readable, output: 44750
 temperature:           readable, output: 43250
 temperature:           readable, output: 46000
 temperature:           readable, output: 49500
 temperature:           readable, output: 46000
performance:   reading all temperatures
 fail frequency:        0
 reads per second:      55

```

output of sensors:
```
applesmc-isa-0300
Adapter: ISA adapter
ODD :        898 RPM  (min =  900 RPM)
HDD :       1399 RPM  (min = 1400 RPM)
CPU :       1400 RPM  (min = 1400 RPM)
temp1:       +18.2                                 
temp2:       +36.0                                 
temp3:       +36.5                                  
temp4:       +40.0                                    
temp5:       +44.2                                  
temp6:       +42.5                                   
temp7:       +45.0                                   
temp8:       +49.8                                  
temp9:       +46.2                                  
temp10:      +42.2                                   
temp11:      +35.0                                   
temp12:      +41.5                                  
temp13:      +65.0              
```

looks good, but... what the heck is "temp13" with 65°C???

---

### Post by kosumi68 on 2008-10-28
> **moviemaniac said:**
> 
looks good, but... what the heck is "temp13" with 65°C???


According to this (rather outdated) page: [http://www.mactel-linux.org/wiki/AppleSMC](http://www.mactel-linux.org/wiki/AppleSMC), it is an expansion slot. Fun hardware attached? :-)

---

### Post by kosumi68 on 2008-10-28
Ok - from patch to test to mail to lkml.org to Andrew Morton's -mm tree in less than one hour - that must be a world record.

[http://lkml.org/lkml/2008/10/28/353](http://lkml.org/lkml/2008/10/28/353)

New version of applesmc-dkms (0.12.1) available in the mactel PPA.

Enjoy!

---

### Post by moviemaniac on 2008-10-28
whoa, that's pretty quick, indeed! :D

Oh, and according to the Wiki (thanks for the link!) Tp0P would refer to the power supply. In that case 65° would make sense as I don't know of any expansion slot or any fun hardware :D

---

### Post by kosumi68 on 2008-10-28
> **moviemaniac said:**
> 
[...]Tp0P would refers to the power supply. In that case 65° would make sense as I don't know of any expansion slot or any fun hardware :D


My bad - all good then!

---

### Post by cyberdork33 on 2008-10-29
Glad we got that all situated.

---

