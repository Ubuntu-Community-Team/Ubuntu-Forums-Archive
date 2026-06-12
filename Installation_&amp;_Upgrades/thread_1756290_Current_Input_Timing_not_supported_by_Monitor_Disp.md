---
title: "Current Input Timing not supported by Monitor Display"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by pushkar.sambhus on 2011-05-12
Hi,

I recently upgraded to Ubuntu 11.04 , and on reboot the following message was displayed on my monitor
[COLOR=Red]
[/COLOR][HTML]The current input timing is not supported by the monitor display.
Please change your input timing to 1366*768@60Hz or any other monitor listed timing as per the monitor specifications[/HTML]My monitor specifications are Dell IN1920 LCD.

I searched a lot for the solution on this issue but none of them seem to work. I am unable to proceed as the GRUB is also not visible.

Any help in solving this problem would be greatly appreciated.

Thanks in advance
Pushkar

---

### Post by Najubhai on 2011-05-12
Try connecting it to another display.If it works then change the resolution to the required amount

---

### Post by pushkar.sambhus on 2011-05-12
Hi Najubhai,

I do not have access to another monitor as this is my Home PC. 

Therefore would like to know if there are any other solutions to this problem.

Thanks,
Pushkar

---

### Post by Najubhai on 2011-05-12
When your PC starts and you choose to load Ubuntu (from BIOS not Grub2)
there will be a purple screen,press left shift or esc then you'll get access to grub menu on first line there will be "Ubuntu 11.04 with Linux 2.xx (generic)"
Hover your selection over it and press e
some 5 or 6 lines will show up

On the line which starts with linux \boot go to the end of that sentence and then type:
If you have ATi GPU : radeon.modeset=0
If you have NVidia : nomodeset
For Generic : xforcevesa

after that press ctrl+x

Hopefully it will boot to the GUI and there you can change the resolution.

Hope that helps :)

---

### Post by pushkar.sambhus on 2011-05-12
I will try it out and will update the status soon... !!! 

Thanks :)

---

### Post by abscond on 2011-05-12
I would like to know your results.   My system went into kernel panic while updating and now the same statement is made.  I can't get past post.

---

### Post by pushkar.sambhus on 2011-05-13
Hi,

@Najubhai
Boot from BIOS .... did u mean through the LiveUSB ?? 
If not then can u tell me the steps to boot from BIOS , cause am a noob to Ubuntu.


@abscond
Haven't yet tried out the solution given by Najubhai.. will post an update once I try it out.

---

### Post by charliehmmnd on 2011-08-30
hey there. I've had this exact same problem. but there is no purple screen. and i never have the option to choose an OS in bios...

---

