---
title: "Display Problem after installing"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by Wrkcncanter on 2006-05-24
I'm very new to Ubuntu, and I have no idea where to type that in, so could you please spell out exactly how to solve the problem?

It's basically the same thing as the guy in "Installing Problems =(" who posted earlier: 

I'm using a Dell desktop pc pentium II

I've finished installing and configuring (eveything execpt the network which I skipped). Now when I turn it on, it goes up to the brown splash screen where says "ubuntu" and has a progress bar and modules that are loading. The only thing that fails is the clock syncronization. After it finishes though, random horizontal white line segments flash on a black screen for about 2 seconds and then the little light on the monitor turns yellow instead of green, and you can't see anything. It makes a konga drum noise, and then stops. If I press enter it makes more drum noises. If I press the power button, it says "login username:" except when I try typing the password, only some of the keys work. Then it turns off.

Could someone give me a step by step thing to try?
Thanks

---

### Post by nalmeth on 2006-05-25
here's what to do:
when you hear the drum's (that is GDM, the login manager BTW) hit CNTL-ALT-F2
type in the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
pick the vesa driver for video rather than the default you are offered, it didn't work.
pick defaults for the rest of the options, unless you know better.

---

### Post by Wrkcncanter on 2006-05-26
I did what you said
it asked me to login, I logged in as the user, and I didn't have enough priveleges. So I logged out and tried to login as root but it said "login incorrect" funny as it seems I couldn't find an answer on google for how to login as root.

---

### Post by Wrkcncanter on 2006-05-27
The computer's name is linuxLARRY. When I try that command it says: 

unable to lookup linuxLARRY via gethostbyname(

When I try typing "su" and put in my password, it says

su: authentication failure
Sorry

What should I do?

---

### Post by Wrkcncanter on 2006-05-30
Does anyone know what's going on?

---

