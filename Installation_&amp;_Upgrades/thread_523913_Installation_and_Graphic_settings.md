---
title: "Installation and Graphic settings?"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by JeppeV on 2007-08-12
Hey all!

I have some problems with installing ubuntu 64 bit.

It only loads when i change the graphicsetting to anything but VGA.
Then the ubuntu logo is shown, where the bar bounces back and forth. When its done, it shows the underscore thing in upper left corner. Suddenly my keyboard starts to blink, and the screen goes black.
Do you guys have any idea of what could be wrong? 

I'm really looking forward to trying Ubuntu, have heard so many great things about it,

Thanks:)

-Jeppe

---

### Post by Pumalite on 2007-08-12
Lets start from the basics: did you do md5sum of iso, burn at 4x, check for corruption of CD before install? What are you installing?: Post your specs, so we can help you better.

---

### Post by JeppeV on 2007-08-12
Hey, and thanks for replying.

I dont know what md5 mean? I burned the iso with alcohol , 16 x. I can't test the cd, it crashes the same way.
My setup is : amd athlon 64 3000+, Radeon x800gto , 1500 ram(approx)

ill try burning the cd in 4 x, and try to look after the md5 thing you talked about

Thanks:)

Jeppe

---

### Post by Pumalite on 2007-08-12
[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)

---

### Post by JeppeV on 2007-08-12
Hey! I dont have any SHN files, i just downloaded the iso from the page. I tried to run the md5sum.exe, but it only shows a prompt for a split secund.
What am I missing?

Thanks again:)

Ps: I use Alcohol 120%

---

### Post by Pumalite on 2007-08-12
I don't use Windblows, so, I couldn't tell you. Here you have Linux info.[http://www.gnu.org/software/textutils/manual/textutils/html_node/textutils_21.html](http://www.gnu.org/software/textutils/manual/textutils/html_node/textutils_21.html)

[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)

---

### Post by JeppeV on 2007-08-12
Okay, thanks anyway.

Anyone else? It's really annoying:D I'm really looking forward to Ubuntu!

---

### Post by Pumalite on 2007-08-12
I advise you to download and use the Alternate CD for the installation: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box below the green sign that says: 'Start Download'.

---

### Post by JeppeV on 2007-08-12
Hey again!
I installed Ubuntu, no problem at all.
BUT when I try to boot up from my hd, the black screen is back again. It seems that Ubuntu is loading, since my keyboard leds starts to blink a few times.

Do yo have any suggestions, that might solve this problem?

Thanks:)

Jeppe

---

### Post by Pumalite on 2007-08-12
Do you end up with a command line? If no, try: Ctrl+Alt+F1. If you get a command line, try this: sudo dpkg-reconfigure -phigh xserver-xorg. Say yes to most defaults. Choose 'vesa' as your driver.

---

### Post by JeppeV on 2007-08-12
Hey! The ctrl + alt + F1 didn't work, so i booted up in recoverymode , and got to the prompt that way.
Is that ok?
I typed in the command you posted,and got this: "Warning: Overwriting possibly-customized configuration File; backup in /etc/x11/xorg.conf. (alot of numbers)

I dont know what that means, but I sure hope you do!

again, thank you very much for taking the time to help me:)

Jeppe

---

### Post by Pumalite on 2007-08-12
Go ahead and do what I told you. Overwrite the file.

---

### Post by JeppeV on 2007-08-12
Boy.. this is akward. How do I do that? as far as I can see, the command doesn't give me a choice, just another"underscore""

---

### Post by Pumalite on 2007-08-12
The command should give you a graphical interface where you choose what I told. Most defaults are OK.

---

### Post by JeppeV on 2007-08-12
Hmm. it doesn't. Weird. Do you have any idea why? any other suggestions is more than welcome!

---

### Post by JeppeV on 2007-08-13
Bump! :confused:

---

### Post by JeppeV on 2007-08-13
bump-ti:)

---

### Post by JeppeV on 2007-08-13
bump-ti-bump

---

### Post by Pumalite on 2007-08-13
At the end of configuring xserver, you have to type 'startx' at the command line.

---

### Post by JeppeV on 2007-08-13
I'm not sure I understand. Like this? sudo dpkg-reconfigure -phigh xserver-xorg startx `? It doesn't work, as far as I can see
I'm sorry for being so noobish, i've never tried linux, at all.

---

### Post by Pumalite on 2007-08-13
If the other command didn't work; try this: sudo dpkg-reconfigure  xserver-xorg.

---

### Post by LurkerLito on 2007-08-13
> **JeppeV said:**
> I'm not sure I understand. Like this? sudo dpkg-reconfigure -phigh xserver-xorg startx `? It doesn't work, as far as I can see
I'm sorry for being so noobish, i've never tried linux, at all.

2 separate lines.
first do:
sudo dpkg-reconfigure -phigh xserver.org

the above reconfigures the xserver settings

then do:
startx

this will start the xserver.

----

I am having a similar problem so I guess I'll post here. I can't boot into Feisty on my new Quad core rig, but have no issues with getting into the system through the recovery console. I haven't done the dpkg reconfigure command yet, but have a question regarding ctrl+alt+F1. Regardless of how the xserver is configured, shouldn't  ctrl+alt+F1 always work? I ask because it doesn't work at all for me. 

I also booted to recovery mode and started gdm (remember I haven't done the reconfigure command yet so the settings should be the same as regular booting) and the login window comes up fine. But when I go and press ctrl+alt+f1 I am presented with a black screen and no way to get back to the xserver window (ctrl+alt+f7 or any ctrl+alt+f# combination). The only recourse is to press ctrl+alt+del. So it doesn't seem to sound like a xerver config problem, but I could be wrong.

---

### Post by JeppeV on 2007-08-13
Hey, it worked, sort of. The gui started and I chose Vesa as my driver. Then I rebooted, and still got the error thing. hmm
a new dialogue opened: Failed to start the x  server. It is likely that it's not set up correctly. Would you like to view the x server output to diagnose the problem?"

I pressed yes, and now it shows a lot of numbers, and the graphics is very messed up. Weird

---

### Post by JeppeV on 2007-08-13
bump

---

### Post by jim_p on 2007-08-13
To do an md5 sum in windows. dowload and place md5sum.exe in your windows directory so that the os will instantly find it. Then, in order to avoid changing directories and stuff, put your .iso file in C:
and type these in a DOS prompt

```
cd / (this will get you to c: from anywhere)
md5sum name-of-file.iso
```

Wait a few seconds, and a 20+ string of numbers and letters will appear.
Compare this to the server's md5sum to see if it matches


ps. In order to find md5sum.exe, google it!

---

### Post by jimhaddon on 2007-08-13
I really do not think you're ready for ubuntu yet.. keep practicing with Windows. If you cant even md5 something, or even reasearch and implement it you really need more experience

---

### Post by JeppeV on 2007-08-13
> **jimhaddon said:**
> I really do not think you're ready for ubuntu yet.. keep practicing with Windows. If you cant even md5 something, or even reasearch and implement it you really need more experience

Well. It seems that the iso is OK. 

what do you mean by practice? I do consider myself an experinced windows user, and all the advices above doesn't seem to work.

Thanks:)

Jeppe

---

### Post by JeppeV on 2007-08-13
Update: I tried the command (again) and got this error: "Fatal server error:
AddScreen/screeninit failed for driver 0"

XIO: Fatal IO error 104 (connection reset by peer) on X server ":0.0" atfter 0 requests (0 known processed) with 0 events remaining.

Suggestions?

Edit: This too: set VBE Mode Failed!

---

