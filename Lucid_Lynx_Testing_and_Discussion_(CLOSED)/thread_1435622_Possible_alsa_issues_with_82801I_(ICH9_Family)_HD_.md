---
title: "Possible alsa issues with 82801I (ICH9 Family) HD Audio Controller"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mykrob on 2010-03-21
I have an Asus K50IJ laptop, the hardware specifications from lshw output are attached.

This laptop worked fine with Karmic, but in Lucid Beta 1, I am having issues with the audio. If i increase the volume from a low level, around what appears to be 25%, the audible sound level increases to maximum. Subsequent presses increase the volume slider, but audible volume remains unchanged. This process reverses itself for decreasing the volume.

I am able to duplicate this problem using alsamixer. I find it interesting that with my master front all the way down, volume is still up. Increasing any one slider seems to affect multiple sliders, whereas in Karmic, all sliders responded as they should and I had proper volume control.

Not sure what information I can provide to help. I'd like to file a bug report, but am unsure what is actually causing the problem.

Would like some assistance formulating a proper bug report to help get this resolved.

Thanks,
-myk

---

### Post by mykrob on 2010-03-23
Bump

---

### Post by yelo3 on 2010-03-23
Might I ask you a thing?
open a terminal and run alsamixer
Then put the master volume to 0% using the down arrow key.
You will see that over the bar there is a value called dB gain.
Please report all values with a volume step of 10%.
I have (note that my setup is buggy too, but in a different way)
 0%   -48,00
11%   -42,75
20%   -38,25
30%   -33,75
41%   -28,50
50%   -24,00
61%   -18,75
70%   -14,25
80%   -9,75
91%   -4,50
100%  0,00

---

### Post by mykrob on 2010-03-23
Hard to explain how it works here..

Running alsamixer but then using the laptop volume control yields this..

Volume all the way down provides:
Master Front: 00
PCM: 00
Front: 00

Next, I press the volume up key one time, and alsamixer yields:
Master Front: 00
PCM: 98
Front: 60

One more press up yields:
Master Front: 00
PCM: 98
Front:88

One more press up yields:
Master Front: 6
PCM: 98
Front: 100

One more press yields:
Master Front: 23
PCM: 98
Front: 100

Next press:
Master Front: 35
PCM: 98
Front: 100

Next press:
Master Front: 45
PCM: 98
Front: 100


and so on. Bear in mind that by the second press, the volume output is audibly maxed out, so even though the sliders are moving in alsamixer, the audible volume remains the same,.

---

### Post by lidex on 2010-03-23
Try this section "Volume range anomalies" of this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and report back.

---

### Post by mykrob on 2010-03-23
Thanks for the assist. I installed the alsa backports module, or however its worded, and it is working as normal now.

Thank you again.
-myk

---

### Post by lidex on 2010-03-23
Good work. Bad hat ;)

---

### Post by mykrob on 2010-03-23
You mean the avatar? Its "Dumb Donald" from Fat Albert and the Cosby Kids :)

---

### Post by mykrob on 2010-03-28
I wanna re-open this one for further troubleshooting. As of the past several days, things are back to problematic again :(
It may be due to the alsa backports modules not being updated..

Any ideas?

Thanks,
-myk

---

### Post by lidex on 2010-03-28
Same issue as before?

---

### Post by mykrob on 2010-03-28
yessir, exactly the same:)

---

### Post by lidex on 2010-03-28
Did you install karmic backports or lucid?

---

### Post by mykrob on 2010-03-28
lucid backports. Attempted uninstalling just in case, i get the same results either way. Looks like alsa was upgraded, but the backports were not. If i attempt to run an update in terminal, it advises that the lucid alsa backports are being help back.

---

### Post by lidex on 2010-03-28
When the updates are held back, there's a reason for it. Give it some time and try again. Did you upgrade alsa to the latest version via the upgrade script or is it the lucid repo version?

---

### Post by mykrob on 2010-03-28
everything has been done through the repositories.

---

