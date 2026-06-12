---
title: "nvidia drivers just won't install."
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by roker on 2009-12-10
I'm dual booting xp and karmic on my pc atm and have recently installed karmic.
my issue is that whenever i go into hardware drivers and attempt to install the nvidia drivers for my 9500 regardless of what drivers i attempt to install (version 173 and version 185) the installing window will automatically jump to quarter way done and then hang there doing nothing, my experiences with installing things into linux would normally lead me to believe that because its below 50% its downloading, however my connection is stable and installing anything using the synaptic package manager or the ubuntu software center is a breeze.

---

### Post by spcwingo on 2009-12-10
Have you tried envyng?

---

### Post by roker on 2009-12-10
never knew it existed, i apt-got it and ran it in text mode and attempted to install 185
it started at 50% downloaded and spammed the console with this

```
[===================================50.0%                                      ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 76, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required

```

---

### Post by spcwingo on 2009-12-10
> **roker said:**
> never knew it existed, i apt-got it and ran it in text mode and attempted to install 185
it started at 50% downloaded and spammed the console with this

```
[===================================50.0%                                      ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 76, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required

```

Sorry, I don't have that script on my install (I'm still on Hardy), so I have no point of reference...BTW, when you say that you ran it from text mode do you mean that you dropped to the console or ran it in a terminal emulator?

---

### Post by roker on 2009-12-10
> **spcwingo said:**
> BTW, when you say that you ran it from text mode do you mean that you dropped to the console or ran it in a terminal emulator?

uh I opened up the terminal and typed envyng -t then popped in the relevent numbers when it displayed options in the terminal.

---

### Post by presence1960 on 2009-12-10
When you installed envyng did you install all 3 packages? They are:

envyng-core
envyng-qt
envyng-gtk

Once all 3 are installed open a terminal and run envyng -t

---

### Post by spcwingo on 2009-12-10
> **roker said:**
> uh I opened up the terminal and typed envyng -t then popped in the relevent numbers when it displayed options in the terminal.

What I would do is hold CTRL+ALT then press F1.  This will drop you to the console.  From there log in and run these commands:

```
sudo /etc/init.d/gdm stop
```

followed by envyng -t

Then just follow the on-screen instructions.  I never could get the driver installed through "Hardware Drivers" to work either, but in my case I did just as I described above and they are working perfectly now.  I truly hope it works for you too.

---

### Post by roker on 2009-12-10
well I followed both of your instructions and to no avail it still supplied me with the same error message and the download still started at 50% (in console that is). :(

I'm starting to think karmic doesn't like me very much.

---

### Post by spcwingo on 2009-12-11
You can try to reinstall envyng b/c it sounds like there is something wrong with the python script "packagemanager.py".  To do that just run this command:

```
sudo apt-get remove --purge envyng-core && sudo apt-get install envyng-core
```

---

### Post by streetfi8er on 2010-01-06
i too am facing exactly the same problem , but in my case, enving is hanging at 62.5% , anyone with  a solution???:confused:

---

### Post by CaptConan on 2010-01-19
I have a similar problem except I have an ATI card. After hearing that Envyng could handle all my graphics drivers I jumped at the chance. I had originally installed the linux drivers right from ATI's website, but moving windows around on the desktop became very choppy, as if there were no drivers installed at all. SO i used Envyng to uninstall those ATI drivers and then tried to install the new drivers using envyng. From the gui version, it sits at 50% progress bar and does nothing. From console, I get the same error as above: Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 76, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi

I tried to reinstall the python script, to no avail. What is going on here?

---

### Post by Krovas on 2010-04-17
> **CaptConan said:**
> I have a similar problem except I have an ATI card. After hearing that Envyng could handle all my graphics drivers I jumped at the chance. I had originally installed the linux drivers right from ATI's website, but moving windows around on the desktop became very choppy, as if there were no drivers installed at all. SO i used Envyng to uninstall those ATI drivers and then tried to install the new drivers using envyng. From the gui version, it sits at 50% progress bar and does nothing. From console, I get the same error as above: Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 76, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi

I tried to reinstall the python script, to no avail. What is going on here?

A big fat pain in the ***. Count me in as another accelerated-graphics-challenged Karmic user.

---

### Post by cryptotheslow on 2010-04-17
For my NVidia GTS 250 on karmic I downloaded the v190.53 driver from the NVidia site. (There is a newer v195.36.15, but I haven't tried it yet).

Switch to a terminal (Ctrl-Alt-F1) - login then stop gdm, run the downloaded installer with sudo sh, start gdm before switching back to it (Ctrl-Alt-F7). You may need to run the nvidia-xconfig utility from a terminal prompt to update your xorg.conf settings.

---

