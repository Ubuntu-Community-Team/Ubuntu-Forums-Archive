---
title: "Cannot Load Live CD"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by frank cox on 2010-11-09
This may not have anything to do with Ubuntu but I tried loading a 10.10  disk i know is good in a Systemax Comercial PC. set up as below:

  	 	 	 	 	 	   	 	 		 			[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2](1) 			Intel Celeron-D Processor 335 2.8GHz/533FSB/256K Cache x2 
[/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]
[/SIZE][/FONT]
   	 	 	 	 	 	   	 	 		 			[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2](1) 			Mini-Tower mATX Chassis w/300W PS P4M266 Motherboard[/SIZE][/FONT]



   	 	 	 	 	 	   	 	 	 		 			[IMG]http://www.supportforyourpc.com/tools/images/bullet3.gif[/IMG]
 		 		 			[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2](1) 			80GB 7200RPM ATA100 IDE Hard Drive[/SIZE][/FONT]
[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]
			[/SIZE][/FONT] 			
 		 	   	   	  
  	 	 	 	 	 	   	 	 	 		 			[IMG]http://www.supportforyourpc.com/tools/images/bullet3.gif[/IMG]
 		 		 			[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2](1) 			Intel Celeron-D Processor 335 2.8GHz/533FSB/256K Cache 			[/SIZE][/FONT] 			
 		 	  

The XP that was on it was unusable because the mouse and keyboard would freeze within seconds of booting so I wiped the drive, ran diagnostics on the hard drive, stress tested the CPU , checked the memory and everything checked out.
Once it loaded the live cd and then did the same thing, the mouse froze up. Now it won't even load the live cd, any ideas? I put the live cd in another machine and no problem.

---

### Post by wilee-nilee on 2010-11-09
Have you tried any other install discs, it sounds kind of strange.

I know you say the disc is good but have you done a MD5SUM.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by pb3 on 2010-11-09
That sounds like a hardware issue, maybe something wrong with the motherboard. Are you sure the keyboard and mouse connections are good? If they are usb, have you tried them in different usb ports?

---

### Post by frank cox on 2010-11-10
> **wilee-nilee said:**
> Have you tried any other install discs, it sounds kind of strange.

I know you say the disc is good but have you done a MD5SUM.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Yes I do a md5sum on all my disk with gIsoMount . I put that disk in another machine and it came up and I also tried a puppy linux disk I know to be good.
It was locking up in windows so I assumed that wiping the drive would wipe away the problem .
It is probably not an os problem but I am clueless what it might be,

Thanks

---

### Post by frank cox on 2010-11-10
> **pb3 said:**
> That sounds like a hardware issue, maybe something wrong with the motherboard. Are you sure the keyboard and mouse connections are good? If they are usb, have you tried them in different usb ports?

You are probably right but I ran diagnostics on everything and it checked out. I tried usb and ps2 mouse and keyboards. There are no beeps on startup

Thanks

---

### Post by sikander3786 on 2010-11-10
> The XP that was on it was unusable because the mouse and keyboard would freeze within seconds of booting

If you've got problems with 2 different operating systems, it definitely is an hardware issue.

Sometimes when there is some problem with USB controllers, switching its mode from 2.0 to 1.1 from Bios really helps.

I have this problem on my own system and am posting right now from the very same system :-)

If you've got PS/2 ports, trying a keyboard and mouse there and completely disabling the USB controller from Bios might also help.

---

### Post by frank cox on 2010-11-10
> **sikander3786 said:**
> If you've got problems with 2 different operating systems, it definitely is an hardware issue.

Sometimes when there is some problem with USB controllers, switching its mode from 2.0 to 1.1 from Bios really helps.

I have this problem on my own system and am posting right now from the very same system :-)

If you've got PS/2 ports, trying a keyboard and mouse there and completely disabling the USB controller from Bios might also help.

I will give that a go.
Thanks

---

### Post by frank cox on 2010-11-10
I disabled the USB ports in the Bios and it made no difference . Then I put on a video card {NVidia w/250 mg ram in AGP slot} and no difference.
It seems to be video related somehow as this boot I told the Live CD to run the memory test and it seems to be running that fine. When I boot it opens the Live CD quickly and goes to the page that allows you to select the ;language quickly but whether I ask it to run Xubuntu without installing or to install it it clings in a black screen and then stops blinking.

---

### Post by frank cox on 2010-11-10
Well I have decided that defeat is here. As a last ditch effort I unplugged the last thing I had , the sound card, reset the defaults to fail safe and rebooted and it shows a pretty screen telling me which board it is and that is that.
It don't move no more as my favorite cartoon character said to his little friend he kept in his pocket.

Thanks for trying, I appreciate your time.

---

