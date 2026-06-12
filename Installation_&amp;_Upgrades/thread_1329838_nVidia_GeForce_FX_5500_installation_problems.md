---
title: "nVidia GeForce FX 5500 installation problems"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Jag8917 on 2009-11-17
Hi.

I want to set up my dual monitors but am having problems getting my second display to work.  I have an nVidia GeForce FX 5500 PCI graphics card.  I put it in my computer where it's nice and snug, then downloaded the drivers after booting.  The driver I downloaded was accelerated graphics driver version 173.  Now when I go to Administration then to NVIDIA X SERVER SETTINGS I get this message upon opening:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I am fairly new to Ubuntu.  What is being asked and how do I perform what was said above?

---

### Post by overdrank on 2009-11-17
Hi and welcome, what version of Ubuntu are you using?
You can find this under system, about Ubuntu. Did you install the nvidia drivers under system, administration, hardware drivers?

---

### Post by Jag8917 on 2009-11-17
> **overdrank said:**
> Hi and welcome, what version of Ubuntu are you using?
You can find this under system, about Ubuntu. Did you install the nvidia drivers under system, administration, hardware drivers?

I am using version 9.04.  And yes I installed the drivers from under system, administration, and hardware drivers.

---

### Post by Jag8917 on 2009-11-17
Actually, I was able to login as root.  I then went to the terminal and typed in 'nvidia-xconfig' like previously mentioned and nothing happened.

---

### Post by Jag8917 on 2009-11-18
No one knows?  Am I even on the right board?

---

### Post by notgoingbackto_ms on 2009-11-18
do LSPCI in terminal and see if FX5500 is listed

---

### Post by dhavalbbhatt on 2009-11-18
> **Jag8917 said:**
> I am using version 9.04.  And yes I installed the drivers from under system, administration, and hardware drivers.

Was this the only driver available to you? There are times when the system will prompt you to install drivers, but will have a couple of options, with one being the recommended option. Are these the recommended drivers? 

I also think the card that you are using is really old and maybe nVidia does not support the card anymore. If I remember right, these cards were supported by 169.xx version of nVidia drivers and we are now at 190.xx - so, its definitely been a while.

---

### Post by Jag8917 on 2009-11-18
> **dhavalbbhatt said:**
> Was this the only driver available to you? There are times when the system will prompt you to install drivers, but will have a couple of options, with one being the recommended option. Are these the recommended drivers? 

I also think the card that you are using is really old and maybe nVidia does not support the card anymore. If I remember right, these cards were supported by 169.xx version of nVidia drivers and we are now at 190.xx - so, its definitely been a while.

Yes, this was the recommended driver.  Maybe should I look for 169 and uninstall 173?

EDIT:  I looked for 169 but couldn't find it.  Another option I was presented with was 96.

---

### Post by Jag8917 on 2009-11-18
> **notgoingbackto_ms said:**
> do LSPCI in terminal and see if FX5500 is listed

I typed in LSPCI into the terminal and it said:

"bash: LSPCI: command not found"

---

### Post by overdrank on 2009-11-19
> **Jag8917 said:**
> I typed in LSPCI into the terminal and it said:

"bash: LSPCI: command not found"

Hi and do not use capital letters in the command ```
lspci
```
You may try the nvidia driver 96 to see if it works better.

---

### Post by Jag8917 on 2009-11-19
> **overdrank said:**
> Hi and do not use capital letters in the command ```
lspci
```You may try the nvidia driver 96 to see if it works better.
96 either doesn't work or I am not doing something right.

I also typed "lspci" into the terminal and the graphics card was listed:

"02:04.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)"

---

