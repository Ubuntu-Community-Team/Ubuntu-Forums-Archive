---
title: "No Screen error"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by bunnybash on 2007-07-27
I am trying to install Ubuntu 7.04 on my Asus A6J... 

Intel Core Duo
ATI X1600
1Gb 

Anyways i cannot even boot the live CD as it comes up with an error half way through saying that it cannot find a screen, which is really annoying because it is telling me this on a screen!!!

GDM error or something... man it is confusing...

I tried booting Gparted too, and it cannot find me a screen either... even after choosing the drivers and resolution... 

Any suggestions??

I really want to install Ubuntu Studio, but wanted to run the live CD first to make sure that everything worked...

HELP!!

---

### Post by Pumalite on 2007-07-27
Sounds like it doesn't like your monitor. What do you have. You might have to review your monitor's Manual and then edit your xorg file with the settings in the 'Monitor' Section. Do you have access to a command line? You might have to go the Alternate CD route if you don't.

---

### Post by Soybean on 2007-07-27
It's trying to start the graphical interface at that point... the Xorg definition of the word "Screen" is probably a little different from the definition you're used to. ;) A Screen is actually a combination of a "Device" (usually a video card) and a "Monitor" (which is an actual monitor -- this one is exactly what it sounds like).

So that error can come up if it improperly identifies your Monitor (as Pumalite suggested), or if it misidentified your video card or doesn't have a driver for it. Having an ATI card makes it more complicated, because the driver comes down to a choice between two bad options.

Alternate install is one good solution, although it's likely you'll still have some trouble getting things set up in the end. Another idea would be to look around the forums for other people having trouble with the same monitor or video card as you, and see what they came up with.

Good luck! :)

---

### Post by bunnybash on 2007-07-29
> **Soybean said:**
> It's trying to start the graphical interface at that point... the Xorg definition of the word "Screen" is probably a little different from the definition you're used to. ;) A Screen is actually a combination of a "Device" (usually a video card) and a "Monitor" (which is an actual monitor -- this one is exactly what it sounds like).

So that error can come up if it improperly identifies your Monitor (as Pumalite suggested), or if it misidentified your video card or doesn't have a driver for it. Having an ATI card makes it more complicated, because the driver comes down to a choice between two bad options.

Alternate install is one good solution, although it's likely you'll still have some trouble getting things set up in the end. Another idea would be to look around the forums for other people having trouble with the same monitor or video card as you, and see what they came up with.

Good luck! :)

Hmm

Well my screen is part of the laptop... so i can't really change it...

I have tried a few diff distro's all have the same problem, if that is what you mean by "alternative install"

i am really really really newb so please be gentle with me!!!

---

### Post by Pumalite on 2007-07-29
'Alternate CD? can be Ubuntu, Kubuntu or Xubuntu. It's a text mode of installation that avoids graphical interface problems:  Go to Ubuntu site, choose your flavor and when you are ready to download, check the box below the green sign that says 'Start Download?

---

### Post by bunnybash on 2007-07-29
> **Pumalite said:**
> 'Alternate CD? can be Ubuntu, Kubuntu or Xubuntu. It's a text mode of installation that avoids graphical interface problems:  Go to Ubuntu site, choose your flavor and when you are ready to download, check the box below the green sign that says 'Start Download?

what about ubuntu studio??  the reason i tried the ubuntu live CD was to see if everything worked so i could use ubuntu studio... ubuntu studio is what i am really after... that and creative/software freedom!

sorry for so many inane questions...

---

### Post by Pumalite on 2007-07-29
I'm not sure if an Ubuntu Studio Alternate CD exists. Dig around.

---

