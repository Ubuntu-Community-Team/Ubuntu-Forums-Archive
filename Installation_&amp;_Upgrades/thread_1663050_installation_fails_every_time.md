---
title: "installation fails every time"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by Alexarm on 2011-01-09
Hi, I recently decided to install ubuntu netbook remix 10.10 to my Toshiba NB200. I was using windows and I wanted to completely erase them. I burned the USB, I followed every single instruction the site had, and even though the installation seemed to work, and a message to reboot my computer appeared  at the end, the installation finally fails. When I reboot, the only thing I get is a black screen with an underscore at the top left corner. I tried the installation four to six times and even tried older versions as well but all I get is the black screen. What do you suggest?

---

### Post by Rubi1200 on 2011-01-09
Hi and welcome to the forums :)

What are the full specifications for the netbook?

From the LiveUSB, choose to try not install and then post the results of the following information (use the terminal; Applications > Accessories > Terminal)

```
sudo parted -l
```
Lowercase L not 1

and the results of the boot info script linked at the bottom of my post (instructions included).

Thanks.

---

### Post by iamyiannis on 2011-01-09
> **Rubi1200 said:**
> Hi and welcome to the forums :)

What are the full specifications for the netbook?

From the LiveUSB, choose to try not install and then post the results of the following information (use the terminal; Applications > Accessories > Terminal)

```
sudo parted -l
```Lowercase L not 1

and the results of the boot info script linked at the bottom of my post (instructions included).

Thanks.

Hi,

I am having similar issues with a toshiba p205 laptop.

I try to install Ubuntu 10.10 and it reaches the information screen asking about me. I fill it in, the files load and nothing happens. Ie the forward button stays inactive.

Any suggestions?

---

### Post by Rubi1200 on 2011-01-09
Hi and welcome to the forums iamyiannis :)

Not really a similar problem, but I can hopefully help.

At the who are you screen the username cannot contain an uppercase letter.

For example;

Your name: John Smith

User name: Not John but john

Also, make sure the password meets the minimum requirements.

Hope that helps.

---

### Post by iamyiannis on 2011-01-09
> **Rubi1200 said:**
> Hi and welcome to the forums iamyiannis :)

Not really a similar problem, but I can hopefully help.

At the who are you screen the username cannot contain an uppercase letter.

For example;

Your name: John Smith

User name: Not John but john

Also, make sure the password meets the minimum requirements.

Hope that helps.

Thanks for that. Damned semantics!

Will give it a try tomorrow.

Thank you.

Good night from NSW Australia.

---

### Post by Rubi1200 on 2011-01-09
Good night and good luck with the install :)

---

### Post by Alexarm on 2011-01-10
Hey Rubi1200, yesterday not even the try mode was working so i decided  to try and install the 10.04 version, and the installation was  successful!! The only problem is that now i don't have either sound or mic. When I use extra speakers the sound works but I would like to fix them as well. Sorry to disturb you but i have absolutely no idea what to do. :)

---

### Post by dino99 on 2011-01-10
with synaptic (system admin synaptic) install gnome-alsamixer, then set your prefs (applications sound&video alsamixer)

look at: system pref sound, to know if the sound hardware is well identified

---

### Post by Alexarm on 2011-01-10
> **dino99 said:**
> with synaptic (system admin synaptic) install gnome-alsamixer, then set your prefs (applications sound&video alsamixer)

look at: system pref sound, to know if the sound hardware is well identified

The sound now works perfectly but i still have no microphone. When I try to look at system pref sound all i get is a "Waiting for sound system to respond" message on the screen

---

### Post by 0N3 on 2011-01-10
Under sound preferences Hardware Tab have you the Internal Audio set to Analog output or analog duplex?

---

### Post by Alexarm on 2011-01-10
> **0N3 said:**
> Under sound preferences Hardware Tab have you the Internal Audio set to Analog output or analog duplex?


As i said I only get a waiting for sound system to respond message and now it started making an annoying loud beep that stops when i mute the internal from the  GNOME ALSA Mixer. 
Also since the sound started working the Fn+3 and Fn+4 which control the sound stopped working. I am completely lost   :confused:

---

### Post by 0N3 on 2011-01-10
[http://ubuntuforums.org/showthread.php?t=1495061](http://ubuntuforums.org/showthread.php?t=1495061)

Check that out let me know if it works

---

### Post by Alexarm on 2011-01-10
> **0N3 said:**
> [http://ubuntuforums.org/showthread.php?t=1495061](http://ubuntuforums.org/showthread.php?t=1495061)

Check that out let me know if it works

I did this, I also rebooted after the log out and log in again didn't  work but I still get the same error.

---

### Post by Alexarm on 2011-01-10
Someone posted to follow the part A to solve  the problem. Shall I try it?  : 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

