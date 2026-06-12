---
title: "no sound"
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by w3rt on 2009-05-14
Just upgraded to karmic koala from jaunty, as soon as i rebooted i had no sound, tried 3 different media players, tried flash in browser, nothing works, has anybody had any problems after upgrading?

---

### Post by chrismine on 2009-05-14
Same here - if I can get sound it is very soft - using Intel ALC833 on Asus P5K motherboard

---

### Post by w3rt on 2009-05-14
Iam using a cmedia 3878 card i get NO sound what so ever, not even soft

---

### Post by davideotape on 2009-05-14
Have you tried looking in gnome-alsamixer to see if the levels aren't down?

---

### Post by Gina on 2009-05-14
Same here - no sound - and I've tried everything I know without success.  I know this is being worked on and I wish the devs good luck.  Guess it's just a matter of waiting.

---

### Post by pferraro on 2009-05-14
Try this:

pulseaudio --kill
rm ~r ~/.pulse
rm ~/.pulse-cookie
pulseaudio --start

---

### Post by taavikko on 2009-05-14
Try messing with options model=x

```
ALC883/888
==========
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targs/MSI with 2-channel
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  auto		auto-config reading BIOS (default)
```

---

### Post by taavikko on 2009-05-14
As for anyone suffering from audio problems, specially on laptops,
/usr/share/doc/alsa-base/driver/ contains a lot of documentation to read.

You can use zcat to easily direct these files to more readable form
```
zcat /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz > Templates/HD-A-Models.txt

```

---

### Post by taavikko on 2009-05-14
just experienced this, 
Fixed by opening volume-applet->Volume-control-> Selecting pulseaudio playback and mute&unmute device, after that sound worked.

---

### Post by fifth on 2009-05-14
Anyone with no sound might want to check your user groups. I had this problem yesterday.

Check you are a member of;

* pulse
* pulse-access
* pulse-rt

[Edit] Unfortunately didnt work after a reboot, still a member of the above user groups but back to having no sound.

---

### Post by fifth on 2009-05-14
> **pferraro said:**
> Try this:

pulseaudio --kill
rm ~r ~/.pulse
rm ~/.pulse-cookie
pulseaudio --start

Thanks pferro. My earlier tip to check the user groups didnt work after a reboot :( Came home today and booted into a silent Koala.

Didn't realise PusleAudio stored settings in the user home folder. Your advise worked well :D.

Could the problem be booting between Jaunty and Karmic with the same user? has PusleAudio been upgraded and using different settings now?

---

### Post by freeman2000 on 2009-05-14
I'm having a similar problem, losing sound, but it comes back.  I'm running a dual Karmic - both Ubuntu (gnome) & Kubuntu (kde) on my laptop.  If I'm in gnome all is well - sound works from Rhythmbox, internet, etc. I then log out and go into KDE.  Again all is well -  I have sound in Amarok, internet, etc.  

However... when I shut down or log out of KDE, and try going back into gnome something is shutting down / muting my sound card.  The blue light for my speakers turns to orange.  I get back into gnome and I have no sound!  I then have to do a "restart" in gnome to get my sound back - the speaker light turns blue again.  And then once again everything works.  This has happened numerous times over the last day plus.  Don't know if it's a bug or just a freak thing.

---

### Post by Didius Falco on 2009-05-15
My sound was working fine, but now it's not working at all.

But judging from the updates I'm getting over the last day, I think it's because the devs are working on the sound. I've been getting some Pulse updates, and just about 10 minutes ago I received updates on the whole gstreamer0.10- series, including ones for pulse audio and alsa.

I've got to give them credit - the updates just keep rolling in...

Regards,

Didius

---

### Post by Dread Knight on 2009-05-26
> **pferraro said:**
> Try this:

pulseaudio --kill
rm ~r ~/.pulse
rm ~/.pulse-cookie
pulseaudio --start

Worked fine! Thanks!

---

### Post by jasballz on 2009-06-02
I also have no sound, but it was after I installed LAME to try to convert flv to mp3 in Karmic Koala working on it still no sound

It recognizes my card and the levels are up in alsamixer:

card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I'm on an Acer 4720z

ok the pulseaudio lines worked on me too!

:)

---

### Post by jasballz on 2009-06-02
nvm it was a temp. fix because now every time
I restart its no sound. :(
I'm going to find jaunty and install that

now that I restarted it doesn't seem to work, the fix

---

### Post by durand on 2009-06-02
> **pferraro said:**
> Try this:

pulseaudio --kill
rm ~r ~/.pulse
rm ~/.pulse-cookie
pulseaudio --start

Thanks, works great!

---

### Post by super.rad on 2009-06-02
Occasionally I have no sound but just have to unmute then log out and back in

---

### Post by Dread Knight on 2009-06-03
I removed everything related to pulseaudio and things are way better now for me (I'm using Kubuntu, so not really sure about Gnome, but KDE has phonon at least, which helps out with this kind of stuff).

---

### Post by cykotiktek on 2009-06-05
I have tried this but when i run the command rm ~r /.pulse it gives me the error 

rm: cannot remove `~r': No such file or directory
rm: cannot remove `/home/ghansen/.pulse': Is a directory

Still have no sound is there anything else that i can try?

> **pferraro said:**
> Try this:

pulseaudio --kill
rm ~r ~/.pulse
rm ~/.pulse-cookie
pulseaudio --start

---

### Post by taavikko on 2009-06-05
Please anyone, don't take the next few statements personally, it's for benefit for all.

I have to say, if basic understanding of simple commands is lost, please restrain yourself of using alpha software...

Using and testing alphas needs some basic knowledge.
We do offer help here, but that's counter-productive to explain users something trivial.

```
pulseaudio --kill; rm -r ~/.pulse; rm ~/.pulse-cookie; pulseaudio --start
```

There were errors in the command, ~ isn't for app options. - is.
Also made it oneliner.

---

### Post by cykotiktek on 2009-06-05
since i don't belong here i will format to jaunty thanks for your support

---

### Post by BwackNinja on 2009-06-06
rm -r, not rm ~r. its thinking of ~r as a file or directory, while -r is the command line option that means 'recursive' so it can delete directories and their contents.

---

### Post by Marko723 on 2009-06-06
Just realized my message doesn't belong here.  Sorry... forgot to look where I ended up in my global searching.

---

