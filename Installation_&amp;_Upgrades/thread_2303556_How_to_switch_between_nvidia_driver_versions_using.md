---
title: "How to switch between nvidia driver versions using the proprietary GPU drivers ppa"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by snarkyCoder on 2015-11-19
Yesterday I installed a nvidia GeForce GTX 960 GPU I used the Proprietary GPU Drivers PPA that was release this year.
I installed the version 355 like this:
```

sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt-get update && sudo apt-get install nvidia-355

```


I want to switch to the 352.63 version which is the most recent. 
Which would be the steps to remove the 355 and then install 352?
Can i just sudo apt-get autoremove nvidia-355 and then install the nvidia-352?

---

### Post by QDR06VV9 on 2015-11-19
> **snarkyCoder said:**
> Yesterday I installed a nvidia GeForce GTX 960 GPU I used the Proprietary GPU Drivers PPA that was release this year.
I installed the version 355 like this:
```

sudo add-apt-repository ppa:graphics-drivers/ppa

sudo apt-get update && sudo apt-get install nvidia-355

```


I want to switch to the 352.63 version which is the most recent. 
Which would be the steps to remove the 355 and then install 352?
Can i just sudo apt-get autoremove nvidia-355 and then install the nvidia-352?
Yes you can use command line but I would suggest this
```
sudo apt-get remove nvidia*
```
Then Reboot and run
```
sudo apt-get install nvidia-352
```
And Again reboot.

---

### Post by Bashing-om on 2015-11-19
snarkyCoder; Hello

Yeah, I see that Nvidia recommends the 352 version driver for that card .
From terminal ( at the login screen key combo ctl+alt+F1 ) execute:
```

sudo service lightdm stop ## for the unity desktop ##
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way##
sudo apt-get purge nvidia*
sudo apt-get install nvidia-352
sudo nvidia-xconfig ##just cheap insurance to make sure the config file gets rebuilt##

```

Reboot the system for the change to take effect:
```

sudo shutdown -r now

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by snarkyCoder on 2015-11-19
> **runrickus said:**
> -

> **Bashing-om said:**
> -


I didn't get to see your answers before doing this:

I seleceted the 352.63 from the additional drivers, applied the changes and restarted the pc. Everything is fine. 
Is this way as good as the others?

[ATTACH=CONFIG]265682[/ATTACH]

---

### Post by Bashing-om on 2015-11-19
snarkyCoder; Hey: Sure:

> 
applied the changes and restarted the pc. Everything is fine. 
Is this way as good as the others?

All that is important is that it works -> all is fine .
Our way was just to make sure the system was clean prior to installing a new driver .. Most times "Additional Drivers" does a good job of the clean up .
It there had of been problems, the errors would have been generated to the terminal for inspection.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-11-19
> **Bashing-om said:**
> snarkyCoder; Hey: Sure:


All that is important is that it works -> all is fine .
Our way was just to make sure the system was clean prior to installing a new driver .. Most times "Additional Drivers" does a good job of the clean up .
It there had of been problems, the errors would have been generated to the terminal for inspection.
[INDENT][INDENT]all's well that ends well
[/INDENT]
[/INDENT]


Could not have put it better myself.
Thanks Old Friend

---

### Post by snarkyCoder on 2015-11-20
> **Bashing-om said:**
> -

> **runrickus said:**
> -


Thanks a lot guys!! :D

---

