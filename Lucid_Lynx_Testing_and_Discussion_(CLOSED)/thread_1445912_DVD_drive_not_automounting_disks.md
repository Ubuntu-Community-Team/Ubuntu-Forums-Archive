---
title: "DVD drive not automounting disks"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by keljaden on 2010-04-03
Once Ubuntu has already started, if I put a CD-ROM, or DVD-ROM, into my Combo optical drive, Ubuntu does not auto detect it.  It can see I have a drive if I go to Places>Computer, it shoes the CD/DVD Drive, but I am unable to open it.  If I restart with the CDROM/DVDROM in the drive, it will work.  What am I doing wrong?

---

### Post by karthick87 on 2010-04-03
I face the same problem,but still i cant find the right solution.

---

### Post by karthick87 on 2010-04-06
Bump..

---

### Post by keljaden on 2010-04-07
Yeah, this problem still exists and it is really bugging me, I am not able to mount disks from my DVD drive once ubuntu has started.

I do not even think my drive is being detected (unless there is something there upon boot) Please help.

---

### Post by bclintbe on 2010-04-07
Are you seeing this in 10.04 Beta 1? Tonight I put a music CD in the drive, ripped it in RythmBox. Ejected the disk and put in another CD... nothing. Not auto-detected. Drive does show up in Computer as HL-DT-ST DVDRAM GH22NS50 but will not let me open it. Any ideas???

---

### Post by Lambertes on 2010-04-07
Ubuntu 10.04 (04-04-2010) does not auto detect DVD and CD.
Help please........?!
 
by
Lambertes (Italian man)

---

### Post by keithpeter on 2010-04-07
> **keljaden said:**
> Once Ubuntu has already started, if I put a CD-ROM, or DVD-ROM, into my Combo optical drive, Ubuntu does not auto detect it.  It can see I have a drive if I go to Places>Computer, it shoes the CD/DVD Drive, but I am unable to open it.  If I restart with the CDROM/DVDROM in the drive, it will work.  What am I doing wrong?

Do you get the same issue with USB thumb drives? See

[http://ubuntuforums.org/showthread.php?t=1448497](http://ubuntuforums.org/showthread.php?t=1448497)

My Lucid Ubuntu test install on a thinkpad t42 automounts a cd-rom no problem. And it can eject.

---

### Post by keljaden on 2010-04-07
My USB drives work flawlessly, I did not notice this problem until i was installing MW2 through crossover as I have already turned all my old games into .iso files because the CD's they were on were starting to get worn.

This is just with CD's and DVD's.  MY Optical drive is IDE if that makes any difference.

---

### Post by Kirk M on 2010-04-07
Same here. I was testing 10.04 when I realized that inserting any type of CD or DVD into either of my optical drives makes the respective drive simply disappear from Nautilus altogether. Eject the disk and the drive shows up again. Completely weird as the machine has no problem like this with Karmic or Linux Mint 8 (fully realizing that 10.04 is a beta of course).

---

### Post by keljaden on 2010-04-07
I am shocked that it has been four days (at least) and the development team of 10.04 have yet to fix such a massive error.  It would be nice to get some feedback as of how to fix this as well.  I realize this is a beta, but I feel like I am going backwards...Slower loading of my DE after login and now this...I just feel like something is REALLY out of place here.

---

### Post by bash on 2010-04-08
Installed Lucid on 3 machines so far and one of them is now suffering from this problem as well. Neither DVDs nor CDs put into the drive are automounted.

I am still able to manually mount the drives through the CLI but I somehow doubt that that is the intended way of how it should work.

Interestingly **dmesg** is litered with errors if I insert a CD/DVD. Here for example is the errors that I get when putting in a Lucid Lynx Live CD. Checked the CD on another machine running Lucid and there it is correctly mounted and I do **not** get these errors. Could other people affected by this also check their **dmesg** output.

DMESG output: 

```
[  891.103070] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.103077] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.103084] Info fld=0x56f44, ILI
[  891.103086] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.103094] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.103107] end_request: I/O error, dev sr0, sector 1424656
[  891.103113] Buffer I/O error on device sr0, logical block 178082
[  891.220486] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.220492] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.220500] Info fld=0x56f44, ILI
[  891.220503] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.220512] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.220525] end_request: I/O error, dev sr0, sector 1424656
[  891.220531] Buffer I/O error on device sr0, logical block 178082
[  891.317663] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.317670] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.317677] Info fld=0x56f44, ILI
[  891.317679] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.317686] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.317700] end_request: I/O error, dev sr0, sector 1424656
[  891.317705] Buffer I/O error on device sr0, logical block 178082
[  891.445395] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.445402] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.445409] Info fld=0x56f44, ILI
[  891.445411] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.445418] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.445432] end_request: I/O error, dev sr0, sector 1424656
[  891.445438] Buffer I/O error on device sr0, logical block 178082
[  891.564758] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.564767] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.564777] Info fld=0x56f44, ILI
[  891.564781] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.564792] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.564810] end_request: I/O error, dev sr0, sector 1424656
[  891.564818] Buffer I/O error on device sr0, logical block 178082
[  891.696209] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.696216] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.696223] Info fld=0x56f44, ILI
[  891.696225] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.696232] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.696246] end_request: I/O error, dev sr0, sector 1424656
[  891.696252] Buffer I/O error on device sr0, logical block 178082
[  891.825394] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.825400] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.825407] Info fld=0x56f44, ILI
[  891.825410] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.825417] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.825430] end_request: I/O error, dev sr0, sector 1424656
[  891.825436] Buffer I/O error on device sr0, logical block 178082
[  891.990580] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  891.990587] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  891.990594] Info fld=0x56f44, ILI
[  891.990597] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  891.990604] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  891.990617] end_request: I/O error, dev sr0, sector 1424656
[  891.990623] Buffer I/O error on device sr0, logical block 178082
[  892.088200] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  892.088207] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  892.088213] Info fld=0x56f44, ILI
[  892.088216] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  892.088223] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  892.088236] end_request: I/O error, dev sr0, sector 1424656
[  892.088242] Buffer I/O error on device sr0, logical block 178082
[  892.210950] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  892.210956] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  892.210964] Info fld=0x56f44, ILI
[  892.210966] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  892.210973] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 44 00 00 02 00
[  892.210989] end_request: I/O error, dev sr0, sector 1424656
[  892.210997] Buffer I/O error on device sr0, logical block 178082
```




**Edit**

There seems already to be a bug report about the problem:
[https://bugs.launchpad.net/ubuntu/+bug/554433](https://bugs.launchpad.net/ubuntu/+bug/554433)

---

