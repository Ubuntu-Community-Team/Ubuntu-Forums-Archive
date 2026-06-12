---
title: "pulseaudio and bluez really rocks!"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by xens on 2009-09-02
Hi there, I've been waiting so long for an easy way to use bluetooth audio devices with ubuntu (headset, speakers, ...).

Now I simply add the bluetooth device with the bluetooth-applet and connect it, then I can see the device in the sound applet and choose to stream the music trough it, all graphically ! without installing padev or other tweaking.

Sound is a bit jerky some times but it's really a great step forward!

Thanks a lot :guitar:

Romain

---

### Post by mapuo on 2009-09-02
yeah, it's really easy to connect audio devices now
my nokia bh-503 has play/pause, prev, next buttons so i had to add ```
uinput
``` in the ```
/etc/modules
``` to make them work
other than that i just turn the headset on to enjoy the sound :)

---

### Post by benmoran on 2009-09-02
Yeah, it's awesome. This is becoming a killer feature for me, and one of the reasons why Pulseaudio kicks ***.

---

### Post by Mr. Picklesworth on 2009-09-02
Oh, we have the new bluetooth applet now? (The one where you get the same menu with a left or a right click, instead of two different ones?)

About time, but yay! :)

---

### Post by 23meg on 2009-09-02
> **Mr. Picklesworth said:**
> Oh, we have the new bluetooth applet now? (The one where you get the same menu with a left or a right click, instead of two different ones?)

Yes, and that's one *killer feature*.

---

### Post by KillerKiwi on 2009-09-02
Hi, Im working on the next release of EarCandy.

I was wondering if you could tell me what the device name/description of your bluetooth headset appears as.. I'd like to add the option of switching all sound to bluetooth when it appears just like with USB devices

Cheers

---

### Post by nanog on 2009-09-02
Pulse audio definitely rocks...but only after manually turning up pcm using alsamixer for the 9th time this development cycle.

---

### Post by tlois on 2009-09-02
I had my bluetooth headsets working just great with karmic and was very excited.  But I had a printer problem that I needed to correct so downloaded daily live karmic yesterday and installed it.  Now when I right (or left!) click on the bluetooth icon and select "set up new device"  nothing happens.  I'm so sad.

Found this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/423090](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/423090)

And it worked. Yeah!

---

### Post by Mr. Picklesworth on 2009-09-02
> **23meg said:**
> Yes, and that's one *killer feature*.

Excellent! I've been jealous of Fedora because it has had the new gnome-bluetooth for two releases now. Many awesome leaps in functionality with that thing - especially the wizards upon connecting certain devices. A sane interface, to boot :)

---

### Post by jwssr on 2009-09-02
in response to # 7 in this thread.

Im using a motorolo s305....awesome bt headset.



i am using an hdmi cable to a 47 in monitor which has awesome sound.

my lspci shows...
VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B 

up until a week or so ago I could get sound from the azalia controller and also thru bt headset.

now,  using gnome alsamixer  and pavucontrol...the option for digital sound  thru azalia is missing....but the analog is very good and bt also works.

I cannot load the fglrx drivers for ati3200...as it fails to bring gdm...
this prevents me from running compiz.   ast the radeon driver does not support it...although I get 1920x1080 res..

I bring up the video stuff because I think that without the fglrx driver the sound does not work thru hdmi...hence no digital sound...

any thoughts?

---

### Post by andresmh on 2009-09-02
I don't have a bluetooth headset but this seems cool. Are you able to use the BT headset also to send audio? That is, can you use the BT headset as a mic?

---

### Post by Jay_Bee on 2009-09-03
somehow, when I connect the bluetooth headset, skype 2.1 Beta will automatically send sound to the headset while the rest of the sounds continue to go through the speakers, that's nice. Microphone on the headset works as well.

---

### Post by xens on 2009-09-03
> **andresmh said:**
> I don't have a bluetooth headset but this seems cool. Are you able to use the BT headset also to send audio? That is, can you use the BT headset as a mic?

Yeah the same way, I can select the input from the sound manager (bluetooth, internal speaker, ...)

I'll put some screenshots later

---

### Post by xens on 2009-09-04
> **KillerKiwi said:**
> Hi, Im working on the next release of EarCandy.

I was wondering if you could tell me what the device name/description of your bluetooth headset appears as.. I'd like to add the option of switching all sound to bluetooth when it appears just like with USB devices

Cheers

Hi KillerKiwi, I've got two bt headset:

Blueparrott Roadwarrior B250, shown as: **VXI B250** 
Sony-Ericsson, shown as: **HBH-PV705**

---

### Post by wilbur.harvey on 2009-09-06
I have the same problem, when I try to add a new device, nothing happens.

---

