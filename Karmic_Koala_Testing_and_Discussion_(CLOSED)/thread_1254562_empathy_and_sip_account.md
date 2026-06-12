---
title: "empathy and sip account"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-08-31
i was quite surprised when i setup empathy with sipgate.co.uk and when you make a call it automatically pauses the music in rhythmbox and then resumes it when you hang up.

well impressed. also like the themes in emapthy currently using gonedark

---

### Post by wmsheep on 2009-09-06
Hmmm, sounds interesting.

Is there any sort of Howto available at all??

Mark

---

### Post by misfitpierce on 2009-09-07
I only saw the 4 themes built into empathy and I couldnt figure out what it was talking about on where exactly or what to put in empathy folder using adium themes or whatever. Very confusing.

---

### Post by mattduckman on 2009-09-07
yeah a howto would be nice. the fields in empathy aren't really that friendly ... hopefully that will change by release.

---

### Post by mattduckman on 2009-09-07
> **misfitpierce said:**
> I only saw the 4 themes built into empathy and I couldnt figure out what it was talking about on where exactly or what to put in empathy folder using adium themes or whatever. Very confusing.

that's kinda off topic, but the instructions are here [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

---

### Post by terry_gardener on 2009-09-07
what how to do you need. 
how to add themes already mentioned above. 
do you need how to get sipgate.co.uk working 

basically you create new sip account and then enter sip id followed by @sipgate.co.uk click the advanced button and enter the stun server. and then port id. thats it. 

see screenshot below.

---

### Post by wmsheep on 2009-09-07
Great, I`ll have a go at that later and get back with the results.

Thanks

mark

---

### Post by linusr on 2009-09-20
> **terry_gardener said:**
> i was quite surprised when i setup empathy with sipgate.co.uk and when you make a call it automatically pauses the music in rhythmbox and then resumes it when you hang up.

well impressed. also like the themes in emapthy currently using gonedark

how to add SIP account in empathy?

I don't see any option!!:(

---

### Post by tretle on 2009-09-20
> **linusr said:**
> how to add SIP account in empathy?

I don't see any option!!:(

Install telepathy-sofiasip

---

### Post by linusr on 2009-09-20
thnx tretle :)

had to restart to SIP to be listed in empathy

---

### Post by linusr on 2009-09-20
thnx tretle :)

had to restart to SIP to be listed in empathy

---

### Post by rykel on 2009-09-21
Hey,

Empathy with SofiaSIP was able to accept incoming calls BUT could someone please help me here:

[LIST=1]
[*]How to I dial a number? (ie. dialpad)
[*]How do I activate my microphone? (tried all options in Sound Preference)
[/LIST]

---

### Post by Tich666 on 2009-09-21
> **rykel said:**
> 
[*]How do I activate my microphone? (tried all options in Sound Preference)
[/LIST]

Start "alsamixer" in terminal, press <tab> so you get to the capture options. Then make sure the microphone levels are at 100% at the input source is configured with your microphone.
In Karmic the "System>Pref.>Sound" Dialogue also has an option for mic boost etc.

Good luck with getting the mic to work.. took me months to figure it out for my laptop. :P

---

### Post by terry_gardener on 2009-09-21
to dial a number is quite strange 

click chat - new conversation, under account select sip account and then type number in field below (contact id), click call.

---

### Post by lighty14 on 2009-09-21
My mic works fine in sound recorder but doesn't seem to work with empathy. Suggestions?

---

### Post by Joe_Bishop on 2009-09-21
Suggestions? Empathy sucks, they didn't do any progress in VOIP since 2007, only regressions.

---

### Post by cassidy on 2009-09-21
Are you using Karmic? Lot of sound issues have been fixed with latest pulseaudio.

---

### Post by jpeddicord on 2009-09-21
> **Joe_Bishop said:**
> Suggestions? Empathy sucks, they didn't do any progress in VOIP since 2007, only regressions.

I like your use of constructive criticism.

---

### Post by linusr on 2009-10-20
> **Joe_Bishop said:**
> Suggestions? Empathy sucks, they didn't do any progress in VOIP since 2007, only regressions.

SIP no longer works for me. Status is 'Connecting' for 30 secs and then 'Dis Connected'.

---

