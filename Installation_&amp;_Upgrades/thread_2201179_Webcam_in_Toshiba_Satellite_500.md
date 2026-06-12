---
title: "Webcam in Toshiba Satellite 500"
date: 2014-01-23
forum: Installation &amp; Upgrades
---

### Post by rhedil.gomez on 2014-01-23
Hello.
Good day.
I am new in using Ubuntu and I am very excited using this operating system. I did successfully installed Ubuntu on my Toshiba satellite 500 and works fine.
However, when I did tried a skype video call the video is a bit dark and then I remembered that in my windows os there is a web cam driver that will enable me to change and fix the brightness of the video.
My question is, is there a web cam driver for Toshiba satellite 500 that is compatible for Ubuntu?

Thank you in advance and I am looking forward to hear from you soon..

Regards,
Rhedil

---

### Post by papibe on 2014-01-23
Hi rhedil.gomez. Welcome to the forum ):P

Could you open a terminal, run these commands and post back its results?
```
lsusb

ls /dev/video

lsmod | grep video
```
Regards.

---

### Post by rhedil.gomez on 2014-01-23
Hello papilbe.
Thanks for the reply.

Here's the results when I ran the command in the terminal.

[ATTACH=CONFIG]249683[/ATTACH]

Please advise.
Thank you.

---

### Post by papibe on 2014-01-24
Thanks.

I believe I have the same webcam on my Toshiba laptop ;)

Install **guvcview** from the Software Center. There you can adjust several settings including brightness and contrast.

Make sure to adjust the settings while the webcam is not being used by other application (Skype may be open but not on a video call, or seeing the camera input in Skype's settings).

Hope it helps. Let us know how it goes.
Regards.

BTW: you can copy paste the text on the terminal using your mouse and mouse right click. It is more easier that taking a screenshot ;)

---

### Post by rhedil.gomez on 2014-02-03
Hello pabibe..
Thank you soo much for your help.. It did worked I downloaded guvcview and it worked like a charm :) Thank you..

I have another question and I need help.
I have an ipad mini and I want to connect it in my laptop.. However, I did connect it in my laptop it says something like this.

[ATTACH=CONFIG]250052[/ATTACH] 
I did already entered my ipad's password but still it won't work. I did even turn off the pass code it's still not working..
Can you help me with this please..
Thanks in advance..

Best regards,
Rhedil

---

### Post by mörgæs on 2014-02-03
The original problem is solved, so please mark the thread so. 
For the Ipad problem please open a new thread in the Apple forum.

---

### Post by Bucky Ball on 2014-02-03
> **mörgæs said:**
> The original problem is solved, so please mark the thread so. 
For the Ipad problem please open a new thread in the Apple forum.

^^^
This. The second support request has nothing to do with the title of the thread so can become confusing and misleading for future travellers as well as reducing your chances of getting support. ;)

---

