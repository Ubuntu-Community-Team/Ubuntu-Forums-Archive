---
title: "WiFi LED won't light up after upgrading to 8.04 from 7.10 on Dell Inspiron 6400"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by qedx on 2008-04-27
I upgraded my install yesterday and everything seems to work fine except for the WiFi LED, and the Fn-F2 key used to turn the WiFi on and off. Everything else works fine, WiFi is always on.
```
$ lspci | grep -i wireless
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

**Solution:**
> **steveneddy said:**
> Try installing the backports for Hardy.


```
sudo apt-get install linux-backports-modules-hardy-generic

```

and then restartThis worked for me :)

**Explanation:**
> **dasunst3r said:**
> This is a confirmed bug, as seen here: [https://bugs.launchpad.net/linux/+bug/176090](https://bugs.launchpad.net/linux/+bug/176090) .  The driver for the Intel PRO/Wireless 3945 has been changed from *ipw3945* to *iwl3945*.  To be honest with you, it does take a while to get used to the fact that the LED is off, but at least the wireless works well, yes?

---

### Post by ajesh on 2008-04-27
I have the same problem

---

### Post by gardara on 2008-04-27
I have the same problem on my dell m1210 xps

---

### Post by ztirffritz on 2008-04-27
I have a similar problem.

---

### Post by Edmund0Dantes on 2008-04-27
Same here with a Dell 9400

---

### Post by sotema on 2008-04-27
Same problem on HP Pavillon DV9650

---

### Post by EricDB on 2008-04-27
> **gardara said:**
> I have the same problem on my dell m1210 xps

Yeah, me too.  Same deal on the m1210.

---

### Post by Onesimus on 2008-04-27
Me too.  I have a DELL 6400, but my Wifi LED never lit under Gutsy - so no change here.

---

### Post by andreimatei on 2008-04-27
Me too. Dell Inspiron 6400. The led used to work in Gutsy...

---

### Post by EricDB on 2008-04-27
I booted back into 7.10 to verify that the light is working.  It's the same driver in both 7.10 and 8.04:

$ lspci |grep -i wireless
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by steveneddy on 2008-04-27
Try installing the backports for Hardy.


```
sudo apt-get install linux-backports-modules-hardy-generic

```

and then restart

---

### Post by EricDB on 2008-04-27
> **steveneddy said:**
> Try installing the backports for Hardy.


```
sudo apt-get install linux-backports-modules-hardy-generic

```

and then restart

Thanks for the suggestion.  Your profile suggests you know what you're talking about...would you mind explaining very briefly what that does and what other consequences it may have?

---

### Post by dasunst3r on 2008-04-27
This is a confirmed bug, as seen here: [https://bugs.launchpad.net/linux/+bug/176090](https://bugs.launchpad.net/linux/+bug/176090) .  The driver for the Intel PRO/Wireless 3945 has been changed from *ipw3945* to *iwl3945*.  To be honest with you, it does take a while to get used to the fact that the LED is off, but at least the wireless works well, yes?

---

### Post by qedx on 2008-04-27
Thanks. I installed the backports and the LED and the Fn-F2 key combo to toggle the WiFi works now. Not quite the same as it used to under gutsy where it'd blink while negotiating with the access point, but it works.

---

### Post by steveneddy on 2008-04-27
> **EricDB said:**
> Thanks for the suggestion.  Your profile suggests you know what you're talking about...would you mind explaining very briefly what that does and what other consequences it may have?

Ah, young Padiwan. I wonder what in my profile suggests that I know what I'm talking about? Maybe my bean count? Word of advise. Just because you have a large bean count doesn't mean lots of knowledge, just lots of forum posts. 

Thanks for asking the question, though.

The hardy backports give another software source that is approved and developed by the Ubuntu people but not put into the regular release because everyone may not need it.

There are no consequences to running software that come from Ubuntu.

I got the answer here

[http://ubuntuforums.org/showthread.php?p=4775217#post4775217](http://ubuntuforums.org/showthread.php?p=4775217#post4775217)

and from reading the bug reports.

I had the same issue, also, which is why I knew the answer. New releases of Ubuntu have been buggy since the beginning. I have been running Ubuntu since 5.04 and believe me, it's getting better. 

Sorry, not preaching, but just be careful about some folks on the forums. Some people will tell you to download this and do that. It's good that you asked, and again, thank you. 

Great places to look for support besides these forums:

[Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

You can go to the URL and change the last word to Gutsy to get a longer guide. Very good info. There may be some good advice on the Gutsy guide for the time being.

[Google]("http://www.google.com/")

[help.ubuntu.com]("https://help.ubuntu.com/")

************************

Search the forums before you post a question. Chances are that we've answered the question before.

Good luck and enjoy Ubuntu!

:popcorn:

---

### Post by EricDB on 2008-04-27
> **steveneddy said:**
> Ah, young Padiwan. I wonder what in my profile suggests that I know what I'm talking about? Maybe my bean count? Word of advise. Just because you have a large bean count doesn't mean lots of knowledge, just lots of forum posts. 

No, but you've been thanked 47 times.  And thanks again for the extra info.

(Make it 48!)

---

### Post by sotema on 2008-05-04
After installing linux-backports-modules-hardy-generic i got my led working but the wireless interface will connect to any lan  only if the switch used to activate the i/f is set to on at boot time, otherwise if i switch it to on with the system booted up no wireless signal is detected. I must remove and reinsert the iw3945 module to get the i/f running.  So i prefer having the opportunity to switch on/off the interface regardless the led and removed the backports.

---

### Post by paul higginbotham sr on 2008-05-07
my wifi light is on but no wireless on my e1505. Huge trial so far to get it working piece by piece, not just the driver, but the firmware for the wireless, must try that backport thing, but with my disappearing synaptic repos, I dont know if they are there.

---

