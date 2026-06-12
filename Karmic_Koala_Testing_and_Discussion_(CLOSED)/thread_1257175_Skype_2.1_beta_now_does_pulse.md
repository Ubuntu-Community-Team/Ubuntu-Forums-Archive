---
title: "Skype 2.1 beta now does pulse"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-09-03
Get rid of your old skype and install the Beta it runs like a charm on my machine.

 [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

I use the intrepid version and it is smooth. Buit what I love most is the pulse support.

Other novelties include

* Skype’s SILK codec for outstanding quality with negligible bandwidth usage,

* HQ video support,

* PulseAudio support,

* SMS send support (*Sending SMS requires available Skype Credit),

* Contact groups,

* Contact labels, or tags, for easier contact organization,

* Chat window improvements (typing notification, message editing, s/geeky text/replacement/, new emoticons),

* Nicer contact list with mood messages and video capability icons,

* Nicer tray icon.

---

### Post by gnomeuser on 2009-09-03
it does pulse but it crashes when I try to start a test call, I think they still have work to do. Regardless I am looking forward to the ability to send text messages, it will save me a TON of money - a message to Brazil where my fiancée lives currently is around 50 cents - a couple of messages a day quickly adds up, skypes rates should cut that in half and allow me easier control of how much money I spend on this. 

Regardless it's still excessively costly, I did the calculation once currently it is 20 times as expensive as getting data from the Hubble space telescope. This for something that is send on the always present, control band which they have to keep open at all times - in other words a cost so insignificant it's a goldmine for the telcos.

---

### Post by vikrant82 on 2009-09-03
> it does pulse but it crashes when I try to start a test call

I think I had the same issue with the test call and as I remember it, I was using Mic 2 as my default Mic and switching it to Mic 1 fixed the issue.

---

### Post by Slug71 on 2009-09-03
> **gnomeuser said:**
> it does pulse but it crashes when I try to start a test call

Im affected by this too.

---

### Post by alexmurray on 2009-09-03
Make sure you uncheck the option to 'Allow skype to adjust my volume levels' otherwise Skype crashes pulseaudio when it starts a call.

---

### Post by Slug71 on 2009-09-03
> **alexmurray said:**
> Make sure you uncheck the option to 'Allow skype to adjust my volume levels' otherwise Skype crashes pulseaudio when it starts a call.

Thanks will try that. Thats exactly what i been getting.

---

### Post by morozsm on 2009-09-03
> **alexmurray said:**
> Make sure you uncheck the option to 'Allow skype to adjust my volume levels' otherwise Skype crashes pulseaudio when it starts a call.

It works perfectly for me!

---

### Post by gnomeuser on 2009-09-04
> **alexmurray said:**
> Make sure you uncheck the option to 'Allow skype to adjust my volume levels' otherwise Skype crashes pulseaudio when it starts a call.

My point was more that Skype has a bug, they have work to do. The user shouldn't need to go through a list of workarounds. That is what makes computers suck for average human beings and Skype should be ashamed of themselves.

---

### Post by aamukahvi on 2009-09-04
> **gnomeuser said:**
> My point was more that Skype has a bug, they have work to do. The user shouldn't need to go through a list of workarounds. That is what makes computers suck for average human beings and Skype should be ashamed of themselves.

It's a beta, no?

---

### Post by n3had on 2009-09-05
Hi i had issues with the webcam going green and fixed it with preloading

**sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so**

obviously i had to download the preload manager first. But now whenever i launch a terminal window 

```
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
n3had@n3had:~$ 

```

Anyone facing the same?

---

### Post by cszikszoy on 2009-09-05
> **gnomeuser said:**
> My point was more that Skype has a bug, they have work to do. The user shouldn't need to go through a list of workarounds. That is what makes computers suck for average human beings and Skype should be ashamed of themselves.

Actually, Skype doesn't have the problem. [ PulseAudio has the problem]("http://www.pulseaudio.org/ticket/638") and it'll be fixed in 0.9.16

---

### Post by alexmurray on 2009-09-06
Well its still a problem in Skype - it is sending invalid volume info which triggers an assertion in pulseaudio - so:

1. Skype should send valid not invalid volume info
2. Regardless, pulseaudio shouldn't assert() and die just because Skype sent it invalid info - which as you mention is fixed in git and is in 0.9.16-test7.

---

### Post by bobince on 2009-09-06
oooh, amd64 package! ...oh.

To be installed: ia32-libs. Ah well, maybe sometime next decade then?

---

### Post by xx58 on 2009-09-06
:rolleyes:I am from Estonia and I use Skype on first day, when it was made. It is made in Estonia.
Right now Skype Beta still rare, but when it will be STABLE version, then it will be very nice, [COLOR=Red]But [COLOR=Black]best is use old version Skype and you can install [COLOR=Red]SMS [COLOR=Black]function separately, witch I have some time. So, I have stable version, where everything works just great and SMS, witch works like charm.
[COLOR=Red]Skype 2.1 Beta [COLOR=Black]is nice. There is SMS function inside and not need SMS install separetly. Yes, but[COLOR=Red] BETA[/COLOR] [/COLOR][/COLOR]have problem with [COLOR=Blue]Voip Phone [COLOR=Black]or anything like Microfon, so best joice is wait little bit and when BETA coming stable, then it will be one step forward and then is the time to install [COLOR=Blue]Skype 2.1. [/COLOR][/COLOR][/COLOR]
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by gnomeuser on 2009-09-06
> **cszikszoy said:**
> Actually, Skype doesn't have the problem. [ PulseAudio has the problem]("http://www.pulseaudio.org/ticket/638") and it'll be fixed in 0.9.16

True, Pulseaudio definitely should have been handling of problems with clients. Say a client is doing something unexpected, there should be no way that should ever be able to crash PulseAudio. However if all programs treated unexpected inputs correctly, computing would be much less painful.. a man can dream... oh please make the hurting stop.

---

