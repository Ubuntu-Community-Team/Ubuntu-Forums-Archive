---
title: "It is supposed to be this difficult!?"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by yomero2k2 on 2006-12-23
Hi everyone. I have been trying for the past 3 days to succesfully install Kubuntu and Xubuntu and I am at my wits end. This is a Compaq Presario (5006US) with a Intel Celeron ™ 766 MHz processor, 192 mb ram, and a Direct AGP 3D Graphics with up to 11 MB video memory. My problems lies after everything is supposedly done being installed. I get the message that says to take out the disc and reboot so it can load it up. The loading window appears and the progress bar finishes, the screen goes blank to where the desktop I assume is supposed to load and then nothing. This is the same scenario for both Kubuntu and Xubuntu. I am trying 6.10. I've also tried doing some research on my own and Im thinking maybe its a graphic card problem? I would appreciate any help in resolving this matter. Please dont make me install Windows ME on it! Thanks in advance!

---

### Post by Lord Illidan on 2006-12-23
Did the Live CD work?

---

### Post by yomero2k2 on 2006-12-23
I havent tried that. I just downloaded the alternate CDs and ran the text mode installations. Is that something I should try?

---

### Post by Lord Illidan on 2006-12-23
> **yomero2k2 said:**
> I havent tried that. I just downloaded the alternate CDs and ran the text mode installations. Is that something I should try?

No, I suggested the live cd because I thought that you had installed via the live cd, in which case you would have already seen the graphics problem.

Now, what make is your graphics card?

Also, can you boot up from failsafe to a terminal?

EDIT : Also, no it is not supposed to be that difficult but if your hardware is unsupported or v. old, then problems can be expected sometimes.

---

### Post by Lord Illidan on 2006-12-23
Yomero, are you fluent in Linux and the terminal?

If I told you to edit your /etc/X11/xorg.conf file in the terminal and change the driver to "vesa" would you know how to do it , or should I give further examples?

EDIT : Let me get you started:

1. From the bootup menu, choose failsafe.
2. You will then be taken to a DOS like terminal.
3. Now type in nano /etc/X11/xorg.conf
4. Scroll down to Section "Device"
5. Change the driver to "vesa"
6. To exit nano press CTRL + X, then press y to save.

---

### Post by yomero2k2 on 2006-12-23
Ok, I was able to follow those directions and change that value. This time, I get the message "Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem" In terms of the video card, I found on the compaq.com website that it is a Direct AGP 3D Graphics. This was given to me a week ago because a friend upgraded to a new computer. Did I change the wrong value?

---

### Post by Lord Illidan on 2006-12-23
> **yomero2k2 said:**
> Ok, I was able to follow those directions and change that value. This time, I get the message "Failed to start the X server. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem" In terms of the video card, I found on the compaq.com website that it is a Direct AGP 3D Graphics. This was given to me a week ago because a friend upgraded to a new computer. Did I change the wrong value?

Um "vesa" should theoretically set up everything.

Direct AGP 3D graphics covers a lot of things...What I want is a brand name, like NVIDIA/ATI/INTEl.

The solution would either be buy a cheapo graphics card, which will probably work better than what was already in there. An FX5200 would work nice, and wouldn't be a burden on the hardware.

---

### Post by yomero2k2 on 2006-12-23
I believe it's intel. I was hoping to avoid having to put any money into this system but I will look into that now then. Thanks for your help, it was greatly appreciated!

---

### Post by bulldog on 2006-12-23
You can try to let ubuntu repair xorg.conf.
```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

Type this in your console in recovery mode and see what happens.

---

### Post by yomero2k2 on 2006-12-23
Thanks for the tip. The computer no longer gives a "failed to start x sever message".. Unfortunately, it does still bring up the blank black screen after loading. I appreciate your input! I will keep trying though so if anyone else has any ideas I am definitely ready to try them. Thanks!

---

### Post by studiesrule on 2006-12-23
You could try a similar thing as what bulldog said, but it is manual:
sudo dpkg-reconfigure xserver-xorg
Then chose the vesa driver from there. It shouldn't give a different result from changing the driver name to vesa, but maybe you'll find some option in there that clicks?

---

### Post by yomero2k2 on 2006-12-23
Yea, it did give the same result changing it to vesa from within there. I wish I knew a bit more so I could play with those options but being  a complete noob to this, I'm not sure where I would even begin tweaking to get the desired results. Maybe I just need to save whatever I can from the machine and junk it. Thanks for your input though!

---

