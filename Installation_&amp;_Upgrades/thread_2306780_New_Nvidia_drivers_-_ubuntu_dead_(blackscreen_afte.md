---
title: "New Nvidia drivers - ubuntu dead (blackscreen after grub)"
date: 2015-12-18
forum: Installation &amp; Upgrades
---

### Post by docdoc2 on 2015-12-18
OK so i used autoremove to get some free space, but i noticed the cpu fan was much louder than before. I checked the "additional drivers" and saw in the menu that i could use a newer nvidia driver (proprietary, tested) i believe it was version nvidia-34x instead of 304 or so.But now after the grub, i get a black screen intead of a logon screen and i hear that nice problem-drum-sound of ubuntu. I can use tty1-6, but i have no clue what commands i need.Also, in the rescue mode of ubuntu the failsafe and dpkg repair do not do anything, just warns me it wants to mount the partitions and then ceases operation.Now back to windows but i need my ubuntu! Please help!(edit: cannot format the text)

---

### Post by oldos2er on 2015-12-18
What Nvidia device do you have? Were you using the nouveau drivers previously?

---

### Post by docdoc2 on 2015-12-18
Thanks. Nouveau drivers? I don't think so, only used 304. The card is a NVIDIA GeForce GT 630M

---

### Post by Bashing-om on 2015-12-18
docdoc2; Hello;

For that card I see that Nvidia recommends the 352 version for the driver .

What returns from terminal commands:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```

Depending then we issue the command to have the system install a graphic's driver .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]it it is hard
[INDENT][INDENT][INDENT]you are doing it wrong
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-12-18
Does recovery mode resume get you to a login screen and working desktop? As far as I am concerned Failsafe mode has been broken for a while. We get out of recovery mode by selecting resume. What happens then?

Does loading an earlier kernel load to a desktop?

Regards.

---

### Post by alex479 on 2015-12-18
I had this same issue and found that if before booting from grub, press e on the Boot Ubuntu option and edit its launch parameters to add nomodeset after quiet splash, and then you will be able to boot without a black screen.  In order to not have to do this manually each time, go edit /etc/default/grub to change the default parameters to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
And then it will use nomodeset for you automatically each time you boot, removing the black screen issue.
I've heard that the black screen issue doesn't occur if using VGA, but my gpu (GTX 980) only has DVI and HDMI ports, so this is a reasonable solution.

---

### Post by docdoc2 on 2015-12-21
ubuntu drivers list (cannot copy 'n paste)
304
352
340
340 -update
304 -update
346
352 -update


When i use recovery mode -> normal start -> login screen in horrible low resoultion and when trying to login, i get the login screen again (also with guest login)
grub + e ->nomodeset -> same in better solution

Please tell how go go back to the old driver by using tty. It would be nice to use the new driver but obviously it's impossible. Would it be bad to use purge nvidia* and do a reinstall?

---

### Post by oldfred on 2015-12-21
With nVidia, you have to purge, before installing any different version or from a different source. Almost best to not install directly from nVidia with .run file. Use standard drivers in repository or add a ppa for pre-configured newer drivers.

Did you use a ppa before?

If you cannot copy & paste, is Internet working. You need to be able to download new driver.

       #see details for version installed
sudo apt-cache policy nvidia*
dkms status

 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
      
 sudo apt-get update && sudo apt-get install nvidia-3xx

# I usually use nvidia-3xx-updates, where 3xx is newest available, if older card do not install newest version, check correct legacy version from nVidia.
If nVidia suggests 352, then that would be best for your system. The older versions are frozen as older cards do not have features newer driver supports. They may get bug fixes occasionally. But if newer card you want to use its newer features.
# While you're at it upgrade libvdpau & nvidia-settings

---

