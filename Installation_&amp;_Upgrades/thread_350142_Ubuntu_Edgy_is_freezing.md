---
title: "Ubuntu Edgy is freezing"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by Jonathan Métillon on 2007-01-31
Hi,

I just convinced my wife to get Linux on her laptop. It's a [Compaq N610c]("http://h18000.www1.hp.com/products/quickspecs/11382_na/11382_na.html") with a Belkin F5D6020 PCMCIA Wi-Fi card.

I installed Ubuntu Edgy with a burned i386 Desktop ISO as a dual boot: I keep a copy of Windows XP on a partition. All went fine. I installed the Wi-Fi card using ndiswrapper and [Realtek 8180]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#371") drivers. Fine too.

Now she can't use it because the system freeze randomly. She is just surfing the web and bam, freeze. I reviewed all logs using the System Log viewer. I spoted the point where it freezed and I can't see anything abnormal. 

How can I know what's causing this freeze? She's back to Windows for now :(

---

### Post by hal10000 on 2007-01-31
According to this thread [http://www.linuxquestions.org/hcl/showproduct.php?product=1348&cat=513](http://www.linuxquestions.org/hcl/showproduct.php?product=1348&cat=513)

you might either use the [COLOR="Red"]acpi=off[/COLOR] option in your /boot/grub/menu.lst or your mainboard might need a BIOS upgrade to enable acpi

---

### Post by Jonathan Métillon on 2007-02-02
Thank you hal10000!

My ROM version is F.1B 05/27/2004, 68P4F serie. It might need an update, but I've not yet found the BIOS files (ROMPaq) from the HP/Compaq website.

It would be curious that this is an ACPI issue because the freeze does not happen when going to sleep mode or else. But anyway I hope it will fix it :-)

I also found these ressources:

[http://ubuntuforums.org/showthread.php?t=332699](http://ubuntuforums.org/showthread.php?t=332699)
[http://lists.freebsd.org/pipermail/freebsd-current/2003-September/010017.html](http://lists.freebsd.org/pipermail/freebsd-current/2003-September/010017.html)
[http://laptop.bsdgroup.de/freebsd/index.html?action=show_laptop_detail&laptop=124](http://laptop.bsdgroup.de/freebsd/index.html?action=show_laptop_detail&laptop=124)
[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=961967&admit=-682735245+1170431836825+28353475](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=961967&admit=-682735245+1170431836825+28353475)
[http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=969900&admit=-682735245+1170431730358+28353475](http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=969900&admit=-682735245+1170431730358+28353475)
[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=940390](http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=940390)


*--- Ubuntu Forums maintenance, so I've not been able to post this message. In between I found the ROMPaq [here]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=316666&prodTypeId=321957&prodSeriesId=316664&swLang=8&taskId=135&swEnvOID=1093#120") ---*

Successfully updated BIOS from 07/18/2003 to 05/27/2004 with Compaq Flash Wizard, under Windows XP (thanks I made a dual boot install).

Will now reboot and use Ubuntu a while, and see if it will freeze again.

---

### Post by Jonathan Métillon on 2007-02-02
Just froze.

Will now try acpi=off...

---

### Post by Jonathan Métillon on 2007-02-02
Frozen again.

What I did is opened a Terminal, then typed ***gksudo gedit /boot/grub/menu.lst*** and added the line ***acpi=off ***at the end of the file. Then rebooted. Was it right?

I don't see where in the BIOS setup I can make sure that ACPI is correctly activated.

Now what can I do?

---

### Post by Jonathan Métillon on 2007-02-02
Note that not as it's said [here]("http://www.linuxquestions.org/hcl/showproduct.php?product=1348&cat=513#review2"), my fan is working correctly at the moment the laptop freeze. So it does not seem to be an overheating issue.

I installed lm-sensor and will check what the temperature is when crashing.

---

### Post by Moulton on 2007-02-02
I've started experiencing random freeze-ups on my x86-based Ubuntu system.  Mine is mostly Dapper, with a few packages from outside the main distribution.

One thing I've noticed is that the freeze always occurs when I am typing a keystroke.  The machine can run indefinitely if I am not typing on the console.

Since I mostly type in application windows in the GUI interface, I can't say if the same problem would occur on one the VT console ttys.  The freeze-ups don't seem to care what application I'm in, as long as I'm actively typing at the keyboard.  It also happens if I am using the X-Server to connect to a remote host.

I tried booting up into older kernels, going backwards from 2.6.15-27 in steps to 2.6.15-23 (four available choices in all).  Made no difference.

There is nothing in the logs to indicate what the problem might be.  If I happen to be playing music, the sound card will also freeze on some audible musical note.  There is nothing to do but hit the hardware reset button.  Even pinging the machine from another host over the LAN fails to rouse an echo.

My current suspicion is that the bug is in the keyboard driver module, but that's only because I've ruled out just about everything else I can think of.

---

### Post by Jonathan Métillon on 2007-02-02
In the previous message I mentionned it is said to check if /proc is messed up. Well I don't know what to look for. Should I post the content of it so one can tell me if all is ok?

Also I needed to install sensors-applet from Universe to have visual feedback of the temperature going in the system.

For now I have 2 sensors and I can read 45°C for CE1A and 58°C for TZ1. I don't know which one is the CPU, but in both case it seems fairly normal for a laptop. My Vaio TX3 runs at 61°C.

While I was installing the package I noticed no freeze. I was not surfing. I'm sure the freeze does not come from Firefox because I tried Opera and the freeze happened too. But it might come from the Wi-Fi card activity?

Maybe the Realtek driver, designed for Windows and loaded with Ndiswrapper, is freezing the laptop?

---

### Post by Jonathan Métillon on 2007-02-02
To make sure this is the network activity that's freezing the system launched several concurrent ping to different websites. It runned like 1 hour, using other applications in the same time, and it did not freeze.

I really don't get it. I'll try again surfing with Firefox and Opera and see if it happens again.

---

### Post by Jonathan Métillon on 2007-02-02
> **Moulton said:**
> One thing I've noticed is that the freeze always occurs when I am typing a keystroke.  The machine can run indefinitely if I am not typing on the console.

Hi Moulton! I don't think your problem is related to mine, because my last freeze happened when I was doing nothing, or just moving the cursor.

You should start your own thread for this matter.

---

### Post by Jonathan Métillon on 2007-02-07
My wife now use the laptop daily but it still crashes randomly. But I got news : this happens only when browsing the web and a **page is loading**.

I could reproduce it with Firefox 2 and Opera. So I don't think it comes from the Gecko engine.

Any clue what could cause that freeze on our N610c?

Thanks! ):P

---

### Post by hal10000 on 2007-02-11
> Frozen again.

What I did is opened a Terminal, then typed gksudo gedit /boot/grub/menu.lst and added the line acpi=off at the end of the file. Then rebooted. Was it right?

I don't see where in the BIOS setup I can make sure that ACPI is correctly activated.

Now what can I do?
You must NOT put the [COLOR="Red"]acpi=off[/COLOR] option to the ebd of the file but to the end of your [COLOR="Red"]kernel[/COLOR] line.
It looks similar to this:
```

title           Ubuntu, kernel 2.6.19
root            (hd0,4)
[COLOR="Red"]kernel          /boot/vmlinuz-2.6.19 root=UUID=7f744eca-334e-431b-8c51-48febd70103b ro elevator=cfq[/COLOR]
initrd          /boot/initrd.img-2.6.19
savedefault
boot

```

no matter what your [COLOR="Red"]kernel [/COLOR]line looks alike, just put acpi=off (separated by a blank) to the end of the red colored line.

---

### Post by Jonathan Métillon on 2007-02-11
Thank you hal10000!

I solved the problem yesterday when I received a new PCMCIA Wi-FI card.

Some days ago the laptop fell and the Wi-Fi card was damaged. Somehow it still worked under Windows. Then I made the move to Ubuntu. And that's when it began to crash, so I though it was related to the OS, not the hardware.

Then we noticed that the crash happened only when loading lots of images on web pages, or flash movies, no matter what browser. And we also noticed later that it crashed also with Windows. That's when I suspected the damaged Wi-Fi card.

So I bought a Linksys [WPC54GS for 17 &#8364;]("http://www.ldlc.com/fiche/PB00022610.html") and replaced the dying Belkin F5D6020. The Linksys was easier to install because I used bcm43xx-fwcutter instead of ndiswrapper, as described [here]("https://help.ubuntu.com/community/WifiDocs/Device/LinksysWPC54GS-UK").

Since then, no freeze!

Thank you all for your help :guitar:

Note: my wife is all but a geek and find Ubuntu/GNOME super fast and super easy. She insisted to get the issue fixed so she can dump Windows XP for good. Also the 256 MB RAM where always eaten under Windows and was swapping like mad. But 256 seems fine under Ubuntu. Linux and FOSS rule! Hope **aMule** to be fixed soon with **protocol obfuscation** and then there will be no more Windows in our home. Die Vista!

---

